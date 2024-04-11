<!-- loioe60fd0483d414f728fd162c9f525513e -->

# Cookies

Session cookies in Identity Authentication are protected with a Transport Layer Security \(TLS\) and with the *Secure* and *HttpOnly* attributes. You don't need to make any additional configurations for Identity Authentication.

**Authentication Session Trackin**


<table>
<tr>
<th valign="top">

Cookie

</th>
<th valign="top">

Path

</th>
<th valign="top">

Expiration

</th>
<th valign="top">

Protection

</th>
<th valign="top">

Value

</th>
<th valign="top">

Info

</th>
<th valign="top">

Reference

</th>
</tr>
<tr>
<td valign="top">

`IDP_J_COOKIE`

</td>
<td valign="top">

/

</td>
<td valign="top">

Session

</td>
<td valign="top">

-   Secure
-   HttpOnly



</td>
<td valign="top">

secure random token

</td>
<td valign="top">

Track the authentication session of the user at the identity provider.

The cookie is sent to the browser so the users can sign in to the application without the need to provide their credentials every time they access it.

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`REMEMBERME_COOKIE`

</td>
<td valign="top">

/

</td>
<td valign="top">

3 months

</td>
<td valign="top">

-   Secure
-   HttpOnly



</td>
<td valign="top">

secure random token

</td>
<td valign="top">

Allow user to keep their session for an extended period of time even after closing the Web browser

</td>
<td valign="top">

[Configure the Remember Me Option](Operation-Guide/configure-the-remember-me-option-08d41f4.md)

</td>
</tr>
</table>

**Authentication & Single Sign-On Screens**


<table>
<tr>
<th valign="top">

Cookie

</th>
<th valign="top">

Path

</th>
<th valign="top">

Expiration

</th>
<th valign="top">

Protection

</th>
<th valign="top">

Value

</th>
<th valign="top">

Info

</th>
<th valign="top">

Purpose

</th>
</tr>
<tr>
<td valign="top">

`XSRF_COOKIE`

</td>
<td valign="top">

/

</td>
<td valign="top">

Session

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`locale`

</td>
<td valign="top">

/

</td>
<td valign="top">

Session

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

``

</td>
<td valign="top">

/

</td>
<td valign="top">

Session

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

``

</td>
<td valign="top">

/

</td>
<td valign="top">

Session

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
</table>

****


<table>
<tr>
<th valign="top">

Cookie

</th>
<th valign="top">

Description

</th>
<th valign="top">

Default Validity

</th>
<th valign="top">

 

</th>
<th valign="top">

Reference

</th>
</tr>
<tr>
<td valign="top">

Remember Me

</td>
<td valign="top">

The cookie is sent to the browser so the users can sign in to the application without the need to provide their credentials every time they access it.

</td>
<td valign="top">

3 months

</td>
<td valign="top">

 

</td>
<td valign="top">

[Configure the Remember Me Option](Operation-Guide/configure-the-remember-me-option-08d41f4.md)

</td>
</tr>
<tr>
<td valign="top">

Conditional Authentication

</td>
<td valign="top">

Identity Authentication stores the user identifier in a persistent cookie in the browser.

</td>
<td valign="top">

36 months

</td>
<td valign="top">

 

</td>
<td valign="top">

[Configure Conditional Authentication for an Application](Operation-Guide/configure-conditional-authentication-for-an-application-0143dce.md)

</td>
</tr>
<tr>
<td valign="top">

Locale

</td>
<td valign="top">

If the locale is set, the emails use the language set there, if there is a template in that language. If there is no template in that language, the emails use the English language template.

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
</table>

**Related Information**  


[Tenants](tenants-93160eb.md "A tenant refers to your (customer-specific) instance of SAP Cloud Identity Services. It's delivered to you as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.")

[Bundles](bundles-25b65a4.md "A bundle is a group of preconfigured products and services which are sold together.")

[Applications](applications-404a11c.md "An application is associated with a consumer of Identity Authentication as an identity provider. This consumer could be for example an SAP cloud solution, a third-party application, SAP BTP subaccount, or the SAP Cloud Identity Services administration console.")

[Provisioning Systems](provisioning-systems-15da6af.md "Identity Provisioning provides connectors to various business applications for provisioning and deprovisioning of users and groups. These business applications are set up as provisioning systems in the administration console of SAP Cloud Identity Services.")

[Properties](properties-e92c1aa.md "Properties hold the configuration of a provisioning system.")

[Transformations](transformations-81f5204.md "Transformations help you transform user and group attributes from the data model of the source system to the data model of the target system.")

[Users](users-70e95d1.md "Users in SAP Cloud Identity Services fall into two categories: administrators and end users.")

[Configure the Remember Me Option](Operation-Guide/configure-the-remember-me-option-08d41f4.md "Tenant administrators can configure the Remember me option as visible or hidden, and checked or unchecked.")

[Use the Remember Me Option](User-Guide/use-the-remember-me-option-bc7c6c6.md "With the Remember me functionality enabled, you can log on to an application without the need to provide your credentials every time you access it.")

[Configure Conditional Authentication for an Application](Operation-Guide/configure-conditional-authentication-for-an-application-0143dce.md "Tenant administrator can define rules for authenticating identity provider according to email domain, user type, user group, and IP range (specified in CIDR notation).")

[Add Logon Overlays in Customer Applications](Development/add-logon-overlays-in-customer-applications-5e98ecf.md "This document describes how service providers that delegate authentication to Identity Authentication can use embedded frames, also called overlays, for the logon pages of their applications.")

[Configure Default Language for End User Screens](Operation-Guide/configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Configuring Email Templates](Operation-Guide/configuring-email-templates-b2afbcd.md "Tenant administrators can use the default or a custom email template set for the application processes.")

[Configure Authentication Provider To Migrate User Passwords from SAP Fieldglass to Identity Authentication](Operation-Guide/configure-authentication-provider-to-migrate-user-passwords-from-sap-fieldglass-to-identi-b0c7ec8.md)

[Configuring Password Policies](Operation-Guide/configuring-password-policies-12b3395.md "Passwords for the authentication of users are subject to certain rules. These rules are defined in the password policy. Identity Authentication provides you with two predefined password policies, in addition to which you can create and configure up to three custom password policies.")

[Security Information](Security/security-information-6e88d82.md "This document is an overview of security-relevant information that applies to Identity Authentication, and contains recommendations about how administrators should secure it.")

[Configure SAP BTP](Operation-Guide/corporate-user-store-cloud-foundry-environment-9942ede.md#loiodd8240d6a4f54e938ec867c21a4e9222)

[User Records](Operation-Guide/corporate-user-store-cloud-foundry-environment-9942ede.md#loio500ac5e7d6574fdb8177ff4b637f1da2)

[Configure Identity Authentication](Operation-Guide/corporate-user-store-cloud-foundry-environment-9942ede.md#loiode5cff7e1ec14bd08d01e429390fe193)

