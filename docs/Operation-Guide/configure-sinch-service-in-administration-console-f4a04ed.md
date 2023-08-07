<!-- loiof4a04ed54b544ee9ac1862b5d79178de -->

# Configure Sinch Service in Administration Console

Configure Sinch Service to enable *Phone Verification via SMS* or *SMS Two-Factor Authentication* in the administration console.



<a name="loiof4a04ed54b544ee9ac1862b5d79178de__prereq_apw_h4w_hdb"/>

## Prerequisites

-   You have an account in Sinch Verification Service. Once you create a Sinch service account, you receive an email with your account information.

-   You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).




<a name="loiof4a04ed54b544ee9ac1862b5d79178de__context_j2w_pc5_ldb"/>

## Context

Sinch service enables multichannel two-factor authentication \(2FA\), adding another layer of security to customers' online accounts, beyond their login and password. The service enables you to configure tokens – such as one-time passwords \(OTPs\), personal identification numbers \(PINs\), and verification codes – that are tailored to businesses and particular use cases.

For the integration between Identity Authentication and Sinch service, you must provide information in the administration console for SAP Cloud Identity Services. You can have a Sinch Verification configuration. You can clear the fields by choosing the *Remove Configuration* button at the top of the screen.

Provide the following:

**Sinch Verification**


<table>
<tr>
<th valign="top">

Configuration



</th>
<th valign="top">

Notes



</th>
</tr>
<tr>
<td valign="top">

*Application Key*



</td>
<td valign="top">

The *Application Key* obtained via Sinch customer dashboard.



</td>
</tr>
<tr>
<td valign="top">

*Application Secret*



</td>
<td valign="top">

The *Application Secret* obtained via Sinch customer dashboard.



</td>
</tr>
<tr>
<td valign="top">

*Code Timeout*



</td>
<td valign="top">

Optional.

Request the Sinch Support team to configure this parameter for the client's Sinch account.

> ### Remember:  
> Before configuring this property in the administration console for SAP Cloud Identity Services, first request this property to the Sinch Support team.



</td>
</tr>
<tr>
<td valign="top">

*SMS Text Template*



</td>
<td valign="top">

Optional.

Request the Sinch Support team to enable this configuration.

The SMS text in the configuration must include the `{{CODE}}` placeholder, where Sinch will include the actual code. For example, `"This is your OTP code {{CODE}}!"`

> ### Remember:  
> Before configuring this property in the administration console for SAP Cloud Identity Services, first request this property to the Sinch Support team.



</td>
</tr>
</table>

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

To configure the administration console, follow the procedure below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Choose the *Sinch Service Configuration* list item.

4.  Choose the *Edit* button.

5.  Select *Sinch Verification* and enter the information that is required.

6.  Save your entries.


**Related Information**  


[Sinch Verification API](https://www.sinch.com/products/apis/verification/)

[Sinch Verification Developer Documentation](https://developers.sinch.com/docs/verification/)

