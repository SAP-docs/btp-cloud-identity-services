<!-- loiocdd3424e8e5c4f3bb903decfb4a5d7ed -->

# Configure Authentication Context \(OpenID Connect\)

Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.



<a name="loiocdd3424e8e5c4f3bb903decfb4a5d7ed__context_fqk_mkb_3bc"/>

## Context

> ### Note:  
> The following configuration is valid for the OpenID connect corporate identity providers.

The authentication context enables administrators to ensure an authentication context. For example, you can require the corporate identity provider to authenticate users for a particular application with multifactor authentication or certificate-based authentication. The corporate identity providers define what authentication contexts that they support as well as the values they require to trigger a particular authentication context. The OIDC standard doesn't define the authentication context values.

For more information, see [OpenID Connect Core 1.0 incorporating errata set 2](https://openid.net/specs/openid-connect-core-1_0.html).

> ### Tip:  
> If the authentication context exists in the metadata of the identity provider it, can be seen in the administration console at *Identity Providers* \> *Corporate Identity Providers* \> *from the list - the corporate IdP that provides user authentication to the application* \> *OpenID Connect Configuration* \> *Supported Authentication Contexts section*.

> ### Restriction:  
> You can add up to 20 authentication context references with a length of up to 99 characters each.



<a name="loiocdd3424e8e5c4f3bb903decfb4a5d7ed__steps_exl_bpk_f4b"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Conditional Authentication*, choose *Configure Requests to Corporate Identity Providers* \> *OpenID Connect*.

6.  Choose *Add* \> *enter the authentication context class references* \> *save your changes*.




<a name="loiocdd3424e8e5c4f3bb903decfb4a5d7ed__result_ysb_fpp_jgc"/>

## Results

The application sends the configured ACRs \(authentication context references\) to the corporate identity provider as part of the authorization request. These values are included in the `acr_values` query parameter and are separated by spaces \( \). You can see this parameter in the network trace of your browser.

**Related Information**  


[Configure Authentication Context \(SAML 2.0\)](configure-authentication-context-saml-2-0-028cee2.md "Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.")

[Configure Different Trust Configurations for the Same Identity Authentication Tenant](configure-different-trust-configurations-for-the-same-identity-authentication-tenant-ba2faa9.md "Tenant administrator can configure the issuer name in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.")

