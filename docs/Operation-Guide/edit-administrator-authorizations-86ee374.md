<!-- loio86ee37423f8945a1898faff1e6308756 -->

# Edit Administrator Authorizations

As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.



## Prerequisites

To edit tenant administrators' authorizations, you must be assigned the Manage Tenant Configuration role.



## Context

To edit an administrator's authorizations, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Administrators* tile.

    This operation opens a list of all administrators in alphabetical order.

    > ### Note:  
    > The list also includes the SAP BTP system, which by default has authorizations to set up the trust with Identity Authentication.

3.  Choose the administrator name whose authorizations you want to edit.

    > ### Tip:  
    > Type the name of the administrator in the search field to filter the list items.

4.  Edit the administrator authorizations as required.

    > ### Note:  
    > To be a tenant administrator, a user must be assigned one or more of the following roles:
    > 
    > **Administrator Roles**
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > Authorization
    > 
    > 
    > 
    > </th>
    > <th valign="top">
    > 
    > Description
    > 
    > 
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Applications
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to configure the applications via the administration console.
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Corporate Identity Providers
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to configure the identity providers via the administration console.
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Users
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to manage, import, and export users via the administration console.
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Read Users
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to retrieve user data and import users via the administration console and the SCIM REST API of Identity Authentication.
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Groups
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to create, edit, and delete groups via the administration console.The tenant administrator can also assign authorization policies.
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Tenant Configuration
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to manage tenant configuration and authorization assignment to users. Tenant administrators with that role can add additional roles to themselves or to other administrators.
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Identity Provisioning
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to configure identity provisioning. The tenant administrator is granted the main IPS\_ADMIN role.
    > 
    > 
    > 
    > </td>
    > </tr>
    > </table>
    > 
    > If you remove all authorizations, the user or system will no longer be an administrator, and the name will be removed from the list on the left.
    > 
    > > ### Remember:  
    > > Removing all authorizations does not delete the user from the user data base of Identity Authentication. For more information about how to delete a user, see [Delete Users](delete-users-bbfaf5f.md).
    > 
    > You cannot remove the Manage Tenant Configuration role from your own user.

5.  Save your changes.

    If the operation is successful, the system displays the message ***Tenant administrator <name of tenant administrator\> updated***.


**Related Information**  


[List Administrators](list-administrators-c79a5c6.md "As a tenant administrator, you can list the administrators and their authorizations in the administration console for SAP Cloud Identity Services.")

[Add Administrators](add-administrators-bbbdbdd.md#loiobbbdbdd3899942ce874f3aae9ba9e21d "As a tenant administrator, you can add new administrators in the administration console for SAP Cloud Identity Services.")

[\(Beta\) Configure Authorizations Based on Policies](beta-configure-authorizations-based-on-policies-08fea39.md "Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.")

[Identity Authentication Tenant as an Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d3df5b457d0c43fca117da0dc14e2f0d.html)

