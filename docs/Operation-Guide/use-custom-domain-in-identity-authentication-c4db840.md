<!-- loioc4db840ff2464e12ab68d94efb0769c3 -->

# Use Custom Domain in Identity Authentication

Identity Authentication allows you to use a custom domain that is different from the default one \(`<tenant ID>.accounts.ondemand.com`\) - for example `www.mytenant.com`.



<a name="loioc4db840ff2464e12ab68d94efb0769c3__prereq_yt4_mqv_zkb"/>

## Prerequisites

-   You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You must have a custom domain.

    > ### Note:  
    > Internationalized domain names \(IDNs\) are not supported.

-   You must have configured the CNAME DNS record on your domain to point to the host name used to access Identity Authentication. The host name can be one of the following, depending on where client's tenant is located:

    <a name="loioc4db840ff2464e12ab68d94efb0769c3__table_gfv_wmq_qmb"/>Host Names


    <table>
    <tr>
    <th valign="top">

    Tenant Location


    
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

    SAP


    
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

    SAP


    
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

    SAP


    
    </td>
    <td valign="top">

    `cn.accounts.ondemand.com.cloud.sap.akadns.net`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Canada


    
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

    China


    
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

    EU


    
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

    Frankfurt


    
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

    Japan


    
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

    AWS


    
    </td>
    <td valign="top">

    `aws-ap-kr.accounts.ondemand.com.cloud.sap.akadns.net`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    UAE


    
    </td>
    <td valign="top">

    Azure


    
    </td>
    <td valign="top">

    `azr-ap-ae.accounts.ondemand.com.cloud.sap.akadns.net`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    US East


    
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

    US West


    
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
> The content in this document is only relevant for for tenants on the SAP infrastructure.

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.



<a name="loioc4db840ff2464e12ab68d94efb0769c3__steps_ip4_f5y_2lb"/>

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

3.  Choose the *Custom Domain* list item.

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


    
    </td>
    <td valign="top">

    The `DN` used for the domain certificate. The `CN` attribute is mandatory and must match the custom domain used for the domain certificate.


    
    </td>
    </tr>
    </table>
    
5.  Save your configuration.

6.  Choose the *Download CSR file* used for the domain certificate. The button and save the generated CSR file.

    1.  Select the size of the certificate key. The supported key sizes are 2048, 3072 and 4096. The default value is 3072.

    2.  Add an additional subject alternative name to the CSR.


    > ### Note:  
    > Use this CSR for the custom domain certificate. Each download generates a new key pair for the CSR. Always use the last downloaded CSR file.

7.  Send the CSR to a trusted Certificate Authority to sign the certificate.

8.  Access the tenant's administration console for Identity Authentication *Applications and Resources* \> *Tenant Settings* \> *Custom Domain* \> *Certificate* and upload or insert as text the SSL certificate signed by the trusted CA.

    > ### Note:  
    > Make sure that the subject DN in the domain certificate and the configured subject DN match exactly.
    > 
    > You can upload the domain certificate or the complete certificate chain.
    > 
    > The certificate chain must contain the domain certificate, the intermediate certificate or certificates, and the trusted CA root certificate in the same order.

9.  Save your configuration.




<a name="loioc4db840ff2464e12ab68d94efb0769c3__result_k4j_fgz_2lb"/>

## Results

The custom domain configuration is enabled with the upgrade of Identity Authentication. Identity Authentication has production releases \(bi-weekly updates\) planned every second Wednesday, 10:00 UTC. There are also immediate updates in case of fixes required for bugs that affect productive application operations, or due to urgent security fixes. For more information on the upgrade calendar of the service, see [What's New for Identity Authentication](../what-s-new-for-identity-authentication-de21efe.md).



<a name="loioc4db840ff2464e12ab68d94efb0769c3__postreq_b2c_njz_2lb"/>

## Next Steps

1.  Configure tenant's name to be the custom host. Select custom host for the name from the dropdown list in the SAML 2.0 or Open ID Connect Configuration settings. For more information, see [Tenant SAML 2.0 Configuration](tenant-saml-2-0-configuration-e81a19b.md) [Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md)

2.  Download the new SAML metadata of the identity provider \(IdP\). Configure the new metadata of the IdP in every application \(service provider\) you have set trusts with. For more information about how to configure the metadata, see the documentation of the respective service providers.

3.  If have you configured social identity providers, please check configuration on the social provider side, and configure correctly the redirect URI, using the new custom host.
4.  If have you configured a corporate identity provider, please update the configuration on the corporate identity provider side.

**Related Information**  


[Tenant SAML 2.0 Configuration](tenant-saml-2-0-configuration-e81a19b.md "You as a tenant administrator can view and download the tenant SAML 2.0 metadata. You can also change the name format and update your certificate used by the identity provider to digitally sign the messages for the applications.")

[Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md "You as a tenant administrator can view and configure the tenant OpenID Connect configurations.")

[Change Tenant Texts Via Administration Console](change-tenant-texts-via-administration-console-c24b1d0.md "The change tenant texts option can be used to change the predefined texts and messages for end-user screens available per tenant in Identity Authentication via the administration console.")

[Configure Master Data Texts Via Administration Console](configure-master-data-texts-via-administration-console-c068ac9.md "The master data texts option can be used to configure the predefined master data for each resource in Identity Authentication via the administration console.")

[Configure Links Section on Sign-In Screen](configure-links-section-on-sign-in-screen-060c032.md "You can configure links to appear on the sign-in screen of your applications.")

[Add Instructions Section on Sign-In Screen](add-instructions-section-on-sign-in-screen-c9e717e.md "You can customize the sign-in sscreen of the Horizon theme with instructions for the user.")

[Configure X.509 Client Certificates for User Authentication](configure-x-509-client-certificates-for-user-authentication-52c7dcb.md "Tenant administrators can configure X.509 client certificates for user authentication as an alternative to authenticating with a user name and a password.")

[Configure a Tenant Logo and Background Image](configure-a-tenant-logo-and-background-image-8742046.md "You can configure a custom global logo and, or a background image on the forms for sign-in in, registration, upgrade, password update, and account activation for all applications in a tenant.")

[Configure Allowed Logon Identifiers](configure-allowed-logon-identifiers-3adf1ff.md "Tenant administrators can choose the allowed logon identifiers for the users.")

[Configure User Identifier Attributes](configure-user-identifier-attributes-8b9fa88.md "Tenant administrators can configure user identifier attributes as required and unique for the tenant.")

[Allow Users to Protect Accounts with Second Factor for Authentication](allow-users-to-protect-accounts-with-second-factor-for-authentication-d9cbb6d.md "Tenant administrator can allow users to decide whether to protect their own accounts with second factor for authentication or not.")

[Configure Trust this browser Option](configure-trust-this-browser-option-5b8377e.md "Tenant administrator can set the number of days for which the users won't get prompted for second-factor authentication, if they sign in from the same browser.")

[Enable Back-Up Channels to Send Passcode for Deactivation of TOTP Two-Factor Authentication Devices](enable-back-up-channels-to-send-passcode-for-deactivation-of-totp-two-factor-authenticati-782935e.md "Tenant administrator can configure back-up channels to send TOTP deactivation passcodes to the user.")

[Enable Users to Recover Password with Security Questions](enable-users-to-recover-password-with-security-questions-d9ae898.md "Users can choose to answer security questions to reset their password.")

[Enable Users to Recover Password with PIN Code](enable-users-to-recover-password-with-pin-code-046a235.md "Users can choose to provide PIN code to reset their password.")

[Configure Initial Password and E-Mail Link Validity](configure-initial-password-and-e-mail-link-validity-f8093f4.md "As a tenant administrator, you can configure the validity of the initial password and link sent to a user in the various application processes.")

[Configure Session Timeout](configure-session-timeout-5ca23e4.md "As a tenant administrator, you can configure when the session, created at the Identity Authentication tenant, expires.")

[Configure Trusted Domains](configure-trusted-domains-08fa1fe.md "Service providers that delegate authentication to Identity Authentication can protect their applications when using embedded frames, also called overlays, or when allowing user self-registration.")

[Change a Tenant's Display Name](change-a-tenant-s-display-name-a513c91.md "You can configure the tenant's name from the administration console for Identity Authentication.")

[Configure Default Risk-Based Authentication for All Applications in the Tenant](configure-default-risk-based-authentication-for-all-applications-in-the-tenant-1aab51a.md#loio1aab51ae62b94f79b4c6dac7a00857c2 "You can define rules for authentication according to different risk factors and apply actions like Allow, Deny, and Two-Factor Authentication for all applications in a tenant.")

[Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-3fdc9e1.md "Configure Sinch Service to enable Phone Verification via SMS or SMS Two-Factor Authentication in the administration console.")

[Configure RADIUS Server Settings \(Beta\)](configure-radius-server-settings-beta-03043ae.md "Configure Remote Authentication Dial-In User Service (RADIUS) server settings in the administration console for Identity Authentication.")

[Configure Mail Server for Application Processes](configure-mail-server-for-application-processes-ccc7ba1.md "Configure mail server for the e-mails sent to the end users in the different application processes.")

[Configure IdP-Initiated SSO](configure-idp-initiated-sso-5d59caa.md)

[Send Security Alert E-Mails](send-security-alert-e-mails-c977464.md "Send security alert e-mails to end-users or administrators when changes in their accounts are made.")

[Send System Notifications via E-Mails](send-system-notifications-via-e-mails-aa04a8b.md "You can configure the administration console to send e-mails with information about expiring certificates, system notifications and new administrators to specific e-mail addresses or to the e-mails of all administrators.")

[Configure Default Language for End User Screens](configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Reuse Identity Authentication Tenants for Different Customer IDs](reuse-identity-authentication-tenants-for-different-customer-ids-ebd0258.md "You as a tenant administrator can reuse an existing tenant for configurations and automated subscriptions.")

