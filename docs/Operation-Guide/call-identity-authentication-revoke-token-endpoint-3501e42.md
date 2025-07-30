<!-- loio3501e42ce4ee4e1bb53d6830dcd3854f -->

# Call Identity Authentication Revoke Token Endpoint

The revoke token endpoint invalidates any access and refresh tokens issued to the client for the same end-user and session.



To revoke tokens from other sessions belonging to the same end-user, find the other session and revoke tokens for those sessions separately. For more information about finding user sessions, see [Call Identity Authentication List Sessions Endpoint](call-identity-authentication-list-sessions-endpoint-daf7e44.md).

The token revocation endpoint is implemented according to [RFC 7009 OAuth 2.0 Token Revocation](https://www.rfc-editor.org/rfc/rfc7009.html).



## **Request**

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/oauth2/revoke</code>

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
-   Bearer *<client\_credential\_token\>*\)



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

Must contain the JWT or opaque token from the issuer.

</td>
<td valign="top">

Path

</td>
</tr>
<tr>
<td valign="top">

`token_type_hint`

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

 

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
token=0ab12345978c51ffe7c4e9a2b1158bb4
```



## **Response**

Token is successfully revoked.



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code

</th>
<th valign="top">

Reason

</th>
</tr>
<tr>
<td valign="top">

200 OK

</td>
<td valign="top">

Successful operation.

</td>
</tr>
<tr>
<td valign="top">

401 Unauthorized

</td>
<td valign="top">

The client is not authenticated.

</td>
</tr>
</table>



