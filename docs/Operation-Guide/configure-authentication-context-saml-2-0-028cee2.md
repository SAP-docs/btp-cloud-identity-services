<!-- loio028cee2589fd418896ae0235b0aeac40 -->

# Configure Authentication Context \(SAML 2.0\)

Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.



<a name="loio028cee2589fd418896ae0235b0aeac40__context_t4h_3mb_3bc"/>

## Context

> ### Note:  
> The following configuration is valid for SAML 2.0 corporate identity providers.



<a name="loio028cee2589fd418896ae0235b0aeac40__steps_exl_bpk_f4b"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Conditional Authentication*, choose *Configure Requests to Corporate Identity Providers* \> *SAML 2.0*.

6.  Choose one of the following options:

    -   *None* - Authentication context isn't sent. The requested authentication context from the service provider is ignored.
    -   *Service Provider Authentication Context* \(Available only for SAML 2.0 applications\) - The received authentication context from the service provider is sent.
    -   *Password Protected Transport* - Authentication context class `urn:oasis:names:tc:SAML:2.0:ac:classes:PasswordProtectedTransport` is sent. The requested authentication context from the service provider is ignored.

7.  Save your configuration.


**Related Information**  


[Configure Authentication Context \(OpenID Connect \(OIDC\)\)](configure-authentication-context-openid-connect-oidc-cdd3424.md "Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.")

[Configure Different Trust Configurations for the Same Identity Authentication Tenant](configure-different-trust-configurations-for-the-same-identity-authentication-tenant-ba2faa9.md "Tenant administrator can configure the issuer name in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.")

