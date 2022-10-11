<!-- loioda55abf8d0e54eb6825a13777bef4eb1 -->

# Send Reset Password E-Mail

You can trigger the sending of an e-mail to the user with reset password information.



## Context

Tenant administrator can trigger the sending of an e-mail to the user with reset password information. When the user follows the link provided in the e-mail, the reset password screen appears and the user is prompted to set a new password.

Identity Authentication can send to the user up to three e-mails \(forgot password, reset password, e-mail verification\) per 24 hours. This counter includes also the e-mails sent with passcode for TOTP deactivation. If you send three e-mails within 24 hours, the user will not be able to request a passcode for TOTP deactivation via the profile page during these 24 hours.

If the user must receive more than three e-mails, the administrator must reset the counter for e-mail sending first. For more information, see [Reset Counter for E-Mail Sending](reset-counter-for-e-mail-sending-08f634b.md).

> ### Tip:  
> [Configure SAML 2.0 Service Provider](configure-saml-2-0-service-provider-51f1f75.md).

> ### Restriction:  
> When a user is with a status `Inactive`, sending reset password e-mail to that user is disabled. For more information, see [Deactivate Users](deactivate-users-99cf468.md).

To send a reset password e-mail, proceed as follows:



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

3.  Choose the user whose password needs to be reset.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

    > ### Remember:  
    > The maximum number of e-mails that can be sent to a user within 24 hours is three. This counter includes also the e-mails sent with passcode for TOTP deactivation. If you send three e-mails within 24 hours, the user will not be able to request a passcode for TOTP deactivation via the profile page during these 24 hours.
    > 
    > If you need to send more e-mails, first reset the password counter. For more information, see [Reset Counter for E-Mail Sending](reset-counter-for-e-mail-sending-08f634b.md).

4.  Choose *Password Details* under the *Authentication* tab.

5.  Press *Send E-Mail*.




<a name="loioda55abf8d0e54eb6825a13777bef4eb1__result_fwb_4vw_t1b"/>

## Results

The user receives an e-mail with information how to reset his or her password. After resetting the password, he or she is able to log on to the account.

