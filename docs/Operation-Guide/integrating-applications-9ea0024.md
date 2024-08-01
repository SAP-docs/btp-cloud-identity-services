<!-- loio9ea0024383de4726b6a4aae471eb1039 -->

# Integrating Applications

Applications sometimes need to propagate principals or have technical communication arrangements between them. To enable one application to consume the APIs of another application, the developer of the application providing APIs defines one or more API groups, which the consuming application can consume.

Under this model, applications that can be called by other applications define API permission groups. Administrators grant access to these groups to consuming applications. You can set up technical communication or principal propagation. With technical communication, you can map authorizations to the communication. With principal propagation, user authorizations apply in the decision whether an API call is allowed or not. These permission groups cover a set of related APIs. An application can expose all its APIs without an API permission group when there's no need to restrict consuming applications.

In the configuration of the consumer application, the tenant administrator defines the dependencies. Consumer applications use the dependency name to identify to SAP Cloud Identity Services which application the consumer wants to access including the API permission group to grant. The actual dependency name depends on the consuming application:

-   Typically, an application needs a specific name for integration with a specific provider application. Find the supported dependency names in the provider application or its documentation.

-   When an application generically integrates with many arbitrary applications, the application rather enables you to define custom dependency names and maintain them both in SAP Cloud Identity Services as well as in the consuming application itself. The configuration informs the application which dependency to use for which integration scenario.


The following figure shows the relationship between two applications in SAP Cloud Identity Services. The provider application offers two API permission groups. The consumer app is allowed to consume one of these groups. The applications can use technical communication or principal propagation.

  
  
**App-to-App Integration of API Permission Groups**

![](images/App2App_Logical_Model_951e1a7.png "App-to-App Integration of API Permission Groups")

In the following figure, the provider application doesn't offer any API permission groups. The consumer application references all the available APIs. The provider application depends on the authorizations of the current user when these APIs are accessed.

  
  
**App-to-App Integration of All APIs**

![](images/App2App_All_APIs_66a960b.png "App-to-App Integration of All APIs")

To configure dependencies, see [Configure Integration Between Applications](configure-integration-between-applications-9ad7e80.md).

To consume APIs from an application that is not registered in SAP Cloud Identity Services, see [Generate Credentials to Access the APIs of an Application](generate-credentials-to-access-the-apis-of-an-application-e595341.md).

For more information about developing such applications, see [Consuming APIs from Other Applications](../Development/consuming-apis-from-other-applications-29e204d.md).

