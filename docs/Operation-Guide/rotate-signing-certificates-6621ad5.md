<!-- loio6621ad5868a3429d8b79f0c3c188e585 -->

# Rotate Signing Certificates

Tenant administrators must replace existing signing certificates with new ones before they expire. This ensures uninterrupted and secure communication between SAML 2.0 applications \(referred to as service providers\) and Identity Authentication as the identity provider.



## Context

You have received an email notification that your signing certificate is about to expire. You need to create a new one and configure the service provider to use it. Proceed as follows:



## Procedure

1.  Create a new signing certificate.

    1.  Sign in to the administration console for SAP Cloud Identity Services.

    2.  Navigate to *Applications and Resources* \> *Tenant Settings* \> *Single Sign-On* \> *SAML 2.0 Configuration* and add a new certificate. See: [Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md) → *Step 6*.


2.  Configure the service provider to use the new certificate.

    > ### Note:  
    > In case there are many applications, the recommended approach is to renew the certificate for one application at a time following this procedure, as this will minimize or reduce the potential for customer downtime.

    1.  Navigate to *Applications and Resources* \> *Applications* and select the application for which you want to update the trust configuration.

    2.  Under *Trust* \> *Single Sign-On* \> *SAML 2.0 Configuration* \> *Identity Provider Certificate*, select the new certificate and save your configuration.

        > ### Note:  
        > It takes approximately 2 minutes for the new certificate to appear under the trust configuration of the given application.


3.  Upload the new certificate to the backend of the trusted application.

    1.  Navigate to *Applications and Resources* \> *Tenant Settings* \> *Single Sign-On* \> *SAML 2.0 Configuration*.

    2.  Proceed according to your use case below.



    <table>
    <tr>
    <th valign="top">

    Applications
    
    </th>
    <th valign="top">

    Procedure
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Your applications support metadata
    
    </td>
    <td valign="top">
    
    1.  Download the metadata with this certificate in one of the following ways:

        -   Get the SAML 2.0 tenant metadata containing the identity provider certificate by calling the `https://<tenant ID>.<tenant domain>/saml2/metadata` endpoint and provide the `sp_name` parameter, as described in [Get SAML 2.0 IdP Metadata via Parameter](get-saml-2-0-idp-metadata-via-parameter-2c76690.md).

        -   Download the metadata with the new certificate \(which is still a non-default one\), as described in [Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md) → *Step 4*


    2.  Upload this metadata to the backend of the application for which you have updated the trust configuration in step 2.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Your applications support certificate file
    
    </td>
    <td valign="top">
    
    1.  Under *Signing Certificates*, choose the *Download* icon next to the new certificate.

    2.  Upload this certificate file to the backend of the application for which you have updated the trust configuration in step 2.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Your applications support certificate as text
    
    </td>
    <td valign="top">
    
    1.  Under *Signing Certificates*, choose the *Display* icon next to the new certificate.

    2.  Copy and paste the certificate to the backend of the application for which you have updated the trust configuration in step 2.



    
    </td>
    </tr>
    </table>
    
4.  After updating the trust configuration for each application, set the new certificate as the default.

    Under *Tenant Settings* \> *Single Sign-On* \> *SAML 2.0 Configuration* \> *Signing Certificates*, select the new certificate and save your configuration.


**Related Information**  


[Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md "You as a tenant administrator can view and download the tenant SAML 2.0 metadata. You can also change the name format and update your certificate used by the identity provider to digitally sign the messages for the applications.")

[Get SAML 2.0 IdP Metadata via Parameter](get-saml-2-0-idp-metadata-via-parameter-2c76690.md "Tenant administrator can get the SAML 2.0 metadata via specific parameters.")

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

[Configure IdP-Initiated SSO](configure-idp-initiated-sso-5d59caa.md)

[Send Security Alert Emails](send-security-alert-emails-c977464.md "Send security alert emails to end-users or administrators when changes in their accounts are made.")

[Send System Notifications via Emails](send-system-notifications-via-emails-aa04a8b.md "You can configure the administration console to send emails with information about expiring certificates, system notifications, new administrators, and new applications to specific email addresses or to the emails of all administrators.")

[Configure Customer Managed Keys in Administration Console \(Restricted Availability\)](configure-customer-managed-keys-in-administration-console-restricted-availability-fe6e30c.md "")

[Configure Default Language for End User Screens](configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Configure P-User Next Index](configure-p-user-next-index-045bb1c.md "Set the value for the P-user next index.")

[Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](reuse-sap-cloud-identity-services-tenants-for-different-customer-ids-ebd0258.md "You as a tenant administrator can reuse an existing tenant for configurations and automated subscriptions.")
