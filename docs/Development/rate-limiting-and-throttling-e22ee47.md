<!-- loioe22ee47abf614565bcb29bb4ddbbf209 -->

# Rate Limiting and Throttling

This section provides information on the rate limiting and SCIM API throttling Identity Authentication.

To ensure safe and stable environment, all requests have a limit of 50 concurrent requests per second. The requests are associated with the originating IP address, and not with the user making the requests.

When the limit is exceeded, the client receives the ***HTTP 429 Too Many Requests*** response status code.



<a name="loioe22ee47abf614565bcb29bb4ddbbf209__section_xql_wfh_qkb"/>

## SCIM API

To prevent Identity Authentication from being overloaded by too many requests, we have introduced SCIM API throttling to regulate the API usage per tenant.

**SCIM API Throttling**


<table>
<tr>
<th valign="top">

Requests per minute

</th>
<th valign="top">

Notes

</th>
</tr>
<tr>
<td valign="top">

up to 200

</td>
<td valign="top">

The requests are executed.

</td>
</tr>
<tr>
<td valign="top">

201 to 280

</td>
<td valign="top">

The requests are delayed by 1 second.

</td>
</tr>
<tr>
<td valign="top">

281 and more

</td>
<td valign="top">

The client receives the ***HTTP 429 Too Many Requests*** response status code for 60 seconds.

</td>
</tr>
</table>



<a name="loioe22ee47abf614565bcb29bb4ddbbf209__section_tnl_kqj_25b"/>

## OpenID Connect \(OIDC\) Endpoints

To ensure safe and stable environment, all requests to the `/oauth2` endpoints have a limit of 1000 requests per minute per tenant. When the limit is exceeded, the client receives the ***HTTP 429 Too Many Requests*** response status code. The requests are associated with the originating IP address, and not with the user making the requests.

For a list of the relevant endpoints, use the following URL:

<code>https://<i class="varname">&lt;tenant ID&gt;</i>.accounts.ondemand.com/.well-known/openid-configuration</code>

*Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).

If you've a custom domain configured, the URL has the following pattern:

<code>https://<i class="varname">&lt;your custom domain&gt;</i>/.well-known/openid-configuration</code>

