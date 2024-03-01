<!-- loio9d2fe839a8c8428e98aa93affed1bda3 -->

# Provide APIs for Consumption by Other Applications

SAP Cloud Identity Services can help you expose your application to other applications. You can expose APIs with an access control list or tie the access to the authorizations of the current user \(principle propagation\).



## Context

You can protect APIs by adding a name for an API permission group. Other applications that are allowed to consume this API permission group, pass this name as a claim in the ID token issued by Identity Authentication. Your application must parse the `ias_apis` claim for this name to allow access.

In addition, your application can check the authorizations assigned to the current user if the consuming application is using a token exchange flow and not a technical user scenario. The service also offers the option for token exchange flows to suppress inclusion of the names of API permission groups in the `ias_apis` claim. In this case, your application must rely on the authorizations available to the current user alone.

As the providing application, you've the following options for configuring identity authentication for API permission groups:

-   Use the administration console for SAP Cloud Identity Services as described in the following procedure.

-   The provider application can set the API permission groups with the parameters of the Identity service of SAP BTP.

    The following example shows an API permission group named `sales-orders`.

    ```
      "provided-apis": [
        {
          "name": "sales-orders",
          "description": "Access sales orders"
        }
      ]
    
    ```

    For more information, see [Reference Information for the Identity Service of SAP BTP](../Integrating-the-Service/reference-information-for-the-identity-service-of-sap-btp-9379444.md).




## Procedure

1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*

2.  Choose the provider application.

3.  Choose the *Trust* tab.

4.  Under *Application APIs*, choose *Provided APIs*.

5.  Check that the name of the API permission group you check in your application is listed or enter the required data.

    > ### Caution:  
    > The API name must match exactly what is expected by any consumer applications. The name must be unique within all APIs provided by the same provider application. Consumer applications use this name to determine if their application has the rights to access the provider application.
    > 
    > The name can be any URN-compliant string of 32 characters. You can define a maximum of 20 APIs.
    > 
    > For more information about URNs, see [RFC 8141](https://datatracker.ietf.org/doc/rfc8141/).

    To suppress the use of access control lists and rely solely on the permissions of the current user, select the *Allow all APIs for principal propagation* option.


