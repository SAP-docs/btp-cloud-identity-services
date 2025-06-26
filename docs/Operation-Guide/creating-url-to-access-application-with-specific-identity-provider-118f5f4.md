<!-- loio118f5f4203fd42c98255b1ecf6baa484 -->

# Creating URL To Access Application with Specific Identity Provider

Create a URL which takes users to a specific application with a specific corporate identity provider when Identity Authentication acts as proxy to multiple corporate identity providers \(IdP\), and users do not decide which one to use.

<a name="task_sp4_k4c_nzb"/>

<!-- task\_sp4\_k4c\_nzb -->

## SAML 2.0 Application



<a name="task_sp4_k4c_nzb__prereq_ysc_gfd_nzb"/>

## Prerequisites

-   You have configured one of the following options:
    -   You have set the corporate IdP as default identity provider in the administration console. For more information, see [Authenticating Identity Provider for an Application](authenticating-identity-provider-for-an-application-b3aae12.md).
    -   You have enabled IdP-initiated Single Sign-On \(SSO\) from all configured corporate IdPs. For more information, see [Enable SSO with All Corporate Identity Providers](enable-sso-with-all-corporate-identity-providers-f7ec8d2.md) .

-   The application supports IdP-initiated Single Sign-On \(SSO\). For more information, see [Security Assertion Markup Language \(SAML\) V2.0 Technical Overview](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html).




<a name="task_sp4_k4c_nzb__context_nv4_tfd_nzb"/>

## Context

The link for IdP-Initiated SSO follows the pattern: `https://<tenant_ID>.accounts.ondemand.com/saml2/idp/sso?sp=<sp_name>&idp=<corporateIdP1_name>,<corporateIdP2_name>`

When there is more than one corporate IdP, the user is redirected to the first idp from the parameter, and additionally the second IdP from the parameter is added to the request again in an `idp` parameter.

> ### Note:  
> -   `sp`
> 
>     Name of the SAML 2 service provider for which SSO is performed. The `sp_name` value of the parameter equals to the `Entity ID` of the service provider. This parameter is needed for Identity Authentication to know which service provider to redirect the user to after successful authentication.
> 
> -   `idp`
> 
>     The technical name of the corporate identity provider as configured in the administration console for SAP Cloud Identity Services.
> 
>     When a chain of identity providers are allowed for an application via conditional authentication, these parameters enable the client to specify which corporate identity providers are to be used. Identity Authentication uses the `idp` parameter to detect the correct corporate identity providers and redirect the request to them. When there is more than one corporate IdP in the IdP-initiated link, they are separated by comma "`,`" without space between them.
> 
>     > ### Remember:  
>     > If there is more than one corporate IdP in the IdP-initiated link, use *HTTP-Redirect* as default binding in the trust configuration with SAML 2.0 Corporate Identity Provider. For more information, see [Configure Trust on Identity Authentication Side](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md#loio33832e58695345eea2cd91a2cc8ab24c__chunked_trust_ias).

<a name="task_ppl_l4c_nzb"/>

<!-- task\_ppl\_l4c\_nzb -->

## OpenID Connect Application



<a name="task_ppl_l4c_nzb__prereq_ojc_g4d_nzb"/>

## Prerequisites

-   You have set the corporate identity provider \(IdP\) as default identity provider in the administration console. For more information, see [Authenticating Identity Provider for an Application](authenticating-identity-provider-for-an-application-b3aae12.md).
-   The application supports selection of the corporate IdP via the `idp` parameter in the application URL. For more information how to configure the `idp` parameter, see [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md).


