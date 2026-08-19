<!-- loiocc35d85d445340ff86342f7ff0638852 -->

# Update Identity Authentication

Update the Identity Authentication connector to a new version.

Following the deprecation of the Identity Authentication SCIM API \(SCIM API v1\), the API will be decommissioned on **November 30, 2026**. You must migrate to its successor, the Identity Directory SCIM API \(SCIM API v2\). This migration requires updating all Identity Authentication provisioning systems \(source, target, and proxy\) from connector version 1 to connector version 2.

> ### Note:  
> Migrate each provisioning system separately and complete one migration before proceeding to the next.



## Procedure

1.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

    > ### Note:  
    > Repeat the steps below for each Identity Authentication source, target, and proxy system.

2.  From the list on the left, select your system of type *Identity Authentication*.
3.  Select the *Properties* tab and add the following property `ias.api.version`=2.

    > ### Note:  
    > The property prefix depends on the SCIM API version being used.
    > 
    > -   For SCIM API v2, property names use the `ias` prefix. For example: `ias.user.unique.attribute`
    > 
    > -   For SCIM API v1, property names use the `scim` prefix. For example: `scim.user.unique.attribute`

    When migrating from SCIM API v1 to SCIM API v2, ensure that all configuration properties using the `scim` prefix are updated to their corresponding `ias`-prefixed properties.

    In addition, configure the following Identity Provisioning properties:

    -   `ips.application.id`=*<application\_ID\>*

        The ID of the application created under *Applications & Resources* for the corresponding Identity Authentication provisioning system.

    -   `ips.delete.existedbefore.entities`=***true***

        This property must be set for all Identity Authentication target systems.


    For more information, see [List of Properties](../list-of-properties-d6f3577.md).

4.  Select the *Transformations* tab and update the user and group attribute mappings that have changed in SCIM API v2 as explained in [Attributes Mapping](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api?version=Cloud#attributes-mapping).

    > ### Example:  
    > Replace the `mailVerified` attribute from SCIM API v1 with `urn:ietf:params:scim:schemas:extension:sap:2.0:User.emails.verified`.

    In addition to updating existing mappings, review the default transformations delivered for SCIM API v2 and add newly supported attributes that are not present in your current configuration. The Identity Authentication connector documentation provides default transformation mappings for both SCIM API v1 and SCIM API v2.

    Compare the mappings and include the additional SCIM API v2 attributes required for your scenario.

    > ### Example:  
    > Examples of attributes that may need to be added when migrating to SCIM API v2 include:
    > 
    > > ### Code Syntax:  
    > > ```
    > > {
    > >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    > >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']",
    > >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    > >       },
    > >       {
    > >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    > >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    > >         "optional": true,
    > >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    > >       },
    > >       {
    > >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    > >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    > >         "optional": true,
    > >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    > >       },
    > >       {
    > >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    > >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']",
    > >         "optional": true,
    > >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    > >       },
    > >       {
    > >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    > >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalLocation']",
    > >         "optional": true,
    > >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalLocation']",
    > >         "scope": "createEntity"
    > >       }
    > > ```

    If your provisioning system uses customized transformations, manually compare them with the SCIM API v2 default transformations to ensure that both updated and newly supported attributes are included after the migration.

    For more information on the default transformations, see:

    -   [Identity Authentication source system](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/source-identity-authentication?version=Cloud)

    -   [Identity Authentication target system](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/target-identity-authentication?version=Cloud)

    -   [Identity Authentication proxy system](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/proxy-identity-authentication?version=Cloud)


5.  [Reset the system](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/reset-identity-provisioning-system?locale=en-US&state=DRAFT&version=Dev). This is necessary because it is assumed that you have already run provisioning jobs to the target systems.

6.  Save your changes and run a provisioning job.


