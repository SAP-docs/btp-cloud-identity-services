<!-- loiob1b638d6724e4dc48ee3e116263f567c -->

# Create a Group

As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.



## Prerequisites

You are assigned the *Manage Groups* and *Manage Users* roles. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

You can choose whether to create just a user group or a user group that is application-specific. For more information about the different groups in the Identity Directory of Cloud Identity Services, see [Groups](../groups-d93be69.md).

To create a new user group, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Groups* tile.

    This operation opens a list of the groups in the tenant.

3.  Press the *\+ Create* button at the top of the page.

4.  In the *General* screen, fill in the required information, and choose *Next Step*.

    You have the following options:

    ****


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Notes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Name
    
    </td>
    <td valign="top">
    
    Required. The name of the group.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Display Name
    
    </td>
    <td valign="top">
    
    Required. The display name of the group.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Description
    
    </td>
    <td valign="top">
    
    Optional. Additional information for the group.
    
    </td>
    </tr>
    </table>
    
5.  **Optional:** In the *Application \(Optional\)* screen, fill in the information if you want to create an application-specific group.

    1.  Select an application from the list to create an application-specific group.

    2.  Choose a group type:

        -   *userGroup*
        -   *authorization*
        -   *deepLinkActivationPermission*

    3.  Choose the supported operations for the group:

        -   *readWrite*
        -   *readOnly*
        -   *userOnlyMembership*
        -   *membership*


6.  Choose *Next Step* \> *Finish*.




<a name="loiob1b638d6724e4dc48ee3e116263f567c__result_mfg_cxk_pkb"/>

## Results

If the operation is successful, the system displays the message: `Group "<name of the group>" updated`. Identity Authentication creates the new group and assigns the *Group ID* to it. *Group ID* is in the universally unique identifier \(UUID\) format. If the group is application-specific the *Application Name* is also assigned to the group.

**Related Information**  


[Import Groups via CSV File](import-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new groups or update existing ones with the assigned users, via a CSV file upload.")

[List and Edit Groups](list-and-edit-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.")

[List and Search Users in Groups](list-and-search-users-in-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

[Delete Groups](delete-groups-9853912.md "As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.")

[Groups](../groups-d93be69.md "SAP Cloud Identity Services offers groups to organize users based on common characteristics, authorization, or application. Use them to efficiently manage user access and permissions within your organization's SAP Cloud Identity Services environment.")

