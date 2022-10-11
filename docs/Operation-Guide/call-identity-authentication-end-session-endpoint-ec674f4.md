<!-- loioec674f477fec47928e55888a97ca01da -->

# Call Identity Authentication End Session Endpoint

This document explains how to call the end session endpoint and what are the parameters supported by Identity Authentication.





## **Call End Session Endpoint**

**URI:**`https://<tenant ID>.accounts.ondemand.com/oauth2/logout`

**HTTP Method:***GET*



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

`id_token_hint`



</td>
<td valign="top">

No

> ### Remember:  
> The parameter is optional, but either `id_token_hint` or `client_id` must be present.



</td>
<td valign="top">

String



</td>
<td valign="top">

Previously issued `id_token`.



</td>
<td valign="top">

Query



</td>
</tr>
<tr>
<td valign="top">

`post_logout_redirect_uri`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The redirection URIs where the user will be forwarded after logout.



</td>
<td valign="top">

Query



</td>
</tr>
<tr>
<td valign="top">

`state`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

Used by the application to maintain state between the logout request and the callback to the endpoint specified by the `post_logout_redirect_uri` query parameter. If included in the logout request, the identity provider passes this value back to the application using the state query parameter when redirecting the browser back to the application.



</td>
<td valign="top">

Query



</td>
</tr>
<tr>
<td valign="top">

`client_id`



</td>
<td valign="top">

No

> ### Remember:  
> The parameter is optional, but either `id_token_hint` or `client_id` must be present.



</td>
<td valign="top">

String



</td>
<td valign="top">

Used to identify the corresponding Identity Authentication application.



</td>
<td valign="top">

Query



</td>
</tr>
</table>

> ### Note:  
> All request parameters can be combined in any order. Either the `id_token_hint` or `client_id` parameter must be present.



### Request Examples

```
https://my-tenant.ondemand.com/oauth2/logout
```

```
https://my-tenant.ondemand.com/oauth2/logout?id_token_hint=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJUMTIzNDU2Iiwic3ViIjoiUDEyMzQ1NiIsIm1
							haWwiOiJkb25hLm1vb3JlQGV4YW1wbGUuY29tIiwiaXNzIjoiaHR0cHM6Ly9teS10ZW5hbnQuYWNjb3VudHMu
							b25kZW1hbmQuY29tIiwibGFzdF9uYW1lIjoiTW9vcmUiLCJleHAiOjE1MzkwNzQyMDYsImlhdCI6MTUzOTAyO
							TU0NCwiZmlyc3RfbmFtZSI6IkRvbmEiLCJqdGkiOiJjODM1NjZlZi0yZDc4LTQyZTgtOTk1M2M1NGZiZDkyIn
							0.n2KkMD9MUPekF_chd65wMdAu1Dv-m4yPE6i6ZeMOtAg
```

```
https://my-tenant.ondemand.com/oauth2/logout?post_logout_redirect_uri=https://example.com
```

```
https://my-tenant.ondemand.com/oauth2/logout?state=state
```



## **Result**



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

User session is terminated.

If `post_logout_redirect_uri` is not provided, then the user will be redirected to the profile page.



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

 



</td>
</tr>
</table>

 

**Related Information**  


[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

[Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md "This document is intended to help you configure an OpenID Connect application in the administration console for Identity Authentication.")

[Configure Trusted Domains](configure-trusted-domains-08fa1fe.md "Service providers that delegate authentication to Identity Authentication can protect their applications when using embedded frames, also called overlays, or when allowing user self-registration.")

[RP-Initiated Logout](https://openid.net/specs/openid-connect-session-1_0.html#RPLogout)

