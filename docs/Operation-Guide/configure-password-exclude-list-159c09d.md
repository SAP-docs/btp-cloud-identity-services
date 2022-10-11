<!-- loio159c09de5ecb4ee49814b0e0a52b0e30 -->

# Configure Password Exclude List

As a tenant administrator, you can create a password exclude list to restrict their usage.



## Context

The exclude list can include *first name*, *last name* and *login name*, and passwords entered as free text.

You can enter up to 1000 passwords in the list. Each password can be up to 256 characters long.

> ### Remember:  
> All new passwords cannot contain configured strings. The restriction is case insensitive. For example, the *qwer* string will exclude passwords like "Qwer&Dfdstg", "TestPasswordqwer", etc.



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

2.  Under *Users & Authorizations*, choose the *Exclude Lists* tile.

3.  Choose the *Password* tab.

4.  Enable the switch next to the options that you want to restrict:


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
    
5.  Choose *Create* and enter the password exclude terms as free text in the field.

    For multiple values, use comma between them.

6.  Confirm your changes by choosing *Create*.


**Related Information**  


[Set a Password Policy for an Application](set-a-password-policy-for-an-application-04a6e45.md "As a tenant administrator, you can set a password policy that matches your application logon requirements.")

[Configure Custom Password Policy](configure-custom-password-policy-67bece2.md "Tenant administrators can create and configure a custom password policy for scenarios where Identity Authentication is the authenticating authority.")

[Delete Custom Password Policy](delete-custom-password-policy-697fd2b.md "As a tenant administrator, you can delete the custom password policy that you have created in the administration console for Identity Authentication.")

