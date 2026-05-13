<!-- loio885320dfd56d45af9a1837256565e089 -->

# Configure Technical User Authorizations

Configure granular access control for the technical users in the SAP Cloud Identity Services administration console.



<a name="loio885320dfd56d45af9a1837256565e089__prereq_yys_bdw_fzb"/>

## Prerequisites

You have enabled the authorizations based on policies option in the admin console for SAP Cloud Identity Services. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).



## Context

> ### Restriction:  
> This feature is relevant only for the Administration Console application.

> ### Remember:  
> If your tenant has been migrated to a new region, you need to configure your authorizations based on policies again.

Tenant administrators can assign specific authorizations to end users or administrators, allowing them to create, read, update, delete technical users, or a combination of these operations in the administration console of SAP Cloud Identity Services. The distribution of responsibilities enables the authorized users \(not necessarily administrators\) within your organization to concentrate on their specific areas of access and expertise.

The following authorization policies related to technical users are available in the administration console application under the package name *technical\_users*. These policies are non-editable, meaning you can't add or delete rules \(i.e., restrictions\). You can only assign users to the authorization policy.


<table>
<tr>
<th valign="top">

Authorization Policy

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`CREATE_TECHNICAL_USERS` 

</td>
<td valign="top">

Allows users only to create technical users.

</td>
</tr>
<tr>
<td valign="top">

`READ_TECHNICAL_USERS` 

</td>
<td valign="top">

Allows users only to view the technical users and the information about them. The user with this policy can see the tile *Technical Users* in the administration console for SAP Cloud Identity Services.

</td>
</tr>
<tr>
<td valign="top">

`UPDATE_TECHNICAL_USERS` 

</td>
<td valign="top">

Allows users only to update the technical users.

</td>
</tr>
<tr>
<td valign="top">

`DELETE_TECHNICAL_USERS` 

</td>
<td valign="top">

Allows users only to delete the technical users.

</td>
</tr>
<tr>
<td valign="top">

`MANAGE_TECHNICAL_USERS` 

</td>
<td valign="top">

Allows users to manage the technical users. The `MANAGE_TECHNICAL_USERS` policy combines the authorizations from the other policies: `CREATE_TECHNICAL_USERS`, `READ_TECHNICAL_USERS`, `UPDATE_TECHNICAL_USERS`, and `DELETE_TECHNICAL_USERS`

</td>
</tr>
</table>



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Under *System Applications*, choose the *Administration Console*.

4.  Under the *Authorization Policies* tab, search for the authorization policy and select it.

    You can type the policy name or package in the search field, filter the policy by package type, or choose it directly from the list.

    The policy names follow this convention: *<action\>*\_*<functionality\>*\_*<resource\>*, for example: *MANAGE\_TECHNICAL\_USERS*

5.  Under the *Assignments* tab, choose *Add* and add a user.

    To assign a user to multiple authorization policies, repeat steps 4 and 5 as necessary. Alternatively, you can combine multiple policies by creating a new policy of type *Customer Package* and assign the user to all included policies at once. For more information, see [Combine Authorization Policies](combine-authorization-policies-1a69414.md).




<a name="loio885320dfd56d45af9a1837256565e089__result_j4y_qdl_bdc"/>

## Results

When an authorization policy is assigned to a user, a user group named after the policy is also assigned to that user. For example, if a user is assigned the `MANAGE_TECHNICAL_USERS` policy, they become members of the following user group: `technical_users - MANAGE_TECHNICAL_USERS`



## Next Steps

Administrators with assigned technical user authorizations can create and manage the technical users. See [Managing Technical Users](managing-technical-users-fd1a636.md).

**Related Information**  


[Configure User Authorizations](configure-user-authorizations-424b64c.md "Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.")

[Configure Group Authorizations](configure-group-authorizations-7a09cad.md "Configure granular access and control over the groups in the administration console of SAP Cloud Identity Services.")

[Configure Application Authorizations](configure-application-authorizations-01cff18.md "Configure granular access and control over the applications in the administration console of SAP Cloud Identity Services.")

[Configure Provisioning Authorizations](configure-provisioning-authorizations-a8f8e31.md "Configure granular access control for the Identity Provisioning systems and logs in the SAP Cloud Identity Services administration console.")

