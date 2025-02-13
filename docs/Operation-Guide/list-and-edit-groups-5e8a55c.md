<!-- loio5e8a55cdadad40d49c83b443c68fbd62 -->

# List and Edit Groups

As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.



## Prerequisites

-   You are assigned the *Manage Groups* and *Manage Users* roles. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have created groups in your tenant. For more details on how to create groups, see [Create a Group](create-a-group-b1b638d.md).




<a name="loio5e8a55cdadad40d49c83b443c68fbd62__context_vnl_blv_knb"/>

## Context

The groups are sorted in alphabetical order of the display name.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Groups* tile.

    This operation opens a list of the groups in the tenant.

3.  **Optional:** Type a `Group ID`, `Display Name`, or `Name` of a group in the search field to filter the list items.

    > ### Tip:  
    > Choose *Show Filter Bars* for advanced search. You must be assigned to a policy that allows reading applications to view the information for *Application Name*.

4.  **Optional:** Choose a group from the list on the left to view its details.

5.  **Optional:** Press the *Edit* button at the top-right corner of the screen.

6.  Edit the *Display name* or *Description* fields if necessary, and choose *Next Step*.

7.  Edit the list of applications. You can choose between one of the following three options:

    -   \(if no application is selected\) Select an application from the list to create an application-specific group.
    -   \(if an application is selected\) Deselect an application from the list. The group will be no longer application-specific.
    -   \(if an application is selected\) Select another application from the list. The group will continue to be application-specific.

8.  **Optional:** Choose a group type:

    -   *userGroup*
    -   *authorization*
    -   *deepLinkActivationPermission*

9.  **Optional:** Choose the supported operations for the group:

    -   *readWrite*
    -   *readOnly*
    -   *userOnlyMembership*
    -   *membership*

10. Choose *Next Step* \> *Finish*.


**Related Information**  


[Import Groups via CSV File](import-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new groups or update existing ones with the assigned users, via a CSV file upload.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[Enable or Disable Central Store-Based Provisioning](enable-or-disable-central-store-based-provisioning-657bbaa.md "You can enable or disable the Central Store-Based Provisioning option in the administration console for SAP Cloud Identity Services.")

[Manage Application-Specific Groups by Identity Provisioning](manage-application-specific-groups-by-identity-provisioning-a9ff3e3.md "By running provisioning jobs, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant and provision them afterward to target systems of your choice.")

[List and Search Users in Groups](list-and-search-users-in-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

[Delete Groups](delete-groups-9853912.md "As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

