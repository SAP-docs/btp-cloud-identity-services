<!-- loio3501e42ce4ee4e1bb53d6830dcd3854f -->

# Call Identity Authentication Revoke Token Endpoint

The revoke token endpoint invalidates any access and refresh tokens issued to the client for the same end-user.



The token revocation endpoint is implemented according to [RFC 7009 OAuth 2.0 Token Revocation](https://www.rfc-editor.org/rfc/rfc7009.html).



## **Request**

**URI:**`https://<tenant ID>.accounts.ondemand.com/oauth2/revoke`

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

-   POST
-   X.509 Certificate
-   Bearer <client\_credential\_token\>\)



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

 

