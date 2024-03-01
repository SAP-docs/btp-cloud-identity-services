<!-- loio29e204da5b794c4683289ee0384ec781 -->

# Consuming APIs from Other Applications

OpenID Connect \(OIDC\) applications sometimes need to propagate principals or have technical communication arrangements between applications. To enable one application to consume the APIs of another application, configure an application to include the audience of the other application in tokens issued by Identity Authentication.

In this scenario, you have one application that provides an API and another application that consumes the API. The provider and consumer applications must be configured as OpenID Connect \(OIDC\) applications. At runtime, the consuming application gets a token according to the appropriate flow.

-   Use the client credential flow for technical communication.

-   Use token-exchange flow for principal propagation and exchanges of token type, such as ID token to SAML 2 bearer token.


In either case, use the `resource` parameter to identify the provider. The `resource` parameter is a uniform resource name \(URN\).

**Options to Identify the Provider Application**


<table>
<tr>
<th valign="top">

URN

</th>
<th valign="top">

Provider Determined by

</th>
</tr>
<tr>
<td valign="top">

<code>urn:sap:identity:application:provider:name:<i class="varname">&lt;logical_name&gt;</i></code>

</td>
<td valign="top">

Logical name: Document the name in a scenario guide similar to how you do for destinations.

</td>
</tr>
<tr>
<td valign="top">

<code>urn:sap:identity:application:provider:clientid:<i class="varname">&lt;client_id&gt;</i></code>

</td>
<td valign="top">

Client ID: Identity Authentication can resolve the provider application with the `client_id` parameter.

</td>
</tr>
<tr>
<td valign="top">

<code>urn:sap:identity:application:provider:clientid:<i class="varname">&lt;client_id&gt;</i>:apptid:<i class="varname">&lt;app_tid&gt;</i></code>

</td>
<td valign="top">

Client ID and application tenant ID: Identity Authentication can resolve the provider application with the `client_id` and `app_tid` parameters.

Use this resource URN when there are multiple subscriptions of the same application with the same Identity Authentication tenant.

</td>
</tr>
</table>

The service returns a token, which includes the audience \(`aud`\) claim of the provider application and a string for access control under the `ias_api` claim. The consumer application uses this token with to call the API endpoint of the provider application. The provider application validates the token and its claims and processes the call. The following figure illustrates this scenario for a technical communication between systems.

  
  
**Technical Communication Sequence Between Applications**

![](images/app2apptechnical_pptx_8db2315.png "Technical Communication Sequence Between Applications")

The administrator must ensure that the two applications can share the APIs between each other, if the applications weren't deployed with this configuration.

**Related Information**  


[Provide APIs for Consumption by Other Applications](provide-apis-for-consumption-by-other-applications-9d2fe83.md "SAP Cloud Identity Services can help you expose your application to other applications. You can expose APIs with an access control list or tie the access to the authorizations of the current user (principle propagation).")

[Consume an API from Another Application](consume-an-api-from-another-application-9675b64.md "Define a dependency to the API of another application. Your consumer application can request an access token from Identity Authentication to consume that API.")

