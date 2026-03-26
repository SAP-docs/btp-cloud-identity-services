<!-- loio7bf3c18b29e643eab15fc5445d1338c5 -->

# Claims of SAP Cloud Identity Services OAuth Tokens

Understanding OAuth token claims helps you to achieve secure and efficient authentication and authorization. This knowledge helps you use tokens correctly, reduce security risks, and maintain trust in your system.



## Viewing Claims Supported by SAP Cloud Identity Services

View the claims issued by SAP Cloud Identity Services by calling the discovery endpoint and checking the `claims_supported` property.

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/.well-known/openid-configuration</code>

For more information, see [Call Identity Authentication Discovery Endpoint](call-identity-authentication-discovery-endpoint-c297516.md).



## Supported Claims

The following table describes the claims supported by SAP Cloud Identity Services.

**Claims Supported by SAP Cloud Identity Services**


<table>
<tr>
<th valign="top">

Claim

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`app_tid`

</td>
<td valign="top">

An SAP claim that identifies the tenant of the application. This claim is used in multitenant scenarios, for example, if you subscribed to a BTP application.

</td>
</tr>
<tr>
<td valign="top">

`at_hash`

</td>
<td valign="top">

This claim contains a hash of the access token. Clients can hash the access token that it received and compare it to the `at_hash` value in the ID token to ensure they belong together and prevent token substitution attacks.

</td>
</tr>
<tr>
<td valign="top">

`aud`

</td>
<td valign="top">

Identifies the recipient of the token. It can be a string or array of audience identifiers, such as the client ID of the application requesting access.

</td>
</tr>
<tr>
<td valign="top">

`auth_time`

</td>
<td valign="top">

This claim shows the time when the client authenticated, in seconds since the Unix epoch in UTC. Applications can use this claim to determine how long ago a user authenticated and to enforce reauthentication.

</td>
</tr>
<tr>
<td valign="top">

`azp`

</td>
<td valign="top">

The authorized party identifies the client ID to which the ID token was issued.

</td>
</tr>
<tr>
<td valign="top">

`email`

</td>
<td valign="top">

Email address of the user for whom the token was issued. This claim is included when the ***email*** scope is requested.

</td>
</tr>
<tr>
<td valign="top">

`email_verified`

</td>
<td valign="top">

Indicates whether or not the email has been verified. It's a boolean. This claim is included when the ***email*** scope is requested.

</td>
</tr>
<tr>
<td valign="top">

`exp`

</td>
<td valign="top">

The expiration time after which the token must not be accepted.

</td>
</tr>
<tr>
<td valign="top">

`family_name`

</td>
<td valign="top">

The surname \(last name\) of the user for whom the token was issued. This claim is included when the ***profile*** scope is requested.

</td>
</tr>
<tr>
<td valign="top">

`given_name`

</td>
<td valign="top">

The given name \(first name\) of the user for whom the token was issued. This claim is included when the ***profile*** scope is requested.

</td>
</tr>
<tr>
<td valign="top">

`groups`

</td>
<td valign="top">

The groups the user belongs to. These groups are associated with authorizations. This claim is included when the ***groups*** scope is requested.

</td>
</tr>
<tr>
<td valign="top">

`ias_apis`

</td>
<td valign="top">

An SAP claim that lists the API permission groups or a fixed value for when all APIs of an application are consumed. They're used to make authorization decisions. See also [Consuming APIs from Other Applications](../Development/consuming-apis-from-other-applications-29e204d.md).

</td>
</tr>
<tr>
<td valign="top">

`ias_iss`

</td>
<td valign="top">

An SAP claim that identifies an SAP tenant even if the token was issued from a custom domain in a non SAP domain.

</td>
</tr>
<tr>
<td valign="top">

`iat`

</td>
<td valign="top">

The time when the token was issued in seconds of the Unix epoch. Used to determine the age of the token.

</td>
</tr>
<tr>
<td valign="top">

`iss`

</td>
<td valign="top">

Identifies the issuer of the token. Typically a URL, for example, <code>https://<i class="varname">&lt;tenant&gt;</i>.accounts.ondemand.com</code>.

</td>
</tr>
<tr>
<td valign="top">

`jti`

</td>
<td valign="top">

A unique identifier for the JWT. Used to avoid replay attack. Defined in RFC 7519. This claim is included when the ***profile*** scope is requested.

</td>
</tr>
<tr>
<td valign="top">

`middle_name`

</td>
<td valign="top">

Middle name of the user for whom the token was issued.

</td>
</tr>
<tr>
<td valign="top">

`name`

</td>
<td valign="top">

Full display name of the user for whom the token was issued.

</td>
</tr>
<tr>
<td valign="top">

`nonce`

</td>
<td valign="top">

A string associated with the client session to help mitigate against replay attacks. Clients can verify that it matches was the client sent in its authentication request.

</td>
</tr>
<tr>
<td valign="top">

`preferred_username`

</td>
<td valign="top">

A human-readable display name for the user for whom the token was issued. The claim shows what the user recognizes as their username.

</td>
</tr>
<tr>
<td valign="top">

`sap_id_type`

</td>
<td valign="top">

An SAP claim that identifies the type of token. Values:

-   ***app***: The token is a credential for an application.

-   ***user***: The token is a credential for a user.




</td>
</tr>
<tr>
<td valign="top">

`scim_id`

</td>
<td valign="top">

An SAP claim that identifies the user with their SCIM ID in SAP Cloud Identity Services.

</td>
</tr>
<tr>
<td valign="top">

`sid`

</td>
<td valign="top">

The session ID is used to track the session of a user over multiple applications and logout scenarios.

</td>
</tr>
<tr>
<td valign="top">

`sub`

</td>
<td valign="top">

The subject is a unique identifier for the user for whom the token was issued.

</td>
</tr>
</table>

