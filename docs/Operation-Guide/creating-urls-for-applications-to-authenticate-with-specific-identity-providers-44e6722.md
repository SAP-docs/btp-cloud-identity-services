<!-- copy44e67223a98f45ed94aaee7513e90a95 -->

# Creating URLs for Applications to Authenticate with Specific Identity Providers

The URL to access an application is generally determined by the application. When you have multiple identity providers available, you can steer users to the correct identity provider with the `idp` parameter.



<a name="copy44e67223a98f45ed94aaee7513e90a95__prereq_idz_3kf_3gc"/>

## Prerequisites

-   You have set a corporate IdP as the default identity provider in the administration console.

    For more information, see [Choose a Corporate Identity Provider as Default](choose-a-corporate-identity-provider-as-default-44dd636.md).

-   The application supports selection of the corporate IdP with the idp parameter in the application URL. See the documentation of the application.

    > ### Example:  
    > Example: Many BTP applications use the application router, which requires the `sap_idp` query parameter.
    > 
    > For more information, see [@sap/approuter](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fwww.npmjs.com%2Fpackage%2F%40sap%2Fapprouter) at *npm*.

-   If you have enabled the *Allow Identity Authentication Users Log On* option, you can use the reserved name `local` to authenticate with your Identity Authentication tenant.

    For more information, see [\(Optional\) Use the Allow Identity Authentication Users Log On Option](optional-use-the-allow-identity-authentication-users-log-on-option-2ec9a7f.md).




## Procedure

Use the `idp` parameter in the URL for OIDC or in the URL or body for SAML.

> ### Caution:  
> It depends on the service provider whether the parameter can be passed in body or URL. Identity Authentication doesn't control how the SAML 2.0 request is sent.

**Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`idp`

</td>
<td valign="top">

Name of the identity provider as defined under the *Name* in the *Trust* configuration of the identity provider.

-   For SAML, see [Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md).

-   For OIDC, see [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).


If you need a chain of identity providers, use a comma without spaces \(,\) to separate them.

Use the value `local` to override the conditional authentication configuration and authenticate with Identity Authentication instead.

</td>
</tr>
</table>

