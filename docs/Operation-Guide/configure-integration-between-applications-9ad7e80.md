<!-- loio9ad7e8052d054e83adf10aff1bdae1bf -->

# Configure Integration Between Applications

Define a dependency to the API of another application. With this configuration, you authorize one application to consume the API of another application.



<a name="loio9ad7e8052d054e83adf10aff1bdae1bf__prereq_ygs_hc3_pwb"/>

## Prerequisites

-   You know the name of the provider application and API permission group needed by the consumer application.

    The provider application defines the name of the API permission group during deployment, in the documentation of the application, or from the developers directly for custom developments.

    If the provider application offers all APIs, then you don't need to know the name of a specific API permission group.

    For more information, see [Provide APIs for Consumption by Other Applications](../Development/provide-apis-for-consumption-by-other-applications-9d2fe83.md).

-   You know the name of the dependency to enter for the consumer application.

    The consumer application must define this name automatically during deployment, in the documentation of the application, or from the developers directly for custom developments.

    For more information, see [Integrating Applications](integrating-applications-9ea0024.md).




## Procedure

1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*

2.  Choose the consumer application.

3.  Choose the *Trust* tab.

4.  Under *Application APIs*, choose *Dependencies*.

5.  Enter the required data.

    You can create a maximum of 20 dependencies.

    1.  Enter a unique name for the dependency.

    2.  Choose the provider application and the API that the consumer application consumes.


6.  Save your entries.




<a name="loio9ad7e8052d054e83adf10aff1bdae1bf__result_g5m_ms3_pwb"/>

## Results

The consumer application can consume the specified API of the provider application.



<a name="loio9ad7e8052d054e83adf10aff1bdae1bf__postreq_brw_kp3_hdc"/>

## Next Steps

If the applications were developed with a generic implementation, you must configure the consumer application with the dependency name you provided. See the documentation of the consumer application.

For more information about how application developers use this dependency, see [Consume an API from a Provider Application](../Development/consume-an-api-from-a-provider-application-9675b64.md).

