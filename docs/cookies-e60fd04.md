<!-- loioe60fd0483d414f728fd162c9f525513e -->

# Cookies

Session cookies in Identity Authentication are protected with a Transport Layer Security \(TLS\) and with the *Secure* and *HttpOnly* attributes. You don't need to make any additional configurations for Identity Authentication.

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

If the locale is set, the e-mails use the language set there, if there is a template in that language. If there is no template in that language, the e-mails use the English language template.



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


[Tenant Types](tenant-types-069b25d.md "Identity Authentication provides three types of tenants - productive, test, and trial")

[Application Types](application-types-8f61880.md "Application types in the administration console for SAP Cloud Identity Services.")

[User Types](user-types-70e95d1.md "")

[Configure the Remember Me Option](Operation-Guide/configure-the-remember-me-option-08d41f4.md "Tenant administrators can configure the Remember me option as visible or hidden, and checked or unchecked.")

[Use the Remember Me Option](User-Guide/use-the-remember-me-option-bc7c6c6.md "With the Remember me functionality enabled, you can log on to an application without the need to provide your credentials every time you access it.")

[Configure Conditional Authentication for an Application](Operation-Guide/configure-conditional-authentication-for-an-application-0143dce.md "Tenant administrator can define rules for authenticating identity provider according to email domain, user type, user group, and IP range (specified in CIDR notation).")

[Add Logon Overlays in Customer Applications](Development/add-logon-overlays-in-customer-applications-5e98ecf.md "This document describes how service providers that delegate authentication to Identity Authentication can use embedded frames, also called overlays, for the logon pages of their applications.")

[Configure Default Language for End User Screens](Operation-Guide/configure-default-language-for-end-user-screens-2cb73c3.md "Select the language that the end user screen uses if the language of the browser isn’t in the list of supported languages.")

[Access Applications with Single Sign-On on Mobile Devices](User-Guide/access-applications-with-single-sign-on-on-mobile-devices-89bbb0b.md "You can access trusted applications that require two-factor authentication via your mobile devices using single sign-on (SSO).")

[Configuring Email Templates](Operation-Guide/configuring-email-templates-b2afbcd.md "Tenant administrators can use the default or a custom email template set for the application processes.")

[Configure Source System To Migrate User Passwords from SAP Fieldglass to Identity Authentication](Operation-Guide/configure-source-system-to-migrate-user-passwords-from-sap-fieldglass-to-identity-authent-b0c7ec8.md)

[Configuring Password Policies](Operation-Guide/configuring-password-policies-12b3395.md "Passwords for the authentication of users are subject to certain rules. These rules are defined in the password policy. Identity Authentication provides you with two predefined password policies, in addition to which you can create and configure up to three custom password policies.")

[Security Information](Security/security-information-6e88d82.md "This document is an overview of security-relevant information that applies to Identity Authentication, and contains recommendations about how administrators should secure it.")

[Configure SAP BTP](Operation-Guide/corporate-user-store-cloud-foundry-environment-9942ede.md#loiodd8240d6a4f54e938ec867c21a4e9222)

[User Records](Operation-Guide/corporate-user-store-cloud-foundry-environment-9942ede.md#loio500ac5e7d6574fdb8177ff4b637f1da2)

[Configure Identity Authentication](Operation-Guide/corporate-user-store-cloud-foundry-environment-9942ede.md#loiode5cff7e1ec14bd08d01e429390fe193)

