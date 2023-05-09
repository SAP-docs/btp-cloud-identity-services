<!-- loio9379444abf3f4e2cbaade7c4001df381 -->

# Reference Information for the Identity Service of SAP BTP

Properties enable you to customize the configuration of the Identity service.



<a name="loio9379444abf3f4e2cbaade7c4001df381__section_sy4_ffh_wnb"/>

## Service Properties

Provide properties in JSON format.

The syntax of the properties is as follows:

```
{
	"oauth2-configuration": {
		"redirect-uris": ["https://*.myapp_namespace.cfapps.eu10.hana.ondemand.com/**"],
		"post-logout-redirect-uris": ["https://*.myapp_namespace.cfapps.eu10.hana.ondemand.com/logout/**"],
		"public-client": false
		"token-policy": {
			"token-validity": 1800,
			"refresh-validity": 7776000,
			"refresh-parallel" : 3
			"refresh-usage-after-renewal" : "off",
		}
	},
	"consumed-services": [{
		"service-instance-name": "app_log"
	}],
	"display-name": "Opportunity Management",
	"subject-name-identifier": {
		"attribute": "userUuid",
		"fallback-attribute": "uid"
	},
	"provided-apis": [{
		"name": "write-access",
		"description": "grants access to write APIs"
	}]
}
```

**Properties for the Creation of an Instance of the Identity Service**


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`redirect-uris`



</td>
<td valign="top">

Is an array of redirect URIs that are explicitly allowed for the authorization code flow.

> ### Restriction:  
> Redirect URIs are required for the authorization code flow to redirect back to your application.

This property is empty by default.

For more information, see [OpenID Connect Application Configurations](../Operation-Guide/openid-connect-application-configurations-1ae324e.md).



</td>
</tr>
<tr>
<td valign="top">

`post-logout-redirect-uris`



</td>
<td valign="top">

Is an array of redirect URIs, where users are forwarded after logout.

This property is empty by default.

For more information, see [Call Identity Authentication End Session Endpoint](../Operation-Guide/call-identity-authentication-end-session-endpoint-ec674f4.md) and [OpenID Connect Application Configurations](../Operation-Guide/openid-connect-application-configurations-1ae324e.md).



</td>
</tr>
<tr>
<td valign="top">

`public-client`



</td>
<td valign="top">

Set to `true` to enable OAuth flows with public clients. Use public clients in environments where it’s difficult to protect the client credential, such as mobile and desktop applications or client-side parts of web applications.

This property is `false` by default.

For more information, see:

-   [Configure OpenID Connect Application for Authorization Code Flow](../Operation-Guide/configure-openid-connect-application-for-authorization-code-flow-4a94254.md)

-   [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow with PKCE](../Operation-Guide/configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-a721157.md)




</td>
</tr>
<tr>
<td valign="top">

`token-policy`



</td>
<td valign="top">

Defines the token policy for the application as determined by the optional properties `token-validity`, `refresh-validity`, and `refresh-parallel`.

The admin console also supports the configuration of token policies.

For more information, see [Token Policy Configuration for Applications](../Operation-Guide/token-policy-configuration-for-applications-c4ba52e.md).



</td>
</tr>
<tr>
<td valign="top">

`token-validity`



</td>
<td valign="top">

Sets the lifetime in seconds of tokens issued by the service. The value can range from 60 to 3600, in other words, from 1 minute to 1 hour.

The default value is 3600 seconds, which translates to 1 hour.



</td>
</tr>
<tr>
<td valign="top">

`refresh-validity`



</td>
<td valign="top">

Sets the refresh lifetime of tokens issued by the service. During the refresh lifetime of a token, the service can reissue the token for a user. The value can range from 3600 to 15552000, in other words, from 1 hour to 180 days. Setting the value to 0 disables the refreshing of tokens.

The default value is 43200 seconds, which translates to 12 hours.



</td>
</tr>
<tr>
<td valign="top">

`refresh-parallel`



</td>
<td valign="top">

Determines the number of tokens that can be issued for the same session in parallel. Imagine you're logged on to the application through a web interface and a command-line interface in parallel. Then you would want this property to be set to 2. The value can range from 1 to 5.

The default value is 1.



</td>
</tr>
<tr>
<td valign="top">

`refresh-usage-after-renewal`



</td>
<td valign="top">

Defines the validity of the old refresh token after requesting a new one through the refresh token grant type. The attribute supports the following values:

-   `off` - The new refresh token immediately invalidates the old one.

-   `online` - The new refresh token is created and the old one is still active for 5 minutes.

-   `mobile` - The new and old refresh token are valid during the configured refresh token life time.



</td>
</tr>
<tr>
<td valign="top">

`consumed-services`



</td>
<td valign="top">

Use this array to enable the application to consume the APIs of reuse services. Name the reuse services consumed by the application you’re protecting. The system adds the client IDs of the reuse services to the audience claim of the identity token.

> ### Note:  
> If the token is retrieved based on a public flow \(`public-client` is true\) without client authentication, Identity Authentication doesn't add the client IDs of the dependent services to the audience claim.

This property is empty by default.



</td>
</tr>
<tr>
<td valign="top">

`xsuaa-cross-consumption`



</td>
<td valign="top">

Set to `true` to add the client ID of the Identity Authentication application created by the SAP Authorization and Trust Management service \(XSUAA\) to the audience claim. Setting `xsuaa-cross-consumption` enables cross consumption of SAP Authorization and Trust Management service.

> ### Note:  
> If the token is retrieved based on a public flow \(`public-client` is true\) without client authentication, Identity Authentication doesn't add the client IDs of the dependent services to the audience claim.

Default value is `false`.



</td>
</tr>
<tr>
<td valign="top">

`display-name`



</td>
<td valign="top">

Sets the name of the application you create with the Identity Authentication service. Enter a maximum of 99 characters.

> ### Recommendation:  
> Provide a display name, which helps the person who administrates the Identity Authentication service to understand the purpose of the application.

By default, the Identity Authentication service uses the name of the instance you provide in the `create-instance` command.



</td>
</tr>
<tr>
<td valign="top">

`subject-name-identifier`



</td>
<td valign="top">

Sets the value to use to fill the subject claim in tokens issues by the service.

The `attribute` attribute identifies the user attribute used to fill the subject claim. The attribute supports the following values:

-   `userUuid`

-   `uid`

-   `mail`

-   `displayName`

-   `loginName`

-   `personnelNumber`


For more information about attributes for the subject name identifier, see [Configure the Subject Name Identifier Sent to the Application](../Operation-Guide/configure-the-subject-name-identifier-sent-to-the-application-1d020e3.md).



</td>
</tr>
<tr>
<td valign="top">

`provided-apis`



</td>
<td valign="top">

An array of API names \(`name`\) and descriptions \(`description`\) which this application makes available for other applications to consume. The name can be any unique string of 32 characters. You can define a maximum of 20 APIs.

For more information, see [Configure Integration Between Applications](../Operation-Guide/configure-integration-between-applications-9ad7e80.md).



</td>
</tr>
</table>



<a name="loio9379444abf3f4e2cbaade7c4001df381__section_sv2_4d2_ynb"/>

## Binding Properties

Provide binding properties in JSON format. If you provide no properties, the binding uses the `SECRET` credential type. The syntax of the properties is as follows:

```
{"credential-type": "SECRET"}
```

Or:

```
{
    "credential-type": "X509_GENERATED", 
    "key-length": 2048, 
    "validity": 30, 
    "validity-type": "DAYS",
    "app-identifier":"myApplication"
}
```

Or:

```
{
    "credential-type": "X509_PROVIDED", 
    "certificate": "-----BEGIN CERTIFICATE-----\nMIID6zC…\n-----END CERTIFICATE-----"
}
```

Or:

```
{"credential-type": "NONE"}
```

> ### Restriction:  
> You can bind a maximum of 20 applications to a single service instance.

**Credential Types for the Binding of an Instance of the Identity Service**


<table>
<tr>
<th valign="top">

Credential Type



</th>
<th valign="top">

Credential Properties



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" colspan="2">

`SECRET`



</td>
<td valign="top">

Generates a client secret. If no properties are provided, `SECRET` is the default type.



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

`X509_GENERATED`



</td>
<td valign="top">

 



</td>
<td valign="top">

Generates an X.509 certificate and private key.



</td>
</tr>
<tr>
<td valign="top">

`key-length`



</td>
<td valign="top">

Specifies the byte length of the generated private key. The default length is `2048` bytes. You can also choose `4096` bytes.



</td>
</tr>
<tr>
<td valign="top">

`validity`



</td>
<td valign="top">

Specifies the number of time units for `validity-type`. The default value is `30`.

Together with the `validity-type` the range of validity runs from 1 day to 1 year.



</td>
</tr>
<tr>
<td valign="top">

`validity-type`



</td>
<td valign="top">

Specifies the time unit for `validity`. Supported values are `DAYS`, `MONTHS`, and `YEARS`. The default value is `DAYS`.



</td>
</tr>
<tr>
<td valign="top" colspan="2">

`X509_PROVIDED`



</td>
<td valign="top">

Creates a binding using certificate you provide from a trusted certificate authority \(CA\). This certificate can be used to request tokens.

> ### Restriction:  
> Don't forget the new lines \(`\n`\) after `-----BEGIN CERTIFICATE-----` and before `-----END CERTIFICATE-----`. See the previous example.
> 
> The certificate you provide must be unique in the Identity Authentication tenant.



</td>
</tr>
<tr>
<td valign="top" colspan="2">

`NONE`



</td>
<td valign="top">

No credentials are added to the binding. Used for public clients.

For more information, see [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow with PKCE](../Operation-Guide/configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-a721157.md).



</td>
</tr>
</table>



<a name="loio9379444abf3f4e2cbaade7c4001df381__section_ss1_htq_xnb"/>

## Binding Information

The service key or binding provides the following information.

-   Client ID

-   Secrets

    Secrets provided depend on how the service was configured.

    -   By default the service generates a client secret.

    -   If you had the service generate an X.509 certificate, the binding includes the key and the certificate.

        If you provided the service with your own X.509 certificate, the binding includes the certificate.

    -   For public clients, you can suppress the creation of a secret.


-   Identity Authentication domains

-   Identity Authentication URL


The following examples show the information stored in the binding:

Binding with client ID and client secret:

```
{
  "clientid": "1aa234ca-faed-4fb2-966e-7c86262ba93c",
  "clientsecret": "<secret>",
  …
  "domains": ["accounts.ondemand.com", "accounts.cloud.sap"],
  "url": "https://caev6ngwk.accounts.ondemand.com"
}
```

Binding with generated X.509 certificate:

```
{
  "clientid": "1aa234ca-faed-4fb2-966e-7c86262ba93c",
  "key": "<content>",
  "certificate": "<content>",
  …
  "domains": ["accounts.ondemand.com", "accounts.cloud.sap"],
  "url": "https://caev6ngwk.accounts.ondemand.com"
}
```

Binding with provided X.509 certificate:

```
{
  "clientid": "1aa234ca-faed-4fb2-966e-7c86262ba93c",
  "certificate": "<content>",
  …
  "domains": ["accounts.ondemand.com", "accounts.cloud.sap"],
  "url": "https://caev6ngwk.accounts.ondemand.com"
}
```

Binding with no credentials:

```
{
  "clientid": "1aa234ca-faed-4fb2-966e-7c86262ba93c",
  "credential-type": "NONE",
  …
  "domains": ["accounts.ondemand.com", "accounts.cloud.sap"],
  "url": "https://caev6ngwk.accounts.ondemand.com"
}
```



<a name="loio9379444abf3f4e2cbaade7c4001df381__section_lc5_qh4_znb"/>

## Code Flows

For information about how the Identity Authentication service supports code flows, see [OpenID Connect](../Operation-Guide/openid-connect-a789c9c.md).



<a name="loio9379444abf3f4e2cbaade7c4001df381__section_tc5_qh4_znb"/>

## Token Validation

To validate tokens, we provide a client libraries to support the authentication of tokens.

-   For Java, see [ SAP BTP Java Security Client Library](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/java-security) on *GitHub*. The Java library supports authentication of tokens from version 2.8.0.

-   For node.js, see [@sap/xssec: XS Advanced Container Security API for node.js](https://www.npmjs.com/package/@sap/xssec) on *npm*.




<a name="loio9379444abf3f4e2cbaade7c4001df381__section_dqz_qh4_znb"/>

## Token Attributes

The administrator of the Identity Authentication service determines what attributes are available in tokens. For more information, see [Configure the User Attributes Sent to the Application](../Operation-Guide/configure-the-user-attributes-sent-to-the-application-d361407.md).

