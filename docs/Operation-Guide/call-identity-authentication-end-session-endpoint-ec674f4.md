<!-- loioec674f477fec47928e55888a97ca01da -->

# Call Identity Authentication End Session Endpoint

To propagate a user's logout to other applications and any corporate identity providers used, an OIDC application can call the end session endpoint of Identity Authentication.



After the entire single logout \(SLO\) operation has completed, by default, Identity Authentication redirects the user agent to the Identity Authentication profile page of the user. To redirect the user after logout to a different page of the application that triggered the logout, include a post logout URI in your request. The URI must be among the allowed post logout redirect URIs configured for the application.

For more information, see [OpenID Connect \(OIDC\) Application Configurations](openid-connect-oidc-application-configurations-1ae324e.md).

If you include a post logout redirect URI in your request, include the client ID. Instead of including the client ID, you can include the ID token and the service reads the client ID from the token.



## **Call End Session Endpoint**

**URI:**`https://<Cloud Identity Services domain>/oauth2/logout`

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

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
> The parameter is optional, but either `id_token` or `client_id` must be present.



</td>
<td valign="top">

string

</td>
<td valign="top">

Previously issued `id_token`.

> ### Note:  
> The token must be from the current session.



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

string

</td>
<td valign="top">

The redirection URI where the user will be forwarded after logout.

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

string

</td>
<td valign="top">

Used by the application to maintain state between the logout request and the callback to the endpoint specified by the `post_logout_redirect_uri` query parameter. If included in the logout request, the identity provider passes this value back to the application using the `state` query parameter when redirecting the browser back to the application.

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
> The parameter is optional, but either `id_token` or `client_id` must be present.



</td>
<td valign="top">

string

</td>
<td valign="top">

Used to identify the corresponding Identity Authentication application.

</td>
<td valign="top">

Query

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

Required for multitenant scenarios to identify corresponding Identity Authentication application.

</td>
<td valign="top">

Query

</td>
</tr>
</table>

> ### Note:  
> All request parameters can be combined in any order.



### Request Examples

```
https://my-tenant.ondemand.com/oauth2/logout?id_token_hint=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJUMTIzNDU2Iiwic3ViIjoiUDEyMzQ1NiIsIm1
							haWwiOiJkb25hLm1vb3JlQGV4YW1wbGUuY29tIiwiaXNzIjoiaHR0cHM6Ly9teS10ZW5hbnQuYWNjb3VudHMu
							b25kZW1hbmQuY29tIiwibGFzdF9uYW1lIjoiTW9vcmUiLCJleHAiOjE1MzkwNzQyMDYsImlhdCI6MTUzOTAyO
							TU0NCwiZmlyc3RfbmFtZSI6IkRvbmEiLCJqdGkiOiJjODM1NjZlZi0yZDc4LTQyZTgtOTk1M2M1NGZiZDkyIn
							0.n2KkMD9MUPekF_chd65wMdAu1Dv-m4yPE6i6ZeMOtAg
```

```
https://my-tenant.ondemand.com/oauth2/logout?post_logout_redirect_uri=https%3A%2F%2Fexample.com&client_id=a0b22cd0-f2d5-45d8-9937-3a4bebd6598c

```

```
https://my-tenant.ondemand.com/oauth2/logout?state=state&client_id=a0b22cd0-f2d5-45d8-9937-3a4bebd6598c
```



## **Result**



### Response Status and Error Codes

Identity Authentication terminates all user sessions and finally redirects the user to the post logout page.



**Related Information**  


[Configuring OpenID Connect \(OIDC\)](configuring-openid-connect-oidc-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect (OIDC) protected applications.")

[Configure OpenID Connect \(OIDC\) Application](configure-openid-connect-oidc-application-8a0aa2e.md "This document is intended to help you configure an OpenID Connect (OIDC) application in the administration console for SAP Cloud Identity Services.")

[RP-Initiated Logout \(Specification from OpenID Foundation\)](https://openid.net/specs/openid-connect-rpinitiated-1_0.html "Specification from OpenID Foundation")

[Single Logout Flows](../Development/single-logout-flows-0584b5f.md "It's good practice to encourage users of your applications to log out at the end of their session. If malicious users can access user sessions, either by gaining access to artifacts such as cookies or by finding unattended clients, malicious users can impersonate the rightful owners of the sessions.")

