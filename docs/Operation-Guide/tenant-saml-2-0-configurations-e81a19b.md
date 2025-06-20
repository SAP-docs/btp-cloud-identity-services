<!-- loioe81a19b0067f4646982d7200a8dab3ca -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Tenant SAML 2.0 Configurations

You as a tenant administrator can view and download the tenant SAML 2.0 metadata. You can also change the name format and update your certificate used by the identity provider to digitally sign the messages for the applications.



<a name="loioe81a19b0067f4646982d7200a8dab3ca__prereq_wcy_1vf_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

> ### Note:  
> The signing certificate is one and the same for SAML 2.0 and OpenId Connect. Note that a change in one of the configurations will also affect the other one.

> ### Remember:  
> The signature and digest methods in the XML of the metadata file depend on the signing certificate, which is configured for the identity provider.
> 
> > ### Remember:  
> > It takes 2 minutes for the configuration changes to take place.

To view and download the tenant SAML 2.0 metadata, or to change the name format, or the default certificate, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Single Sign-On*, choose the *SAML 2.0 Configuration* list item.

    The *SAML 2.0 Configuration* page that opens displays the name of the identity provider, its endpoints, and its signing certificate.

4.  **Optional:** To download the identity provider's metadata, press the *Download Metadata File* button and choose one of the options.

    -   *Default-certificate*
    -   *Non-default certificate*
    -   *All certificates*

5.  **Optional:** To change the name of the identity provider, choose under the *Identity Provider Settings* tab the *Edit* button next to the *Name* field, select the name from the dropdown list, and save your changes.

    The drop-down list offers the following options:


    <table>
    <tr>
    <th valign="top">

    Issuer
    
    </th>
    <th valign="top">

    Notes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Default Issuer format
    
    </td>
    <td valign="top">
    
    https://<tenant ID\>.accounts.ondemand.com
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Legacy Issuer format
    
    </td>
    <td valign="top">
    
    <tenant ID\>.accounts.ondemand.com
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Common domain
    
    </td>
    <td valign="top">
    
    https://<tenant ID\>.accounts.cloud.sap
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Custom Domain \(if configured\)
    
    </td>
    <td valign="top">
    
    <custom domain host\>
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Tenants in China region
    
    </td>
    <td valign="top">
    
    https:// <tenant ID\>.accounts.sapcloud.cn
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > Tenant ID is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the tenant ID.

    > ### Remember:  
    > Change the name of the identity provider on the service provider side, or the name of the identity provider on the corporate identity provider side, every time you change the name format of the identity provider in the administration console. If you have set trusts with more than one service provider, or corporate identity provider, change the name in every provider. For more information about how to edit the name, see the documentation of the respective service or corporate identity providers.

    If the change of the name is successful, the system displays the message ***Tenant <name of tenant\> updated***.

6.  **Optional:** To update your signing certificate, choose under the *Signing Certificates* tab the *\+Add* button on the right. You can choose from the following options:

    -   *Regenerate the existing certificate with new validity, reusing the same private key* \> *Next Step* \> *Choose validity from the drop down* \> *Next Step* \> *Finish*.

        > ### Note:  
        > The validity period can be 3, 5 and 10 years.

    -   *Create new a self-signed certificate with a new private key and the same Subject DN* \> *Next Step* \> *Select key size* \> *Choose validity from the drop down* \> *Next Step* \> *Finish*.

        > ### Note:  
        > The key size can be 2048, 3072 and 4096. The validity period can be 3, 5 and 10 years.

    -   *Download your Certificate Signing Request* \> *Next Step* \> *add Subject DN and select key size and validity from the options* \> *Next Step* \> *Download CSR*. Use the downloaded .csr file to generate a certificate from the trusted CA. Copy the newly generated certificate, choose :pencil2:, and paste the certificate as text in the *Certificate Information* field.

        > ### Note:  
        > The signing algorithm can be SHA-256 and SHA-384. The key size can be 2048, 3072 and 4096.





<a name="loioe81a19b0067f4646982d7200a8dab3ca__postreq_ghg_tzy_xqb"/>

## Next Steps

To change the default certificate for the tenant, choose *Edit* \> *the new certificate from the list* \> *Save*.

> ### Caution:  
> When you change the default certificate for the tenant, you must also update the trust with the service provider. For more information see [Configure SAML 2.0 Service Provider](configure-saml-2-0-service-provider-51f1f75.md).

**Related Information**  


[Get SAML 2.0 IdP Metadata via Parameter](get-saml-2-0-idp-metadata-via-parameter-2c76690.md "Tenant administrator can get the SAML 2.0 metadata via specific parameters.")

[Rotate Signing Certificates](rotate-signing-certificates-6621ad5.md "Tenant administrators must replace existing signing certificates with new ones before they expire. This ensures uninterrupted and secure communication between SAML 2.0 applications (referred to as service providers) and Identity Authentication as the identity provider.")

[Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md "You as a tenant administrator can view and configure the tenant OpenID Connect configurations.")

[Change Tenant Texts Via Administration Console](change-tenant-texts-via-administration-console-c24b1d0.md "The change tenant texts option can be used to change the predefined texts and messages for end-user screens available per tenant in Identity Authentication via the administration console.")

[Configure Master Data Texts Via Administration Console](configure-master-data-texts-via-administration-console-c068ac9.md "The master data texts option can be used to configure the predefined master data for each resource in Identity Authentication via the administration console.")

[Configure Links Section on Sign-In Screen](configure-links-section-on-sign-in-screen-060c032.md "You can configure links to appear on the sign-in screen of your applications.")

[Add Instructions Section on Sign-In Screen](add-instructions-section-on-sign-in-screen-c9e717e.md "You can customize the sign-in screen of the Horizon theme with instructions for the user.")

[Configure X.509 Client Certificates for User Authentication](configure-x-509-client-certificates-for-user-authentication-52c7dcb.md "Tenant administrators can configure X.509 client certificates for user authentication as an alternative to authenticating with a user name and a password.")

[Enable Users to Generate and Authenticate with Certificates](enable-users-to-generate-and-authenticate-with-certificates-4cf818a.md "Allow users to generate and authenticate with certificates.")

[Configure Tenant Images](configure-tenant-images-8742046.md "You can configure a custom global logo and, or a background image on the forms for sign-in in, registration, upgrade, password update, and account activation for all applications in a tenant. You can also set a favicon for tenant.")

[Configure Allowed Logon Identifiers](configure-allowed-logon-identifiers-3adf1ff.md "Tenant administrators can choose the allowed logon identifiers for the users.")

[Configure User Identifier Attributes](configure-user-identifier-attributes-8b9fa88.md "Tenant administrators can configure user identifier attributes as required and unique for the tenant.")

[Configure Trust this browser Option](configure-trust-this-browser-option-5b8377e.md "Tenant administrator can set the number of days for which the users won't get prompted for second-factor authentication, if they sign in from the same browser.")

[Enable Back-Up Channels to Send Passcode for Deactivation of TOTP Two-Factor Authentication Devices](enable-back-up-channels-to-send-passcode-for-deactivation-of-totp-two-factor-authenticati-782935e.md "Tenant administrator can configure back-up channels to send TOTP deactivation passcodes to the user.")

[Password Recovery Options](password-recovery-options-777cee1.md "Enable users to reset their password via security questions, PIN code, or email link.")

[Configure Initial Password and Email Link Validity](configure-initial-password-and-email-link-validity-f8093f4.md "As a tenant administrator, you can configure the validity of the initial password and link sent to a user in the various application processes.")

[Configure Session Timeout](configure-session-timeout-5ca23e4.md "As a tenant administrator, you can configure when the session, created at the Identity Authentication tenant, expires.")

[Configure Trusted Domains](configure-trusted-domains-08fa1fe.md "Service providers that delegate authentication to Identity Authentication can protect their applications when using embedded frames, also called overlays, or when allowing user self-registration.")

[Use Custom Domain in Identity Authentication](use-custom-domain-in-identity-authentication-c4db840.md "Identity Authentication allows you to use a custom domain that is different from the default ones (<tenant ID>.accounts.ondemand.com or <tenant ID>.accounts.cloud.sap) - for example www.mytenant.com.")

[Change a Tenant's Display Name](change-a-tenant-s-display-name-a513c91.md "You can configure the tenant's name from the administration console for SAP Cloud Identity Services.")

[Configure Default Risk-Based Authentication for All Applications in the Tenant](configure-default-risk-based-authentication-for-all-applications-in-the-tenant-1aab51a.md#loio1aab51ae62b94f79b4c6dac7a00857c2 "You can define rules for authentication according to different risk factors and apply actions like Allow, Deny, and Two-Factor Authentication for all applications in a tenant.")

[Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-3fdc9e1.md "Configure Sinch Service to enable Phone Verification via SMS or SMS Two-Factor Authentication in the administration console.")

[Configure RADIUS Server Settings \(Beta\)](configure-radius-server-settings-beta-03043ae.md "Configure Remote Authentication Dial-In User Service (RADIUS) server settings in the administration console for SAP Cloud Identity Services.")

[Configure Mail Server for Application Processes](configure-mail-server-for-application-processes-ccc7ba1.md "Configure mail server for the emails sent to the end users in the different application processes.")

[Configure IdP-Initiated SSO](configure-idp-initiated-sso-5d59caa.md "Enable or disable IdP-Initiated SSO via the administration console for SAP Cloud Identity Services.")

[Send Security Alert Emails](send-security-alert-emails-c977464.md "Send security alert emails to end-users or administrators when changes in their accounts are made.")

[Enable Password Expiration Reminder](enable-password-expiration-reminder-a8de1be.md "Enable password expiration reminder for SAP Cloud Identity Services to ensure the users are aware that a password change is due.")

[Send System Notifications via Emails](send-system-notifications-via-emails-aa04a8b.md "You can configure the administration console to send emails with information about expiring certificates, system notifications, new administrators, and new applications to specific email addresses or to the emails of all administrators.")

[Configure Customer Managed Keys in Administration Console \(Restricted Availability\)](configure-customer-managed-keys-in-administration-console-restricted-availability-fe6e30c.md "")

[Configure Default Language for End User Screens](configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Configure P-User Next Index](configure-p-user-next-index-045bb1c.md "Set the value for the P-user next index.")

[Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](reuse-sap-cloud-identity-services-tenants-for-different-customer-ids-ebd0258.md "You as a tenant administrator can reuse an existing tenant for configurations and automated subscriptions.")

[Configuring Tenant Settings](configuring-tenant-settings-d4d6fdc.md "Initially, the tenants are configured to use default settings. This section describes how you as a tenant administrator can make custom tenant configurations.")

