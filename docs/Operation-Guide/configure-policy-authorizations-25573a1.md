<!-- loio25573a1d09804a7b9546d100f5566f63 -->

# Configure Policy Authorizations

Configure granular access and control over the authorization policies in the administration console of SAP Cloud Identity Services.



<a name="loio25573a1d09804a7b9546d100f5566f63__prereq_yys_bdw_fzb"/>

## Prerequisites

-   You have enabled the authorizations based on policies option in the admin console for SAP Cloud Identity Services. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).

-   You need the following authorization policies to fully use Authorization Management in the *Authorization Policies* tab. See [Assign Authorization Policies](assign-authorization-policies-eac8e5e.md).


    <table>
    <tr>
    <th valign="top">

    Authorization Policies
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `READ_POLICIES` 
    
    </td>
    <td valign="top">
    
    Read the authorization policies
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `READ_GROUPS` 
    
    </td>
    <td valign="top">
    
    Read the policy assignments
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `READ_USERS` 
    
    </td>
    <td valign="top">
    
    Display users on the *Assignments* tab
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `READ_APPLICATION` 
    
    </td>
    <td valign="top">
    
    Read the application
    
    </td>
    </tr>
    </table>
    



## Context

> ### Restriction:  
> This feature is relevant only for the Administration Console application.

> ### Remember:  
> If your tenant has been migrated to a new region, you need to configure your authorizations based on policies again.

Once it's enabled, it may take up to 60 seconds before the administrator can see the *Authorization Policies* tab when accessing the administration console application. Under the *policies* package the following base policies are visible: `CREATE_POLICIES` , `DELETE_POLICIES`, `MANAGE_POLICIES`, `READ_POLICIES`, and `UPDATE_POLICIES`. You can add users to these policies so that they can have the rights these policies give.

You can restrict access on the basis of the base policies or you can use a custom policy, restricting the authorization policies on the basis of the `policy.name` and `policy.applicationId` attributes.

**Policy Attributes**


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

`policy.name`

</td>
<td valign="top">

The name of the authorization policy.

</td>
</tr>
<tr>
<td valign="top">

`policy.applicationId`

</td>
<td valign="top">

The ID of the application which is the unique identifier of that application configured in SAP Cloud Identity Services.

</td>
</tr>
</table>



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Under *System Applications*, choose the list item for the administration console.

4.  Under the tab *Authorization Policies*, select an authorization policy with the *policy* package.

    > ### Note:  
    > Type the name or package in the search field, filter the names or packages, or choose the authorization policy from the list.
    > 
    > If you don’t have a created authorization policy in your list, you can create one. For more information, see [Create an Authorization Policy](create-an-authorization-policy-897fc30.md).

5.  Expand the authorization policy you want to assign to an administrator.

6.  Choose *Add* on the *Assignments* tab.

7.  Select the user you want to assign and choose *Add*.


**Related Information**  


[Configure User Authorizations](configure-user-authorizations-424b64c.md "Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.")

[Configure Technical User Authorizations](configure-technical-user-authorizations-885320d.md "Configure granular access control for the technical users in the SAP Cloud Identity Services administration console.")

[Configure Group Authorizations](configure-group-authorizations-7a09cad.md "Configure granular access and control over the groups in the administration console of SAP Cloud Identity Services.")

[Configure Application Authorizations](configure-application-authorizations-01cff18.md "Configure granular access and control over the applications in the administration console of SAP Cloud Identity Services.")

[Configure Provisioning Authorizations](configure-provisioning-authorizations-a8f8e31.md "Configure granular access control for the Identity Provisioning systems and logs in the SAP Cloud Identity Services administration console.")

