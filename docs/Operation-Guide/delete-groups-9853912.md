<!-- loio9853912732d34ff2b7759b151ad8f27b -->

# Delete Groups

As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.



## Prerequisites

You are assigned the *Manage Groups* and *Manage Users* roles. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

> ### Restriction:  
> This document does not apply to groups of type *Authorization* and associated with an authorization policy. These groups are related to the authorization policies, and when you delete a policy, the respective group is also removed. For more information, see [Delete an Authorization Policy](delete-an-authorization-policy-3b78cc4.md).

The delete groups operation removes groups and unassigns all users from them.

Follow the procedure below for each group that you want to delete:



<a name="loio9853912732d34ff2b7759b151ad8f27b__steps_dly_pxx_cqb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Groups* tile.

    This operation opens a list of the groups in the tenant.

3.  Select the user group that you want to delete.

4.  Press the *Delete* button in the right-hand panel.

5.  Confirm the operation in the pop-up dialog.

    If the operation is successful, the system displays the message ***Group <group name\> deleted.***.


**Related Information**  


[Import Groups via CSV File](import-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new groups or update existing ones with the assigned users, via a CSV file upload.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[List and Edit Groups](list-and-edit-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.")

[Enable or Disable Central Store-Based Provisioning](enable-or-disable-central-store-based-provisioning-657bbaa.md "You can enable or disable the Central Store-Based Provisioning option in the administration console for SAP Cloud Identity Services.")

[Manage Application-Specific Groups by Identity Provisioning](manage-application-specific-groups-by-identity-provisioning-a9ff3e3.md "By running provisioning jobs, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant or Identity Authentication (SCIM API version 2) target system and provision them afterward to target systems of your choice.")

[List and Search Users in Groups](list-and-search-users-in-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

