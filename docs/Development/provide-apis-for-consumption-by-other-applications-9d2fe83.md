<!-- loio9d2fe839a8c8428e98aa93affed1bda3 -->

# Provide APIs for Consumption by Other Applications

SAP Cloud Identity Services can help you expose APIs of your application to other applications. You can expose APIs with an API permission group or tie the access to the authorizations of the current user \(principal propagation\).



## Context

You can protect APIs by adding a name for an API permission group. Other applications that are allowed to consume this API permission group pass a token issued by SAP Cloud Identity Services with this name as a claim. Your application must evaluate the `ias_apis` claim for this name to allow access.

If the consuming application is using a principal propagation scenario and not a technical user scenario, your application can check the authorizations assigned to the current user. You can also offer all APIs of the provider application without permission groups. In this case, ***principal-propagation*** is written in the `ias_apis` claim. Your application must rely on the authorizations available to the current user alone.

As the providing application, you have the following options for configuring identity authentication for API permission groups:

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


> ### Remember:  
> The provided APIs for the `Administration Console` for Cloud Identity Services is read-only.



## Procedure

1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*

2.  Choose the provider application.

3.  Choose the *Trust* tab.

4.  Under *Application APIs*, choose *Provided APIs*.

5.  Verify that the name of the API permission group that you check in your application is listed.

    Otherwise enter the required data and save your entries.

    > ### Caution:  
    > The API name must match exactly what is expected by consumer applications. The name must be unique within all APIs provided by the same provider application. Consumer applications use this name to determine if their application has the rights to access the provider application.
    > 
    > The name can be any URN-compliant string of up to 50 characters. You can define a maximum of 50 APIs.
    > 
    > For more information about URNs, see [RFC 8141](https://datatracker.ietf.org/doc/rfc8141/).

    To rely solely on the permissions of the current user, select the *Allow all APIs for principal propagation* option. Identity Authentication adds ***principal-propagation*** to the `ias_apis` claim.


