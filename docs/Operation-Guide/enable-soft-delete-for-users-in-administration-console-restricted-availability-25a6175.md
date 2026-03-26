<!-- loio25a6175d32ef496891b6c0b1e0a08632 -->

# Enable Soft Delete for Users in Administration Console \(Restricted Availability\)

Enable soft deletion \(blocking\) of users in SAP Cloud Identity Services.



## Prerequisites

-   You have the soft delete option enabled for your tenant by the SAP Cloud Identity Services support team. For more information, see [Soft Delete for Users in Cloud Identity Services \(Restricted Availability\)](soft-delete-for-users-in-cloud-identity-services-restricted-availability-2a143e1.md).
-   You are a tenant administrator of SAP Cloud Identity Services in the tenant with enabled soft delete option. For more information, see [KBA 3035908 - How to Find the Identity Authentication / Identity Provisioning Tenant Administrator Information or Tenant URL?](https://me.sap.com/notes/3035908)



## Context

As a tenant administrator, you can delete users in the administration console. Once deleted, the users and their attributes are permanently deleted and can't be restored. Your scenario, for example, might require to easily recover the user and its attributes. When the soft delete option is enabled, the soft-deleted users are retained or blocked in the system, and they can be restored from there. On the other hand, when the option is disabled, the users and their data are permanently deleted. This applies to all user types. The *Soft Delete Users* is disabled by default in the administration console for Cloud Identity Services.

To enable soft delete in the administration console, use the following procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *General*, choose the *Blocking and Deletion* list item.

4.  Choose *Edit*.

5.  Under *Soft Delete Users*, enable the soft delete users status.

6.  Save your changes.




## Next Steps

Assign *Manage Blocked Users* administrator authorizations. For more information, see [Edit Administrator Authorizations \(Restricted Availability\)](edit-administrator-authorizations-restricted-availability-297b3b2.md).

**Related Information**  


[Read Single Soft-Deleted User \(Restricted Availability\)](read-single-soft-deleted-user-restricted-availability-5adef17.md "Read the soft-deleted (blocked) but not permanently deleted user.")

[Read All Soft-Deleted Users \(Restricted Availability\)](read-all-soft-deleted-users-restricted-availability-89a99b9.md "Get a list of all soft-deleted (blocked) but not deleted users in the tenant of SAP Cloud Identity Services.")

[Permanently Delete User \(Restricted Availability\)](permanently-delete-user-restricted-availability-230fc2e.md "Permanently delete the soft-deleted (blocked) but not yet deleted from the system user whose SCIM ID is stated in the request.")

[Restore Soft-Deleted User \(Restricted Availability\)](restore-soft-deleted-user-restricted-availability-114076d.md "Restore a user that is soft-deleted (blocked) in the tenant of SAP Cloud Identity Services.")

[Edit Administrator Authorizations \(Restricted Availability\)](edit-administrator-authorizations-restricted-availability-297b3b2.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

