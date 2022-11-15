<!-- loioc0d4a7676e894d048ee361ae2d2f0012 -->

# Allowed Placeholders per E-Mail Template

This document describes which placeholders can be used in each e-mail template.



The allowed placeholders are marked with *Yes* in the table:

**Placeholders per E-Mail Template**


<table>
<tr>
<th valign="top">

Placeholder/E-Mail Template



</th>
<th valign="top">

Self-Registration



</th>
<th valign="top">

On-Behalf Registration



</th>
<th valign="top">

Invitation



</th>
<th valign="top">

Forgot Password



</th>
<th valign="top">

Locked Password



</th>
<th valign="top">

Reset Password



</th>
<th valign="top">

Send Security Alert



</th>
<th valign="top">

Deactivate TOTP Device



</th>
<th valign="top">

E-Mail OTP Code



</th>
</tr>
<tr>
<td valign="top">

`${user.sp_name}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.activate_account_link}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`${user.firstName}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.lastName}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.mail}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.uid}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.ids_home_link}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.loginName}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.company_logo}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.sap_mailing_logo}`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.target_url}`



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`${user.reset_password_link}`



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`${user.set_locked_password_link}`



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`${other.securityAlertText}`



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`${other.totpResetPasscode}`



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

$\{other.emailOtpCode\}



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`${user.inviter_name}`



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`${user.footer}`



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`${user.header}`



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
</table>

> ### Remember:  
> The *$\{other.securityAlertText\}* is mandatory for the *Send Security Alert* template. The *$\{other.securityAlertText\}* is customizable. For more information, see [Change Tenant Texts REST API](../Development/change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6). The key-value pairs that should be changed are `security.alert.<name of the flow>`.
> 
> The *$\{other.totpResetPasscode\}* is mandatory for the *Deactivate TOTP Device* template.
> 
> See example for the *Deactivate TOTP Device* template below:

**Related Information**  


[Create a New E-Mail Template Set](create-a-new-e-mail-template-set-a6fca8b.md "Tenant administrators can create a new set of e-mail templates so that each template in the set can have a custom language version.")

[View E-Mail Template Document](view-e-mail-template-document-148568a.md "Tenant administrators can view language e-mail templates in the template set uploaded in the administration console for Identity Authentication.")

[Edit or Add an E-Mail Template Set](edit-or-add-an-e-mail-template-set-3c4f397.md "Tenant administrators can configure language versions of each template in the template set. They can also set a custom template for each language, and change the name of each template set.")

[Define an E-Mail Template Set for an Application](define-an-e-mail-template-set-for-an-application-fc6b54a.md "Tenant administrators can define the e-mail template set that the application uses.")

[Delete an E-Mail Template Set](delete-an-e-mail-template-set-6fce69d.md "Tenant administrators can delete an e-mail template set or a language version for a specific application process.")

