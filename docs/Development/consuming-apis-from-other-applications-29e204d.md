<!-- loio29e204da5b794c4683289ee0384ec781 -->

# Consuming APIs from Other Applications

Applications sometimes need to propagate principals or have technical communication arrangements between them. To enable OpenID Connect \(OIDC\) applications to consume the APIs of other applications, the developer defines API permission groups for a provider application, which a consumer application can consume through a defined dependency.



<a name="loio29e204da5b794c4683289ee0384ec781__section_r1q_hc3_hdc"/>

## Design Options

In this scenario, you have a provider application that provides a group of APIs and a consumer application that consumes them. Tenant administrators grant access to the consumer applications for this group. You can take one of the following approaches:

-   Technical communication that retrieves a new token with a client credential flow

-   Principal propagation with a choice between the JWT bearer and token exchange flows


In either case, the audience of the token matches the provider application. In addition, the `ias_apis` claim lists the granted API permission groups or a fixed value for when all APIs are consumed.

The following figure shows the relationship between two applications in SAP Cloud Identity Services. The provider application offers two API permission groups. The dependency of the consumer application refers to one of these groups.

  
  
**App-to-App Integration of API Permission Groups**

![](../Operation-Guide/images/App2App_Logical_Model_951e1a7.png "App-to-App Integration of API Permission Groups")

Alternatively, if your provider application doesn't need to distinguish different API permission groups and is consumed with principal propagation, you can make all APIs available. The provider application must check the principal propagated by the consumer application for the authorizations required by the APIs. In the following figure, the provider application doesn't offer any API permission groups. The consumer application refers to all the available APIs. The provider application depends on the authorizations of the current user when these APIs are accessed.

  
  
**App-to-App Integration of All APIs**

![](../Operation-Guide/images/App2App_All_APIs_66a960b.png "App-to-App Integration of All APIs")



<a name="loio29e204da5b794c4683289ee0384ec781__section_myl_bc3_hdc"/>

## At Runtime

At runtime, the consumer application fetches a token according to the appropriate flow:

-   Use the client credential flow for technical communication.

    For more information, see [Using Client Credentials Flow](../Operation-Guide/using-client-credentials-flow-7d84532.md).

-   Choose the appropriate flow for principal propagation.

    -   If the consumer application already issues a JWT token, use the JWT bearer flow.

        For more information, see [Using JWT Bearer Flow](../Operation-Guide/using-jwt-bearer-flow-2862baf.md).

    -   If the consumer application issues another token type, such as SAML2 assertion to bearer token, use the token exchange flow.

        For more information, see [Using Token Exchange](../Operation-Guide/using-token-exchange-25598b2.md).



In either case, use the `resource` parameter to identify the dependency consumed by the consumer application. The `resource` parameter is a Uniform Resource Name \(URN\).

For example: <code>urn:sap:identity:application:provider:name:<i class="varname">&lt;Dependency_name&gt;</i></code>

The dependency name is the name that the tenant administrator configures for the dependency between the consumer application and the provider application.

> ### Tip:  
> Document the name in a scenario guide so that administrators know which name to use when creating dependencies. If you have experience working with destinations, you're already used to this approach.

In the unusual case that you need a token that reflects multiple dependencies to the same provider application, you can replace <code>name:<i class="varname">&lt;Dependency_name&gt;</i></code> with <code>clientid:<i class="varname">&lt;client_id&gt;</i></code>. Use the client ID of the provider application in Identity Authentication.

The service returns a token, which includes the following relevant claims:

-   The audience \(`aud`\) claim of the provider application.

-   The `ias_api` claim, which includes an array of API permission groups of the provider application.


The consumer application uses this token to call the API endpoint of the provider application. The provider application validates the token and its claims and processes the call. The following figure illustrates this scenario for technical communication between systems.

  
  
**Technical Communication Sequence Between Applications**

![](images/app2apptechnical_pptx_8db2315.png "Technical Communication Sequence Between Applications")

**Related Information**  


[Provide APIs for Consumption by Other Applications](provide-apis-for-consumption-by-other-applications-9d2fe83.md "SAP Cloud Identity Services can help you expose APIs of your application to other applications. You can expose APIs with an API permission group or tie the access to the authorizations of the current user (principal propagation).")

[Consume an API from a Provider Application](consume-an-api-from-a-provider-application-9675b64.md "Your consumer application can request an access token from Identity Authentication to consume the API of a provider application.")

