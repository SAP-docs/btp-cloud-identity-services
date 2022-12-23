<!-- loio9172552b5df14fdb9ad668fe763cfe51 -->

# Unlock User Password

You can unlock a user password when the user must log on to the application before the automatic unlock time of 60 minutes has passed, or if the *Password Locked Period* in the password policy is set at *unlimited*.



## Context

The user locks the password after submitting five incorrect passwords when trying to log on to the account. The user receives a notification e-mail that the password log on to the account has been disabled for 60 minutes. The user can either choose the link provided in the e-mail to set a new password, or wait for 60 minutes and then log on with his or her current password.

If the *Password Locked Period* in the password policy is set at *unlimited*, the password can be unlocked only by the tenant administrator. When a user locks the password and then tries to reset it, they get the following message : "Your password is locked. Please contact your system administrator to unlock it." In this case the e-mail template set must also be changed. Otherwise, the user will receive an e-mail stating that password logon to the account was disabled for - 1 hour. For more information, see [Configuring E-Mail Templates](configuring-e-mail-templates-b2afbcd.md).

> ### Remember:  
> Identity Authentication can send to the user up to three e-mails \(forgot password, reset password, locked password, e-mail verification\) per 24 hours.
> 
> If the user must receive more than three e-mails, the administrator must reset the counter for e-mail sending first. For more information, see [Reset Counter for E-Mail Sending](reset-counter-for-e-mail-sending-08f634b.md).

The tenant administrator can unlock the logon to the user account via the administration console.

> ### Restriction:  
> When a user is with a status `Inactive`, unlocking the user password is disabled. For more information, see [Deactivate Users](deactivate-users-99cf468.md).

To unlock the user password manually, proceed as follows:



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

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  Choose the user whose password you want to unlock.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

4.  Choose *Password Details* under the *Authentication* tab.

5.  Choose *Unlock*.

    > ### Remember:  
    > You can only unlock locked user passwords.




<a name="loio9172552b5df14fdb9ad668fe763cfe51__result_pvt_lpv_t1b"/>

## Results

The password is unlocked. The user can now access his or her account after providing the correct credentials.

**Related Information**  


[Send Reset Password E-Mail](send-reset-password-e-mail-da55abf.md "You can trigger the sending of an e-mail to the user with reset password information.")

