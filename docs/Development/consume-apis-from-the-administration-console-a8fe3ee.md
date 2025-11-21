<!-- loioa8fe3eeb0f2244c6b04edfdfbd040987 -->

# Consume APIs from the Administration Console

Your consumer application can request an access token from Identity Authentication to consume the APIs of the Administration Console for Cloud Identity Services acting as a provider application.



<a name="loioa8fe3eeb0f2244c6b04edfdfbd040987__prereq_dj5_ws3_m1c"/>

## Prerequisites

You have configured the integration between the `Administration Console` application in the tenant and your consumer application that will use the APIs of the `Administration Console`. For more information, see [Configure Integration Between Applications](../Operation-Guide/configure-integration-between-applications-9ad7e80.md).



<a name="loioa8fe3eeb0f2244c6b04edfdfbd040987__context_o5n_sfm_pgc"/>

## Context

Cloud Identity Services have exposed the [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview), [Corporate Identity Providers API](https://api.sap.com/api/SCI_IdentityProvider_Directory/overview), and [SAP Cloud Identity Services Application Directory](https://api.sap.com/api/SCI_Application_Directory/overview) as provided APIs for the Administration Console application. These APIs can be used for principal propagation. For more information, see [Consuming APIs from Other Applications](consuming-apis-from-other-applications-29e204d.md).

> ### Note:  
> Tenant administrators with **Manage Users** and **Manage Groups** roles have full access to the [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview). For all other users, the [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview) supports *GET* and *PATCH* operations about the user for whom the token is issued, and the following attributes of the user can be returned or updated:
> 
> -   `urn:ietf:params:scim:schemas:core:2.0:User:locale`
> -   `urn:ietf:params:scim:schemas:extension:sap:2.0:User:localeSettings.currency`
> -   `urn:ietf:params:scim:schemas:extension:sap:2.0:User:termsOfUse`
> -   `urn:ietf:params:scim:schemas:extension:sap:2.0:User:privacyPolicy`



## Procedure

1.  Develop your consumer application to call the `/oauth2/token` endpoint of Identity Authentication with the respective dependency name.

    > ### Note:  
    > The available names are: `scim`, `identityproviders`, `applications`.

    **Example: Principal Propagation:**

    A consumer application \(client ID 8bbc6f92-0222-46f1-b9c5-b2b48825e78b\) has a dependency to the Administration Console application acting as a provider application \(client ID 09b90b70-3e4c-4fbc-b4ac-ef66848b7fbc\) named `applications`. The application calls the `/oauth2/token` endpoint with its client ID and the `resource` parameter with the dependency name used to identify the API that the consumer application consumes.

    ```
    curl $iashost/oauth2/token  -X POST \
    						-H 'Content-Type: application/x-www-form-urlencoded' \
    						-H 'Accept: application/json' \
    						-d "client_id=8bbc6f92-0222-46f1-b9c5-b2b48825e78b" \
    						-d "client_secret=$secret" \
    						-d "grant_type=urn%3Aietf%3Aparams%3Aoauth%3Agrant-type%3Ajwt-bearer" \
    						-d "assertion=$BEARERTOKEN" \
    						-d "resource=urn:sap:identity:application:provider:name:applications"
    ```

    Identity Authentication returns a token with the access control for the API and audience claim. The audience claim contains the client ID of the provider application. The following is an example of a token with the relevant claims.

    ```
    {
    							"ias_apis": [
    							"applications"
    							],   
    						"sub": "P123456",
    						"mail": "donna.moore@example.com",
    						"last_name": "Moore",
    						"aud": "09b90b70-3e4c-4fbc-b4ac-ef66848b7fbc", 
    						"scim_id": "1a2345bc-4f6b-456b-9bfb-5d58beb97fb7",
    						"user_uuid": "1a2345bc-4f6b-456b-9bfb-5d58beb97fb7",
    						"azp": "8bbc6f92-0222-46f1-b9c5-b2b48825e78b",
    						"first_name": "Donna",
    						…
    						}
    ```

2.  Send the token to the API endpoint of the provider application.


**Related Information**  


[Consuming APIs from Other Applications](consuming-apis-from-other-applications-29e204d.md "Applications sometimes need to propagate principals or have technical communication arrangements between them. To enable OpenID Connect (OIDC) applications to consume the APIs of other applications, the developer defines API permission groups for a provider application, which a consumer application can consume through a defined dependency.")

