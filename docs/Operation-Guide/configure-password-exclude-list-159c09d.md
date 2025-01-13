<!-- loio159c09de5ecb4ee49814b0e0a52b0e30 -->

# Configure Password Exclude List

As a tenant administrator, you can create a password exclude list to restrict their usage.



## Context

The exclude list can include *first name*, *last name* and *login name*, and passwords entered as free text.

You can enter up to 1000 passwords in the list. Each password can be up to 256 characters long.

> ### Remember:  
> All new passwords cannot contain configured strings. The restriction is case insensitive. For example, the *qwer* string will exclude passwords like "Qwer&Dfdstg", "TestPasswordqwer", etc.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Exclude Lists* tile.

3.  Choose the *Password* tab.

4.  **Optional:** Under *Dynamic Passwords*, enable the switch next to the options that you want to restrict:


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *First Name*
    
    </td>
    <td valign="top">
    
    The password must not include the user's first name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Last Name*
    
    </td>
    <td valign="top">
    
    The password must not include the user's last name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Login Name*
    
    </td>
    <td valign="top">
    
    The password must not include the user's login name.
    
    </td>
    </tr>
    </table>
    
5.  **Optional:** nder *Password Exclude List*, choose *Create* and enter the password exclude terms as free text in the field.

    For multiple values, use comma between them.

6.  Confirm your changes by choosing *Create*.


**Related Information**  


[Set a Password Policy for an Application](set-a-password-policy-for-an-application-04a6e45.md "As a tenant administrator, you can set a password policy that matches your application logon requirements.")

[Configure Custom Password Policy](configure-custom-password-policy-67bece2.md "Tenant administrators can create and configure a custom password policy for scenarios where Identity Authentication is the authenticating authority.")

[Delete Custom Password Policy](delete-custom-password-policy-697fd2b.md "As a tenant administrator, you can delete the custom password policy that you have created.")

