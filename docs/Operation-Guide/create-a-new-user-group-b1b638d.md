<!-- loiob1b638d6724e4dc48ee3e116263f567c -->

# Create a New User Group

As a tenant administrator you can create new user groups in the tenant via the administration console for Identity Authentication.



## Prerequisites

You are assigned the *Manage Groups* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

> ### Remember:  
> The maximum number of groups assigned to a user is 500.

To create a new user group, proceed as follows:



## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Choose the *User Groups* tile.

    This operation opens a list of the user groups in the tenant.

3.  Press the *Create* button at the top of the page.

4.  Fill in the required information.

5.  Save your entries.




<a name="loiob1b638d6724e4dc48ee3e116263f567c__result_mfg_cxk_pkb"/>

## Results

If the operation is successful, the system displays the message: `Group "<name of the group>" updated`. Identity Authentication creates the new group and assigns the *Group ID* to it. *Group ID* is in the universally unique identifier \(UUID\) format.

**Related Information**  


[Import User Groups via CSV File](import-user-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new user groups or update existing ones with the assiged users, via a CSV file upload.")

[List and Edit User Groups](list-and-edit-user-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the user groups in a tenant in the administration console for Identity Authentication.")

[List Users in User Groups](list-users-in-user-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a user group in a tenant in the administration console for Identity Authentication.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for Identity Authentication.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for Identity Authentication.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for Identity Authentication.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for Identity Authentication.")

[Delete User Groups](delete-user-groups-9853912.md "As a tenant administrator, you can delete one or more user groups in a tenant of Identity Authentication.")

