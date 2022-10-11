<!-- loio028cee2589fd418896ae0235b0aeac40 -->

# Configure Authentication Context

Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.



<a name="loio028cee2589fd418896ae0235b0aeac40__steps_exl_bpk_f4b"/>

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

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the *Trust* tab.

4.  Under *Conditional Authentication*, choose *Configure SAML 2.0 Requests to Corporate Identity Providers*.

5.  Under *Configure Authentication Context*, choose one of the following options:

    -   *None* - Authentication context is not sent. The requested authentication context from the service provider is ignored.
    -   *Service Provider Authentication Context* - The received authentication context from the service provider is sent.
    -   *Password Protected Transport* - Authentication context class `urn:oasis:names:tc:SAML:2.0:ac:classes:PasswordProtectedTransport` is sent. The requested authentication context from the service provider is ignored.

6.  Save your changes.


**Related Information**  


[Configure Different Trust Configurations for the Same Identity Authentication](configure-different-trust-configurations-for-the-same-identity-authentication-ba2faa9.md "Tenant administrator can configure the issuer name in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.")

