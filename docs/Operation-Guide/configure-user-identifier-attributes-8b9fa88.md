<!-- loio8b9fa88649ae4d86a4ab4baf8fb0e007 -->

# Configure User Identifier Attributes

Tenant administrators can configure user identifier attributes as required and unique for the tenant.



<a name="loio8b9fa88649ae4d86a4ab4baf8fb0e007__prereq_m1z_5zf_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

Identity Authentication ensures the uniqueness only of the newly set values of the attributes. The system doesn’t guarantee the uniqueness of the existing attributes.

The default configuration for the user identifiers are:

**User Identifier Default Configuration**


<table>
<tr>
<th valign="top">

User Identifier



</th>
<th valign="top">

Required



</th>
<th valign="top">

Unique



</th>
</tr>
<tr>
<td valign="top">

*User ID*



</td>
<td valign="top">

Yes/Not Configurable



</td>
<td valign="top">

Yes/Not Configurable



</td>
</tr>
<tr>
<td valign="top">

*Email*



</td>
<td valign="top">

Yes/Configurable



</td>
<td valign="top">

Yes/Configurable



</td>
</tr>
<tr>
<td valign="top">

*Login Name*



</td>
<td valign="top">

No/Configurable



</td>
<td valign="top">

Yes/Not Configurable



</td>
</tr>
<tr>
<td valign="top">

*Display Name*



</td>
<td valign="top">

No/Configurable



</td>
<td valign="top">

No/Configurable



</td>
</tr>
<tr>
<td valign="top">

*Phone*



</td>
<td valign="top">

No/Not Configurable



</td>
<td valign="top">

No/Configurable



</td>
</tr>
</table>

The `Login Name` and *Phone* identifiers of a user can't have values that are equal to the `User ID`, `Email`, `Login Name`, and *Phone* identifiers of another user.

> ### Note:  
> The `Display Name` user identifier for the tenants created before the system upgrade on May 13, 2020 is configured as required and unique.
> 
> The *Phone* user attribute is configured as non-unique by default. If you configure it as unique, all users that are created or updated after this configuration won't be able to have phone numbers taken by someone else.

> ### Remember:  
> If `Email` is marked as not-required on tenant level, it becomes configurable on application level, and must also be changed there, too. For more information, see [Configure Registration and Upgrade Forms](configure-registration-and-upgrade-forms-93a9e18.md).

**Email Required/Unique Configurations**


<table>
<tr>
<th valign="top">

Choice



</th>
<th valign="top">

Yes



</th>
<th valign="top">

No



</th>
</tr>
<tr>
<td valign="top">

Required



</td>
<td valign="top">

-   admin must provide email when creating or editing user in the admin console
-   `emails.value` attribute is mandatory when creating a user via the SCIM REST API
-   email appears as required in the registration form of an application
-   user must provide email, if missing, when an update of the account is triggered
-   admin can't delete user's email in admin console
-   user can't delete his/her email in profile page



</td>
<td valign="top">

-   admin must provide email when creating user in the admin console only when account activation is *Send activation email*
-   `emails.value` attribute must be provided when creating a user via the SCIM REST API only when `sendMail` attribute is *true*
-   email is required in the registration form of the application; the configuration is taken into account for the upgrade process
-   reset password process will be replaced by change password process for users with no email
-   user is not prompted to provide email, if missing, when an update of the account is triggered
-   admin can delete user's email in admin console
-   user can delete his/her email in profile page
-   end-user screen texts differ from the actual tenant configuration; admin can change the tenant texts to match the configuration
-   email verification setting for an application could be skipped for users with no email.



</td>
</tr>
<tr>
<td valign="top">

Unique



</td>
<td valign="top">

-   email can be used for logon
-   email must be unique, if provided, when a user is created or edited via the admin console
-   `emails.value` attribute must be unique, if provided, when a user is created via SCIM REST API
-   user must provide unique email, if required, when an update of the account is triggered
-   user import is supported; email must be provided
-   `email` attribute must be unique, if provided, when a user is registered via User Management REST API

> ### Note:  
> The email user identifier must be selected unique if you use it for logon. For more information about how to configure the allowed logon identifiers, see Next Steps.



</td>
<td valign="top">

-   email can't be used for logon
-   admin can create more than one user with one and the same email in the admin console
-   `emails.value` attribute may not be unique if provided when a user is created via SCIM REST API
-   email, if required, may not be unique when an update of the account is triggered
-   users with nonunique emails can't change their password via the *Forgot Password* process using the email as identifier
-   end-user screen texts differ from the actual tenant configuration; admin can change the tenant texts to match the configuration
-   user import is not supported



</td>
</tr>
</table>

The texts on the end screen are predefined. If you change the required/unique preference in the tenant, this won’t automatically change the texts in the end-user page. To change the text, you must update the predefined texts and messages for end-user screens available per tenant in the Identity Authentication. For more information, see [Change Tenant Texts REST API](../Development/change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6).

Although the choice for the `required` attribute is applied for all applications in the tenant, you can still make the *Email* required on the registration and upgrade form for specific applications via a custom configuration. For more information, see [Configure Registration and Upgrade Forms](configure-registration-and-upgrade-forms-93a9e18.md)

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

If you want to change the configuration for the user identifier for your tenant, follow the procedure below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Authentication*, choose the *Logon Alias* list item.

4.  Select the options for the user identifier according to your needs.

    -   Required
    -   Unique

    If the operation is successful, the system displays the message ***Logon alias updated***. It takes two minutes for the change to be applied.




<a name="loio8b9fa88649ae4d86a4ab4baf8fb0e007__postreq_utd_dt4_gmb"/>

## Next Steps

Choose the allowed logon identifiers for the users. For more information, see [Configure Allowed Logon Identifiers](configure-allowed-logon-identifiers-3adf1ff.md).

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

[Configure Customer-Controlled Encryption Keys in Administration Console \(Early Adoption\)](configure-customer-controlled-encryption-keys-in-administration-console-early-adoption-fe6e30c.md "")

[Configure Default Language for End User Screens](configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Configure P-User Next Index](configure-p-user-next-index-045bb1c.md "Set the value for the P-user next index.")

[Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](reuse-sap-cloud-identity-services-tenants-for-different-customer-ids-ebd0258.md "You as a tenant administrator can reuse an existing tenant for configurations and automated subscriptions.")

