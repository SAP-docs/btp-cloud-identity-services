<!-- loio04e7b54f35794f98ac4da453a32daf91 -->

# Provide APIs for Consumption by Microservices

SAP Cloud Identity Services can help you expose APIs to microservices within your application. You can expose APIs with an API permission group or tie the access to the authorizations of the current user \(principal propagation\).



<a name="loio04e7b54f35794f98ac4da453a32daf91__context_cxd_czv_4bc"/>

## Context

You can protect APIs by adding a name for an API permission group. Microservices that are allowed to consume this API permission group pass a token issued by SAP Cloud Identity Services with this name as a claim. Your microservice must evaluate the `ias_apis` claim for this name to allow access.

If the consuming microservice is using a principal propagation scenario and not a technical user scenario, your microservice can check the authorizations assigned to the current user. The service also offers the option for token exchange flows to offer all APIs of the microservice. In this case, ***principal-propagation*** is written in the `ias_apis` claim. Your microservice must rely on the authorizations available to the current user alone.

As the providing microservice, you have the following options for configuring your application for API permission groups:

-   Use the administration console for SAP Cloud Identity Services as described in the following procedure.

-   Your application can set the API permission groups with the parameters of the Identity service of SAP BTP.

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




<a name="loio04e7b54f35794f98ac4da453a32daf91__steps_xtf_mzv_4bc"/>

## Procedure

1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*

2.  Choose the provider application.

3.  Choose the *Trust* tab.

4.  Under *Application APIs*, choose *Provided APIs*.

5.  Check that the name of the API permission group that you check in your application is listed or enter the required data.

    > ### Caution:  
    > The API name must match exactly what is expected by any consuming microservices. The name must be unique within all APIs provided by the same application. Consuming microservices use this name to determine if their microservice has the rights to access the providing microservice.
    > 
    > The name can be any URN-compliant string of up to 32 characters. You can define a maximum of 20 APIs.
    > 
    > For more information about URNs, see [RFC 8141](https://datatracker.ietf.org/doc/rfc8141/).

    To rely solely on the permissions of the current user, select the *Allow all APIs for principal propagation* option. Identity Authentication adds ***principal-propagation*** to the `ias_apis` claim.


