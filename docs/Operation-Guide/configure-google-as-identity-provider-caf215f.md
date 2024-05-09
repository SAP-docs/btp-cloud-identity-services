<!-- loiocaf215f71fa743d3a67da11e130acd9e -->

# Configure Google as Identity Provider

By configuring Google as a social identity provider, users can log on to applications with their Google credentials by liking their accounts in Identity Authentication to the Google account.



## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.

Identity Authentication uses the OAuth protocol for social sign-on via Google as a social identity provider.

Once a user has allowed Identity Authentication to link his or her account with the Google account, the user can log on to applications via the social provider.

To configure Google as social identity provider for the tenant, you have to register new applications on the Google site. For more details, see Related Information.

> ### Note:  
> You need to type `https://<tenant ID>.accounts.ondemand.com/ui/oauth/googleCallback` in the *Authorized redirect URIs* field when you create your client ID in Google Developers Console. For more information about the redirect URIs for your OAuth 2.0 credentials, see [Set a redirect URI](https://developers.google.com/identity/protocols/OpenIDConnect#setredirecturi).

To perform the social identity provider configuration in the administration console for SAP Cloud Identity Services, you have to provide the following data:

**Required Google Settings**


<table>
<tr>
<th valign="top">

Authentication Attribute

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Google's client ID

</td>
<td valign="top">

The Google OAuth 2.0 credential after you set a project in the Google Developers Console.

</td>
</tr>
<tr>
<td valign="top">

Google's client secret

</td>
<td valign="top">

The Google OAuth 2.0 credential after you set a project in the Google Developers Console.

</td>
</tr>
</table>



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Social Identity Providers* tile.

    This operation opens a list of the social providers.

3.  Choose the Google list item.

4.  Under *Configuration*, choose *Edit*.

5.  Enter the generated authentication attributes from the social provider.

    > ### Note:  
    > Check for leading or trailing spaces in the authentication attributes fields, and delete them. Sign-on through the social identity provider will not work if there are blank spaces before or after the strings in the fields.

6.  Save your configuration.

    If the operation is successful, you will receive the following message: ***Google authentication configured***. The slider next to the social provider is switched to *ON*.

    > ### Note:  
    > With the slider *ON* the social identity provider is shown as authentication option on the logon screen. If you do not want to show any of the social providers on the logon screen, you can drag the slider next to the social provider to *OFF*. The configuration for this social provider will be preserved, but the social provider will not appear on the logon pages of the applications in the tenant.
    > 
    > To disable the social sign option for a specific social provider, remove the configuration for that provider. See Related Information for more details.




## Next Steps

The above configurations are valid for the whole tenant. They will take effect for a specific application if you enable the *Social Sign-On* option via the administration console. For more information about how to enable social sign on for a specific application, see [Enable or Disable Social Sign-On for an Application](enable-or-disable-social-sign-on-for-an-application-ff12d3d.md).

**Related Information**  


[Configure Apple as Identity Provider](configure-apple-as-identity-provider-fe6f7f0.md "Users can log on to applications with their Apple ID credentials by linking their accounts in Identity Authentication to their Apple account.")

[Configure Facebook as Identity Provider](configure-facebook-as-identity-provider-cc16b33.md "By configuring Facebook as a social identity provider, users can log on to applications with their social media credentials by liking their accounts in Identity Authentication to the social media account.")

[Configure LinkedIn as Identity Provider](configure-linkedin-as-identity-provider-9077d6c.md "By configuring LinkedIn as social identity provider, users can log on to applications with their LinkedIn credentials by liking their accounts in Identity Authentication to the LinkedIn account.")

[Configure X as Identity Provider](configure-x-as-identity-provider-f5bc52d.md "By configuring X as social provider, users can log on to applications with their X credentials by liking their accounts in Identity Authentication to the X account.")

[Remove Social Identity Providers Configuration](remove-social-identity-providers-configuration-265e41e.md "You can remove the configurations of the social providers in the administration console for SAP Cloud Identity Services.")

[Obtain OAuth 2.0 credentials](https://developers.google.com/accounts/docs/OAuth2Login#getcredentials)

[Verify your site ownership](https://support.google.com/webmasters/answer/35179?hl=en&ref_topic=4564314)

[Social Authentication](../User-Guide/social-authentication-108607a.md "")

