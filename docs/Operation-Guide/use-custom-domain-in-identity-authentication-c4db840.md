<!-- loioc4db840ff2464e12ab68d94efb0769c3 -->

# Use Custom Domain in Identity Authentication

Identity Authentication allows you to use a custom domain that is different from the default ones \(`<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`\) - for example `www.mytenant.com`.



<a name="loioc4db840ff2464e12ab68d94efb0769c3__prereq_yt4_mqv_zkb"/>

## Prerequisites

-   You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You must have a custom domain.

    > ### Note:  
    > Internationalized domain names \(IDNs\) are not supported.

-   You must have configured the CNAME DNS record on your domain to point to the host name used to access Identity Authentication. The host name can be one of the following, depending on where client's tenant is located:

    **Host Names**


    <table>
    <tr>
    <th valign="top">

    Country/Region
    
    </th>
    <th valign="top">

    Data Center
    
    </th>
    <th valign="top">

    Infrastructure
    
    </th>
    <th valign="top">

    Host Name
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Australia
    
    </td>
    <td valign="top">
    
    Australia \(Sydney\)
    
    </td>
    <td valign="top">
    
    SAP / Azure
    
    </td>
    <td valign="top">
    
    `ap.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Brazil
    
    </td>
    <td valign="top">
    
    Brazil \(São Paulo\)
    
    </td>
    <td valign="top">
    
    AWS
    
    </td>
    <td valign="top">
    
    `br.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    China
    
    </td>
    <td valign="top">
    
    China

    \(Shanghai\)
    
    </td>
    <td valign="top">
    
    SAP
    
    </td>
    <td valign="top">
    
    `accounts.sapcloud.cn.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Europe
    
    </td>
    <td valign="top">
    
    Germany \(Frankfurt\)
    
    </td>
    <td valign="top">
    
    AWS
    
    </td>
    <td valign="top">
    
    `aws-eu-de.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Europe
    
    </td>
    <td valign="top">
    
    Europe \(Frankfurt / Amsterdam\)\)
    
    </td>
    <td valign="top">
    
    SAP
    
    </td>
    <td valign="top">
    
    `accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    India
    
    </td>
    <td valign="top">
    
    India \(Mumbai\)
    
    </td>
    <td valign="top">
    
    AWS
    
    </td>
    <td valign="top">
    
    `aws-ap-in.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Israel
    
    </td>
    <td valign="top">
    
    Israel \(Tel Aviv\)
    
    </td>
    <td valign="top">
    
    Google Cloud
    
    </td>
    <td valign="top">
    
    `il.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Japan
    
    </td>
    <td valign="top">
    
    Japan \(Tokyo / Osaka\)
    
    </td>
    <td valign="top">
    
    SAP
    
    </td>
    <td valign="top">
    
    `jp.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    North America \(Canada Central\)
    
    </td>
    <td valign="top">
    
    Canada \(Toronto\)
    
    </td>
    <td valign="top">
    
    Azure
    
    </td>
    <td valign="top">
    
    `azr-na-ca.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Saudi Arabia \(SA1\)
    
    </td>
    <td valign="top">
    
    Saudi Arabia \(Dammam\)
    
    </td>
    <td valign="top">
    
    Google Cloud
    
    </td>
    <td valign="top">
    
    `sa.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Saudi Arabia \(SA2\)
    
    </td>
    <td valign="top">
    
    Saudi Arabia \(Dammam\) - Regulated
    
    </td>
    <td valign="top">
    
    Google Cloud
    
    </td>
    <td valign="top">
    
    `sa2.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Singapore
    
    </td>
    <td valign="top">
    
    Singapore
    
    </td>
    <td valign="top">
    
    AWS
    
    </td>
    <td valign="top">
    
    `aws-ap-se-1.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    South Korea
    
    </td>
    <td valign="top">
    
    South Korea \(Seoul\)
    
    </td>
    <td valign="top">
    
    AWS
    
    </td>
    <td valign="top">
    
    `aws-ap-kr.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Switzerland
    
    </td>
    <td valign="top">
    
    Switzerland \(Zürich\)
    
    </td>
    <td valign="top">
    
    Azure
    
    </td>
    <td valign="top">
    
    `azr-eu-ch.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    United Arab Emirates
    
    </td>
    <td valign="top">
    
    United Arab Emirates \(Dubai\)
    
    </td>
    <td valign="top">
    
    SAP
    
    </td>
    <td valign="top">
    
    `azr-ap-ae.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    United Kingdom
    
    </td>
    <td valign="top">
    
    United Kingdom \(London\)
    
    </td>
    <td valign="top">
    
    Azure
    
    </td>
    <td valign="top">
    
    `uk.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    US \(North America East\)
    
    </td>
    <td valign="top">
    
    USA \(Sterling, VA / N. Virginia\)
    
    </td>
    <td valign="top">
    
    SAP
    
    </td>
    <td valign="top">
    
    `us-east.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    US East

    > ### Note:  
    > Trial environment.


    
    </td>
    <td valign="top">
    
    Trial \(USA\)
    
    </td>
    <td valign="top">
    
    Azure
    
    </td>
    <td valign="top">
    
    `trial-accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    US West
    
    </td>
    <td valign="top">
    
    USA \(Quincy, WA\)
    
    </td>
    <td valign="top">
    
    Azure
    
    </td>
    <td valign="top">
    
    `azr-us-we.accounts.ondemand.com.cloud.sap.akadns.net`
    
    </td>
    </tr>
    </table>
    



<a name="loioc4db840ff2464e12ab68d94efb0769c3__context_xj4_tb4_5qb"/>

## Context

> ### Note:  
> If you have configured a custom domain and you want to add a deprecation trial token for third party cookies deprecation go to **Step 10**.

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.



<a name="loioc4db840ff2464e12ab68d94efb0769c3__steps_ip4_f5y_2lb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Customization*, choose the *Custom Domain* list item.

4.  Provide the required information in the provided fields:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Information
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Domain*
    
    </td>
    <td valign="top">
    
    The host of your custom domain
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *DN*

    > ### Note:  
    > The `DN` used for the domain certificate.


    
    </td>
    <td valign="top">
    
    -   `CN` \(CommonName\) - mandatory

        > ### Note:  
        > The `CN` attribute must match the custom domain used for the domain certificate.

    -   `OU` \(OrganizationalUnit\) - optional

    -   `O` \(Organization\) - optional

    -   `L` \(Locality\) - optional

    -   `S` \(StateOrProvinceName\) - optional

    -   `C` \(CountryName\) - optional



    
    </td>
    </tr>
    </table>
    
5.  Save your configuration.

6.  Choose the *Download CSR file* used for the domain certificate.

    1.  Select the size of the certificate key. The supported key sizes are 2048, 3072 and 4096. The default value is 3072.

    2.  **Optional:** Add an additional subject alternative name to the CSR.

    3.  Choose the *Download* button and save the generated CSR file.


    > ### Note:  
    > Use this CSR for the custom domain certificate. Each download generates a new key pair for the CSR. Always use the last downloaded CSR file.

7.  Send the CSR to a trusted Certificate Authority to sign the certificate.

    > ### Note:  
    > The supported algorithms are SHA-256, SHA-384 and SHA-512.

8.  Access the tenant's administration console for SAP Cloud Identity Services *Applications and Resources* \> *Tenant Settings* \> *Custom Domain* \> *Certificate* and upload or insert as text the SSL certificate signed by the trusted CA.

    > ### Note:  
    > Make sure that the subject DN in the domain certificate and the configured subject DN match exactly.
    > 
    > You can upload the domain certificate or the complete certificate chain. The certificate chain must contain the domain certificate, the intermediate certificate or certificates, and the trusted CA root certificate in the same order.

9.  Save your configuration.

10. **Optional:** Add the third-party cookies deprecation trial token in the input field and save the configuration.

    > ### Tip:  
    > For more information about how to get the third-party cookies deprecation trial token, see [Deprecation trials](https://developers.google.com/privacy-sandbox/blog/third-party-cookie-deprecation-trial#deprecation_trials).




<a name="loioc4db840ff2464e12ab68d94efb0769c3__result_k4j_fgz_2lb"/>

## Results

The custom domain configuration is enabled with the upgrade of Identity Authentication. We recommend you to renew your certificate as early as possible, preferably 30 days before expiration, and no later than the Sunday before productive system upgrade. Identity Authentication has production releases \(bi-weekly updates\) and immediate updates:

-   **Bi-weekly updates** \(standard\) - planned each second Tuesday at 14:00 UTC.
-   **Immediate updates** - in case of fixes required for bugs that affect productive application operations, or due to urgent security fixes.

For more information on the upgrade calendar of the service, see SAP Note [3409744](https://me.sap.com/notes/3409744) \(Release Schedule for SAP Cloud Identity Services \(SAP BTP\)\).



<a name="loioc4db840ff2464e12ab68d94efb0769c3__postreq_b2c_njz_2lb"/>

## Next Steps

1.  \(Optional\) Configure tenant's name to be the custom host. Select custom host for the name from the dropdown list in the SAML 2.0 or Open ID Connect Configuration settings. For more information, see [Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md) [Tenant OpenID Connect \(OIDC\) Configurations](tenant-openid-connect-oidc-configurations-3d6abcc.md).

    > ### Caution:  
    > After you select the custom host in the administration console, make sure that you also change the name of the identity provider on the service provider side, or the name of the identity provider on the corporate identity provider side. If you have set trusts with more than one service provider, or corporate identity provider, change the name in every provider, otherwise the trusts will not work. For more information about how to edit the name, see the documentation of the respective service or corporate identity providers.

2.  Download the new SAML metadata of the identity provider \(IdP\). Configure the new metadata of the IdP in every application \(service provider\) you have set trusts with. For more information about how to configure the metadata, see the documentation of the respective service providers.

3.  If have you configured social identity providers, please check configuration on the social provider side, and configure correctly the redirect URI, using the new custom host.
4.  If have you configured a corporate identity provider, please update the configuration on the corporate identity provider side.
5.  If you already have a trusted CA added to your tenant, but after that a custom domain has been configured for that tenant, report a new incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS` to update the certificate on the custom domain as well.

**Related Information**  


[Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md "You as a tenant administrator can view and download the tenant SAML 2.0 metadata. You can also change the name format and update your certificate used by the identity provider to digitally sign the messages for the applications.")

[Get SAML 2.0 IdP Metadata via Parameter](get-saml-2-0-idp-metadata-via-parameter-2c76690.md "Tenant administrator can get the SAML 2.0 metadata via specific parameters.")

[Rotate Signing Certificates](rotate-signing-certificates-6621ad5.md "Tenant administrators must replace existing signing certificates with new ones before they expire. This ensures uninterrupted and secure communication between SAML 2.0 applications (referred to as service providers) and Identity Authentication as the identity provider.")

[Tenant OpenID Connect \(OIDC\) Configurations](tenant-openid-connect-oidc-configurations-3d6abcc.md "You as a tenant administrator can view and configure the tenant OpenID Connect (OIDC) configurations.")

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

[Change a Tenant's Display Name](change-a-tenant-s-display-name-a513c91.md "You can configure the tenant's name from the administration console for SAP Cloud Identity Services.")

[Configure Default Risk-Based Authentication for All Applications in the Tenant](configure-default-risk-based-authentication-for-all-applications-in-the-tenant-1aab51a.md#loio1aab51ae62b94f79b4c6dac7a00857c2 "You can define rules for authentication according to different risk factors and apply actions like Allow, Deny, and Two-Factor Authentication for all applications in a tenant.")

[Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-3fdc9e1.md "Configure Sinch Service to enable Phone Verification via SMS or SMS Two-Factor Authentication in the administration console.")

[Configure RADIUS Server Settings \(Beta\)](configure-radius-server-settings-beta-03043ae.md "Configure Remote Authentication Dial-In User Service (RADIUS) server settings in the administration console for SAP Cloud Identity Services.")

[Configure Mail Server for Application Processes](configure-mail-server-for-application-processes-ccc7ba1.md "Configure mail server for the emails sent to the end users in the different application processes.")

[Configure IdP-Initiated SSO](configure-idp-initiated-sso-5d59caa.md "Enable or disable IdP-Initiated SSO via the administration console for SAP Cloud Identity Services.")

[Sync SSO Cookie Between Domains](sync-sso-cookie-between-domains-c76f097.md "Enable the Sync SSO Cookie Between Domains Settings option to allow seamless single sign-on (SSO) and single logout (SLO) across the Cloud Identity Services domains - ondemand.com and cloud.sap.")

[Send Security Alert Emails](send-security-alert-emails-c977464.md "Send security alert emails to end-users or administrators when changes in their accounts are made.")

[Enable Password Expiration Reminder](enable-password-expiration-reminder-a8de1be.md "Enable password expiration reminder for SAP Cloud Identity Services to ensure the users are aware that a password change is due.")

[Send System Notifications via Emails](send-system-notifications-via-emails-aa04a8b.md "You can configure the administration console to send emails with information about expiring certificates, system notifications, new administrators, and new applications to specific email addresses or to the emails of all administrators.")

[Configure Customer Managed Keys in Administration Console \(Restricted Availability\)](configure-customer-managed-keys-in-administration-console-restricted-availability-fe6e30c.md "")

[Configure Default Language for End User Screens](configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Prompt Users to Explicitly Accept Privacy Policy Document](prompt-users-to-explicitly-accept-privacy-policy-document-f703a95.md "Enable the privacy policy configuration in SAP Cloud Identity Services to prompt users to accept the privacy policy document. This ensures that users explicitly confirm their understanding of document.")

[Configure P-User Next Index](configure-p-user-next-index-045bb1c.md "Set the value for the P-user next index.")

[Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](reuse-sap-cloud-identity-services-tenants-for-different-customer-ids-ebd0258.md "You as a tenant administrator can reuse an existing tenant for configurations and automated subscriptions.")

