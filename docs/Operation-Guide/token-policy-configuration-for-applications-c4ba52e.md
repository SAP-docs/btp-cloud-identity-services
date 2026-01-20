<!-- loioc4ba52e748554863917b046bf1b7b355 -->

# Token Policy Configuration for Applications

Set the token policy for a specific OpenID Connect application. Configure the validity of the refresh token, access and id\_token, and the maximum sessions per user.



## Context



### Token Policy

The following table lists the token policy options for OIDC applications.

**Token Policy Configuration Parameters**


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

*Refresh Token* 

</td>
<td valign="top">

Sets the refresh token lifetime issued by Identity Authentication. The value can range from 1 to 4320 hours, in other words, from 1 hour to 180 days.

The default value is 12 hours.

> ### Note:  
> -   If the validity of refresh tokens is less than the validity of access/ID tokens, access/ID tokens can't be refreshed after the access/ID tokens expire.
> 
> -   When using the authorization code flow, if you set the token policy for refresh tokens longer than the session timeout, add the *offline\_access* scope to your authorization code request. Without this scope, the service deletes the refresh token from the database when the resource owner ends the session \(logs out\). Without the refresh token, the OAuth client can't request new tokens anymore.
> 
>     For more information, see:
> 
>     -   [Configure Session Timeout](configure-session-timeout-5ca23e4.md)
> 
>     -   [Using Authorization Code Flow](using-authorization-code-flow-c135fc4.md)



</td>
</tr>
<tr>
<td valign="top">

*Access / ID Token* 

</td>
<td valign="top">

Sets the access and id\_token lifetime issued by Identity Authentication. The value can range from 1 to 720 minutes, in other words, from 1 minute to 12 hours.

The default value is 60 minutes.

</td>
</tr>
<tr>
<td valign="top">

*Max sessions per user* 

</td>
<td valign="top">

Determines the maximum number of tokens that the service issues for the same session in parallel. Imagine you’re logged on to the application through a web interface and a command-line interface in parallel. Then you'd set this parameter to 2. The value can range from 1 to 10.

The default value is 1.

</td>
</tr>
</table>

> ### Remember:  
> The default configurations for the token policy per application are equal to the tenant token policy. If you configure new values for an application, the service ignores the tenant token policy for that application. For more information about the tenant token policy, see [Tenant OpenID Connect \(OIDC\) Configurations](tenant-openid-connect-oidc-configurations-3d6abcc.md)

**Offline Access**

Disable this option to stop users from using this application beyond the regular session validity. You can configure this only for source applications. It is turned off by default. This control isn't visible for single-tenant applications and is enabled by default. Use this option to enable users to access a mobile or native application, such as a command-line interface, without having to authenticate each time.

**Enforce Reauthentication**

Use this option to limit how long the application can refresh user tokens without reauthenticating. This function helps you meet compliance requirements that restrict tokens from being valid beyond a specific period. By default this option is enabled and set to 3 months. When enabled, the maximum possible value is 2,147,483,647 seconds.



### Advanced Settings

**Refresh Token Usage After Renewal** 

When refresh token flows fail, you can enable the server to accept a refresh token that was already submitted. Normally, a refresh token can only be used once. The configuration aims to solve issues, for example network problems in refresh token calls, and allow an application to retry this call. Define the behavior of clients depending on your scenario and the risk. If you extend the rotation life time, we recommend revoking existing tokens with a separate call.

**Refresh Token Usage After Renewal**


<table>
<tr>
<th valign="top">

Settings

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Off \(Default\)

</td>
<td valign="top">

The new refresh token immediately invalidates the old one.

</td>
</tr>
<tr>
<td valign="top">

Online scenarios

</td>
<td valign="top">

The new refresh token is created and the old one is still active for 5 minutes.

</td>
</tr>
<tr>
<td valign="top">

Mobile scenarios

</td>
<td valign="top">

The new and old refresh token are valid during the configured refresh token life time.

</td>
</tr>
</table>

> ### Note:  
> For online and mobile scenarios, calls to refresh the old refresh token end in the new token. Calls with the new refresh token, invalidates the old refresh token.

**Access Token Format** 


<table>
<tr>
<th valign="top">

Settings

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Grant-Type Dependent \(Default\)

</td>
<td valign="top">

The format of the token depends on the grant type. It is as folows:

-   Authorization Code Flow - `JWT`
-   Client Credentials Flow - `JWT`
-   Resource Owner Password Credentials Flow - `opaque`
-   Token Exchange - `opaque`
-   JWT Bearer Flow - `opaque`
-   Refresh Token Endpoint - `opaque`



</td>
</tr>
<tr>
<td valign="top">

JSON Web Token

</td>
<td valign="top">

All tokens are generated in the JWT format.

</td>
</tr>
<tr>
<td valign="top">

Opaque

</td>
<td valign="top">

All tokens are generated in the opaque format.

</td>
</tr>
</table>

To configure the token policy, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *OpenID Connect Configuration*.

6.  Manually configure the token policy for the application. Use the slider or provide a number in the input field above the slider.

    If needed, use the reset button to set to the default value.

7.  **Optional:** Choose values for the *Advanced Settings* configuration from the drop-downs.

8.  Save your changes.


**Related Information**  


[Redirect URIs, Post Logout Redirect URI Rules](redirect-uris-post-logout-redirect-uri-rules-48fdb9a.md "Rules for the redirect URIs or post logout redirect URIs.")

[Logout URI Rules](logout-uri-rules-789c752.md "Rules for the front and back-channel URIs.")

[Configure Grant Types](configure-grant-types-c342a7b.md "Configure the allowed grant type for your OpenID Connect application.")

[Tenant OpenID Connect \(OIDC\) Configurations](tenant-openid-connect-oidc-configurations-3d6abcc.md "You as a tenant administrator can view and configure the tenant OpenID Connect (OIDC) configurations.")

