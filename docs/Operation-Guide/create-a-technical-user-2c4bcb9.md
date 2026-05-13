<!-- loio2c4bcb9d51dd4bdc892cf2fe7f9b98be -->

# Create a Technical User

As a user with assigned special policy authorizations, you can create a technical user in the administration console for SAP Cloud Identity Services.



## Prerequisites

-   The authorizations based on policies option in the admin console for SAP Cloud Identity Services is enabled. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).

-   You are assigned with a `MANAGE_TECHNICAL_USERS` or `CREATE_TECHNICAL_USERS` authorization policy. For more information, see [Configure Technical User Authorizations](configure-technical-user-authorizations-885320d.md).



## Context

You create the new technical user with a *Display Name* as a minimal requirement. The owner's first name, last name, and email are optional and can be added or edited later. The technical user automatically receives an email address, and a SCIM ID that can't be edited.

Later, if you are assigned with the required authorization policy you can edit the technical user attributes, or delete it. For more information, see [Configure Technical User Authorizations](configure-technical-user-authorizations-885320d.md).

To create a technical user, use the following procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose *Users & Authorizations* \> *Technical User*.

3.  Press *Create*.

4.  Fill in the required fields in the dialog box.


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Required
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Display Name**
    
    </td>
    <td valign="top">
    
    Yes
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Owner First Name**
    
    </td>
    <td valign="top">
    
    No
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Owner Last Name**
    
    </td>
    <td valign="top">
    
    No
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Owner Email**
    
    </td>
    <td valign="top">
    
    No
    
    </td>
    </tr>
    </table>
    
5.  Press *Create*




<a name="loio2c4bcb9d51dd4bdc892cf2fe7f9b98be__result_mfg_cxk_pkb"/>

## Results

If the operation is successful, the system displays the message: `Technical user created`.

**Related Information**  


[Manage Technical User Details](manage-technical-user-details-14b36c2.md "As a user with assigned special policy authorizations, you can manage the technical user details and in the administration console for SAP Cloud Identity Services.")

[Users](../users-70e95d1.md "Users in SAP Cloud Identity Services fall into three categories: administrators, end users, and technical users.")

