<!-- loio9ad7e8052d054e83adf10aff1bdae1bf -->

# Configure Integration Between Applications

To enable one application to consume the APIs of another application, applications can request tokens with access privileges for APIs of another application. With this configuration, you authorize one application to consume the API of another application.



<a name="loio9ad7e8052d054e83adf10aff1bdae1bf__prereq_ygs_hc3_pwb"/>

## Prerequisites

You know the name of the API needed by the consumer application.

Either the API name is listed in the documentation of the provider application or you must look it up in the provider application.



## Procedure

1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*

2.  Choose the consumer application.

3.  Choose the *Trust* tab.

4.  Under *Application APIs*, choose *Dependencies*.

5.  Enter the required data.

    1.  Enter the dependency name specified by or negotiated with the consuming application.

    2.  Choose the provider application and the API the consumer application consumes.





<a name="loio9ad7e8052d054e83adf10aff1bdae1bf__result_g5m_ms3_pwb"/>

## Results

The consumer application can consume the specified API of the provider application.

