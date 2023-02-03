<!-- loio06078a681826495eba1f821e5d106dd4 -->

# Search Users

As a tenant administrator, you can search for a specific user or users in the administration console for SAP Cloud Identity Services.



## Prerequisites

You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

You can list all users in the tenant for Identity Authentication or filter your search by *User ID*, *Global User ID*, *Scim ID*, *First Name*, *Last Name*, *E-Mail*, or *Login Name*.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  You can choose one of the following:

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

    **Simple Search**

    -   \(default mode\) Type your search criteria string in the search field and press the *Enter* key

    -   \(when in *Advanced Search* mode\) Press *Simple Search*, type your search criteria string in the search field, and press the *Enter* key



    
    </td>
    <td valign="top">

    Once the search is completed, the system will list the users whose *User ID*, *Global User ID*, *SCIM ID*, *E-Mail*, or *Login Name* match your search criteria string. In this case the system doesn’t include the *First Name* and *Last Name* fields in the search.

    If you aren’t satisfied with the search result, edit your search criteria and repeat the step again.

    > ### Note:  
    > The search is case insensitive. The system searches for entries that begin with the typed string.
    > 
    > If you place asterix \(\*\) in the beginning or in the middle of your search string the system will treat it as a regular character and will include it in the search. For example, if you type ***\*on*** in the *search* field, the system will look for users whose first three letters in any of the three fields are ***\*on***. If you type ***on*** or ***on\**** in the search field, the system will look for users whose first two letters in any of the three fields are ***on***.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Advanced Search**

    Press *Advanced Search* and type your search criteria strings in at least one of the search fields


    
    </td>
    <td valign="top">

    The system checks the search fields simultaneously. Once the search is completed, it will list the users that match the search criteria from all the fields.

    > ### Note:  
    > The search is case insensitive. The system searches for entries that begin with the typed string.
    > 
    > If you place asterix \(\*\) in the beginning or in the middle of your search string the system will treat it as a regular character and will include it in the search. For example, if you type ***\*on*** in the *First Name* field, the system will look for users whose first three letters of the first name are ***\*on***. If you type ***on*** or ***on\**** in the *First Name* field, the system will look for users whose first two letters of the first name are ***on***.


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

