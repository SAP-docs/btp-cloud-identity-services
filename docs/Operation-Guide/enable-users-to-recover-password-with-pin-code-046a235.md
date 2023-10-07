<!-- loio046a2352009f45b9a87eb9dc7478a8df -->

# Enable Users to Recover Password with PIN Code

Users can choose to provide PIN code to reset their password.



<a name="loio046a2352009f45b9a87eb9dc7478a8df__prereq_vnp_bcg_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

You can configure the applications in the tenant to allow users to provide PIN code to reset their password instead of receiving an email with a reset password link.

For this setup, you as a tenant administrator, configure the PIN code option in the *Tenant Settings* section in the administration console, and the users set their PIN code in the profile page.

Once the PIN code is configured, the user can use this option to reset the password. The user must have set their PIN code in the profile page to be able to reset password via this option.

If the PIN code option is configured in the admin console, end users that haven't set up their PIN code are triggered to do it as a post logon step. Optionally, they can choose to set up the PIN code later.

If end users choose the *Don't ask me again* check box, the prompt won't be shown anymore. End users still can set up the PIN code in their profile page.

**PIN Code Characteristics**


<table>
<tr>
<th valign="top">

Characteristics



</th>
<th valign="top">

Notes



</th>
</tr>
<tr>
<td valign="top">

Allowed Characters



</td>
<td valign="top">

Base 10 digits \(0-9\)



</td>
</tr>
<tr>
<td valign="top">

Min Length



</td>
<td valign="top">

Between 4 and 32 characters; configurable on tenant level



</td>
</tr>
<tr>
<td valign="top">

Max Length



</td>
<td valign="top">

32 characters



</td>
</tr>
<tr>
<td valign="top">

Required



</td>
<td valign="top">

*Setup later* and *Don't ask me again* are configurable



</td>
</tr>
<tr>
<td valign="top">

Target Users



</td>
<td valign="top">

-   *None* - the PIN code option isn't offered to the users and all PIN code configurations in the administration console are disabled
-   *Users without email* - only users that don't have emails are able to reset password via PIN code
-   *All users* - everyone can choose this option to reset the password
-   *Specific groups* - only users that belong to the selected groups can reset password via PIN code.



</td>
</tr>
<tr>
<td valign="top">

Lock



</td>
<td valign="top">

The reset password action with PIN code locks after 5 failed attempts. The logon with correct username and password is not interrupted.



</td>
</tr>
<tr>
<td valign="top">

Unlock



</td>
<td valign="top">

To unlock the PIN code, set an initial password for the user.



</td>
</tr>
</table>

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

To configure PIN code option in the administration console, follow the procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Authentication*, choose the *Password Recovery* list item.

4.  Select the *PIN Code* tab.

5.  Under *Target Users*, choose users that can reset passwords with PIN code:

    -   *None* - default choice

        > ### Note:  
        > If selected, the PIN code configurations in the administration console are disabled.

    -   *Users without email*
    -   *All users*
    -   *Specific groups*

        > ### Note:  
        > When you select this option, you must specify the specific group or groups for which you enable password recovery via PIN code.


6.  Under *Settings*, choose the minimum required length of the PIN code.

7.  **Optional:** Select the *Show "Setup later"* check box.

    When selected, the end users see the option to set up the PIN code later.

8.  **Optional:** Select the *Show "Don't ask again"* check box.

    When selected, the end users see the option to hide the prompt to set up their PIN code.

9.  Save your configuration.


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

[Configure Customer-Controlled Encryption Keys in Administration Console \(Early Adoption\)](configure-customer-controlled-encryption-keys-in-administration-console-early-adoption-fe6e30c.md "")

[Configure Default Language for End User Screens](configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Configure P-User Next Index](configure-p-user-next-index-045bb1c.md "Set the value for the P-user next index.")

[Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](reuse-sap-cloud-identity-services-tenants-for-different-customer-ids-ebd0258.md "You as a tenant administrator can reuse an existing tenant for configurations and automated subscriptions.")

