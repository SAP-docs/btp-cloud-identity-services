<!-- loiofe6e30cf1431438a94425e934d0d9e2b -->

# Configure Customer-Controlled Encryption Keys in Administration Console \(Restricted Availability\)



<a name="loiofe6e30cf1431438a94425e934d0d9e2b__prereq_wmk_x5l_vyb"/>

## Prerequisites

-   You have an SAP Data Custodian tenant. For more information, see [SAP Data Custodian Help Guide](https://help.sap.com/docs/sap-data-custodian/help-guide/overview?version=latest) .
-   You have read and accept all Customer-Controlled Encryption Keys \(CCEK\) limitations. For more information, see *Limitations* section in [Customer-Controlled Encryption Keys \(Restricted Availability\)](../Security/customer-controlled-encryption-keys-restricted-availability-177108a.md).
-   You have tested all your scenarios on a test tenant, before activating CCEK on a productive tenant. For more information, see [Tenant Model and Licensing](../tenant-model-and-licensing-93160eb.md).



## Context

> ### Tip:  
> CCEK activation makes the tenant unavailable during the execution of the encryption procedure. Consider scheduling maintenance windows accordingly.
> 
> ****
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Number of Users
> 
> </th>
> <th valign="top">
> 
> Activation Time
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> less than 1 000
> 
> </td>
> <td valign="top">
> 
> less than 1 min
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> between 1 000 and 10 000
> 
> </td>
> <td valign="top">
> 
> between 1 min and 5 min
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> between 10 000 and 100 000
> 
> </td>
> <td valign="top">
> 
> between 10 min and 20 min
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> between 100 000 and 1 000 000
> 
> </td>
> <td valign="top">
> 
> between 100 min and 150 min
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> more than 1 000 000
> 
> </td>
> <td valign="top">
> 
> > ### Note:  
> > Request the activation by reporting an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`.
> 
> 
> 
> </td>
> </tr>
> </table>

> ### Restriction:  
> If Identity Provisioning is enabled, make sure that no provisioning jobs are running during the execution of the encryption procedure. Stop manually triggered jobs and pause the scheduled ones. For more information, see [Start and Stop Provisioning Jobs](https://help.sap.com/docs/identity-provisioning/identity-provisioning/start-and-stop-provisioning-jobs?version=Cloud).

> ### Note:  
> If issues during the encryption procedure, report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`.

To configure the customer-controlled encryption keys via the administration console for SAP Cloud Identity Services, follow the procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *General*, choose the *CCEK Configuration* list item.

4.  Fill in the required information:


    <table>
    <tr>
    <th valign="top">

    Configuration
    
    </th>
    <th valign="top">

    Notes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **API URL**
    
    </td>
    <td valign="top">
    
    The base URL of Data Custodian API \(the URL without the `/kms/v1` or `/kms/v2` suffix\). You can find it in the API Endpoints.txt document you receive when you generate a new key in the Data Custodian API.

    > ### Example:  
    > `https://kms-apiaws-<data custodian kmsname>datacustodian.cloud.sap`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Key ID**
    
    </td>
    <td valign="top">
    
    Data Custodian Key ID. You can find in it in `Key Management Service/General/Iaas Applications/Test_group/Keys/<tenant name>` under the *Details* tab.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Client ID**
    
    </td>
    <td valign="top">
    
    The Access Key you receive with the API Endpoints.txt document when you generate a new key in the Data Custodian API.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Client Secret**
    
    </td>
    <td valign="top">
    
    The Secret Key you receive with the API Endpoints.txt document when you generate a new key in the Data Custodian API.
    
    </td>
    </tr>
    </table>
    
5.  Save your configuration.

6.  Activate the configuration.

    This starts an asynchronous activation of the configuration.


**Related Information**  


[Tenant SAML 2.0 Configuration](tenant-saml-2-0-configuration-e81a19b.md "You as a tenant administrator can view and download the tenant SAML 2.0 metadata. You can also change the name format and update your certificate used by the identity provider to digitally sign the messages for the applications.")

[Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md "You as a tenant administrator can view and configure the tenant OpenID Connect configurations.")

[Change Tenant Texts Via Administration Console](change-tenant-texts-via-administration-console-c24b1d0.md "The change tenant texts option can be used to change the predefined texts and messages for end-user screens available per tenant in Identity Authentication via the administration console.")

[Configure Master Data Texts Via Administration Console](configure-master-data-texts-via-administration-console-c068ac9.md "The master data texts option can be used to configure the predefined master data for each resource in Identity Authentication via the administration console.")

[Configure Links Section on Sign-In Screen](configure-links-section-on-sign-in-screen-060c032.md "You can configure links to appear on the sign-in screen of your applications.")

[Add Instructions Section on Sign-In Screen](add-instructions-section-on-sign-in-screen-c9e717e.md "You can customize the sign-in screen of the Horizon theme with instructions for the user.")

[Configure X.509 Client Certificates for User Authentication](configure-x-509-client-certificates-for-user-authentication-52c7dcb.md "Tenant administrators can configure X.509 client certificates for user authentication as an alternative to authenticating with a user name and a password.")

[Configure Tenant Images](configure-tenant-images-8742046.md "You can configure a custom global logo and, or a background image on the forms for sign-in in, registration, upgrade, password update, and account activation for all applications in a tenant. You can also set a favicon for tenant.")

[Configure Allowed Logon Identifiers](configure-allowed-logon-identifiers-3adf1ff.md "Tenant administrators can choose the allowed logon identifiers for the users.")

[Configure User Identifier Attributes](configure-user-identifier-attributes-8b9fa88.md "Tenant administrators can configure user identifier attributes as required and unique for the tenant.")

[Configure Trust this browser Option](configure-trust-this-browser-option-5b8377e.md "Tenant administrator can set the number of days for which the users won't get prompted for second-factor authentication, if they sign in from the same browser.")

[Enable Back-Up Channels to Send Passcode for Deactivation of TOTP Two-Factor Authentication Devices](enable-back-up-channels-to-send-passcode-for-deactivation-of-totp-two-factor-authenticati-782935e.md "Tenant administrator can configure back-up channels to send TOTP deactivation passcodes to the user.")

[Enable Users to Recover Password with Security Questions](enable-users-to-recover-password-with-security-questions-d9ae898.md "Users can choose to answer security questions to reset their password.")

[Enable Users to Recover Password with PIN Code](enable-users-to-recover-password-with-pin-code-046a235.md "Users can choose to provide PIN code to reset their password.")

[Configure Initial Password and Email Link Validity](configure-initial-password-and-email-link-validity-f8093f4.md "As a tenant administrator, you can configure the validity of the initial password and link sent to a user in the various application processes.")

[Configure Session Timeout](configure-session-timeout-5ca23e4.md "As a tenant administrator, you can configure when the session, created at the Identity Authentication tenant, expires.")

[Configure Trusted Domains](configure-trusted-domains-08fa1fe.md "Service providers that delegate authentication to Identity Authentication can protect their applications when using embedded frames, also called overlays, or when allowing user self-registration.")

[Use Custom Domain in Identity Authentication](use-custom-domain-in-identity-authentication-c4db840.md "Identity Authentication allows you to use a custom domain that is different from the default one (<tenant ID>.accounts.ondemand.com) - for example www.mytenant.com.")

[Change a Tenant's Display Name](change-a-tenant-s-display-name-a513c91.md "You can configure the tenant's name from the administration console for SAP Cloud Identity Services.")

[Configure Default Risk-Based Authentication for All Applications in the Tenant](configure-default-risk-based-authentication-for-all-applications-in-the-tenant-1aab51a.md#loio1aab51ae62b94f79b4c6dac7a00857c2 "You can define rules for authentication according to different risk factors and apply actions like Allow, Deny, and Two-Factor Authentication for all applications in a tenant.")

[Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-3fdc9e1.md "Configure Sinch Service to enable Phone Verification via SMS or SMS Two-Factor Authentication in the administration console.")

[Configure RADIUS Server Settings \(Beta\)](configure-radius-server-settings-beta-03043ae.md "Configure Remote Authentication Dial-In User Service (RADIUS) server settings in the administration console for SAP Cloud Identity Services.")

[Configure Mail Server for Application Processes](configure-mail-server-for-application-processes-ccc7ba1.md "Configure mail server for the emails sent to the end users in the different application processes.")

[Configure IdP-Initiated SSO](configure-idp-initiated-sso-5d59caa.md)

[Send Security Alert Emails](send-security-alert-emails-c977464.md "Send security alert emails to end-users or administrators when changes in their accounts are made.")

[Send System Notifications via Emails](send-system-notifications-via-emails-aa04a8b.md "You can configure the administration console to send emails with information about expiring certificates, system notifications and new administrators to specific email addresses or to the emails of all administrators.")

[Configure Default Language for End User Screens](configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Configure P-User Next Index](configure-p-user-next-index-045bb1c.md "Set the value for the P-user next index.")

[Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](reuse-sap-cloud-identity-services-tenants-for-different-customer-ids-ebd0258.md "You as a tenant administrator can reuse an existing tenant for configurations and automated subscriptions.")
