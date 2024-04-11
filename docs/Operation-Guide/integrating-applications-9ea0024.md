<!-- loio9ea0024383de4726b6a4aae471eb1039 -->

# Integrating Applications

OpenID Connect \(OIDC\) applications sometimes need to propagate principals or have technical communication arrangements between them. To enable one application to consume the APIs of another application, the application developer defines one or more groups of APIs, which the consuming application can consume.

Under this model, applications that can be called by other applications, define API permission groups. API permission groups are the granularity at which administrators can grant access to the APIs of a provider application. Such groups cover a set of related APIs. An application can expose a single group when there's no need to restrict consuming applications.

In the application configuration of the consumer application, the dependencies are defined. Consumer applications use the dependency name to identify to SAP Cloud Identity Services, which API permission group the consumer wants to access. Consumer applications need:

-   Specific dependency names for integration with a specific application.

-   Arbitrary dependency names and a way for you as tenant administrator to configure which dependency name is meant for which purpose. Such a solution is for a generic integration with various applications that support this kind of integration.


As the tenant administrator, you configure the dependency of a consumer application to the provider application or manage a dependency that has been created for you by a solution.

The following figure shows the relationship between two applications in SAP Cloud Identity Services. The provider application offers two API permission groups. The dependency of the consumer application references one of these groups.

  
  
**App-to-App Integration**

![](images/App2App_Logical_Model_951e1a7.png "App-to-App Integration")

To configure dependencies, see [Configure Integration Between Applications](configure-integration-between-applications-9ad7e80.md).

For more information about developing such applications, see [Consuming APIs from Other Applications](../Development/consuming-apis-from-other-applications-29e204d.md).

