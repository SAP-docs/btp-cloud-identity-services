<!-- loioe933711e7a0545dda3cfb39c80a63f01 -->

# Enforce Issuer Validation for Corporate Identity Providers

To mitigate mix-up attacks, require corporate identity providers acting as authorization servers to identify themselves in their responses. The OAuth 2.0 Authorization Framework, as defined in [RFC6749](https://datatracker.ietf.org/doc/html/rfc6749), doesn't require the authorization server to identify itself in its responses for all grant types. Enable this option to require the corporate identity provider to identify itself in the `iss` parameter of the response.



<a name="loioe933711e7a0545dda3cfb39c80a63f01__prereq_osk_lxb_rgc"/>

## Prerequisites

> ### Caution:  
> Make sure that your corporate identity provider supports and is configured to issue the `iss` parameter. If the corporate identity provider doesn't include this parameter, SAP Cloud Identity Services rejects the response. You can't use this corporate identity provider for authentication as long as issuer validation is enforced.
> 
> To check if you corporate identity provider supports this feature, visit its discovery endpoint and look for ***"authorization\_response\_iss\_parameter\_supported":true***. For an example of the discovery endpoint, see `https://accounts.sap.com/.well-known/openid-configuration`.
> 
> The service also rejects responses that include values in `iss` that aren't trusted identity providers. Verify that the corporate identity provider sends the issuer in your trust configuration.
> 
> For more information, [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md)



## Context

With this implementation, SAP Cloud Identity Services supports [RFC9207](https://datatracker.ietf.org/doc/html/rfc9207).



## Procedure

1.  In the administration console for SAP Cloud Identity Services, navigate to the OpenID Connect configuration of your corporate identity provider.

    For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).

2.  Enable the *Enforce Issuer Validation* check box.

3.  Use the *Validate* button to confirm that the configuration is still working.

4.  Save your entries.


