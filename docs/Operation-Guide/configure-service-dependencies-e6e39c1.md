<!-- loioe6e39c169e30448ba644192988662f51 -->

# Configure Service Dependencies

Enable an application to consume a reuse service using its own token by adding the service to the `consumed-services` property in the Identity service instance parameters.



## Prerequisites

-   For Cloud Foundry, the reuse service instance exists in the same space as your application.

    For more information, see [Creating Service Instances](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-instances?version=Cloud) in the SAP BTP documentation.

-   You know the name of the service instance of the reuse service.




## Context

Use service dependencies when your application needs to call a platform reuse service, such as the Destination service or the Job Scheduling service, using its own application token. The developer of your application must design the application to use mutual TLS when calling the reuse service. The reuse service validates the audience claim of that token to confirm the caller is authorized.

You can reference only reuse services that are designed and documented to support the `consumed-services` parameter. SAP BTP platform services such as the Destination service and Job Scheduling service support this pattern.

> ### Note:  
> You configure service dependencies in the Identity service instance parameters at deployment time. The resulting dependency is visible in the administration console under the application's *Dependencies* \> *Services* tab, but you can't modify it there.



## Procedure

1.  In the Identity service instance parameters of your application, configure the `consumed-services` property.

    In the `consumed-services` array, list each reuse service by its service instance name:

    ```
    {
    …
      "consumed-services": [
        {
          "service-instance-name": "<name-of-reuse-service-instance>"
        }
      ],
    …
    }
    ```

    You can list up to 400 services.

    > ### Note:  
    > If the token is retrieved based on a public client flow \(`public-client` is `true`\) without client authentication, SAP Cloud Identity Services doesn't add the client IDs of the dependent services to the audience claim.

2.  Create or update the Identity service instance, referencing this parameter file.

    The Identity service instance creation validates that each entry in `consumed-services`refers to an existing, SAP Cloud Identity Services-based service instance. If validation fails, the instance creation fails with an error identifying the unresolvable entry.




## Results

SAP Cloud Identity Services adds the client IDs of the named reuse services to the audience \(`aud`\) claim of tokens issued for this application. Your application can then obtain a token and present it when calling the reuse service with mTLS. The reuse service validates the `aud` claim to confirm the caller is a trusted consumer.

**Related Information**  


[Reference Information for the Identity Service of SAP BTP](../Integrating-the-Service/reference-information-for-the-identity-service-of-sap-btp-9379444.md "Properties enable you to customize the configuration of the Identity service.")

