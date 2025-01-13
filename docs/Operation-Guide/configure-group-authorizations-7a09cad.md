<!-- loio7a09caddb16f41e4bb9544385c96f31a -->

# Configure Group Authorizations

Configure granular access and control over the groups in the administration console of SAP Cloud Identity Services.



<a name="loio7a09caddb16f41e4bb9544385c96f31a__prereq_yys_bdw_fzb"/>

## Prerequisites

You have enabled the authorizations based on policies option in the admin console for SAP Cloud Identity Services. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).



## Context

> ### Restriction:  
> This feature is relevant only for the Administration Console application.

Once it's enabled, it may take up to 60 seconds before the administrator can see the *Authorization Policies* tab when accessing the administration console application. Under the "groups" package the following base policies are visible: `CREATE_GROUPS` , `DELETE_GROUPS`, `MANAGE_GROUPS`, `READ_GROUPS`, and `UPDATE_GROUPS`. You can add users to these policies so that they can have the rights these policies give.

> ### Note:  
> The Manage Groups authorization overrides all "groups" package policies. If you want to configure access to the groups based on policies, you must remove the Manage Groups authorization. For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

You can restrict access on the basis of the base policies or you can use a custom policy, restricting the groups on the basis of the `group.name`, `group.displayName`, `group.type`, or `group.applicationId` attributes.

**Group Attributes**


<table>
<tr>
<th valign="top">

Attributes

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`group.name`

</td>
<td valign="top">

The name of the group.

</td>
</tr>
<tr>
<td valign="top">

`group.displayName`

</td>
<td valign="top">

The display name of the group.

</td>
</tr>
<tr>
<td valign="top">

`group.type`

</td>
<td valign="top">

The type of the group. The supported values are:

-   `userGroup`
-   `authorization`
-   `deepLinkActivationPermission`



</td>
</tr>
<tr>
<td valign="top">

`group.applicationId`

</td>
<td valign="top">

The ID of the application which is the unique identifier of that application configured in Cloud Identity Services.

</td>
</tr>
</table>



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Under *System Applications*, choose the list item for the administration console.

4.  Under the tab *Authorization Policies*, you can choose the following options:


    <table>
    <tr>
    <th valign="top">

     
    
    </th>
    <th valign="top">

     
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Use base policy**
    
    </td>
    <td valign="top">
    
    1.  Filter the policies by the "groups" package.

        > ### Note:  
        > This limits the policies to the following: *CREATE\_GROUPS* , *DELETE\_GROUPS*,*MANAGE\_GROUPS*, *READ\_GROUPS*, and *UPDATE\_GROUPS*.

    2.  Select a policy from the list.
    3.  Choose the *Add* button.
    4.  Select the user or users and choose Add.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Use custom policy**
    
    </td>
    <td valign="top">
    
    1.  Select a custom authorization policy.

        > ### Note:  
        > If you don’t have an authorization policy in your list, you can create a restriction policy using the `groups.DELETE_GROUPS`, `groups.READ_GROUPS`, `groups.UPDATE_GROUPS` parameters. For more information about how to create a custom authorization policy, see [Create an Authorization Policy](create-an-authorization-policy-897fc30.md).

    2.  Choose the *Edit* button.
    3.  To customize the rules of the authorization policy, choose *Rules*.
        1.  For each `USE` statement of the selected authorization policy, add a `RESTRICT` condition with `Value`, choose one of the available attributes, an operation, and enter a value.

        2.  Save your changes.

    4.  To assign user to this policy, choose the *Assignments* tab and add users from the list.

        > ### Restriction:  
        > If the user is a tenant administrator you must remove the *Manage Groups* role from that user, otherwise they won't be able to see and have control \(read, update or delete\) over the groups for this policy.

    5.  Save your changes.

        > ### Note:  
        > Now the assigned users can see and have control over the groups with that are specified in the custom policy.



    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Configure User Authorizations](configure-user-authorizations-424b64c.md "Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.")

[Configure Application Authorizations](configure-application-authorizations-01cff18.md "Configure granular access and control over the applications in the administration console of SAP Cloud Identity Services.")

[Configure Provisioning Authorizations](configure-provisioning-authorizations-a8f8e31.md "Configure granular access control for the Identity Provisioning systems and logs in the SAP Cloud Identity Services administration console.")

