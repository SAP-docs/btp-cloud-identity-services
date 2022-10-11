<!-- loio265e41ee33a24b51bb1a2e51cf97afbd -->

# Remove Social Identity Providers Configuration

You can remove the configurations of the social providers in the administration of Identity Authentication.



## Prerequisites

You have a configured social provider in the administration console for Identity Authentication



<a name="loio265e41ee33a24b51bb1a2e51cf97afbd__context_hyl_jsg_vgb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.



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

2.  Choose the *Social Identity Providers* tile.

    This operation opens a list of the social providers.

3.  Choose the list item of the social provider whose configuration you want to remove.

4.  Choоse *<Social Provider Name\> Sign-On*.

5.  Choоse the *Remove Configuration* button.

6.  Confirm your choice.




## Results

The configuration for the selected social provider will be removed. The social provider will not appear on the logоn pages of the applications in the tenant.

**Related Information**  


[Configure Apple as Identity Provider](configure-apple-as-identity-provider-fe6f7f0.md "Users can log on to applications with their Apple ID credentials by linking their accounts in Identity Authentication to their Apple account.")

[Configure Facebook as Identity Provider](configure-facebook-as-identity-provider-cc16b33.md "By configuring Facebook as a social identity provider, users can log on to applications with their social media credentials by liking their accounts in Identity Authentication to the social media account.")

[Configure Google as Identity Provider](configure-google-as-identity-provider-caf215f.md "By configuring Google as a social identity provider, users can log on to applications with their Google credentials by liking their accounts in Identity Authentication to the Google account.")

[Configure LinkedIn as Identity Provider](configure-linkedin-as-identity-provider-9077d6c.md "By configuring LinkedIn as social identity provider, users can log on to applications with their LinkedIn credentials by liking their accounts in Identity Authentication to the LinkedIn account.")

[Configure Twitter as Identity Provider](configure-twitter-as-identity-provider-f5bc52d.md "By configuring Twitter as social provider, users can log on to applications with their Twitter credentials by liking their accounts in Identity Authentication to the Twitter account.")

