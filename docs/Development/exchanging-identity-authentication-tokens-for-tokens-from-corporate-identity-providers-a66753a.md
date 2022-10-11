<!-- loioa66753aa32314f089c8d4dc4aa59b65d -->

# Exchanging Identity Authentication Tokens for Tokens from Corporate Identity Providers

The service endpoint returns the tokens issued by the corporate identity provider received during the OpenID Connect \(OIDC\) authentication process. Use this endpoint when you integrate with external applications that don't accept tokens from Identity Authentication and require instead tokens issued from the corporate identity provider.



<a name="loioa66753aa32314f089c8d4dc4aa59b65d__section_m3q_bhz_rfb"/>

## Prerequisites

-   For your business application, there’s an OIDC application in Identity Authentication.

    For more information, see [Create OpenID Connect Application](../Operation-Guide/create-openid-connect-application-62fb1c3.md).

-   For your OIDC application in Identity Authentication, you've prepared an authentication credential for the API call. The API supports the following authentication schemes:

    -   Basic

    -   X.509

    -   JWT Bearer


    For more information, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).

-   Your business application has a corporate identity provider as the default identity provider using OIDC.

    For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](../Operation-Guide/configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md) and [Choose Default Identity Provider for an Application](../Operation-Guide/choose-default-identity-provider-for-an-application-e9d8274.md).

-   The user, who needs a token exchange, has authenticated to this application using Identity Authentication and the corporate OIDC identity provider.




<a name="loioa66753aa32314f089c8d4dc4aa59b65d__section_unk_zjw_wsb"/>

## **Call Corporate Identity Provider Endpoint**

**URI:**<code>https://<i class="varname">&lt;tenant ID&gt;</i>.accounts.ondemand.com/oauth2/exchange/corporateidp</code>

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

Description



</th>
<th valign="top">

Parameter Type



</th>
</tr>
<tr>
<td valign="top">

`assertion`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

string



</td>
<td valign="top">

Provide the Identity Authentication user token that identifies Identity Authentication session.



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`response_type`



</td>
<td valign="top">

No



</td>
<td valign="top">

string



</td>
<td valign="top">

Specifies the token requested from the corporate identity provider. By default, only the `access_token` is requested. Otherwise, you can request the ID token or both.

Possible values:

-   `token`

-   `id_token`

-   `token` `id_token`


Separate multiple values with a space \( \).



</td>
<td valign="top">

Request body



</td>
</tr>
</table>



### Request Example

```
POST /oauth2/exchange/corporateidp
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer eyJbiOi…
 
response_type=token id_token&
assertion=eyJ0eab…
```



## **Result**

```
	
Content-Type: application/json
 
{
    "access_token": "YTU1OGU0NzdjYzRkNjA4YzI3ODk4MWEzM2UyYmFlYTI
w",
    "id_token": "eyJraWQiOiJUdDV0Wkt5RHlxSzV4em93VUhrdkNBS3c3bkE
iLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiJUMTIzNDU2Iiwic3ViIjoibWFuYWdlci
IsIm1haWwiOiJkb25hLm1vb3JlQGV4YW1wbGUuY29tIiwiaXNzIjoiZG9tYS1tYW
4ubWFuLXVuaS51cy5ldS1wdC0xLmNsb3VkLmNvbSIsImxhc3RfbmFtZSI6Ik1vb3
JlIiwiZXhwIjoxNTQ4NjgzNzE4LCJpYXQiOjE1NDg2ODM0MTgsImZpcnN0X25hbW
UiOiJEb25hIiwianRpIjoiZmIxMjM0YTUtMTIzYS0xYmQzLWExYWItMGExMjNiYz
Q1ZDZlIn0.3ormYv_nxnimm6xB972qSGOk_YTc_gpE4wVhgaA7q0I",
    "token_type": "Bearer",
    "expires_in": 3569
}
```

 

**Related Information**  


[OpenID Connect](../Operation-Guide/openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

