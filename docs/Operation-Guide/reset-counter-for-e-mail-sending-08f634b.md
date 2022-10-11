<!-- loio08f634b4f2b24f2badc590406c22c8aa -->

# Reset Counter for E-Mail Sending

You can reset the counter for the number of e-mails that can be sent to the user.



## Context

By default, Identity Authentication sends up to three e-mails per 24 hours. If three e-mails are sent, but it is necessary to send a new e-mail, the tenant administrator must first reset the counter for e-mail sending.

> ### Restriction:  
> When a user is with a status `Inactive`, resetting the counter for that user is disabled. For more information, see [Deactivate Users](deactivate-users-99cf468.md).

To reset the counter for e-mail sending, proceed as follows:



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

3.  Choose the user whose e-mail counter needs to be reset.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

4.  Choose *Password Details* under the *Authentication* tab.

5.  Press *Reset Counter*.




<a name="loio08f634b4f2b24f2badc590406c22c8aa__result_fwb_4vw_t1b"/>

## Results

The counter for the number of e-mails that can be sent to the user is reset to zero.

**Related Information**  


[Send Reset Password E-Mail](send-reset-password-e-mail-da55abf.md "You can trigger the sending of an e-mail to the user with reset password information.")

[Enable E-Mail Verification](enable-e-mail-verification-483d26c.md "Tenant administrators can configure applications to require verification of the user's e-mail address.")

