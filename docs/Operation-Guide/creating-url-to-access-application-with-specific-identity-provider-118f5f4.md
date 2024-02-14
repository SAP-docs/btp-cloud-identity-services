<!-- loio118f5f4203fd42c98255b1ecf6baa484 -->

# Creating URL To Access Application with Specific Identity Provider

Create a URL to access specific application in scenarios where Identity Authentication acts as a proxy to delegate authentication to multiple external corporate identity providers.

<a name="task_sp4_k4c_nzb"/>

<!-- task\_sp4\_k4c\_nzb -->

## SAML 2.0 Application



<a name="task_sp4_k4c_nzb__prereq_ysc_gfd_nzb"/>

## Prerequisites

The application supports IdP-initiated Single Sign-On \(SSO\). For more information, see [Security Assertion Markup Language \(SAML\) V2.0 Technical Overview](http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html).



<a name="task_sp4_k4c_nzb__context_nv4_tfd_nzb"/>

## Context

The link for IdP-Initiated SSO follows the pattern: `https://<tenant_ID>.accounts.ondemand.com/saml2/idp/sso?sp=<sp_name>&idp=<corporateIdP_name>`

> ### Note:  
> -   `sp` - Name of the SAML 2 service provider for which SSO is performed. The `sp_name` value of the parameter equals to the `Entity ID` of the service provider. This parameter is needed for Identity Authentication to know which service provider to redirect the user to after successful authentication.
> -   `idp` - The name of the corporate identity provider as configured in the administration console for SAP Cloud Identity Services.
> 
>     When multiple identity providers are allowed for an application via conditional authentication, this parameter enables the client to determine which corporate identity provider to be used. Identity Authentication uses the `idp` to detect the correct corporate identity provider and redirect the request to it. The user authenticates against the corporate identity provider.

<a name="task_ppl_l4c_nzb"/>

<!-- task\_ppl\_l4c\_nzb -->

## OpenID Connect Application



<a name="task_ppl_l4c_nzb__prereq_ojc_g4d_nzb"/>

## Prerequisites

The application supports selection of the corporate IdP via the application URL. For more information, see [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md).



<a name="task_ppl_l4c_nzb__context_wnq_ppd_nzb"/>

## Context

The link for IdP-Initiated SSO follows the pattern: `https://<tenant_ID>.accounts.ondemand.com/oauth2/authorize?idp=<corporateIdP_name>`.

