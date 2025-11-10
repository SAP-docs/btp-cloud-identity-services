<!-- loio52b93b08f4654e659a9abf93ca86d902 -->

# Configure the Client to Call Identity Authentication Token Endpoint for Client Credentials Flow

The token endpoint is used to get the user's access token.



This document explains how to call the token endpoint and what are the parameters supported by Identity Authentication - for a relying party client and system as administrator.



<a name="loio52b93b08f4654e659a9abf93ca86d902__section_lyw_cqf_n2c"/>

## Prerequisites

-   For your business application, there’s an OpenID Connect \(OIDC\) application in Identity Authentication.

    For more information, see [Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md).

-   For your OpenID Connect \(OIDC\) application in Identity Authentication, you've prepared an authentication credential for the API call. The API supports the following authentication schemes:

    -   Basic

        For more information, see `Authorization` in the *Request Header* table below.

    -   X.509

        For more information, see `Authorization` in the *Request Header* table below.

    -   JWT \(client\_assertion\)

        -   Trust by issuer: You must include the `client_id` in the request.

        -   Trust by URI: Including `client_id` in the request is optional.


        For more information, see the *Request Parameters* table below.


    For more information, see [API Authentication](api-authentication-9d200d5.md).




## **Request - Relying Party**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/token</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

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

`grant_type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

client\_credentials

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

`token_format`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

The `token_format` can be set to `opaque` to retrieve an opaque access token or to `jwt` to retrieve a JWT-based access token. If not set, the current defaults per grant type are used.

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

Reserved

</td>
<td valign="top">

Request body

</td>
</tr>
</table>



### Request Example

```
grant_type=client_credentials&client_id=12b52d2c-1q34-5r5t-a576-75e85asdf523
```



<a name="loio52b93b08f4654e659a9abf93ca86d902__section_o4t_hxp_w1c"/>

## **Request - System as Administrator**

> ### Note:  
> Use the received `access_token` to authenticate when accessing the [Application Configurations API](https://api.sap.com/api/SCI_Application_Directory/overview) and [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview) with a system as administrator.

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/token</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

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

`grant_type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

client\_credentials

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
</table>



### Request Example

```

Client - Relying Party

Request:

grant_type=client_credentials&client_id=12b52d2c-1q34-5r5t-a576-75e85asdf523
```

```

Client - System as Administrator

Request:

grant_type=client_credentials
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

Returns `access_token`.

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

Returns information about the error.

</td>
</tr>
</table>



### Response Payload Example

```

{
  "access_token":
"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOiIxMnM1NHc2YS0xdzU
2LTVlOGItZjI1Ni0wN3YwNXZmZ2IzMTIiLCJzdWIiOiIxMnM1NHc2YS0xdzU2LTVl
OGItZjI1Ni0wN3YwNXZmZ2IzMTIiLCJpc3MiOiJodHRwczovLzx0ZW5hbnQgSUQ-L
mFjY291bnRzLm9uZGVtYW5kLmNvbSIsImV4cCI6MTU4ODAyNzk3MCwiaWF0IjoxNT
g4MDI0MTEyLCJqdGkiOiIzMDhiYTg5NC0zMGE0LTQ4MDUtYWUzOS1vc2EyYXNkMjU
2ZTIifQ.9IJLkgsKQtYzMRrHUY004X7OJYWI-L8QV1oG42EZ0Kc",
  "token_type": "Bearer",
  "expires_in": 3600
}
}
```

> ### Note:  
> The format of the `issuer` depends on the configuration in the administration console for SAP Cloud Identity Services. For more information, see [Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md).



**Related Information**  


[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

