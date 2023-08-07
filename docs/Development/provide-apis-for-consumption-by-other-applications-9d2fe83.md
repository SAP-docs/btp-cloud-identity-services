<!-- loio9d2fe839a8c8428e98aa93affed1bda3 -->

# Provide APIs for Consumption by Other Applications



## Context



## Procedure

1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*

2.  Choose the provider application.

3.  Choose the *Trust* tab.

4.  Under *Application APIs*, choose *Provided APIs*.

5.  Check that the API is listed or enter the required data.

    For more information, see [Reference Information for the Identity Service of SAP BTP](../Integrating-the-Service/reference-information-for-the-identity-service-of-sap-btp-9379444.md).

    > ### Caution:  
    > The API name must match exactly what is expected by any consumer applications. The name must be unique within all APIs provided by the same provider application. Consumer applications use this name to determine if their application has the rights to access the provider application.
    > 
    > The name can be any URN-compliant string of 32 characters. You can define a maximum of 20 APIs.
    > 
    > For more information about URNs, see [RFC 8141](https://datatracker.ietf.org/doc/rfc8141/).

    The provider application can also specify the APIs with the Identity service of SAP BTP.

    For more information, see [Reference Information for the Identity Service of SAP BTP](../Integrating-the-Service/reference-information-for-the-identity-service-of-sap-btp-9379444.md).


