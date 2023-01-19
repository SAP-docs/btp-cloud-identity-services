<!-- loio028cee2589fd418896ae0235b0aeac40 -->

# Configure Authentication Context

Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.



<a name="loio028cee2589fd418896ae0235b0aeac40__steps_exl_bpk_f4b"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

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

