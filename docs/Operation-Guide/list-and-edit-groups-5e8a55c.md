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

3.  Choose a group from the list on the left to view its details.

    > ### Tip:  
    > Type a `Group ID`, `Display Name`, or `Name` of a group in the search field to filter the list items. Choose *Show Filter Bars* for advanced search. You must be assigned to a policy that allows reading applications to view the information for *Application Name*.

4.  **Optional:** Press the *Edit* button at the top-right corner of the screen.

    1.  **Optional:** Edit the *Display name* or *Description* fields, or both.

    2.  Choose *Next Step*.

    3.  In the *Application \(Optional\)* screen:



    <table>
    <tr>
    <th valign="top">

    Group Type
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **User Group**
    
    </td>
    <td valign="top">
    
    Fill in the information if you want to make this group an application-specific group:

    1.  Select an application from the list to create an application-specific group.
    2.  Add *External Name*.
    3.  Choose a group type:

        -   *userGroup* - A group of users who have something in common.
        -   *authorization* - A group related to authorization of users, groups or applications.
        -   *deepLinkActivationPermission* - A group of applications that support deep linking.

        For more information about the group, see [Groups](../groups-d93be69.md).

        > ### Remember:  
        > The *Supported Operations* field is set to `readWrite` and is read-only. For more information about supported operations, refer to the *Application-Specific Groups Supported Operations* table in [Groups](../groups-d93be69.md).

    4.  Choose *Next Step* \> *Finish*.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Application Specific Group \(Read & Write\)**
    
    </td>
    <td valign="top">
    
    Fill in the information if you want to edit this group:

    1.  Select a new application from the list if needed to remove an existing one.

        > ### Remember:  
        > The *External Name*, group type, and supported operations can't be edited.

    2.  Choose *Next Step* \> *Finish*.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Authorization Group**
    
    </td>
    <td valign="top">
    
    Edit the *Display Name* and or *Description*.
    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Import Groups via CSV File](import-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new groups or update existing ones with the assigned users, via a CSV file upload.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[Enable or Disable Central Store-Based Provisioning](enable-or-disable-central-store-based-provisioning-657bbaa.md "You can enable or disable the Central Store-Based Provisioning option in the administration console for SAP Cloud Identity Services.")

[Manage Application-Specific Groups by Identity Provisioning](manage-application-specific-groups-by-identity-provisioning-a9ff3e3.md "By running provisioning jobs, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant or Identity Authentication (SCIM API version 2) target system and provision them afterward to target systems of your choice.")

[List and Search Users in Groups](list-and-search-users-in-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

[Delete Groups](delete-groups-9853912.md "As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

