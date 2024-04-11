<!-- loioe5953413932f4eedac25ad902cc2a09e -->

# Quick Start for Dependent Applications

When working on an application, you want to test your APIs, but don't have a consumer application to integrate with. From your *Provided APIs*, create a dependent application or create a dependency with an existing application.



<a name="loioe5953413932f4eedac25ad902cc2a09e__prereq_tfj_dym_s1c"/>

## Prerequisites

You have created at least one API permission group.

For more information, see [Provide APIs for Consumption by Other Applications](provide-apis-for-consumption-by-other-applications-9d2fe83.md).



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
    > If you chose to create a new application and a secret, a dialog summarizes the new dependency. Copy the client credentials to a safe location. You can navigate directly to the new application configuration from the dialog.




<a name="loioe5953413932f4eedac25ad902cc2a09e__postreq_v1w_rw3_m1c"/>

## Next Steps

With the dependency name and client credentials, the consumer application can call the `/token` endpoint of Identity Authentication.

For more information, see [Consume an API from Another Application](consume-an-api-from-another-application-9675b64.md).

