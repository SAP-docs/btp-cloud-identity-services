<!-- loio3d6abcc02ec945ad9615773e05814003 -->

# Tenant OpenID Connect Configurations

You as a tenant administrator can view and configure the tenant OpenID Connect configurations.



<a name="loio3d6abcc02ec945ad9615773e05814003__prereq_ub1_2vf_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

You can change the name format, the certificate used by the identity provider to digitally sign the messages for the applications, set the token policy by configuring the validity of the refresh token, access and id\_token, and the maximum sessions per user, and extend the standard metadata with custom values.

> ### Note:  
> The signing certificate is one and the same for SAML 2.0 and OpenID Connect. A change in one of the configurations affects the other one.

The *OpenID Connect Configuration* view in the administration console also shows information about the URLs of the *Domain for Browser Flows*, *Authorization Endpoint*, *Token Endpoint*, *UserInfo Endpoint*, and *Logout Endpoint*.

The token policy for the tenant is defined by configuring the validity of the refresh token, access and id\_token, and the maximum sessions per user. It’s valid for all the applications in the tenant.

> ### Remember:  
> If you want a specific token policy per application, you must set a custom token policy for each application. If you modify the settings on the tenant level, all applications without their own custom token policy are affected. For more information, see [Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md)

The following table lists the token policy options for OIDC applications.

**Token Policy Configuration Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*Refresh Token* 

</td>
<td valign="top">

Sets the refresh token lifetime issued by Identity Authentication. The value can range from 1 to 4320 hours, in other words, from 1 hour to 180 days.

The default value is 12 hours.

> ### Note:  
> -   If the validity of refresh tokens is less than the validity of access/ID tokens, access/ID tokens can't be refreshed after the access/ID tokens expire.
> 
> -   When using the authorization code flow, if you set the token policy for refresh tokens longer than the session timeout, add the *offline\_access* scope to your authorization code request. Without this scope, the service deletes the refresh token from the database when the resource owner ends the session \(logs out\). Without the refresh token, the OAuth client can't request new tokens anymore.
> 
>     For more information, see:
> 
>     -   [Configure Session Timeout](configure-session-timeout-5ca23e4.md)
> 
>     -   [Using Authorization Code Flow](using-authorization-code-flow-c135fc4.md)



</td>
</tr>
<tr>
<td valign="top">

*Access / ID Token* 

</td>
<td valign="top">

Sets the access and id\_token lifetime issued by Identity Authentication. The value can range from 1 to 720 minutes, in other words, from 1 minute to 12 hours.

The default value is 60 minutes.

</td>
</tr>
<tr>
<td valign="top">

*Max sessions per user* 

</td>
<td valign="top">

Determines the maximum number of tokens that the service issues for the same session in parallel. Imagine you’re logged on to the application through a web interface and a command-line interface in parallel. Then you'd set this parameter to 2. The value can range from 1 to 10.

The default value is 1.

</td>
</tr>
</table>

The maximum wait time for front-channel logout can be set between 1 and 10 seconds. The default value is 3 seconds.

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

To view or change the tenant OpenID Connect configurations, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Single Sign-On*, choose the *OpenID Connect Configuration* list item.

    The *OpenID Connect Configuration* page that opens displays the name of the identity provider, its endpoints derived from issuer and domain configurations, signing certificate and token policy.

    > ### Note:  
    > By default, applications use the domain from their trust configuration to access all the endpoints. For browser-based logons and logouts, you can choose another domain. Applications use the chosen domain after reloading the OpenID Connect metadata.

4.  **Optional:** To define the token policy, use the slider or provide a number in the input field above the slider. If needed, use the reset button to set to the default value.

5.  **Optional:** To change the name of the identity provider, choose the *Name* field, select the name from the dropdown list, and save your changes.

    Choose from the following options:


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
    > Change the name of the identity provider on the service provider side every time you change the name format of the identity provider in the administration console. If you have set trusts with more than one service provider, change the name in every service provider. For more information about how to edit the name, see the documentation of the respective service providers.

    If the change of the name is successful, the system displays the message ***Tenant <name of tenant\> updated***.

6.  **Optional:** Update your signing certificate. You can choose from the following options:

    -   To regenerate the existing certificate with new validity, reusing the same private key, choose *Add* \> *Regenerate* \> *Next Step* \> *choose validity from the drop down* \> *Next Step* \> *Finish* \> *Save*.

    -   To create a new certificate with a new private key and the same Subject DN, choose *Add* \> *Create new* \> *Next Step* \> *choose key size and validity from the drop downs* \> *Next Step* \> *Finish* \> *Save*.
    -   To create a new certificate, using your own trusted CA, choose *Add* \> *Download CSR* \> *Next Step* \> *add Subject DN and choose key size and validity from the drop downs* \> *Next Step* \> *Download CSR*.

        When you get your certificate, copy and paste it as text in the View Certificate Details dialog.


7.  **Optional:** Set the maximum wait time for front-channel logout.




<a name="loio3d6abcc02ec945ad9615773e05814003__postreq_ghg_tzy_xqb"/>

## Next Steps

To change the default certificate for the tenant, choose the new one from the list, and save your configuration.

> ### Caution:  
> When you change the default certificate for the tenant, you must also update the trust with the service provider. For more information, see [Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md) or [Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md).

**Related Information**  


[Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md "You as a tenant administrator can view and download the tenant SAML 2.0 metadata. You can also change the name format and update your certificate used by the identity provider to digitally sign the messages for the applications.")

[Get SAML 2.0 IdP Metadata via Parameter](get-saml-2-0-idp-metadata-via-parameter-2c76690.md "Tenant administrator can get the SAML 2.0 metadata via specific parameters.")

[Rotate Signing Certificates](rotate-signing-certificates-6621ad5.md "Tenant administrators must replace existing signing certificates with new ones before they expire. This ensures uninterrupted and secure communication between SAML 2.0 applications (referred to as service providers) and Identity Authentication as the identity provider.")

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

[Send System Notifications via Emails](send-system-notifications-via-emails-aa04a8b.md "You can configure the administration console to send emails with information about expiring certificates, system notifications, new administrators, and new applications to specific email addresses or to the emails of all administrators.")

[Configure Customer Managed Keys in Administration Console \(Restricted Availability\)](configure-customer-managed-keys-in-administration-console-restricted-availability-fe6e30c.md "")

[Configure Default Language for End User Screens](configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Configure P-User Next Index](configure-p-user-next-index-045bb1c.md "Set the value for the P-user next index.")

[Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](reuse-sap-cloud-identity-services-tenants-for-different-customer-ids-ebd0258.md "You as a tenant administrator can reuse an existing tenant for configurations and automated subscriptions.")

[Configuring Tenant Settings](configuring-tenant-settings-d4d6fdc.md "Initially, the tenants are configured to use default settings. This section describes how you as a tenant administrator can make custom tenant configurations.")

[Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md "Set the token policy for a specific OpenID Connect application. Configure the validity of the refresh token, access and id_token, and the maximum sessions per user.")

