<!-- loio08f634b4f2b24f2badc590406c22c8aa -->

# Reset Counter for Email Sending

You can reset the counter for the number of emails that can be sent to the user.



## Context

By default, Identity Authentication sends up to three emails per 24 hours. If three emails are sent, but it is necessary to send a new email, the tenant administrator must first reset the counter for email sending.

> ### Restriction:  
> When a user is with a status `Inactive`, resetting the counter for that user is disabled. For more information, see [Deactivate Users](deactivate-users-99cf468.md).

To reset the counter for email sending, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  Choose the user whose email counter needs to be reset.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

4.  Choose *Password Details* under the *Authentication* tab.

5.  Press *Reset Counter*.




<a name="loio08f634b4f2b24f2badc590406c22c8aa__result_fwb_4vw_t1b"/>

## Results

The counter for the number of emails that can be sent to the user is reset to zero.

**Related Information**  


[Unlock User Password](unlock-user-password-9172552.md "You can unlock a user password when the user must log on to the application before the automatic unlock time of 60 minutes has passed, or if the Password Locked Period in the password policy is set at unlimited.")

[Send Reset Password Email](send-reset-password-email-da55abf.md "You can trigger the sending of an email to the user with reset password information.")

[Set Initial Password](set-initial-password-16149d5.md "You can set initial password for a user that has already activated his or her account.")

[Send Reset Password Email](send-reset-password-email-da55abf.md "You can trigger the sending of an email to the user with reset password information.")

[Enable Email Verification](enable-email-verification-483d26c.md "Tenant administrators can configure applications to require verification of the user's email address.")

