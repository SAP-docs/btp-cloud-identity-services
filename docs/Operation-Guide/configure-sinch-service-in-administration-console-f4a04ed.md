<!-- loiof4a04ed54b544ee9ac1862b5d79178de -->

# Configure Sinch Service in Administration Console

Configure Sinch Service to enable *Phone Verification via SMS* or *SMS Two-Factor Authentication* in the administration console.



<a name="loiof4a04ed54b544ee9ac1862b5d79178de__prereq_apw_h4w_hdb"/>

## Prerequisites

-   You have either an account in Sinch Authentication 365 or in Sinch Verification Service. Once you create a Sinch service account, you receive an e-mail with your account information.

-   You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).




<a name="loiof4a04ed54b544ee9ac1862b5d79178de__context_j2w_pc5_ldb"/>

## Context

Sinch service enables multichannel two-factor authentication \(2FA\), adding another layer of security to customers' online accounts, beyond their login and password. The service enables you to configure tokens – such as one-time passwords \(OTPs\), personal identification numbers \(PINs\), and verification codes – that are tailored to businesses and particular use cases.

For the integration between Identity Authentication and Sinch service, you must provide information in the administration console for Identity Authentication. You can have eithet a Sinch Authentication 365 or Sinch Verification configuration. You can clear the fields by choosing the *Remove Configuration* button at the top of the screen.

Based on your Sinch service type, provide the following:

<a name="loiof4a04ed54b544ee9ac1862b5d79178de__table_jtz_whv_tsb"/>Sinch Authentication 365


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

*Account ID*



</td>
<td valign="top">

This is your Authentication 365 Account ID. The information is available in the accounts menu of Authentication 365 web-based administrative user interface. For more information, see [Sinch Authentication 365/Account Information](https://authentication.sapdigitalinterconnect.com/documentation/ui/account_information/).



</td>
</tr>
<tr>
<td valign="top">

*OAuth Token URL*



</td>
<td valign="top">

The OAuth token URL. Example: `https://<domain>/oauth/token`



</td>
</tr>
<tr>
<td valign="top">

*Client ID*



</td>
<td valign="top">

Your API Secret Key for Sinch Authentication 365. For more information, see, [Sinch Authentication 365/API Key Management.](https://authentication.sapdigitalinterconnect.com/documentation/ui/api_keys/)



</td>
</tr>
<tr>
<td valign="top">

*Client Secret*



</td>
<td valign="top">

Your API Key Code for Sinch Authentication 365. For more information, see [Sinch Authentication 365/API Key Management.](https://authentication.sapdigitalinterconnect.com/documentation/ui/api_keys/).



</td>
</tr>
<tr>
<td valign="top">

*Code Timeout*



</td>
<td valign="top">

The timeout in seconds. Provide a number between 30 and 900.



</td>
</tr>
<tr>
<td valign="top">

*Code Length*



</td>
<td valign="top">

The length of the generated code. Code length must be between 4 and 8 digits.



</td>
</tr>
<tr>
<td valign="top">

*Send Code URL*



</td>
<td valign="top">

The Sinch Authentication 365 URL that is used to generate the tokens \(codes\). Example: `https://authentication.<domain>/tokens/generate`



</td>
</tr>
<tr>
<td valign="top">

*Validate Code URL*



</td>
<td valign="top">

The Sinch Authentication 365 URL that is used to validate the tokens \(codes\). Example: `https://authentication.<domain>/tokens/validate` 



</td>
</tr>
<tr>
<td valign="top">

*SMS text*



</td>
<td valign="top">

The text that the user will receive in the SMS. The text is followed by the verification code. For example: "Your verification code is: \[the generated token\]".



</td>
</tr>
</table>

> ### Remember:  
> All fields are required.

<a name="loiof4a04ed54b544ee9ac1862b5d79178de__table_hcd_rph_k5b"/>Sinch Verification


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
> Before configuring this property in the administration console for Identity Authentication, first request this property to the Sinch Support team.



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
> Before configuring this property in the administration console for Identity Authentication, first request this property to the Sinch Support team.



</td>
</tr>
</table>

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

To configure the administration console, follow the procedure below:



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

3.  Choose the *Sinch Service Configuration* list item.

4.  Choose the *Edit* button.

5.  Select your Sinch service type and enter the information that is required for the chosen type.

    -   Sinch Verification
    -   Sinch Authentication 365

6.  Save your entries.


**Related Information**  


[Sinch Authentication 365](https://authentication.sapdigitalinterconnect.com/)

[Sinch Verification API](https://www.sinch.com/products/apis/verification/)

[Sinch Verification Developer Documentation](https://developers.sinch.com/docs/verification/)

