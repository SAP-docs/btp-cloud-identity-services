<!-- loio297b3b2ab35b4504a629b4180ec70b80 -->

# Edit Administrator Authorizations \(Restricted Availability\)

As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.



## Prerequisites

To edit tenant administrators' authorizations, you must be assigned the Manage Tenant Configuration role.



## Context

> ### Note:  
> The following document contains information specific only for the soft-delete option, and differes from the same document in the official documentation in Cloud Identity Services.

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
    > </th>
    > <th valign="top">
    > 
    > Description
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Applications
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to configure applications and their authorization policies via the administration console.
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Corporate Identity Providers
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to configure the identity providers via the administration console.
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Users
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to manage, import, and export users via the administration console.
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Blocked Users \(Restricted Availability\)
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to read, restore, and delete blocked users.
    > 
    > > ### Note:  
    > > To assign this role you must have the *Soft Delete Users* option enabled in the *Tenant Settings* of your tenant. For more information, see [Enable Soft Delete for Users in Administration Console \(Restricted Availability\)](enable-soft-delete-for-users-in-administration-console-restricted-availability-25a6175.md).
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
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to retrieve user data and export users via the administration console and the SCIM REST API of Identity Authentication.
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Groups
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to create, edit, and delete groups via the administration console.The tenant administrator can also assign authorization policies to users.
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Tenant Configuration
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to manage tenant configuration and authorization assignment to users. Tenant administrators with that role can add additional roles to themselves or to other administrators.
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Manage Identity Provisioning
    > 
    > </td>
    > <td valign="top">
    > 
    > This role gives the tenant administrator permission to configure identity provisioning. The tenant administrator is granted the main IPS\_ADMIN role.
    > 
    > </td>
    > </tr>
    > </table>
    > 
    > > ### Tip:  
    > > **Remove Administrator**
    > > 
    > > If you remove all authorizations, the user or system will no longer be an administrator, and the name will be removed from the list on the left. However, removing all authorizations does not delete the user from the user data base of Identity Authentication.For more information about how to delete a user, see [Delete Users](delete-users-bbfaf5f.md).
    > 
    > You cannot remove the *Manage Tenant Configuration* role from your own user.

5.  Save your changes.

    If the operation is successful, the system displays the message ***Tenant administrator <name of tenant administrator\> updated***.


**Related Information**  


[Enable Soft Delete for Users in Administration Console \(Restricted Availability\)](enable-soft-delete-for-users-in-administration-console-restricted-availability-25a6175.md "Enable soft deletion (blocking) of users in SAP Cloud Identity Services.")

[Read Single Soft-Deleted User \(Restricted Availability\)](read-single-soft-deleted-user-restricted-availability-5adef17.md "Read the soft-deleted (blocked) but not permanently deleted user.")

[Read All Soft-Deleted Users \(Restricted Availability\)](read-all-soft-deleted-users-restricted-availability-89a99b9.md "Get a list of all soft-deleted (blocked) but not deleted users in the tenant of SAP Cloud Identity Services.")

[Permanently Delete User \(Restricted Availability\)](permanently-delete-user-restricted-availability-230fc2e.md "Permanently delete the soft-deleted (blocked) but not yet deleted from the system user whose SCIM ID is stated in the request.")

[Restore Soft-Deleted User \(Restricted Availability\)](restore-soft-deleted-user-restricted-availability-114076d.md "Restore a user that is soft-deleted (blocked) in the tenant of SAP Cloud Identity Services.")

[Identity Authentication Tenant as an Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d3df5b457d0c43fca117da0dc14e2f0d.html)

