<!-- loiod2e1a016846747c7ad0fcd23e2174989 -->

# Add Users to a Group

As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.



## Prerequisites

-   You are assigned the *Manage Groups* and *Manage Users* roles. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have groups created in your tenant.




<a name="loiod2e1a016846747c7ad0fcd23e2174989__context_jtr_1vj_d2c"/>

## Context

> ### Caution:  
> The supported number of users in a group is 344,000 members. If you exceed this number, the operations with the group might mot work properly.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Groups* tile.

    This operation opens a list of the groups in the tenant.

3.  Choose a group from the list on the left.

    This will show the group details and the users that are added to that group.

4.  Press the *Add* button.

5.  Add users to the group. You have the following options:

    -   Select users from the list.
    -   Search for the users.
        -   *starts with* - \(default/reccomended operator\) returns only users that start with the entered value.

        -   *contains* - retuns all the users that contain the entered value. Using the *contains* operator may result in longer processing time.


    > ### Note:  
    > You can filter your search by *First Name*, *Last Name*, *Scim ID*, *Email*, or *Login Name*.

6.  Save your changes.




## Next Steps

Configure the attributes that are sent to the application in the assertion. For more information, see [Configuring User Attributes from the Identity Directory](configuring-user-attributes-from-the-identity-directory-d361407.md)

**Related Information**  


[Import Groups via CSV File](import-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new groups or update existing ones with the assigned users, via a CSV file upload.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[List and Edit Groups](list-and-edit-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.")

[Enable or Disable Central Store-Based Provisioning](enable-or-disable-central-store-based-provisioning-657bbaa.md "You can enable or disable the Central Store-Based Provisioning option in the administration console for SAP Cloud Identity Services.")

[Manage Application-Specific Groups by Identity Provisioning](manage-application-specific-groups-by-identity-provisioning-a9ff3e3.md "By running provisioning jobs, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant or Identity Authentication (SCIM API version 2) target system and provision them afterward to target systems of your choice.")

[List and Search Users in Groups](list-and-search-users-in-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

[Delete Groups](delete-groups-9853912.md "As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

