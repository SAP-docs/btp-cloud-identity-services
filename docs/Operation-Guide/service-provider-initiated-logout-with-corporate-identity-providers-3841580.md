<!-- loio3841580082cb4af6a13289e98a0cce12 -->

# Service Provider Initiated Logout with Corporate Identity Providers

This document provides information about the service provider initiated logout with corporate identity providers.

In this scenario, Identity Authentication has to be configured as an identity provider proxy. The corporate identity provider acts as an authenticating IdP to the application.

The logout procedure is triggered by the user at the service provider and results in a logout request sent to the identity provider proxy. Consequently, the identity provider proxy processes the request and destroys any local session information about the user. The identity provider proxy then checks whether there are other service providers in the single sign-on \(SSO\) session and sends logout requests to all of them. In return, the service providers send logout responses to the identity provider proxy informing it that the logout process is successful. Finally, the identity provider proxy sends a logout response to the original requesting service provider or the service provider of the application.

As an additional option, the tenant administrator of Identity Authentication can configure a URL which is sent in the SAML 2.0 Logout Response as an extension. The URL can be used to redirect the users after logging out of the application. The URL is specific for each corporate identity provider with which Identity Authentication has established a trust. For more information about this option, see [Configure Logout URL](service-provider-initiated-logout-with-corporate-identity-providers-3841580.md#loio50d8f6b818fc40dba3f693c3f609986f).



## Corporate Identity Provider Logout Flow

When Identity Authentication acts as a proxy to delegate authentication to an external corporate identity provider, and the user who is logged on to one or more applications chooses the *Log Out* link in one of the applications, the following flow is in force:

1.  The user triggers a logout from the application.
2.   Identity Authentication checks if the user is logged on to other applications. If yes, Identity Authentication sends logout requests to the applications, and terminates the sessions.
3.   Identity Authentication sends logout requests to the corporate identity provider or corporate identity providers, if there are more than one.
4.  The user is logged out of the corporate identity providers.
5.  The user is logged out of Identity Authentication.
6.  A logout response is sent to the initiating application.
7.  \(Optional\) If the Redirect URL option is configured in the administration console for SAP Cloud Identity Services, the URL is sent as an extension in the SAML 2.0 Logout Response. This option can be used by the application to redirect the user to the destination from the link configured for the specific corporate identity provider.

    > ### Note:  
    > This step is valid only if the application supports the redirect of the user, as for example SAP SuccessFactors HCM Suite.


 <a name="loio50d8f6b818fc40dba3f693c3f609986f"/>

<!-- loio50d8f6b818fc40dba3f693c3f609986f -->

## Configure Logout URL

As a tenant administrator, you can specify a link which is sent as an extension in the SAML 2.0 Logout Response. The link can be used by the application to redirect the user after successfully logging out of the application when Identity Authentication acts as an identity provider proxy.



## Prerequisites

Identity Authentication must be configured to act as an identity provider proxy to delegate the authentication to a corporate identity provider. For more information, see [Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md).



## Context

When the user logs out of an application via a service provider initiated logout he or she can be redirected to a specific URL. This configuration can be applied to scenarios with one or more corporate identity providers. You configure a specific redirect URL in the administration console for SAP Cloud Identity Services for each corporate identity provider.

![](images/SP-Initiated_Log_Out_Redirect_cd77718.png)

1.  Triggers Logout from the application.
2.  Sends SAML Logout Request.
3.  Sends SAML Logout Request.
4.  Sends SAML Logout Response.
5.  Sends SAML Logout Response with redirect URL.
6.  Application redirects the user to the configured URL.

To configure the logout URL, follow the procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md)..

4.  Choose *Logout Redirect URL*.

5.  Type the redirect URL in the provided field.

6.  Save your changes.




## Results

Once the user has logged out of the application, Identity Authentication sends the logout URL in the SAML 2.0 Response as an extension to the application. The logout URL can be used by the application to redirect the user to the URL configured for the corporate identity provider in the administration console for SAP Cloud Identity Services.

