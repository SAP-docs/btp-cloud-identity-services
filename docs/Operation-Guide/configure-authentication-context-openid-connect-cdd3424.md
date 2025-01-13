<!-- loiocdd3424e8e5c4f3bb903decfb4a5d7ed -->

# Configure Authentication Context \(OpenID Connect\)

Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.



<a name="loiocdd3424e8e5c4f3bb903decfb4a5d7ed__context_fqk_mkb_3bc"/>

## Context

> ### Note:  
> The following configuration is valid for the OpenID connect corporate identity providers.

> ### Tip:  
> If the authentication context exists in the metadata of the identity provider it, can be seen in the administration console at *Identity Providers* \> *Corporate Identity Providers* \> *from the list - the corporate IdP that provides user authentication to the application* \> *OpenID Connect Configuration* \> *Supported Authentication Contexts section*.

> ### Restriction:  
> You can add up to 20 authentication context class references with a length of up to 99 characters each.



<a name="loiocdd3424e8e5c4f3bb903decfb4a5d7ed__steps_exl_bpk_f4b"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Conditional Authentication*, choose *Configure Requests to Corporate Identity Providers* \> *OpenID Connect*.

6.  Choose *Add* \> *enter the authentication context class references* \> *save your changes*.


**Related Information**  


[Configure Authentication Context \(SAML 2.0\)](configure-authentication-context-saml-2-0-028cee2.md "Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.")

[Configure Different Trust Configurations for the Same Identity Authentication](configure-different-trust-configurations-for-the-same-identity-authentication-ba2faa9.md "Tenant administrator can configure the issuer name in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.")

