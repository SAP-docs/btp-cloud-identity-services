<!-- loio8376adbed2e94f04b99ec5cf01adf465 -->

# Transformation Variables

System variables specify particular attributes of the read and written entities. They help you map attributes between source and target transformations so that the entities are provisioned correctly to the target systems.

**Transformation Variables**


<table>
<tr>
<th valign="top">

Variable

</th>
<th valign="top">

Definition & Example

</th>
<th valign="top">

System Types

</th>
</tr>
<tr>
<td valign="top">

assignGroup

</td>
<td valign="top">

An optional variable, which enables you to assign groups to a user in the target system. It can be used for standard provisioning with or without configured bulk operation on the target, and real-time provisioning.

To enable the group assignment, you need to modify the target system transformation by adding a mapping under the user resource containing the following configuration parts:

-   **Condition** - Defines for which users the condition will apply. For example, all users with emails.

-   **Constant** - Holds the IDs of the groups in the target system. Currently, you can only identify groups by ID.

-   **targetVariable** - Specifies whether you want to assign users to groups or unassign users from groups.


> ### Example:  
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
> 
> This mapping will result in assigning all users with emails to two groups in a target system.

For more information, see [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

</td>
<td valign="top">

Target systems

</td>
</tr>
<tr>
<td valign="top">

entityIdSourceSystem

</td>
<td valign="top">

Mandatory for every read transformation \(in source and proxy systems\). It specifies which attribute of a read entity to be considered as a unique ID in the source system.

Use this mapping with caution, as it can overwrite the value of the ID returned by the source system.

> ### Example:  
> ```
> {
>   "targetVariable": "entityIdSourceSystem",
>   "sourcePath": "$.name"
> }
> ```



</td>
<td valign="top">

-   Source systems
-   Proxy systems



</td>
</tr>
<tr>
<td valign="top">

entityIdTargetSystem

</td>
<td valign="top">

Mandatory for every write transformation \(in target and proxy systems\). It specifies which attribute of a written entity to be considered as a unique ID in the target system. This variable is defined by the target system according to the system response during entity creation, or is read from the Identity Provisioning database during entity modification or deletion.



> ### Example:  
> ```
> {
>   "scope": "deleteEntity",
>   "sourceVariable": "entityIdTargetSystem",
>   "targetVariable": "entityIdTargetSystem",
>   "functions": [
>     {
>       "type": "decode",
>       "algorithm": "base32",
>       "skipPadding": true
>     },
>     {
>       "type": "toString"
>     }
>   ]
> }
> ```



</td>
<td valign="top">

-   Target systems
-   Proxy systems



</td>
</tr>
<tr>
<td valign="top">

entityBaseLocation

</td>
<td valign="top">

Mandatory only for read transformations in proxy systems. It contains the proxy application URL featuring the entity type endpoint:

**`https://ipsproxy<proxy_provider_account>-<consumer_account>.<neo_landscape>:443/ipsproxy/api/v1/scim/<system_ID>/Users`**

> ### Example:  
> ```
> {
>   "sourceVariable": "entityBaseLocation",
>   "targetVariable": "entityLocationSourceSystem",
>   "targetPath": "$.meta.location",
>   "functions": [
>     {
>       "type": "concatString",
>       "suffix": "${entityIdSourceSystem}"
>     }
>   ]
> }
> 
> ```



</td>
<td valign="top">

Proxy systems

</td>
</tr>
<tr>
<td valign="top">

entityLocationSourceSystem

</td>
<td valign="top">

Mandatory only for read transformations in proxy systems. It contains the proxy application URL featuring the SCIM 2.0 resource endpoint for an entity:

**`https://ipsproxy<proxy_provider_account>-<consumer_account>.<neo_landscape>:443/ipsproxy/api/v1/scim/<system_ID>/Users/<user_ID>`**

> ### Example:  
> ```
>   "sourceVariable": "entityBaseLocation",
>   "targetVariable": "entityLocationSourceSystem",
>   "targetPath": "$.meta.location",
>   "functions": [
>     {
>       "type": "concatString",
>       "suffix": "${entityIdSourceSystem}"
>     }
>   ]
> }
> 
> ```



</td>
<td valign="top">

Proxy systems

</td>
</tr>
<tr>
<td valign="top">

currentDate

</td>
<td valign="top">

An optional variable, which contains the current date, in format: *yyyy-MM-dd HH:mm:ss.SSS*

You can configure this variable by using property `ips.date.variable.format`, according to the [Java Class DateTimeFormatter](https://docs.oracle.com/javase/8/docs/api/java/time/format/DateTimeFormatter.html).

> ### Example:  
> ```
> {
>     "targetPath": "$.PersonalDetails.ValidityPeriod.StartDate",
>     "sourceVariable": "currentDate",
>     "functions": [
>         {
>             "type": "manipulateDate",
>             "targetDateFormat": "yyyy-MM-dd"
>         }
>     ]
> }
> 
> ```



</td>
<td valign="top">

-   Source systems
-   Target systems
-   Proxy systems



</td>
</tr>
<tr>
<td valign="top">

unassignGroup

</td>
<td valign="top">

An optional variable, which enables you to remove the group assignments of a deleted user from the source system. In that case, you need to modify the target system transformation by adding a mapping under the user resource containing the following configuration parts:.

-   **Constant** - Holds the IDs of the groups in the target system which will be updated. Currently, you can only identify groups by ID.

-   **targetVariable** - Use `"unassignGroup"` to specify that you want to unassign users from the defined groups.

-   **scope** - Use `"deleteEntity"` to define that the deleted user from the source system should be persisted in the target system.


> ### Example:  
> ```
> {
>     "constant": [
>         {
>             "id": "groupID"
>         }
>     ],
>     "targetVariable": "unassignGroup",
>     "scope": "deleteEntity"
> }
> 
> ```
> 
> This mapping will result in updating the assignments to the defined group in the target system.

When using the group unassignment for users that are deleted from the source system, these are two possible scenarios based on the system where the user was created and the value of the property `ips.delete.existedbefore.entities`. For more information, see [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

</td>
<td valign="top">

Target systems

</td>
</tr>
</table>

**Related Information**  


[Transformation Types](transformation-types-1a92c56.md "Learn about the types of JSON transformations needed for the provisioning jobs.")

[Transformation Examples](transformation-examples-901c759.md "The following examples explain how transformations work.")

[Transformation Expressions](transformation-expressions-bb8537b.md "")

[Transformation Functions](transformation-functions-0cdac7c.md "")

[Transformation Editors](transformation-editors-9ea770b.md "Identity Provisioning provides graphical and JSON text editor for managing provisioning system transformations.")

