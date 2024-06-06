<!-- loio9675b64bc8014f4282e49d0cd8ce60fa -->

# Consume an API from Another Application

Your consumer application can request an access token from Identity Authentication to consume the API of a provider application.



<a name="loio9675b64bc8014f4282e49d0cd8ce60fa__prereq_dj5_ws3_m1c"/>

## Prerequisites

You know the name of the dependency defined in the application configuration of SAP Cloud Identity Services. The tenant administrator enters the dependency name in the application configuration. As the owner of the consumer application, you must provide documentation to enable the administrator to:

-   Enter the name that you expect.

-   Configure the same dependency name in your application.


For more information, see [Configure Integration Between Applications](../Operation-Guide/configure-integration-between-applications-9ad7e80.md).



## Procedure

1.  With the dependency name, the consumer application can call the `/token` endpoint of Identity Authentication.

    **Example: Technical Communication**

    A consumer application \(client ID 3ab1ba0e-c573-4ad5-20a4-28aa4e587a19\) has a dependency to the provider application \(client ID 77f42d85-7da7-1aa1-84a2-e65a76308cd3\) named `techDependency`. The application calls the `/token` endpoint with its client ID and the `resource` parameter and the dependency name used to identify the API that the consumer application consumes.

    ```
    curl  $iashost/oauth2/token -X POST \
       -H 'Content-Type: application/x-www-form-urlencoded' \
       -H 'Accept: application/json' \
       -d "client_id=3ab1ba0e-c573-4ad5-20a4-28aa4e587a19" \
       -d "client_secret=$secret" \
       -data-urlencode 'grant_type=client_credentials' \
       -data-urlencode 'resource=urn:sap:identity:application:provider:name:techDependency'
    
    ```

    Identity Authentication returns a token with the access control for the APIs and audience claim. The audience claim contains the client ID of the provider application. The following is an example of a token with the relevant claims.

    ```
    {
        "ias_apis": [
            "weather_temperature_read"
        ],
    
        "sub": "3ab1ba0e-c573-4ad5-20a4-28aa4e587a19",
        "aud": "77f42d85-7da7-1aa1-84a2-e65a76308cd3",
        "azp": "3ab1ba0e-c573-4ad5-20a4-28aa4e587a19",
    }
    ```

    **Example: Principal Propagation:**

    A consumer application \(client ID e7c7e327-86c0-48a6-af57-a1234b567869\) has a dependency to the provider application \(client ID 7ab2cd3e-c573-4ad5-9007-28aa4e587a19\) named `myDependency`. The application calls the `/token` endpoint with its client ID and the `resource` parameter and the dependency name used to identify the API that the consumer application consumes.

    ```
    curl $iashost/oauth2/token  -X POST \
        -H 'Content-Type: application/x-www-form-urlencoded' \
        -H 'Accept: application/json' \
        -d "client_id=e7c7e327-86c0-48a6-af57-a1234b567869" \
        -d "client_secret=$secret" \
        -d "grant_type=urn%3Aietf%3Aparams%3Aoauth%3Agrant-type%3Ajwt-bearer" \
        -d "assertion=$IDTOKEN" \
        -d "resource=urn:sap:identity:application:provider:name:myDependency"
    ```

    Identity Authentication returns a token with the access control for the APIs and audience claim. The audience claim contains the client ID of the provider application. The following is an example of a token with the relevant claims.

    ```
    {
        "ias_apis": [
            "sales-order"
        ],   
        "sub": "P123456",
        "mail": "donna.moore@example.com",
        "last_name": "Moore",
        "aud": "7ab2cd3e-c573-4ad5-9007-28aa4e587a19", 
        "scim_id": "1a2345bc-4f6b-456b-9bfb-5d58beb97fb7",
        "user_uuid": "1a2345bc-4f6b-456b-9bfb-5d58beb97fb7",
        "azp": "e7c7e327-86c0-48a6-af57-a1234b567869",
        "first_name": "Donna",
        …
    }
    ```

2.  Send the token to the API endpoint of the provider application.


**Related Information**  


[Consuming APIs from Other Applications](consuming-apis-from-other-applications-29e204d.md "Applications sometimes need to propagate principals or have technical communication arrangements between them. To enable OpenID Connect (OIDC) applications to consume the APIs of other applications, the developer defines API permission groups for a provider application, which a consumer application can consume through a defined dependency.")

