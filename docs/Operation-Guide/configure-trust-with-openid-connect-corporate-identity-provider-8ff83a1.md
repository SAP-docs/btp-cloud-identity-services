<!-- loio8ff83a12bbb8491c9558d635d6bbb287 -->

# Configure Trust with OpenID Connect Corporate Identity Provider

This document is intended to help you configure trust with an OpenID Connect \(OIDC\) corporate identity provider. In this scenario, Identity Authentication acts as a proxy to delegate the authentication to an OIDC-compliant corporate identity provider.



## Context

Identity Authentication can use OIDC-compliant identity providers as external authenticating authorities. The service acts as a proxy to delegate authentication to the external corporate identity provider. The requests for authentication sent by the relying party are forwarded to the corporate identity provider.

As an identity provider proxy, Identity Authentication acts as an OpenID identity provider to the relying party, and as a relying party to the corporate identity provider. Once a user is authenticated at the corporate identity provider, successive authentication requests from relying parties, which use the same corporate identity provider aren't forwarded to it as long as the session at Identity Authentication is active. Identity Authentication issues JSON Web Tokens \(JWTs\) based on the user data received during the first authentication.

To use Identity Authentication as a proxy to delegate authentication to an external OpenID Connect corporate identity provider, configure trust with that corporate identity provider.

> ### Tip:  
> If you want to change one corporate identity provider with another, for example move from a SAML identity provider to an OpenID Connect one, it's helpful to know the applications that the corporate identity provider uses. To see the applications that have established trust with a specific corporate identity provider, sign in to the administration console and go to *Identity Providers* \> *Corporate Identity Providers* \> *identity provider from the list* \> *Trusting Applications*.

To configure trust with the corporate identity provider, use the following procedures:

<a name="task_jlj_2rm_qgb"/>

<!-- task\_jlj\_2rm\_qgb -->

## 1. Configure the Corporate Identity Provider Side

Configure Identity Authentication as an application at the corporate identity provider side.



<a name="task_jlj_2rm_qgb__prereq_nmf_kby_wsb"/>

## Prerequisites

-   You have registered Identity Authentication as an application at the corporate identity provider.
-   You have created a client secret.

    > ### Note:  
    > Use the client credentials of the application's registration for Client ID and Client Secret. Use corporate identity provider tenant as Issuer. You can retrieve the information by calling the discovery endpoint of the corporate identity provider:
    > 
    > ```
    > https://<OpenID-Connect-IdP>/.well-known/openid-configuration
    > ```

-   \(For the authorization code flow\) - You have configured the callback endpoint of the Identity Authentication tenant as `Redirect URI` 

    ```
    https://<Cloud Identity Services domain>/oauth2/callback
    ```

    > ### Note:  
    > The domain part has the following pattern:
    > 
    > `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).


> ### Note:  
> Use the *OIDC Callback URL* button to copy the callback URL of the Identity Authentication tenant.



<a name="task_jlj_2rm_qgb__context_ryl_55m_qgb"/>

## Context

The information retrieved from `.well-known/openid-configuration` endpoint can contain:


<table>
<tr>
<th valign="top">

Attribute

</th>
<th valign="top">

Notes

</th>
</tr>
<tr>
<td valign="top">

`issuer`

</td>
<td valign="top">

Required. Must be a valid URI.

</td>
</tr>
<tr>
<td valign="top">

`jwks_uri`

</td>
<td valign="top">

Required. Must be a valid URI.

</td>
</tr>
<tr>
<td valign="top">

`token_endpoint`

</td>
<td valign="top">

Optional. If present it must be a valid URI.

> ### Note:  
> If the `token_endpoint` isn't supported, it can't participate in browser-based SSO flows. JWT Bearer flow is still possible.



</td>
</tr>
<tr>
<td valign="top">

`authorization_endpoint`

</td>
<td valign="top">

Optional. If present it must be a valid URI.

</td>
</tr>
<tr>
<td valign="top">

`end_session_endpoint`

</td>
<td valign="top">

Optional. If present it must be a valid URI.

> ### Remember:  
> If the `end_session_endpoint` isn't supported by the OpenID Connect corporate identity provider, the corporate identity provider can't participate in single logout flows.



</td>
</tr>
<tr>
<td valign="top">

`grant_types_supported`

</td>
<td valign="top">

Optional.

> ### Remember:  
> If `grant_types_supported` is provided in the metadata, it must contain `authorization_code`, which means that the OpenID Connect provider must support the authorization code flow.



</td>
</tr>
</table>

<a name="task_rkw_frm_qgb"/>

<!-- task\_rkw\_frm\_qgb -->

## 2. Configure the Identity Authentication Side

Configure the corporate identity provider in the administration console for SAP Cloud Identity Services.



<a name="task_rkw_frm_qgb__prereq_z15_55m_qgb"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have registered Identity Authentication as an application at the corporate identity provider.




<a name="task_rkw_frm_qgb__steps_cb5_55m_qgb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

4.  Under *Provider Configuration* enter the following information for the corporate identity provider:


    <table>
    <tr>
    <th valign="top">

    Provider Configuration
    
    </th>
    <th valign="top">

    Notes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Discovery URL
    
    </td>
    <td valign="top">
    
    Required. Issuer or metadata URL of the corporate identity provider.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Name
    
    </td>
    <td valign="top">
    
    Required. Unique URI-based *Name* of the corporate identity provider. The issuer is used by default.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Metadata Refresh Interval
    
    </td>
    <td valign="top">
    
    Refreshes the OpenID Connect metadata of the corporate identity provider automatically if it's older than the selected interval and there are logons which forward the request to the corporate identity provider.

    Optional. Choose from:

    -   24 hours \(default choice\)
    -   12 hours


    
    </td>
    </tr>
    </table>
    
5.  Under *Client Authentication* enter the following information for the corporate identity provider:


    <table>
    <tr>
    <td valign="top">
    
    Client Authentication Method
    
    </td>
    <td valign="top">
    
    Optional. Choose from:

    -   Client secret in body \(default choice\)
    -   Client secret in authorization header
    -   Private key JWT
    -   Client assertion in body

    > ### Tip:  
    > If possible, choose `Private key JWT` or `Client assertion in body`.

    > ### Recommendation:  
    > If you connect Microsoft EntraID, use `Client assertion in body` and configure the trust in EntraID. This configuration enables an automatic trust update, because EntraID fetches the keys for signature validation automatically.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Client ID
    
    </td>
    <td valign="top">
    
    Required. The Client ID of the application on the corporate identity provider side.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Client Secret
    
    </td>
    <td valign="top">
    
    The Client Secret of the application on the corporate identity provider side.

    > ### Note:  
    > Required when *Client Authentication Method* is `Client secret in body` or `Client secret in authorization header`. The Client Secret of the application on the corporate identity provider side.


    
    </td>
    </tr>
    </table>
    
6.  **Optional:** If needed for your scenario, choose from the *Advanced Settings*.

    For more information, see:

    -   [Configure PKCE for Corporate Identity Providers](configure-pkce-for-corporate-identity-providers-f85344d.md)

    -   [Enforce Nonces for Corporate Identity Providers](enforce-nonces-for-corporate-identity-providers-04a1a0b.md)

    -   [Disable ID Token Hints for Corporate Identity Providers](disable-id-token-hints-for-corporate-identity-providers-01171f7.md)


7.  **Optional:** Populate the OpenID Connect issuer and endpoints under the *Endpoints* section.

    The *Endpoints* section is read-only.

8.  **Optional:** Add additional scopes if needed.

    You can have up to 20 scopes. The `openid` scope is added by default. Each scope can have a length of up to 99 characters.

    > ### Tip:  
    > If you're using Microsoft Entra ID as corporate identity provider, the recommended claims are:
    > 
    > -   openid
    > -   email
    > -   profile

9.  **Optional:** Choose the *Validate* button to check the configuration.

    An authorization code flow is run against the corporate identity provider. The configuration is validated in a new tab where additional information about the authorization code, the token with all the claims and scopes, and the token verification is provided.

    > ### Tip:  
    > When SAP Cloud Identity Services works with an OIDC corporate identity provider, we expect a response time within 10 seconds. The response time can be a problem for on-premise identity providers, which don't have defined service level agreements like cloud-based identity providers. To use this configuration, you must ensure that the corporate identity provider can respond within this timeframe. When the corporate identity provider doesn't respond quickly enough, SAP Cloud Identity Services presents the following error message:
    > 
    > ***OpenID provider cannot process the request because the configuration is incorrect. Please contact your system administrator.***

10. Save your configuration.

    Once the identity provider has been updated, the system displays the message ***Identity provider <name of identity provider\> updated***.




<a name="task_rkw_frm_qgb__postreq_eb5_55m_qgb"/>

## Next Steps

-   Select the configured identity provider as the authenticating identity provider for the application. For more information, see [Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md).

-   [\(Optional\) Configure the Subject Name Identifier Sent to the OpenID Connect Corporate IdP](optional-configure-the-subject-name-identifier-sent-to-the-openid-connect-corporate-idp-71a5295.md) 

**Related Information**  


[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

[Logging OpenID Connect Tokens](../Monitoring-and-Reporting/logging-openid-connect-tokens-b6c42b5.md "Tenant administrator can view the JWT payload of the OpenID Connect tokens issued or received by Identity Authentication.")

[Microsoft identity platform application authentication certificate credentials](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-certificate-credentials)

