<!-- loio40c29d2632b744af9bc7b7d353616d52 -->

# Export Existing Users of a Tenant of Identity Authentication



## Prerequisites

-   You are assigned the *Manage Users* or *Read Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   \(For administrators assigned to a custom authorization policy\) You are assigned to `READ_USERS` and `READ_SCIM_SCHEMAS` authorization policies. Otherwise, you won't be able to see and access the *Export Users* tile.




## Context

You can export a CSV file containing information of all tenant users in Identity Authentication including the tenant administrators. The CSV file can contain columns with all user supported SCIM attributes. You can filter the user attributes that you want to include in the exported file. The default columns are: *active*, *userName*, *userType*, *emails\[0\].display*, *emails\[0\].primary*, *emails\[0\].type*, and *emails\[0\].value*.

If the values for the *validTo* and *validFrom* attributes for a specific user aren't in the correct Zulu format yyyyMMddHHmmss'Z', Identity Authentication returns empty values for these attributes in the CSV file.

> ### Remember:  
> The `SCIM ID` serves as the primary identifier if it is found in the CSV file. The users will only be updated, but not created if there are users with a new `SCIM ID`. This process works within the same tenant because the `SCIM ID`s differ across tenants.
> 
> If the `SCIM ID` doesn't exist in the CSV file, the create and update functionality will function as expected, but the administrator won't be able to modify the username or email.

> ### Restriction:  
> Each multivalued attribute is limited to 3 fixed values, and each custom attribute is limited to 10 values.
> 
> For example, if a user in the administration console has more than 3 emails, the export functionality will export only 3 emails. On the other hand, if a user has only one email, then the csv file will show 3 emails, but two of them will be empty.
> 
> If you need to export multivalued attributes with more than 3 values, or custom attributes with more than 10 values, you can use the Identity Provisioning service. For more information, see [Real-Time Provisioning from Identity Authentication](https://help.sap.com/docs/identity-provisioning/identity-provisioning/real-time-provisioning-identity-authentication?version=Cloud) or [Provisioning from Source to Target Systems](https://help.sap.com/docs/identity-provisioning/identity-provisioning/system-types?version=Cloud).

> ### Note:  
> If the *active* attribute of a user is `FALSE`, he or she can’t perform any operations on the tenant.

> ### Example:  
> A tenant administrator exports a CSV file with the current users in the system and only the following attributes: *active*, *userName*, *userType*, and *emails\[0\].value*. As a result, the administrator receives the following information:
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> active
> 
> </th>
> <th valign="top">
> 
> userName
> 
> </th>
> <th valign="top">
> 
> userType
> 
> </th>
> <th valign="top">
> 
> emails\[0\].value
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> TRUE
> 
> </td>
> <td valign="top">
> 
> EID00001
> 
> </td>
> <td valign="top">
> 
> public
> 
> </td>
> <td valign="top">
> 
> michael.adams@example.com
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> TRUE
> 
> </td>
> <td valign="top">
> 
> EID00002
> 
> </td>
> <td valign="top">
> 
> employee
> 
> </td>
> <td valign="top">
> 
> julie.armstrong@example.com
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> TRUE
> 
> </td>
> <td valign="top">
> 
> EID00003
> 
> </td>
> <td valign="top">
> 
> partner
> 
> </td>
> <td valign="top">
> 
> donna.moore@example.com
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> FALSE
> 
> </td>
> <td valign="top">
> 
> EID00004
> 
> </td>
> <td valign="top">
> 
> customer
> 
> </td>
> <td valign="top">
> 
> john.miller@example.com
> 
> </td>
> </tr>
> </table>

To export tenant users from Identity Authentication, proceed as follows:



<a name="loio40c29d2632b744af9bc7b7d353616d52__steps_evb_bvz_r4"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Export Users* tile.

    This operation opens the *Export Users* page.

3.  Choose the attributes that you want to include in the CSV file.

    The default choice is: *active*, *userName*, *userType*, *emails\[0\].display*, *emails\[0\].primary*, *emails\[0\].type*, and *emails\[0\].value*.

4.  Choose the *Export* button.


