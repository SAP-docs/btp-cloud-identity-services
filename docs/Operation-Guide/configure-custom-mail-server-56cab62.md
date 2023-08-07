<!-- loio56cab62fe326483b83a64271f60fef0b -->

# Configure Custom Mail Server

Configure custom mail server for the emails sent to the end-users in the different application processes.



<a name="loio56cab62fe326483b83a64271f60fef0b__prereq_nht_ncc_ffb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

The custom mail server must support SSL \(Secure Sockets Layer\). Identity Authentication trusts all certificates from Java SE Runtime Environment 8, therefore the mail server should use only them as a certificate authority when communicating with Identity Authentication. All certificate authorities from the certificate chain must be trusted by Identity Authentication to be able to communicate with the mail server.

> ### Remember:  
> You can have only one mail server configuration. Once you configure the custom mail server, all emails will go through this configuration.
> 
> To return to the default settings, remove the configuration.

To configure the custom mail server, follow the procedure below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *External Services*, choose the *Mail Server Configuration* list item.

4.  Choose the *Custom Mail Server* radio-button.

5.  Enter the required information in all the fields.

    > ### Remember:  
    > SAP is not responsible for the information in the fields. Contact your IT Department for the custom mail server configurations in the administration console.

6.  Save your entries.

    If the operation is successful, you receive the message ***Configuration saved***.

    > ### Tip:  
    > To return to the default settings, remove the configuration.




## Example

**Testing Mail Server Configuration**

Access the profile page at `https://<tenant ID>.accounts.ondemand.com/` from a new browser where you do not have an active session with Identity Authentication. Choose the *Forgot password?* link from the logon page to start the reset password process.

> ### Remember:  
> Only three emails are allowed to be sent via Identity Authentication for 24 hour. If you have already reached the limit, the system will not send an email. To check the number of emails sent to the user, access *administration console for SAP Cloud Identity Services* \> *Users & Authorizations* \> *User Management* \> *your user* \> *Authentication* \> *Password Details*. Next to *Password Reset* you can see the number of emails sent to the user. If necessary, choose *Reset Counter* to be able to send more emails.

If the reset password email is sent successfully, and the configuration is correct, the email that you receive should have as a sender the email specified in the configuration.

If the configuration is not correct, no email is sent.

**Related Information**  


[Configure Amazon Simple Email Service](configure-amazon-simple-email-service-9153d6e.md "Configure mail server for the emails sent to the end users in the different application processes.")

[Configuring Email Templates](configuring-email-templates-b2afbcd.md "Tenant administrators can use the default or a custom email template set for the application processes.")

