<!-- loio9172552b5df14fdb9ad668fe763cfe51 -->

# Unlock User Password

You can unlock a user password when the user must log on to the application before the automatic unlock time of 60 minutes has passed, or if the *Password Locked Period* in the password policy is set at *unlimited*.



## Context

The user locks the password after submitting five incorrect passwords when trying to log on to the account. The user receives a notification email that the password log on to the account has been disabled for 60 minutes. The user can either choose the link provided in the email to set a new password, or wait for 60 minutes and then log on with his or her current password.

If the *Password Locked Period* in the password policy is set at *unlimited*, the password can be unlocked only by the tenant administrator. When a user locks the password and then tries to reset it, they get the following message : "Your password is locked. Please contact your system administrator to unlock it." In this case the email template set must also be changed. Otherwise, the user will receive an email stating that password logon to the account was disabled for - 1 hour. For more information, see [Configuring Email Templates](configuring-email-templates-b2afbcd.md).

> ### Remember:  
> Identity Authentication can send to the user up to three emails \(forgot password, reset password, locked password, email verification\) per 24 hours.
> 
> If the user must receive more than three emails, the administrator must reset the counter for email sending first. For more information, see [Reset Counter for Email Sending](reset-counter-for-email-sending-08f634b.md).

The tenant administrator can unlock the logon to the user account via the administration console.

> ### Restriction:  
> When a user is with a status `Inactive`, unlocking the user password is disabled. For more information, see [Deactivate Users](deactivate-users-99cf468.md).

To unlock the user password manually, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

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


[Send Reset Password Email](send-reset-password-email-da55abf.md "You can trigger the sending of an email to the user with reset password information.")

