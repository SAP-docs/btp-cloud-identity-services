<!-- loio72e3cafc63b14123bda1d10f26007a0d -->

# Restrict User Security Keys for Web Two-Factor Authentication

This document shows you how to restrict the security keys used by users of type employee for access to applications requiring web two-factor authentication \(FIDO2 standard\).



## Context

You restrict the employee user's security key by creating a list of security keys that are allowed for authentication. All other security keys that aren't in the allow list are forbidden for usage by the users.

> ### Remember:  
> The allow list is valid only for users of the type employee. The other user types aren't affected by the creation of a security key allow list.

When you include a security key in the list, the users will be able to log on to applications that require web authentication only with the security keys are in the list. To be able to access the applications with other security keys, the employee user has to activate a new one on the user profile page or when prompted when logging on to an application. For more information, see the Related Information.

When the allow list is empty, all security keys are permitted for usage by the user.

When you add security keys in the administration console, you can choose from a predefined list, or you can add custom security keys. The AaGuid of the security keys must be in the format `XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX`.

> ### Example:  
> Michael Adams is an administrator at retail company A. He would like to restrict the access to the company's internal portal page only to employees using security keys controlled by the company.

> ### Example:  
> In the administration console, Michael creates the following rule:
> 
> **Default Authentication Rule**
> 
> 
> <table>
> <tr>
> <th valign="top" align="center">
> 
> Action
> 
> 
> 
> </th>
> <th valign="top" align="center">
> 
> IP Range
> 
> 
> 
> </th>
> <th valign="top" align="center">
> 
> Group
> 
> 
> 
> </th>
> <th valign="top">
> 
> Authentication Method
> 
> 
> 
> </th>
> <th valign="top">
> 
> User Type
> 
> 
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> Web Two-Factor Authentication
> 
> 
> 
> </td>
> <td valign="top">
> 
> Any
> 
> 
> 
> </td>
> <td valign="top">
> 
> Any
> 
> 
> 
> </td>
> <td valign="top">
> 
> Any
> 
> 
> 
> </td>
> <td valign="top">
> 
> Employee
> 
> 
> 
> </td>
> </tr>
> </table>
> 
> **Default Authentication Rule**
> 
> Default Action: [Deny\]
> 
> Michael Adams restricts also the Web Two-Factor Authentication to only the company's custom security key by providing `ab1c23de-4f56-7890-1g23-4h56а78б9012` for the AaGuid.
> 
> Dona Moore is working at Company A and as such her user type is `Employee`. As an employee she has a company's security key. She has registered it at her profile page. So when she logs on to the portal page she provides her user name and password, and then she proves her identity with the company's security key.
> 
> Julie Armstrong is also an employee at company A, but she does't have a custom security key like Dona. When she is prompted to prove her identity, she tries another security key, but the authentication fails.
> 
> Richard Wilson is a supplier to Company A. His user type is `Partner`. When he tries to log on to the portal page with his user name and password, his authentication fails.

To create an allow list of the security keys, proceed as follows:



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

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page you can view the administrative and license relevant information of the tenant.

3.  Choose *Multi-Factor Authentication* \> *WebAuthn Security Keys*.

4.  Choose the *Add* button.

5.  Provide the required information in the input fields.

6.  Confirm the information with the *Add* button.

7.  Repeat the procedure for all security keys that you want to put into the allow list.


