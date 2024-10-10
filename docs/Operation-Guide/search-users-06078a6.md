<!-- loio06078a681826495eba1f821e5d106dd4 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Search Users

As a tenant administrator, you can search for a specific user or users in the administration console for SAP Cloud Identity Services.



## Prerequisites

You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

You can list all users in the tenant for Identity Authentication or filter your search by *User ID*, *Global User ID*, *Scim ID*, *First Name*, *Last Name*, *Email*, or *Login Name*.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  **Optional:** You can choose one of the following:

    **Search Options**


    <table>
    <tr>
    <td valign="top">
    
    **List All Users**

    Press *More*
    
    </td>
    <td valign="top">
    
    This will expand the list by 20 users.

    > ### Note:  
    > This option is available only if the users in the tenant are more than 20.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Unfiltered Search**

    -   \(default mode\) Type your search criteria string in the search field and press the *Enter* key

    -   \(when in *Filtered Search* mode\) Press *Hide Filters*, type your search criteria string in the search field, and press the *Enter* key



    
    </td>
    <td valign="top">
    
    Once the search is completed, the system will list the users whose *User ID*, *Global User ID*, *SCIM ID*, *Email*, or *Login Name* match your search criteria string. In this case the system doesn’t include the *First Name* and *Last Name* fields in the search.

    If you aren’t satisfied with the search result, edit your search criteria and repeat the step again.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Filtered Search**

    Press *Show Filters*, type your search criteria strings in at least one of the search fields, and press the *Enter* key
    
    </td>
    <td valign="top">
    
    The system checks the search fields simultaneously. Once the search is completed, it will list the users that match the search criteria from all the fields.
    
    </td>
    </tr>
    </table>
    
4.  **Optional:** To configure the user details columns, choose the *Settings* icon :gear: and select the columns that you want to see.


**Related Information**  


[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

