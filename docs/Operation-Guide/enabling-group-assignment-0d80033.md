<!-- loio0d80033336474468bb64ef8aeb7e3dd8 -->

# Enabling Group Assignment

When provisioning users from source to target systems, in addition to replicating the user data, you can also assign them to groups in the target system. This works for standard provisioning with or without configured bulk operation on the target, and real-time provisioning.



<a name="loio0d80033336474468bb64ef8aeb7e3dd8__section_snd_mn5_fwb"/>

## Prerequisites

-   You have configured a SCIM-based target system which supports patch operation.

    -   To view the list of these systems, refer to [List of Properties](../list-of-properties-d6f3577.md) → `scim.support.patch.operation` → *System Type*.

    -   To enable the patch operation for each of these systems, refer to its specific property in [List of Properties](../list-of-properties-d6f3577.md) →*<system\_prefix\>* `.support.patch.operation`


-   The groups that you want to assign exist on the target system.




<a name="loio0d80033336474468bb64ef8aeb7e3dd8__section_mwx_mn5_fwb"/>

## Context

To enable the group assignment, you need to modify the target system transformation by adding a mapping under the user resource containing the following configuration parts:

-   **Condition** - Defines for which users the condition will apply. For example, all users with emails.

-   **Constant** - Holds the IDs of the groups in the target system. Currently, you can only identify groups by ID.

-   **targetVariable** - Specifies whether you want to assign users to groups or unassign users from groups.



<table>
<tr>
<th valign="top">

Assign Users to Groups

</th>
<th valign="top">

Unassign Users from Groups

</th>
</tr>
<tr>
<td valign="top">

This mapping will result in assigning all users with emails to two groups in a target system.

> ### Code Syntax:  
> ```
> {
>    "user":{
>       "mappings":[
>          
> <Existing transformation>
> 
> {
>             "condition":"($.emails EMPTY false)",
>             "constant":[
>                {
>                   "id":"00f8ab94-a732-48fa-9169-e51f87b8dcd5"
>                },
>                {
>                   "id":"01231139-4711-4a28-8f9d-6745843ef716"
>                }
>             ],
>             "targetVariable":"assignGroup"
>          }
>       ]
>    },
>    "group":{
>       "mappings":[
>          
> 
> ```



</td>
<td valign="top">

This mapping will result in unassigning all users with emails from two groups in a target system.

> ### Code Syntax:  
> ```
> {
>    "user":{
>       "mappings":[
> 
> <Existing transformation>
> 
> {
>             "condition":"($.emails EMPTY false)",
>             "constant":[
>                {
>                   "id":"006aeaea-3486-479e-8c65-eabd2868653e"
>                },
>                {
>                   "id":"00bbae67-6b9d-4f46-9306-6aad28c40861"
>                }
>             ],
>             "targetVariable":"unassignGroup"
>          }
>       ]
>    },
>    "group":{
>       "mappings":[
>          
> ```



</td>
</tr>
</table>

Groups which are assigned to users through the user resource are referred to as user managed groups. Following a successful provisioning, if the user managed groups are managed through the group resource, the assignments made through the user managed groups will be overwritten.

> ### Note:  
> If the group doesn't exist in the target system during user creation or update, the user provisioning fails.
> 
> If the group doesn't exist in the target system during user deletion, the user deletion succeeds.

If you want to remove the group assignments of a deleted user from the source system, you need to modify the target system transformation by adding a mapping under the user resource containing the following configuration parts:

-   **Constant** - Holds the IDs of the groups in the target system which will be updated. Currently, you can only identify groups by ID.

-   **targetVariable** - Use `"unassignGroup"` to specify that you want to unassign users from the defined groups.

-   **scope** - Use `"deleteEntity"` to define that the deleted user from the source system should be persisted in the target system.


```
{
    "constant": [
        {
            "id": "groupID"
        }
    ],
    "targetVariable": "unassignGroup",
    "scope": "deleteEntity"
}

```

This mapping will result in updating the assignments to the defined group in the target system.

When using the group unassignment for users that are deleted from the source system, these are the possible scenarios based on the system where the user was created and the value of the property `ips.delete.existedbefore.entities`:

-   When the user was provisioned from another system by the Identity Provisioning service or it was initially created in the target system and the property `ips.delete.existedbefore.entities` is set to `true`

    In this case only transformation mappings for the affected user containing scope `deleteEntity` are executed. This mapping could be used, for example, for disabling a user account in the target system. For more information, see [Transformation Expressions](../transformation-expressions-bb8537b.md) → `deleteEntity`.

    > ### Note:  
    > The update is executed via PUT or PATCH operation, based on the configuration of the property `*.support.patch.operation` in the target system.

-   When the user was initially created in the target system and the property `ips.delete.existedbefore.entities` is set to `false`, the group assignments of the user in the target system will be updated.

**Related Information**  


[Manage Transformations](manage-transformations-2d0fbe5.md "You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.")

[Transformation Expressions](../transformation-expressions-bb8537b.md "")

[**Blog Post**: Group Assignments Based on User Attributes – a Flexible Solution for Managing Conditional & Risk-Based Authentication and Much More](https://blogs.sap.com/2023/03/16/group-assignments-based-on-user-attributes-a-flexible-solution-for-managing-conditional-risk-based-authentication-and-much-more/)

