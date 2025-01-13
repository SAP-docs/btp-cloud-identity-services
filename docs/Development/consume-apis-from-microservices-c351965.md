<!-- loioc3519650b7fa406b81dea8e808e1cd13 -->

# Consume APIs from Microservices

Your consumer microservice can request an access token from Identity Authentication to consume the API of a provider microservice within your application.



<a name="loioc3519650b7fa406b81dea8e808e1cd13__prereq_dj5_ws3_m1c"/>

## Prerequisites

You know the name of the dependency defined in the application configuration of SAP Cloud Identity Services. The tenant administrator enters the dependency name in the application configuration. As the owner of the consumer microservice, you must provide documentation to enable the administrator to:

-   Enter the name that you expect.

-   Configure the same dependency name in your microservice.


For more information, see [Restricting Access to Microservices Within Applications](restricting-access-to-microservices-within-applications-e004379.md).



<a name="loioc3519650b7fa406b81dea8e808e1cd13__steps_ysd_x1w_4bc"/>

## Procedure

1.  With the dependency name, the consumer microservice can call the `/token` endpoint of Identity Authentication.

    **Example: Technical Communication**

    Your microservice calls the credentials defined for your dependency within your application \(client ID 3ab1ba0e-c573-4ad5-20a4-28aa4e587a19\) named `techDependency`. The microservice calls the `/token` endpoint with its client ID and the `resource` parameter and the dependency name used to identify the API that the microservice consumes.

    ```
    curl  $iashost/oauth2/token -X POST \
       -H 'Content-Type: application/x-www-form-urlencoded' \
       -H 'Accept: application/json' \
       -d "client_id=3ab1ba0e-c573-4ad5-20a4-28aa4e587a19" \
       -d "client_secret=$secret" \
       -data-urlencode 'grant_type=client_credentials' \
       -data-urlencode 'resource=urn:sap:identity:api:name:techDependency'
    
    ```

    Identity Authentication returns a token with the access control for the APIs and audience claim. The following is an example of a token with the relevant claims.

    ```
    {
        "ias_apis": [
            "weather_temperature_read"
        ],
    
        "sub": "3ab1ba0e-c573-4ad5-20a4-28aa4e587a19",
        "aud": "(client ID 3ab1ba0e-c573-4ad5-20a4-28aa4e587a19)",
        "azp": "3ab1ba0e-c573-4ad5-20a4-28aa4e587a19",
    }
    ```

    **Example: Principal Propagation:**

    Your microservice calls the credentials defined for your dependency \(client ID e7c7e327-86c0-48a6-af57-a1234b567869\) named `myDependency`. The microservice calls the `/token` endpoint with the client ID and the `resource` parameter and the dependency name used to identify the API that the microservice consumes.

    ```
    curl $iashost/oauth2/token  -X POST \
        -H 'Content-Type: application/x-www-form-urlencoded' \
        -H 'Accept: application/json' \
        -d "client_id=e7c7e327-86c0-48a6-af57-a1234b567869" \
        -d "client_secret=$secret" \
        -d "grant_type=urn%3Aietf%3Aparams%3Aoauth%3Agrant-type%3Ajwt-bearer" \
        -d "assertion=$IDTOKEN" \
        -d "resource=urn:sap:identity:api:name:myDependency"
    ```

    Identity Authentication returns a token with the access control for the APIs and audience claim. The following is an example of a token with the relevant claims.

    ```
    {
        "ias_apis": [
            "sales-order"
        ],   
        "sub": "P123456",
        "mail": "donna.moore@example.com",
        "last_name": "Moore",
        "aud": "e7c7e327-86c0-48a6-af57-a1234b567869", 
        "scim_id": "1a2345bc-4f6b-456b-9bfb-5d58beb97fb7",
        "user_uuid": "1a2345bc-4f6b-456b-9bfb-5d58beb97fb7",
        "azp": "e7c7e327-86c0-48a6-af57-a1234b567869",
        "first_name": "Donna",
        …
    }
    ```

2.  Send the token to the API endpoint of the application.


