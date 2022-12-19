<!-- loio8ff83a12bbb8491c9558d635d6bbb287 -->

# Configure Trust with OpenID Connect Corporate Identity Provider

This document is intended to help you configure trust with an OpenID Connect corporate identity provider. In this scenario Identity Authentication acts as a proxy to delegate the authentication to the OpenID Connect corporate identity provider.



## Context

> ### Note:  
> Currently only Microsoft Azure is supported as OpenID Connect corporate identity provider.

Identity Authentication can use an OpenID Connect identity provider as an external authenticating authority. Identity Authentication thus acts as a proxy to delegate authentication to the external corporate identity provider. The requests for authentication sent by the relying party will be forwarded to the corporate identity provider.

As an identity provider proxy, Identity Authentication will act as an OpenID identity provider to the relying party, and as relying party to the corporate identity provider. Once a user is authenticated at the corporate identity provider, successive authentication requests from relying parties, which use the same corporate identity provider will not be forwarded to it as long as the session at Identity Authentication is active. Identity Authentication will issue JSON Web Tokens \(JWTs\) based on the user data received during the first authentication.

To use Identity Authentication as a proxy to delegate authentication to an external OpenID Connect corporate identity provider you have to configure trust with that corporate identity provider.

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




<a name="task_jlj_2rm_qgb__context_ryl_55m_qgb"/>

## Context

The information retrieved from `.well-known/openid-configuration` endpoint must contain:


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

Configure the corporate identity provider in the administration console for Identity Authentication.



<a name="task_rkw_frm_qgb__prereq_z15_55m_qgb"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have registered Identity Authentication as an application at the corporate identity provider.




<a name="task_rkw_frm_qgb__steps_cb5_55m_qgb"/>

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

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

4.  Under *OpenID Connect Configuration* enter the following information for the corporate identity provider:


    <table>
    <tr>
    <th valign="top">

    Configuration


    
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

    Issuer


    
    </td>
    <td valign="top">

    Optional. Issuer URL of the corporate identity provider. Must be `https` and equal to the Issuer in the corporate identity provider OpenID Connect metadata.


    
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

    Client Secret


    
    </td>
    <td valign="top">

    The Client Secret of the application on the corporate identity provider side.

    > ### Note:  
    > Required when *Client Authentication Method* is ***Client secret in body*** or ***Client secret in authorization header***. The Client Secret of the application on the corporate identity provider side.


    
    </td>
    </tr>
    </table>
    
5.  Add additional scopes if needed.

    You can have up to 20 scopes. The `openid` scope is added by default. Each scope can have a length of up to 99 characters.

6.  Choose the *Validate* button to check the configuration.

    A client credentials token request is sent to the corporate identity provider to receive a token to validate the client credentials.

7.  Save your configuration.

    Once the identity provider has been updated, the system displays the message ***Identity provider <name of identity provider\> updated***.

8.  Refresh the OpenID Connect metadata of the corporate identity provider.

    The metadata is refreshed automatically if it is older than 24 hours and there are logons which forward the request to the corporate identity provider.

    By choosing the *Refresh Metadata* button you manually refresh the OpenID Connect metadata of the coroprate identity provider. Do this if there is a need for that.




<a name="task_rkw_frm_qgb__postreq_eb5_55m_qgb"/>

## Next Steps

-   Select the configured identity provider as the authenticating identity provider for the application. For more information, see [Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md).

-   [\(Optional\) Configure the Subject Name Identifier Sent to the OpenID Connect Corporate IdP](optional-configure-the-subject-name-identifier-sent-to-the-openid-connect-corporate-idp-71a5295.md) 

**Related Information**  


[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for Identity Authentication. By editing the administrator authorizations you can also delete an administrator.")

[Microsoft identity platform application authentication certificate credentials](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-certificate-credentials)

