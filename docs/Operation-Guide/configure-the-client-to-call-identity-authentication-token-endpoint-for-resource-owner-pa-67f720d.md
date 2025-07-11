<!-- loio67f720de8a36466585a1e9074e6f457c -->

# Configure the Client to Call Identity Authentication Token Endpoint for Resource Owner Password Credentials Flow

The token endpoint is used to get the user's access token, id token and refresh token.



<a name="loio67f720de8a36466585a1e9074e6f457c__section_lyw_cqf_n2c"/>

## Prerequisites

-   For your business application, there’s an OIDC application in Identity Authentication.

    For more information, see [Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md).

-   For your OIDC application in Identity Authentication, you've prepared an authentication credential for the API call. The API supports the following authentication schemes:

    -   Basic

        For more information, see `Authorization` in [Request Header](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md#loio94ff0b4b0baa45a893c7cd24254b72b7__request_header_table) table below.

    -   X.509

        For more information, see `Authorization` in [Request Header](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md#loio94ff0b4b0baa45a893c7cd24254b72b7__request_header_table) table below.

    -   JWT \(client\_assertion\)

        -   Trust by issuer: You must include the `client_id` in the request.

        -   Trust by URI: Including `client_id` in the request is optional.


        For more information, see [Request Parameters](configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md#loio94ff0b4b0baa45a893c7cd24254b72b7__request_parameter_table) table below.


    For more information, see [API Authentication](api-authentication-9d200d5.md).




This document explains how to call the token endpoint and what are the parameters supported by Identity Authentication.



## **Request**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/token</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).

**HTTP Method:***POST*



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

`grant_type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The supported value is `password`

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`username`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The user identifier.

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`password`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The user password, and the one-time password \(OTP\) generated by the user's registered device if the application is configured to require two-factor authentication.

> ### Note:  
> If the application requires two-factor authentication, the OTP code must be linked to the password. For example,`password=mypassword123456`.



</td>
<td valign="top">

Request body

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

Used to identify the corresponding Identity Authentication application.

> ### Note:  
> The `client_id` parameter is optional if the request is provided with authentication.



</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`refresh_expiry`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Reduces the expiration of a refresh token. It's useful if your application is called from mobile and web applications, and both have different session requirements. If you set the token lifetime to 0, you won't receive a `refresh_token` in response.

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`max_exchange_period`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

You can set а limit on how long the application can exchange user tokens without re-authenticating after having acquired the initial token. The `max_exchange_period` parameter has a numeric value which can be set at between 1 hour and 4320 hours \(six months\).

> ### Remember:  
> If the `max_exchange_period` value is smaller than the configuration defined in token policy, this value overrides the configuration defined in token policy configuration and propagates it once the token is exchanged or refreshed. If the value is bigger, it is ignored and the configuration defined in token policy is taken into consideration. For more information, see [Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md)



</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`token_format`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

The `token_format` can be set to `opaque` to retrieve an opaque access token or to `jwt` to retrieve a JWT based access token. If not set, the current defaults per grant type are used.

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`app_tid`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Reserved.

</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`scope`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Value must be space deliminated parameter, for example: `scope=openid email`.

The supported values are:

-   `openid`
-   `email`
-   `profile`
-   `groups`



</td>
<td valign="top">

Request body

</td>
</tr>
</table>



### Request Example

```
grant_type=password&username=<user identifier>&password=<user password>[<otpcode>]
```



## **Response**



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code

</th>
<th valign="top">

Result or X-Message Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

200 OK

</td>
<td valign="top">

Successful operation.

</td>
<td valign="top">

Returns `access_token`, `refresh_token`, and `id_token`.

> ### Note:  
> The `refresh_token` is used to obtain a new `id_token` and `access_token` when the current token becomes invalid or expires. For more information, see [Call Identity Authentication Refresh Token](call-identity-authentication-refresh-token-c62c09e.md).
> 
> The `id_token` is in the form of a JWT \(JSON Web Token\) and contains information about the user. The `id_token` is valid for 60 minutes.



</td>
</tr>
<tr>
<td valign="top">

400 Bad Request

</td>
<td valign="top">

Missing or wrong parameter.

</td>
<td valign="top">

Returns an information about the error.

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

401 Unauthorized

</td>
<td valign="top">

Wrong user ID or password parameters passed for the basic authentication. For more information, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

</td>
<td valign="top">

The authentication of the client \(relying party\) failed.

</td>
</tr>
<tr>
<td valign="top">

PASSWORD\_CHANGE\_REQUIRED

</td>
<td valign="top">

When the user must change his or her password before logon.

</td>
</tr>
<tr>
<td valign="top">

INITIAL\_PASSWORD\_EXPIRED

</td>
<td valign="top">

When the initial password of the user has expired. After the validity of the initial password expires, the user can't log on to the application and must contact the administrator.

</td>
</tr>
</table>



### Response Payload Example

```

{
 "access_token": "387qb8bc-7t78-4eb8-8a8c-cfbe31860811",
 "refresh_token": "d12a12abcd198765dd54r456e98321"
 "id_token": 
"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIxMmEzNGI1Yy02ZDc4LTll
MWYtZzM0NS02N2g4OWlqa2wxMjMiLCJzdWIiOiJQMTIzNDU2IiwibWFpbCI6ImRvbmEubW
9vcmVAZXhhbXBsZS5jb20iLCJpc3MiOiJodHRwczovL215LXRlbmFudC5hY2NvdW50cy5v
bmRlbWFuZC5jb20iLCJsYXN0X25hbWUiOiJNb29yZSIsInNhcF91aWQiOiIxMjM0NTZhYmM
3ZGU4LWZnaGktOTEyMy1qNDU2LTc4OTEya2wzNG01NiIsImV4cCI6MTU4ODAxODkyNSwiaW
F0IjoxNTg4MDEzNzYwLCJmaXJzdF9uYW1lIjoiRG9uYSIsImp0aSI6IjM4ZTQyMzMwLWRlN
2EtNDEzMC1hM2ExLWI1ODJiNTI4ZGE5OCJ9.-LSwBN2WSqnnqSkzSbg9iRmtAMR4moU5TpE
40mX0Umwg",
 "token_type": "Bearer",
 "expires_in": 300
}
```

> ### Note:  
> The format of the `issuer` depends on the configuration in the administration console for SAP Cloud Identity Services. For more information, see [Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md).



