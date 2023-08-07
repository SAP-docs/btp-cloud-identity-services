<!-- loio94ff0b4b0baa45a893c7cd24254b72b7 -->

# Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow

The authorize endpoint is used for authentication and returns authorization code when using the authorization code flow. It's recommended for confidential clients, that can keep the client secret.



This document explains how to call the authorize endpoint and what are the authorize request parameters supported by Identity Authentication for the authorization code flow.

> ### Note:  
> Confidential clients are applications that can keep the client secret. These clients are the so-called web applications.



## **Request**

**URI:**`https://<tenant ID>.accounts.ondemand.com/oauth2/authorize`

``

**HTTP Method:***GET*



### Request Headers


<table>
<tr>
<th valign="top">

Header



</th>
<th valign="top">

Required



</th>
<th valign="top">

Values



</th>
</tr>
<tr>
<td valign="top">

`Content-Type`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

application/x-www-form-urlencoded



</td>
</tr>
<tr>
<td valign="top">

`Authentication`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

-   Basic Authentication -

    Client ID and a Secret to authenticate the client \(relying party\). For more information, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

    > ### Note:  
    > The client ID and secret must be encoded using the "application/x-www-form-urlencoded" encoding algorithm.

-   X.509 Certificate
-   JWT \(client\_assertion\)



</td>
</tr>
</table>



### Request Parameters


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Required



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Additional Information



</th>
<th valign="top">

Parameter Type



</th>
</tr>
<tr>
<td valign="top">

`redirect_uri`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

[Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md).



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`response_type`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

The supported value is `code`



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`scope`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

The supported values are:

-   `openid`
-   `email`
-   `profile`
-   `groups`
-   `offline_access`

    > ### Note:  
    > The new tokens are independently created from the Identity Authentication Web session. This means that even if a user logs out from Identity Authentication the `refresh_token` will exist in the database until it expires, and can be used to perform the refresh token flow if the user is not present in Identity Authentication with a Web session.


Values must be space-delimited parameter, for example: `scope=openid email`.



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`client_id`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

The user ID configured for basic authentication for the application. For more information, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`state`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

Free text.



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`nonce`



</td>
<td valign="top">

No



</td>
<td valign="top">

string



</td>
<td valign="top">

Free text.



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`login_hint`



</td>
<td valign="top">

No



</td>
<td valign="top">

string



</td>
<td valign="top">

The `login_hint` parameter helps the user when he or she is known to the service provider \(SP\). Thus it prevents the user from re-typing the user identifier on the logon or conditional screen.

Supported values are the allowed logon identifiers for the users. The options are *User ID*, *Login Name*, and *Email* \(For SAML 2.0\). For more information, see [Configure Allowed Logon Identifiers](configure-allowed-logon-identifiers-3adf1ff.md) .



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`logout_uri`



</td>
<td valign="top">

No



</td>
<td valign="top">

string



</td>
<td valign="top">

-   [Configure OpenID Connect Application for Authorization Code Flow](configure-openid-connect-application-for-authorization-code-flow-4a94254.md)
-   [Front-Channel Logout URI Rules](front-channel-logout-uri-rules-789c752.md)



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`prompt`



</td>
<td valign="top">

No



</td>
<td valign="top">

string



</td>
<td valign="top">

This parameter enables the client to determine if the user is still present in the current session.

Supported values are:

-   *login*

    Force reauthentication of the user.

-   *none*

    Without user interaction, check if there is an exisiting user session. If there is a session, continue as normal. If there is no session or if the user is forced to authenticate for other reasons, return the error code ***login\_required***.




</td>
<td valign="top">

Path



</td>
</tr>
</table>



### Request Example

```
https://my-tenant.ondemand.com/oauth2/authorize?response_type=code&scope=openid+email&client_id=94ff0b4b0baa45a893c7cd24254b72b7&state=state&nonce=m-0G6_FaS3Kg&redirect_uri=https://example.com&login_hint=dona.moore@example.com
```



## **Response**



### Response Headers


<table>
<tr>
<th valign="top">

Header



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`code`



</td>
<td valign="top">

The `code` is generated by Identity Authentication and is returned in the URL as a parameter. It must be used when calling the token endpoint.

> ### Note:  
> The parameter can be used within two minutes after it is generated and returned in the URL. It can be used only once.



</td>
</tr>
</table>



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code



</th>
<th valign="top">

Reason



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

302 Found



</td>
<td valign="top">

Successful operation.



</td>
<td valign="top">

Additionally provides a URL in the header field Location.

> ### Note:  
> The URL contains `code` necessary for the token endpoint.



</td>
</tr>
<tr>
<td valign="top">

400 Bad Request



</td>
<td valign="top">

Missing or wrong parameter



</td>
<td valign="top">

 



</td>
</tr>
</table>



### Response Example

```
Location:
 https://www.example.com/?code=4454554df477w01s34540672dc462e6f0&state=state
```



**Related Information**  


[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

