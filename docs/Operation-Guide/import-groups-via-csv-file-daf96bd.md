<!-- loiodaf96bd4bdcf4f1b99b33f4d57db6ca8 -->

# Import Groups via CSV File

As a tenant administrator, you can create new groups or update existing ones with the assigned users, via a CSV file upload.



## Prerequisites

-   You are assigned the *Manage Groups* and *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).




## Context

With the CSV file, you can import up to 25000 groups to create new groups or to update existing ones with their user assignments.

If the group does not exist in the tenant, and you provide that group in the CSV file, the group will be created. The CSV file must contain the `groups` column. The value of the `groups` column is recorded as `name` and `displayName` in the newly created group. You cant set `description`, or separately provide `name` or `displayName` in the CSV file. No user assignment is required when creating a new group.

You can only add users to the groups via the import groups option, you don't remove users from the groups.

> ### Remember:  
> When you create new groups with user assignments, or update existing ones with their user assignments, make sure that the CSV file contains unique users with unique identifiers.
> 
> The CSV file must contain the `groups` column and a column with at least one of the following identifiers:
> 
> -   *Global User ID*
> -   *Email* - `emails[0].value`
> 
>     > ### Note:  
>     > -   If the `emails[0].value` is not unique, and there are more than one users with one and the same email, all the users with that email in the CSV will be assigned to the group.
>     > -   If the `emails[0].value` is not unique, and there are more than one users with one and the same email, you can distinguish the users by the `userName` or `userUuid` attribute. If you use the `userUuid` attribute, make sure that the user that you want to assign the group has it.
> 
> -   *User Name*
> 
> If the file contains more than one identifier then the priority will be:
> 
> 1.  Global User ID
> 2.  Email
> 3.  User Name
> 
> If the file contains email and user name, a combination of both will be used as identifier. Thus the user will be matched with the email and user name at the same time.
> 
> If the CSV file contains one and the same email identifier, then the group will be assigned to all users that has this email.

> ### Note:  
> The user import doesn't assign any special rights or roles to the users for the specific application.
> 
> The CSV file can contain only columns with no spaces between the values.
> 
> If you enter the data in the CSV file as text, you must separate the entries with commas. Beware not to put any spaces before or after the commas. If you enter more than one value in a single entry, separate the values within the entry with semicolons.

> ### Example:  
> > ### Sample Code:  
> > ```
> > groups,urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid,emails[0].value
> > HR,1ab2e307-1c7c-4c37-9bcf-ed0123456789,dona.moore@example.com
> > Management,1ab2e307-1c7c-4c37-9bcf-ed0123456700,management@example.com
> > IT,1ab2e307-1c7c-4c37-9bcf-ed0123456712,management@example.com
> > ```

To import groups via CSV file into Identity Authentication, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Groups* tile.

3.  Press the *Import* button.

4.  Choose the *Browse...* button and specify the location of the CSV file.

    > ### Note:  
    > Use a UTF-8 encoded file with up to 25000 groups and an extension `.csv`. If your file contains more than 25000 groups, you have to import the groups information in iterations within the group number limit.

    > ### Tip:  
    > If you import groups from one tenant to another, you can first export the users from the first tenant via the export users option, and then use the exported CSV file for the import to the other tenant or tenants. For more information, see [Export Existing Users of a Tenant of Identity Authentication](export-existing-users-of-a-tenant-of-identity-authentication-40c29d2.md).

5.  Choose the *Save* button.

    If the operation is successful, the system displays a message with the number of imported and updated groups.


**Related Information**  


[Create a New Group](create-a-new-group-b1b638d.md "As a tenant administrator you can create new user groups in the tenant via the administration console for SAP Cloud Identity Services.")

[List and Edit Groups](list-and-edit-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.")

[List and Search Users in Groups](list-and-search-users-in-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

[Delete Groups](delete-groups-9853912.md "As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.")

