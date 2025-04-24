<!-- loio657bbaa67ba641ccbaa54cc7b89f6bc1 -->

# Enable or Disable Central Store-Based Provisioning

You can enable or disable the *Central Store-Based Provisioning* option in the administration console for SAP Cloud Identity Services.



## Prerequisites

-   You have an application specific group in your tenant. For more details on how to create groups, see [Create a Group](create-a-group-b1b638d.md).

-   You have configured the **Central Store-Based Provisioning** in the administration console for SAP Cloud Identity Services. For more information, see [Central Store-Based Provisioning](../central-store-based-provisioning-33eae39.md).



<a name="loio657bbaa67ba641ccbaa54cc7b89f6bc1__context_vnl_blv_knb"/>

## Context

When you enable the *Central Store-Based Provisioning* for a specific application, whenever you update an application-specific group associated with this application, a provisioning of the updates is triggered from the Local Identity Directory to a target system of your choice. There is no need to run manual or scheduled jobs in the Identity Provisioning.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Under the *Provisioning* tab, enable or disable the *Central Store-Based Provisioning* option.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


**Related Information**  


[Import Groups via CSV File](import-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new groups or update existing ones with the assigned users, via a CSV file upload.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[List and Edit Groups](list-and-edit-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.")

[Manage Application-Specific Groups by Identity Provisioning](manage-application-specific-groups-by-identity-provisioning-a9ff3e3.md "By running provisioning jobs, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant or Identity Authentication (SCIM API version 2) target system and provision them afterward to target systems of your choice.")

[List and Search Users in Groups](list-and-search-users-in-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

[Delete Groups](delete-groups-9853912.md "As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.")

