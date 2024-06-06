<!-- loio4ac340a1c5754b199cc681b66300630e -->

# List and Search Users in Groups

As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.



## Prerequisites

-   You are assigned the *Manage Groups* and *Manage Users* roles. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have created at least one user group in the tenant. For more details about how to create groups, see Related Information.

-   You have assigned at least one user to the selected user group. For more details about how to assign groups to a user, see Related Information.



## Context



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Groups* tile.

    This operation opens a list of the groups in the tenant.

3.  Type a `Group ID`, `Display Name`, or `Name` of a group in the search field in order to filter the list items.

    > ### Tip:  
    > Choose *Show Filter Bars* for advanced search. You must be assigned to a policy that allows reading applications to view the information for *Application Name*.

4.  Choose a group from the list.

    This will open the groups details \(*Group ID*, *Name*, *Display Name*, *Description*, *Type*, and *Application Name*\) on the right. The users that are part of the group are listed below the user group details.

    > ### Restriction:  
    > The group must be application specific and you must be assigned to a policy that allows reading applications to view the *Application Name*. For more information, see [Groups](../groups-d93be69.md).

5.  To search for a specific user, type the *SCIM ID*, *Email*, *Login Name* of the user in the search field and press the *Enter* key.


**Related Information**  


[Import Groups via CSV File](import-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new groups or update existing ones with the assiged users, via a CSV file upload.")

[Create a New Group](create-a-new-group-b1b638d.md "As a tenant administrator you can create new user groups in the tenant via the administration console for SAP Cloud Identity Services.")

[List and Edit Groups](list-and-edit-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

[Delete Groups](delete-groups-9853912.md "As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.")

[Create a New Group](create-a-new-group-b1b638d.md "As a tenant administrator you can create new user groups in the tenant via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

