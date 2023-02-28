<!-- loio9153d6ef5f3441da8f0633a3f009d86d -->

# Configure Amazon Simple Email Service

Configure mail server for the e-mails sent to the end users in the different application processes.



<a name="loio9153d6ef5f3441da8f0633a3f009d86d__prereq_nht_ncc_ffb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

By using *Amazon Simple Email Service* you can modify the sender and receiver of the e-mail without the need to have a custom mail server.

To use the Amazon Simple Email Service with custom domain, you must own the domain.

If you don't have an own domain you can use the domain, which is the default one, and just modify the `<username>` part in the *From* and *Reply to* fields. You can add up to two domains in addition to the default one.

Once the tenant administrator configures the mail server, all e-mails will go through this configuration.

> ### Remember:  
> To return to the default settings, remove the configuration.
> 
> Note that it takes two minutes for each configuration change to be applied.

To configure the mail server, follow the procedure below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page you can view the administrative and license relevant information of the tenant.

3.  Choose the *Mail Server Configuration* list item.

4.  Choose the *Amazon Simple Email Service* radio-button

5.  **Optional:** To use the Amazon Simple Email Service with custom domain, аdd a valid domain name in the dialog box that appears.

    1.  Copy the TXT and CNAME records that are created in the administration console for SAP Cloud Identity Services and enter them in the DNS server.

    2.  Choose *Verify* to check the status of the domain in the administration console.

        Domain verification may take up to 72 hours to complete \(usually it takes around 5 minutes\).

        Status of the domain will change from *Pending* to *Verified* if Amazon has verified the domain, otherwise it will change to *Failed* after 72 hours.

        If you want to start the verification process again, you need to delete the domain and add it again.


6.  Configure the <username\> parts in the *From* and *Reply to* fields under *Communication E-Mails*.

    > ### Note:  
    > The <username\> part of the e-mail address can have the following:
    > 
    > -   uppercase and lowercase Latin letters
    > 
    > -   digits from 0 to 9
    > 
    > -   special characters !\#$%&'\*+-/=?^\_\`\{|\}~
    > 
    > 
    > The <domain\> part of the e-mail address can have the following:
    > 
    > -   uppercase and lowercase Latin letters
    > 
    > -   digits from 0 to 9
    > 
    > -   hyphen
    > 
    > 
    > You can't specify a hyphen at the beginning or end.

    > ### Caution:  
    > If you have more than one verified domain, make sure that you have selected the correct ones from the drop down in the domain part under *Communication E-Mails*.

7.  Save your entries.

    If the operation is successful, you receive the message ***Configuration saved***.

    > ### Tip:  
    > To return to the default settings, remove the configuration.




**Testing Mail Server Configuration**

Access the profile page at `https://<tenant ID>.accounts.ondemand.com/` from a new browser where you do not have an active session with Identity Authentication. Choose the *Forgot password?* link from the logon page to start the reset password process.

> ### Remember:  
> Only three e-mails are allowed to be sent via Identity Authentication for 24 hour. If you have already reached the limit, the system will not send an e-mail. To check the number of e-mails sent to the user, access *administration console for SAP Clou Identity Services* \> *Users & Authorizations* \> *User Management* \> *your user* \> *Authentication* \> *Password Details*. Next to *Password Reset* you can see the number of e-mails sent to the user. If necessary, choose *Reset Counter* to be able to send more e-mails.

If the reset password e-mail is sent successfully, and the configuration is correct, the e-mail that you receive should have as a sender the e-mail specified in the configuration.

If the configuration is not correct, no e-mail is sent.

**Related Information**  


[Configure Custom Mail Server](configure-custom-mail-server-56cab62.md "Configure custom mail server for the e-mails sent to the end-users in the different application processes.")

[Configuring E-Mail Templates](configuring-e-mail-templates-b2afbcd.md "Tenant administrators can use the default or a custom e-mail template set for the application processes.")

