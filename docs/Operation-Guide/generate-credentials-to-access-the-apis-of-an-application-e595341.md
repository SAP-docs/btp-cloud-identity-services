<!-- loioe5953413932f4eedac25ad902cc2a09e -->

# Generate Credentials to Access the APIs of an Application

When integrating applications, create API credentials for the consumer application. From your *Provided APIs*, create a dependent application or create a dependency with an existing application.



<a name="loioe5953413932f4eedac25ad902cc2a09e__prereq_tfj_dym_s1c"/>

## Prerequisites

You have created at least one API permission group.

For more information, see [Provide APIs for Consumption by Other Applications](../Development/provide-apis-for-consumption-by-other-applications-9d2fe83.md).



<a name="loioe5953413932f4eedac25ad902cc2a09e__context_lsz_2t1_fbc"/>

## Context

The main use cases for this method are as follows:

-   You want to integrate an application, which otherwise isn't aware of SAP Cloud Identity Services, such as a non-SAP application. The application requires OAuth credentials, which you provide with this procedure. These credentials enable you to integrate this non-SAP application with the provider application.

-   As a developer of a provider application, you want to test your APIs, but don't have a consumer application to integrate with.




## Procedure

1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*

2.  Choose the provider application.

3.  Choose the *Trust* tab.

4.  Under *Application APIs*, choose *Provided APIs*.

5.  Under *Dependent Applications*, choose *Create*.

    > ### Note:  
    > If you haven't configured an API permission group, the *Dependent Applications* section doesn't appear.

6.  Enter the required data.

    1.  Enter a unique name for the dependency.

    2.  Select the API that the consumer application consumes.

    3.  Decide whether you want to create a new application or use an existing one.

        -   Create a new application, to create a consumer you can use to test your provided API with. Enable *Generate Secret* to generate client credentials for the new application.

        -   Use an existing application to integrate an existing consumer with your provider.



7.  Choose *Create*.

    > ### Remember:  
    > If you chose to create a new application and a secret, a dialog summarizes the new dependency. Copy the *Client ID* and *Client Secret* to a safe location. Also copy the *Resource*. You provide this information to the consumer application so it can get a token for the provider application.
    > 
    > For example, using the client credentials flow for a technical communication arrangement, the consumer application can call the `/token` endpoint of Identity Authentication. The service returns a token that the application uses to call the APIs of the provider application. The following is a cURL example of such a call.
    > 
    > ```
    > curl  $iashost/oauth2/token -X POST \
    >    -H 'Content-Type: application/x-www-form-urlencoded' \
    >    -H 'Accept: application/json' \
    >    -d "client_id=3ab1ba0e-c573-4ad5-20a4-28aa4e587a19" \
    >    -d "client_secret=$secret" \
    >    -data-urlencode 'grant_type=client_credentials' \
    >    -data-urlencode 'resource=urn:sap:identity:application:provider:name:techDependency'
    > 
    > ```
    > 
    > For more information, see [Consume an API from Another Application](../Development/consume-an-api-from-another-application-9675b64.md).
    > 
    > You can navigate directly to the new application configuration from the dialog.


