<!-- loioda55abf8d0e54eb6825a13777bef4eb1 -->

# Send Reset Password Email

You can trigger the sending of an email to the user with reset password information.



## Context

Tenant administrator can trigger the sending of an email to the user with reset password information. When the user follows the link provided in the email, the reset password screen appears and the user is prompted to set a new password.

> ### Note:  
> In this scenario, the email that is sent uses the Forgot Password template set that is defined for the User Prfile application. For more information, see [View Email Template Document](view-email-template-document-148568a.md).

Identity Authentication can send to the user up to three emails \(forgot password, reset password, email verification\) per 24 hours. This counter includes also the emails sent with passcode for TOTP deactivation. If you send three emails within 24 hours, the user will not be able to request a passcode for TOTP deactivation via the profile page during these 24 hours.

If the user must receive more than three emails, the administrator must reset the counter for email sending first. For more information, see [Reset Counter for Email Sending](reset-counter-for-email-sending-08f634b.md).

> ### Tip:  
> [Configure SAML 2.0 Service Provider](configure-saml-2-0-service-provider-51f1f75.md).

> ### Restriction:  
> When a user is with a status `Inactive`, sending reset password email to that user is disabled. For more information, see [Deactivate Users](deactivate-users-99cf468.md).

To send a reset password email, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  Choose the user whose password needs to be reset.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

    > ### Remember:  
    > The maximum number of emails that can be sent to a user within 24 hours is three. This counter includes also the emails sent with passcode for TOTP deactivation. If you send three emails within 24 hours, the user will not be able to request a passcode for TOTP deactivation via the profile page during these 24 hours.
    > 
    > If you need to send more emails, first reset the password counter. For more information, see [Reset Counter for Email Sending](reset-counter-for-email-sending-08f634b.md).

4.  Choose *Password Details* under the *Authentication* tab.

5.  Press *Send Email*.




<a name="loioda55abf8d0e54eb6825a13777bef4eb1__result_fwb_4vw_t1b"/>

## Results

The user receives an email with information how to reset his or her password. After resetting the password, he or she is able to log on to the account.

**Related Information**  


[Unlock User Password](unlock-user-password-9172552.md "You can unlock a user password when the user must log on to the application before the automatic unlock time of 60 minutes has passed, or if the Password Locked Period in the password policy is set at unlimited.")

[Reset Counter for Email Sending](reset-counter-for-email-sending-08f634b.md "You can reset the counter for the number of emails that can be sent to the user.")

[Set Initial Password](set-initial-password-16149d5.md "You can set initial password for a user that has already activated his or her account.")

