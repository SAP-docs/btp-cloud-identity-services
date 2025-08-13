<!-- loio52c7dcb7bbb94f38ab75a4cc9a8cbe03 -->

# Configure X.509 Client Certificates for User Authentication

Tenant administrators can configure X.509 client certificates for user authentication as an alternative to authenticating with a user name and a password.



<a name="loio52c7dcb7bbb94f38ab75a4cc9a8cbe03__prereq_ofg_hzf_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

User authentication with a trusted X.509 certificate takes place using the underlying Secure Sockets Layer \(SSL\) protocol and users don’t need to enter a password for their logon.

Certificates for API Authentication cannot be used for user authentication.

Remember that it may take between two and four weeks to enable the certificate.

> ### Note:  
> If you want to configure a certificate, using your own trusted CA, for example for scenarios like authentication of technical users or OAuth clients, skip the procedure in this document and report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`. Attach to the incident the root and intermediate certificates and provide the Identity Authentication tenant host.
> 
> If you already have a trusted CA added to your tenant, but after that a custom domain has been configured for that tenant, report a new incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS` to update the certificate on the custom domain as well.

> ### Caution:  
> If the users have generated their own certificates via the profile page, they won't be able to authenticate with the configured X.509 client certificate, and vice versa.



### Edit and Delete Certificates

If you want to edit an already configured certificate, choose certificate, choose the *Edit* button, make your changes and save them.

> ### Remember:  
> If you have made changes to the root certificate, report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`, attach to the incident the root and intermediate certificates, and provide the Identity Authentication tenant host.

If you want to delete an already configured certificate, choose the certificate, choose the *Delete* button, and report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS` providing the Identity Authentication tenant host.

To configure a trusted X.509 certificate, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Authentication*, choose the *Trusted Certificate Configuration* list item.

4.  Choose the *\+Add* button.

5.  Enter the name of the certificate.

    > ### Note:  
    > The name and the *Subject DN* must be unique.

6.  Choose one of the following options:


    <table>
    <tr>
    <th valign="top">

    Certificate Options
    
    </th>
    <th valign="top">

    Notes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Upload Certificate**
    
    </td>
    <td valign="top">
    
    The uploaded certificates must be in `PEM` format. Use `.cer` or `.crt` files.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Root Certificate**
    
    </td>
    <td valign="top">
    
    Insert the public key in the text field.
    
    </td>
    </tr>
    </table>
    
7.  Choose one of the following source options:

    -   *Distinguished Name* - If selected *Distinguished Name* as source, the pattern must match the *Subject DN* of the user certificate. The *CN* attribute from the *DN Pattern* can take the following formats:
        -   `CN=${<logonIdentifier>}`. In this case the CN must completely map to one of the supported logon identifiers, `loginName`, `uid`, and `mail`.

            > ### Example:  
            > CN=$\{loginName\},O=Management,C=US.

        -   `CN=${mail:<user_email>}`. This case allows you to specify a unique DN pattern for single user authentication.

            > ### Example:  
            > CN=$\{mail:dona.moore@example.com\},O=Management,C=US.


    -   *Subject Alternative Name - Other Name* - If selected *Subject Alternative Name - Other Name*, the pattern must match the `subjectAltName` extension entry of type `otherName` \(Microsoft User Principal Name form\) of the user certificate. The pattern for SAN value must be in format `${<logonIdentifier>}` and must completely map to one of the supported logon identifiers, `loginName`, `uid`, and `mail`.

        > ### Example:  
        > `${loginName}`

    -   *Subject Alternative Name - Email \(RFC822 Name\)* - If selected *Subject Alternative Name - Email \(RFC822 Name\)*, the pattern must match the `subjectAltName` extension entry of type `rfc822Name` of the user certificate. The pattern for SAN value must be in format `${mail}`.

    Two configurations with different source options in one Identity Authentication tenant are not supported.

8.  Enter the *Pattern* of the certificate.

    > ### Note:  
    > If you want to log on with a certificate where the common name contains the user ID \(for example: `Subject DN: CN=P000000,O=MyOrg,C=US`\) then the pattern value must be: `CN=${uid},O=MyOrg,C=US`.
    > 
    > If you want to log on with a certificate where the common name contains the email of the user \(for example: `Subject DN: CN=my_email@example.com,O=MyORG,C=US`\), then the pattern value must be: `CN=${mail},O=M,C=US`.

9.  Choose the *\+Add* button.

10. To add the certificate to your tenant, report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`. The SAP Cloud Root CA certificates are trusted by default.

    1.  Attach to the incident the root and intermediate certificates.

    2.  Provide the Identity Authentication tenant host.


    > ### Remember:  
    > The following certificates are trusted by default:
    > 
    > ****
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > CA Display Name
    > 
    > </th>
    > <th valign="top">
    > 
    > Subject
    > 
    > </th>
    > <th valign="top">
    > 
    > Serial number
    > 
    > </th>
    > <th valign="top">
    > 
    > Expiry Date
    > 
    > MM-DD-YYYY
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > SAP Cloud Root CA
    > 
    > </td>
    > <td valign="top">
    > 
    > CN=SAP Cloud Root CA, O=SAP SE, L=Walldorf, C=DE
    > 
    > </td>
    > <td valign="top">
    > 
    > 18 77 0f be 65 06 6b bf 4c ea 93 38 d9 b1 85 62
    > 
    > </td>
    > <td valign="top">
    > 
    > 02-13-‎‎2039
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > DigiCert Global Root CA
    > 
    > </td>
    > <td valign="top">
    > 
    > CN=DigiCert Global Root CA, OU=www.digicert.com, O=DigiCert Inc, C=US
    > 
    > </td>
    > <td valign="top">
    > 
    > 08 3b e0 56 90 42 46 b1 a1 75 6a c9 59 91 c7 4a
    > 
    > </td>
    > <td valign="top">
    > 
    > 11-10-‎‎2031
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > DigiCert Global Root G2
    > 
    > </td>
    > <td valign="top">
    > 
    > CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US
    > 
    > </td>
    > <td valign="top">
    > 
    > 03 3a f1 e6 a7 11 a9 a0 bb 28 64 b1 1d 09 fa e5
    > 
    > </td>
    > <td valign="top">
    > 
    > 01-15-‎‎‎2038
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > DigiCert TLS RSA SHA256 2020 CA1
    > 
    > </td>
    > <td valign="top">
    > 
    > CN=DigiCert Global G2 TLS RSA SHA256 2020 CA1, O=DigiCert Inc, C=US
    > 
    > </td>
    > <td valign="top">
    > 
    > 0c f5 bd 06 2b 56 02 f4 7a b8 50 2c 23 cc f0 66
    > 
    > </td>
    > <td valign="top">
    > 
    > 03-30-2031
    > 
    > </td>
    > </tr>
    > </table>


**Related Information**  


[Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md "You as a tenant administrator can view and download the tenant SAML 2.0 metadata. You can also change the name format and update your certificate used by the identity provider to digitally sign the messages for the applications.")

[Get SAML 2.0 IdP Metadata via Parameter](get-saml-2-0-idp-metadata-via-parameter-2c76690.md "Tenant administrator can get the SAML 2.0 metadata via specific parameters.")

[Rotate Signing Certificates](rotate-signing-certificates-6621ad5.md "Tenant administrators must replace existing signing certificates with new ones before they expire. This ensures uninterrupted and secure communication between SAML 2.0 applications (referred to as service providers) and Identity Authentication as the identity provider.")

[Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md "You as a tenant administrator can view and configure the tenant OpenID Connect configurations.")

[Change Tenant Texts Via Administration Console](change-tenant-texts-via-administration-console-c24b1d0.md "The change tenant texts option can be used to change the predefined texts and messages for end-user screens available per tenant in Identity Authentication via the administration console.")

[Configure Master Data Texts Via Administration Console](configure-master-data-texts-via-administration-console-c068ac9.md "The master data texts option can be used to configure the predefined master data for each resource in Identity Authentication via the administration console.")

[Configure Links Section on Sign-In Screen](configure-links-section-on-sign-in-screen-060c032.md "You can configure links to appear on the sign-in screen of your applications.")

[Add Instructions Section on Sign-In Screen](add-instructions-section-on-sign-in-screen-c9e717e.md "You can customize the sign-in screen of the Horizon theme with instructions for the user.")

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

[Configure Allowed Logon Identifiers](configure-allowed-logon-identifiers-3adf1ff.md "Tenant administrators can choose the allowed logon identifiers for the users.")

[SAP Note 2801396](https://me.sap.com/notes/2801396 "SAP Global Trust List")

