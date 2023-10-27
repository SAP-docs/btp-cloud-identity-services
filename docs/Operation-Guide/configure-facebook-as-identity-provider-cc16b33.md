<!-- loiocc16b335cb5941ddb92ecb7478251c81 -->

# Configure Facebook as Identity Provider

By configuring Facebook as a social identity provider, users can log on to applications with their social media credentials by liking their accounts in Identity Authentication to the social media account.



## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.

Identity Authentication uses the OAuth protocol for social sign-on via Facebook as a social identity provider.

Once a user has allowed Identity Authentication to link his or her account with the Facebook account, the user can log on to applications via the social provider.

To configure Facebook as social identity provider for the tenant, you have to register new applications on the Facebook site. For more details, see Related Information.

> ### Note:  
> You need to type `https://<tenant ID>.accounts.ondemand.com/ui/oauth/oauthCallback` in the *Valid OAuth redirect URIs* field in the Settings section of Facebook Login in the App Dashboard. For more information about Facebook Valid OAuth redirect URIs, see [Enable Strict Mode](https://developers.facebook.com/docs/facebook-login/security/#strict_mode).

To perform the social identity provider configuration in the administration console for SAP Cloud Identity Services, you have to provide the following data:

**Required Facebook Settings**


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

Facebook's application ID

</td>
<td valign="top">

The ID generated after you add an application on Facebook.

</td>
</tr>
<tr>
<td valign="top">

Facebook's application secret

</td>
<td valign="top">

The secret generated after you add an application on Facebook.

</td>
</tr>
</table>



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Social Identity Providers* tile.

    This operation opens a list of the social providers.

3.  Choose the Facebook list item.

4.  Under *Configuration*, choose *Edit*.

5.  Enter the generated authentication attributes from the social provider.

    > ### Note:  
    > Check for leading or trailing spaces in the authentication attributes fields, and delete them. Sign-on through the social identity provider will not work if there are blank spaces before or after the strings in the fields.

6.  Save your configuration.

    If the operation is successful, you will receive the following message: ***Facebook authentication configured***. The slider next to the social provider is switched to *ON*.

    > ### Note:  
    > With the slider *ON* the social identity provider is shown as authentication option on the logon screen. If you do not want to show any of the social providers on the logon screen, you can drag the slider next to the social provider to *OFF*. The configuration for this social provider will be preserved, but the social provider will not appear on the logon pages of the applications in the tenant.
    > 
    > To disable the social sign option for a specific social provider, remove the configuration for that provider. See Related Information for more details.




## Next Steps

The above configurations are valid for the whole tenant. They will take effect for a specific application if you enable the *Social Sign-On* option via the administration console. For more information about how to enable social sign on for a specific application, see [Enable or Disable Social Sign-On for an Application](enable-or-disable-social-sign-on-for-an-application-ff12d3d.md).

**Related Information**  


[Configure Apple as Identity Provider](configure-apple-as-identity-provider-fe6f7f0.md "Users can log on to applications with their Apple ID credentials by linking their accounts in Identity Authentication to their Apple account.")

[Configure Google as Identity Provider](configure-google-as-identity-provider-caf215f.md "By configuring Google as a social identity provider, users can log on to applications with their Google credentials by liking their accounts in Identity Authentication to the Google account.")

[Configure LinkedIn as Identity Provider](configure-linkedin-as-identity-provider-9077d6c.md "By configuring LinkedIn as social identity provider, users can log on to applications with their LinkedIn credentials by liking their accounts in Identity Authentication to the LinkedIn account.")

[Configure Twitter as Identity Provider](configure-twitter-as-identity-provider-f5bc52d.md "By configuring Twitter as social provider, users can log on to applications with their Twitter credentials by liking their accounts in Identity Authentication to the Twitter account.")

[Remove Social Identity Providers Configuration](remove-social-identity-providers-configuration-265e41e.md "You can remove the configurations of the social providers in the administration console for SAP Cloud Identity Services.")

[Facebook Login](https://developers.facebook.com/docs/facebook-login/v2.2)

[Enable or Disable Social Sign-On for an Application](enable-or-disable-social-sign-on-for-an-application-ff12d3d.md "Social sign-on allows users to link their Identity Authentication accounts with social network accounts.")

[Remove Social Identity Providers Configuration](remove-social-identity-providers-configuration-265e41e.md "You can remove the configurations of the social providers in the administration console for SAP Cloud Identity Services.")

[Social Authentication](../User-Guide/social-authentication-108607a.md "")

