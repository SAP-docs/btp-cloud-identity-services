<!-- loio1ca3dc0ed2f0463380c86355a52c47b9 -->

# Configure the Client to Call Identity Authentication Authorize Endpoint for Implicit Flow

The `authorize` endpoint is used for authentication and returns the `id_token` when using the implicit flow.



<a name="loio1ca3dc0ed2f0463380c86355a52c47b9__section_lyw_cqf_n2c"/>

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




This document explains how to call the `authorize` endpoint and what are the request parameters supported by Identity Authentication for the implicit flow.



## **Request**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/authorize</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).

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

Request

</td>
</tr>
<tr>
<td valign="top">

`nonce`

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

Request

</td>
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

One of the valid URIs configured for the application. You can configure up to five URIs. For more information, see [Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md).

</td>
<td valign="top">

Request

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

The supported value is `id_token`

</td>
<td valign="top">

Request

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

The supported value is `openid`

</td>
<td valign="top">

Request

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

Request

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

-   [Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md)
-   [Logout URI Rules](logout-uri-rules-789c752.md)



</td>
<td valign="top">

Request

</td>
</tr>
<tr>
<td valign="top">

`max_age`

</td>
<td valign="top">

No

</td>
<td valign="top">

integer

</td>
<td valign="top">

Maximum time in seconds since the user was last authenticated. When `max_age` has been reached, the user must re-authenticate.

</td>
<td valign="top">

Request

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

Request

</td>
</tr>
<tr>
<td valign="top">

state

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

Request

</td>
</tr>
</table>



### Request Example

```
https://my-tenant.ondemand.com/oauth2/authorize?response_type=id_token&scope=openid&client_id=T000000&state=state&nonce=m-0G6_FaS3Kg&redirect_uri=https://example.com&login_hint=dona.moore@example.com
```



## **Response**



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

200 OK

</td>
<td valign="top">

Successful operation.

</td>
<td valign="top">

Additionally provides a URL in the header field Location.

> ### Note:  
> The URL contains `id_token`.
> 
> The `id_token` is in the form of a JWT \(JSON Web Token\) and contains information about the user. The `id_token` is valid for 60 minutes.



</td>
</tr>
<tr>
<td valign="top">

400

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
https://www.example.com/#id_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.ey
JhdWQiOiIxMmEzNGI1Yy02ZDc4LTllMWYtZzM0NS02N2g4OWlqa2wxMjMiLCJzdWIiOiJQMTIzNDU2Iiw
ibWFpbCI6ImRvbmEubW9vcmVAZXhhbXBsZS5jb20iLCJpc3MiOiJodHRwczovL215LXRlbmFudC5hY2Nv
dW50cy5vbmRlbWFuZC5jb20iLCJsYXN0X25hbWUiOiJNb29yZSIsInNhcF91aWQiOiIxMjM0NTZhYmM3Z
GU4LWZnaGktOTEyMy1qNDU2LTc4OTEya2wzNG01NiIsImV4cCI6MTU4ODAxODkyNSwiaWF0IjoxNTg4MD
EzNzYwLCJmaXJzdF9uYW1lIjoiRG9uYSIsImp0aSI6IjM4ZTQyMzMwLWRlN2EtNDEzMC1hM2ExLWI1ODJ
iNTI4ZGE5OCJ9.-LSwBN2WSqnnqSkzSbg9iRmtAMR4moU5TpE40mX0Umw&state=state&token_type=Bearer
```



**Related Information**  


[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

