<!-- loio56cab62fe326483b83a64271f60fef0b -->

# Configure Custom Mail Server

Configure custom mail server for the e-mails sent to the end-users in the different application processes.



<a name="loio56cab62fe326483b83a64271f60fef0b__prereq_nht_ncc_ffb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

The custom mail server must support SSL \(Secure Sockets Layer\). Identity Authentication trusts all certificates from Java SE Runtime Environment 8, therefore the mail server should use only them as a certificate authority when communicating with Identity Authentication. All certificate authorities from the certificate chain must be trusted by Identity Authentication to be able to communicate with the mail server.

> ### Remember:  
> You can have only one mail server configuration. Once you configure the custom mail server, all e-mails will go through this configuration.
> 
> To return to the default settings, remove the configuration.

To configure the custom mail server, follow the procedure below:



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

3.  Choose the *Mail Server Configuration* list item.

4.  Choose the *Custom Mail Server* radio-button.

5.  Enter the required information in all the fields.

6.  Save your entries.

    If the operation is successful, you receive the message ***Configuration saved***.

    > ### Tip:  
    > To return to the default settings, remove the configuration.




**Testing Mail Server Configuration**

Access the profile page at `https://<tenant ID>.accounts.ondemand.com/` from a new browser where you do not have an active session with Identity Authentication. Choose the *Forgot password?* link from the logon page to start the reset password process.

> ### Remember:  
> Only three e-mails are allowed to be sent via Identity Authentication for 24 hour. If you have already reached the limit, the system will not send an e-mail. To check the number of e-mails sent to the user, access *administration console for Identity Authentication* \> *Users & Authorizations* \> *User Management* \> *your user* \> *Authentication* \> *Password Details*. Next to *Password Reset* you can see the number of e-mails sent to the user. If necessary, choose *Reset Counter* to be able to send more e-mails.

If the reset password e-mail is sent successfully, and the configuration is correct, the e-mail that you receive should have as a sender the e-mail specified in the configuration.

If the configuration is not correct, no e-mail is sent.

**Related Information**  


[Configure Amazon Simple Email Service](configure-amazon-simple-email-service-9153d6e.md "Configure mail server for the e-mails sent to the end users in the different application processes.")

[Configuring E-Mail Templates](configuring-e-mail-templates-b2afbcd.md "Tenant administrators can use the default or a custom e-mail template set for the application processes.")

