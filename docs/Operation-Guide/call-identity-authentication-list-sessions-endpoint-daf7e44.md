<!-- loiodaf7e449865641f99b57b21b1653b821 -->

# Call Identity Authentication List Sessions Endpoint

The service endpoint returns the list of sessions associated with the OpenID Connect \(OIDC\) token submitted with the request. Use this endpoint to enable your application to see how many tokens are still active after the application has performed a token exchange.



> ### Note:  
> The result is similar to when the authenticated user looks at their sessions and tokens in their user profile. For an example, view the self-service application.
> 
> 1.  Navigate to <code>https://<i class="varname">&lt;my_tenant&gt;</i>.sap.com/ui/protected/profilemanagement</code>.
> 
> 2.  Under *Sessions and Tokens*, choose *Show*.



<a name="loiodaf7e449865641f99b57b21b1653b821__section_m3q_bhz_rfb"/>

## Prerequisites

-   For your business application, there’s an OIDC application in Identity Authentication.

    For more information, see [Create OpenID Connect \(OIDC\) Application](create-openid-connect-oidc-application-62fb1c3.md).

-   For your OIDC application in Identity Authentication, you've prepared an authentication credential for the API call. The API supports the following authentication schemes:

    -   Basic

    -   X.509

    -   JWT Bearer


    For more information, see [API Authentication](api-authentication-9d200d5.md).

-   Your application has an access, ID, or refresh token.




<a name="loiodaf7e449865641f99b57b21b1653b821__section_unk_zjw_wsb"/>

## **Call Session List Endpoint**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/token/list</code>

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

`token`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

Provide the Identity Authentication token. The endpoint supports ID tokens, access tokens, and refresh tokens.

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

No

</td>
<td valign="top">

string

</td>
<td valign="top">

Used to identify the corresponding Identity Authentication application.

> ### Note:  
> The `client_id` parameter is mandatory if the request is provided without authentication.



</td>
<td valign="top">

Request body

</td>
</tr>
</table>



### Request Example

```
POST /oauth2/token/list
Content-Type: application/x-www-form-urlencoded
Authorization: Basic eyJbiOi…
 
token=eyJ0eab…
```



## **Result**

The result is an array of sessions for the user associated with token your application submitted.

```
	
Content-Type: application/json
 
[
    {
        "sub": "dona.moore@example.com",
        "iss": "https://my_tenant.accounts.ondemand.com",
        "client_id": "a1b23cd4-f2d5-45d8-9937-3a4bebd6598c",
        "uid": "dona.moore@example.com",
        "sp_name": "XSUAA_1a2b3c45-ae93-4450-ba12-4becb1c345ab",
        "client_agent": "PostmanRuntime/7.29.2",
        "grant_type": "AUTHORIZATION_CODE",
        "scope": "openid",
        "client_ip": "10.10.10.201",
        "exp": 1669151188,
        "iat": 1669107988,
        "value": "eyJraW…_3421YaZjwFNVoZucjs-PU32SZ7Yd33BihtGczV8bkig",
        "jti": "ab123c45-e3d5-441c-ba07-b404e3d36465",
        "client_auth_method": "client_secret_basic"
    }
]
```

**Related Information**  


[Configuring OpenID Connect \(OIDC\)](configuring-openid-connect-oidc-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect (OIDC) protected applications.")

