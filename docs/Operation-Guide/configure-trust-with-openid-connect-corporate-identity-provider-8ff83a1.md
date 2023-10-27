<!-- loio8ff83a12bbb8491c9558d635d6bbb287 -->

# Configure Trust with OpenID Connect Corporate Identity Provider

This document is intended to help you configure trust with an OpenID Connect \(OIDC\) corporate identity provider. In this scenario Identity Authentication acts as a proxy to delegate the authentication to an OIDC-compliant corporate identity provider.



## Context

Identity Authentication can use OIDC-compliant identity providers as external authenticating authorities. The service acts as a proxy to delegate authentication to the external corporate identity provider. The requests for authentication sent by the relying party are forwarded to the corporate identity provider.

As an identity provider proxy, Identity Authentication acts as an OpenID identity provider to the relying party, and as relying party to the corporate identity provider. Once a user is authenticated at the corporate identity provider, successive authentication requests from relying parties, which use the same corporate identity provider aren't forwarded to it as long as the session at Identity Authentication is active. Identity Authentication issues JSON Web Tokens \(JWTs\) based on the user data received during the first authentication.

To use Identity Authentication as a proxy to delegate authentication to an external OpenID Connect corporate identity provider you have to configure trust with that corporate identity provider.

> ### Tip:  
> If you want to change one corporate identity provider with another, for example move from a SAML identity provider to an OpenID Connect one, it's helpful to know the applications that the corporate identity provider uses. To see the applications that have established trust with a specific corporate identity provider, sign in to the administration console and go to *Identity Providers* \> *Corporate Identity Providers* \> *identity provider from the list* \> *Trusting Applications*.

To configure trust with the corporate identity provider, follow the procedures below:

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
    https://<tenant_id>.accounts.ondemand.com/oauth2/callback
    ```


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

`token_endpoint`

</td>
<td valign="top">

Required. Must be a valid URI.

</td>
</tr>
<tr>
<td valign="top">

`authorization_endpoint`

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

`end_session_endpoint`

</td>
<td valign="top">

Optional. If present it must be a valid URI.

> ### Remember:  
> If the `end_session_endpoint` is not supported by the OpenID Connect corporate identity provider, the corporate identity provider can't participate in single logout flows.



</td>
</tr>
<tr>
<td valign="top">

`grant_types_supported`

</td>
<td valign="top">

Optional.

> ### Remember:  
> If `grant_types_supported` is provided in the metadata, it must contain `authorization_code`, which means that the OpenID Connect provider must support the Authorization Code Flow.



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
    
    Refreshes the OpenID Connect metadata of the corporate identity provider automatically if it is older than the selected interval and there are logons which forward the request to the corporate identity provider.

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

        > ### Tip:  
        > If possible, choose *Private key JWT*. This choice allows also automatic credential rotation.



    
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
    <tr>
    <td valign="top">
    
    Enable PKCE \(S256\)
    
    </td>
    <td valign="top">
    
    Optional. Disabled by default. If enabled, Identity Authentication will execute the authorization code flow enhanced with PKCE against the corporate identity provider.

    > ### Note:  
    > The authorization code flow with PKCE is recommended. Only code challenge method S256 is supported.


    
    </td>
    </tr>
    </table>
    
6.  **Optional:** Populate the OpenID Connect issuer and endpoints under the *Endpoints* section.

    The *Endpoints* section is read-only.

7.  **Optional:** Add additional scopes if needed.

    You can have up to 20 scopes. The `openid` scope is added by default. Each scope can have a length of up to 99 characters.

    > ### Tip:  
    > If you are using Azure Active Directory \(Azure AD\) as corporate identity provider, the recommended claims are:
    > 
    > -   openid
    > -   email
    > -   profile

8.  **Optional:** Choose the *Validate* button to check the configuration.

    An authorization code flow will be executed against the corporate identity provider. The configuration is validated in a new tab where additional information about the authorization code, the token with all the claims and scopes, and the token verification is provided.

9.  Save your configuration.

    Once the identity provider has been updated, the system displays the message ***Identity provider <name of identity provider\> updated***.




<a name="task_rkw_frm_qgb__postreq_eb5_55m_qgb"/>

## Next Steps

-   Select the configured identity provider as the authenticating identity provider for the application. For more information, see [Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md).

-   [\(Optional\) Configure the Subject Name Identifier Sent to the OpenID Connect Corporate IdP](optional-configure-the-subject-name-identifier-sent-to-the-openid-connect-corporate-idp-71a5295.md) 

**Related Information**  


[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

[Logging OpenID Connect Tokens](../Monitoring-and-Reporting/logging-openid-connect-tokens-b6c42b5.md "Tenant administrator can view the JWT payload of the OpenID Connect tokens issued or received by Identity Authentication.")

[Microsoft identity platform application authentication certificate credentials](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-certificate-credentials)

