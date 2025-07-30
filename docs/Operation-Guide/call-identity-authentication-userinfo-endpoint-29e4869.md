<!-- loio29e48698ae314b3896abd8e14a4d9138 -->

# Call Identity Authentication UserInfo Endpoint

OpenID Connect UserInfo endpoint enables the clients to retrieve information about the authenticated user.



The client makes a request to the UserInfo endpoint using the access token obtained from the OpenID Connect authentication from the user-based flows.





## **Request**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/userinfo</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

**HTTP Method:***GET* or *POST*



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

`Authorization`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Bearer <access\_token\>

</td>
</tr>
</table>



### Request Example

```
GET /oauth2/userinfo 
  Host: https://<tenant ID>.accounts.ondemand.com
  Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9
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

200

</td>
<td valign="top">

Successful operation.

</td>
<td valign="top">

Returns information about the user.

</td>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Bad request

</td>
<td valign="top">

Returns an error with error description. For example, expired token.

</td>
</tr>
<tr>
<td valign="top">

403

</td>
<td valign="top">

Forbidden

</td>
<td valign="top">

Returns an error with error description.

</td>
</tr>
</table>



### Response Example

```

{
 "aud": "a123456e-314a-4923-899c-05c535c3d7f9",
 "sub": "P12345",
 "user_uuid": "158a1b2c7-981az-69ab9-8079-d824da69c681",
 "mail": "dona.moore@example.com",
 "iss": "https://my-_tenant.accounts.ondemand.com",
 "last_name": "Moore",
 "exp": 1588019044,
 "iat": 158801376,
 "first_name": "Dona",
 "jti": "38e42330-de7a-4130-a3a1-b582b528da98"
}

```



