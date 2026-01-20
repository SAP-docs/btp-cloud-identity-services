<!-- loio1a1637d69fe043ed948b5c1800ebe780 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Find Which Applications Trust a Corporate Identity Provider

The administration console for SAP Cloud Identity Services enables you to quickly find applications which trust a given corporate identity provider. This information enables you to find the applications you need to consider when you change or remove a corporate identity provider.



## Context

Applications trust in corporate identity providers is founded in one or more of the following ways:

-   Client authentication

    This source is configured by trust by issuer. For more information, see [Configure JWT for OAuth Client Authentication](configure-jwt-for-oauth-client-authentication-db97a69.md).

-   Conditional authentication

    For more information, see [Configure Conditional Authentication for an Application](configure-conditional-authentication-for-an-application-0143dce.md).

-   Trust identity providers

    For more information, see [Enable SSO with Corporate Identity Providers](enable-sso-with-corporate-identity-providers-f7ec8d2.md).


> ### Note:  
> Only conditional authentication and trust in identity providers can't be combined.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md).

4.  Choose *Trust* \> *Trusting Applications*.

    The system displays a list of applications which trust this corporate identity provider. Search for a specific application or sort by the source of trust.




<a name="loio1a1637d69fe043ed948b5c1800ebe780__postreq_kz5_nx4_xfc"/>

## Next Steps

To navigate to the source of the trust configuration in the relevant application, choose the <span class="SAP-icons-V5"></span> \(check mark\) icon.

