<!-- loioe3efade8dd1844cea5a8fa4a729b02e1 -->

# Configure Shared Authorization Dependencies

Enable a consumer application to receive authorization group information from a provider application as claims in its access token. With this configuration, the access token of the consumer application includes the authorization groups that the authenticated user holds in the provider application.



## Prerequisites

-   The provider application has application-specific groups of type authorization.

-   You know the display name or application ID of the provider application in your SAP Cloud Identity Services tenant.

-   The token claim has been configured by mapping the `dependencyGroups` user attribute to a claim name required by the consumer application.

    To check look for *<consumer-claim-name\>* mapped to a self-defined attribute in the application configuration of the consumer application. For more information about self-defined attributes, see [User Attributes](user-attributes-ed2797d.md).

    If there is no mapping or you haven't deployed the application yet, use one of the following methods:

    -   When the provider application was deployed, an entry was added to the `assertion-attributes` property in the Identity service instance parameters for the provider application.

        ```
        {
          "assertion-attributes": {
            "<consumer-claim-name>": "dependencyGroups"
          }
        }
        ```

        For more information, refer to the documentation of the consumer and provider applications.

    -   Send a PATCH request to the Applications REST API of your SAP Cloud Identity Services tenant:

        ```
        PATCH ${iasUrl}/Applications/v1/${consumerAppId}
        Content-Type: application/json
        
        {
          "operations": [
            {
              "op": "add",
              "path": "/urn:sap:identity:application:schemas:extension:sci:1.0:Authentication/assertionAttributes",
              "value": [
                {
                  "assertionAttributeName": "<consumer-claim-name>",
                  "userAttributeName": "dependencyGroups"
                }
              ]
            }
          ]
        }
        ```

        > ### Caution:  
        > If you set assertion-attributes through the Identity service instance parameters or use the `replace` operation when using the REST API, your map fully replaces the default set of five user profile claims \(`groups`, `given_name`, `family_name`, `email`, `user_uuid`\). To keep these claims, restate them alongside your new entry.


    > ### Tip:  
    > Replace *<consumer-claim-name\>* with the claim name that the consumer application reads from the token, for example, `dependency_groups`.
    > 
    > For more information, refer to the documentation of the consumer and provider applications.




## Context

Use shared authorization dependencies when a consumer application \(such as a portal, shell, or assistant\) needs to know what a user is authorized to do in a provider application, without calling that application directly. The provider application's application-specific groups for that user are included as a claim in the consumer's access token. The consumer application reads this claim and uses it to tailor its behavior, for example, to show or hide tiles or features.

The dependency is one-directional: only the consumer's tokens carry the claim. No configuration is required on the provider application. You can add up to 20 shared authorization dependencies per consumer application.

The claim appears only in access tokens, not in ID tokens.



## Procedure

1.  Add the shared authorization dependency in the administration console.

    1.  In the administration console for SAP Cloud Identity Services, choose *Applications and Resources* \> *Applications*.

    2.  Choose the consumer application.

    3.  Choose the *Trust* tab.

    4.  Under *Application APIs*, choose *Dependencies*.

    5.  Choose *Shared Authorizations*.

    6.  Choose *Add* and select the provider application.

    7.  Save your entries.


2.  Assign the application-specific groups of the provider application to the users who require authorizations.

    To determine which groups to assign, refer to the documentation of the consumer and provider applications.

    For more information about application-specific groups, see [Groups](../groups-d93be69.md).




## Results

When an authenticated user obtains an access token for the consumer application, the token includes a claim named *<consumer-claim-name\>* that contains a map of the authorization groups that the user holds in the configured provider applications.

**Related Information**  


[Groups](../groups-d93be69.md "SAP Cloud Identity Services offers groups to organize users based on common characteristics, authorization, or application. Use them to efficiently manage user access and permissions within your organization's SAP Cloud Identity Services environment.")

[Claims of SAP Cloud Identity Services OAuth Tokens](claims-of-sap-cloud-identity-services-oauth-tokens-7bf3c18.md "Understanding OAuth token claims helps you to achieve secure and efficient authentication and authorization. This knowledge helps you use tokens correctly, reduce security risks, and maintain trust in your system.")

