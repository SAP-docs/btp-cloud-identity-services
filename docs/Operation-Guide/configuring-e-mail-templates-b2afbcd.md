<!-- loiob2afbcdccdf7410f8953e1e833e77de0 -->

# Configuring E-Mail Templates

Tenant administrators can use the default or a custom e-mail template set for the application processes.



## Overview

The e-mail template set is a semantic grouping of different e-mail templates. Each e-mail template from the set is used for the respective application process, such as self-registration, for example. When a user makes a registration for an application, Identity Authentication uses the e-mail template for self-registration from the template set to communicate with that user.

The administration console for Identity Authentication provides the possibility to use a default e-mail template set with English templates only. The default set is named *Default*.

You can also configure your own templates in a custom template set. There you can customize the texts and branding according to your needs.

You can define a set of e-mail templates with different language versions for the following processes:


<table>
<tr>
<th valign="top">

E-Mail Template



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Self-Registration



</td>
<td valign="top">

This e-mail template is used when a user registers via the Registration page. The user then receives an e-mail with instructions about how to activate his or her account. The name of the e-mail template used for this process is *Self-Registration*.



</td>
</tr>
<tr>
<td valign="top">

On-Behalf Registration



</td>
<td valign="top">

This e-mail template is used when somebody else registers the user on his or her behalf via the import user option for Identity Authentication. In this case, the registered user receives an e-mail with instructions about how to activate his or her account. The name of the e-mail template used for this process is *On-Behalf Registration.* 



</td>
</tr>
<tr>
<td valign="top">

Invitation



</td>
<td valign="top">

This e-mail template is used when a user invites another user for registration via the Invitation REST API. In this case, the invitee receives an e-mail with instructions about how to register. The name of the e-mail template used for this process is *Invitation*.



</td>
</tr>
<tr>
<td valign="top">

Forgot Password



</td>
<td valign="top">

This e-mail template is used when a user wants to change his or her password by going through the Forgot Password page. In this case, the user receives an e-mail with instructions about how to change his or her password. The name of the e-mail template used for this process is *Forgot Password*.



</td>
</tr>
<tr>
<td valign="top">

Locked Password



</td>
<td valign="top">

This e-mail template is used when a user locks his or her password by exceeding the allowed number of logon attempts. In this case, the user receives an e-mail with instructions about how to log on. The name of the e-mail template used for this process is *Locked Password*.



</td>
</tr>
<tr>
<td valign="top">

Reset Password



</td>
<td valign="top">

This e-mail template is used when a user has to reset his or her password. In this case, the user receives an e-mail with instructions about how to reset his or her password.

The name of the e-mail template used for this process is *Reset Password*.

The e-mail template for *Reset Password* process are used when the process is triggered from the system, based on the password policy \(for example, the user's password length is not enough according to the password policy requirements\) and the user receive reset password notification e-mail.



</td>
</tr>
<tr>
<td valign="top">

Deactivate TOTP Device



</td>
<td valign="top">

This e-mail-template is used when a user has requested to receive a passcode via e-mail. The passcode is used to deactivate the devices used to generate passcodes for TOTP Two-Factor Authentication. The name of the e-mail template used for this process is *Deactivate TOTP Device*.



</td>
</tr>
<tr>
<td valign="top">

E-Mail OTP Code



</td>
<td valign="top">

This e-mail-template is used when a user has requested to receive an 8-digit code via e-mail. The user needs the code for two-factor authentecation.



</td>
</tr>
<tr>
<td valign="top">

Send Security Alert



</td>
<td valign="top">

This e-mail-template is used when the user's password is set, changed, or reset, the e-mail, or login name is changed, or when TOTP or Web TFA devices are activated or deactivated. The name of the e-mail template used for this process is *Send Security Alert*.

> ### Note:  
> The sending of security alert e-mails is switched off by default. For more information, see [Send Security Alert E-Mails](send-security-alert-e-mails-c977464.md).



</td>
</tr>
</table>

To activate a user registration or to reset a password, users choose links sent to them in the e-mails. For these cases, you can use placeholders. For more information about which placeholders can be used, see [Edit or Add an E-Mail Template Set](edit-or-add-an-e-mail-template-set-3c4f397.md).

You can also define which languages each e-mail template uses, and you can set custom versions for each language. You can set the following languages:

Arabic, Azerbaijani, Bulgarian, Catalan, Chinese \(PRC\), Chinese \(Taiwan\), Croatian, Czech, Danish, Dutch, English \(United Kingdom\), English \(United States\), Estonian, Finnish, French \(Standard\), French \(Canada\), German \(Standard\), Greek, Hebrew, Hungarian, Italian, Japanese, Korean, Latvian, Norwegian, Polish, Portuguese \(Portugal\), Romanian, Russian, Serbian, Slovak, Slovenian, Spanish \(Spain\), Spanish \(Mexico\), Swedish, Turkish, Ukrainian, Welsh.



The language for the e-mail template sets is set according to the following order of priorities:

1.  If the locale is set, the e-mails use the language set there, if there is a template in that language. If there is no template in that language, the e-mails use the English language template.

     

    Setting the locale, sets an Identity Authentication cookie. This cookie is used for all the applications in this session that are configured to use Identity Authentication as identity provider.

    > ### Note:  
    > The locale can be set in either of the following ways:
    > 
    > -   The locale is communicated to Identity Authentication by adding a locale parameter to *SAP\_IDS.js*.
    > 
    >     > ### Source Code:  
    > 
    >     `<script src="https://<tenant ID>.accounts.ondemand.com/ui/resources/javascripts/SAP_IDS.js?locale=en_GB" />` 
    > 
    > -   The locale is communicated to Identity Authentication by a direct `GET` request.
    > 
    >     > ### Source Code:  
    > 
    >     `https://<tenant ID>.accounts.ondemand.com/ui/public/setLocale?locale=DE`

2.  If the locale is not set, the e-mails use the language that the user's browser is set to.

    -   If the language is not in the list of supported languages, the e-mails use *English* instead.

    -   If the language is in the list of supported languages, the e-mails use this language.





If you want to use a custom e-mail template you should create one if it does not exist. Add or edit the e-mail template set, if necessary, and then define that e-mail template set for the application. To add or edit the e-mail template, first you must open the uploaded e-mail templates, and then save a copy. Optionally you can delete an e-mail template set or a language version for a specific application process.



You can perform the following steps:

