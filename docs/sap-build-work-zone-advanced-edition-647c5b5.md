<!-- loio647c5b5b59df4669ab21cc95d7b5fd1c -->

# SAP Build Work Zone, advanced edition

Follow this procedure to set up SAP Build Work Zone, advanced edition as a source system.



<a name="loio647c5b5b59df4669ab21cc95d7b5fd1c__prereq_ih3_smx_rdb"/>

## Prerequisites

You have OAuth credentials for SAP Build Work Zone, advanced edition. To learn how, see [SAP Build Work Zone, advanced edition: Add an OAuth Client](https://help.sap.com/viewer/b03c84105ff74f809631e494bd612e83/Cloud/en-US/b3c804e1f999448b8011a475fea1da6c.html)



<a name="loio647c5b5b59df4669ab21cc95d7b5fd1c__context_zhf_2vx_ybb"/>

## Context

After fulfilling the prerequisites, follow the procedure below to create a source SAP Build Work Zone, advanced edition system to read users and groups.

These source systems consume SCIM 2.0 API provided by SAP Build Work Zone, advanced edition.



<a name="loio647c5b5b59df4669ab21cc95d7b5fd1c__steps_b2z_wmx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Build Work Zone, advanced edition* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP Build Work Zone, advanced edition and configure the authentication method \(basic or OAuth certificate-based\).

    > ### Note:  
    > We recommend that you use OAuth certificate-based authentication in the regions where it is supported by SAP Build Work Zone, advanced edition. This authentication method is supported for subaccounts created on the recommended data centers for new customers according to the [SAP Build Work Zone, advanced edition documentation](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/prerequisites#create-a-subaccount).

    1.  In your newly added SAP Build Work Zone, advanced edition source system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](Operation-Guide/generate-and-manage-certificates-for-outbound-connection-76867db.md).

        Skip step **a.** if you want to use basic authentication.

        The next steps are performed in the SAP Build Work Zone, advanced edition Admin Console and are relevant for certificate-based authentication only.

    2.  Login to the SAP Build Work Zone, advanced edition Admin Console and execute substep *2. f. iii. Use X.509 Certificate-Based Authentication* from *Step 3: Configure the Identity Authentication service and the Identity Provisioning service* in [Option 1: Create a new tenant](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/run-configurator?locale=en-US#option-1%3A-create-a-new-tenant).


5.  Choose the *Properties* tab to configure the connection settings for your system.

    > ### Note:  
    > If your tenant is running on SAP BTP, Neo environment, you can create a [connectivity destination](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/72696d6d06c0490394ac3069da600278.html) in your subaccount in the SAP BTP cockpit, and then select it from the *Destination Name* combo box in your Identity Provisioning User Interface.
    > 
    > If one and the same property exists both in the cockpit and in the *Properties* tab, the value set in the *Properties* tab is considered with higher priority.
    > 
    > We recommend that you use the *Properties* tab. Use a connectivity destination only if you need to reuse one and the same configuration for multiple provisioning systems.

    **Mandatory Properties**


    <table>
    <tr>
    <th valign="top">

    Property Name
    
    </th>
    <th valign="top">

    Description & Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `Type`
    
    </td>
    <td valign="top">
    
    Enter: *HTTP*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    Enter the URL related to your SAP Build Work Zone, advanced edition system, in format: `https://<account><sap_wz_domain>.workzone.ondemand.com`

    For example: *https://mytenant.mydomain123.workzone.ondemand.com*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Enter: *Internet*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    Enter your authentication method:

    -   *BasicAuthentication*

    -   *ClientCertificateAuthentication*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    Enter the OAuth client key, created for your SAP Build Work Zone, advanced edition tenant \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    \(Credential\) Enter the OAuth client secret, created for your SAP Build Work Zone, advanced edition tenant \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Build Work Zone, advanced edition instance, based on the configured authentication method:

    -   *BasicAuthentication* - `https://<account><sap_wz_domain>.workzone.ondemand.com/api/v1/auth/token` 

        For example: *https://myaccountmydomain123.workzone.ondemand.com/api/v1/auth/token*



    -   *ClientCertificateAuthentication* - `https://<company_uuid>.api-<region_host>.dws.workzone.ondemand.com/api/v2/auth/token` 

        > ### Note:  
        > The `api-` prefix before `<region_host>` is necessary for using *ClientCertificateAuthentication* authentication.

        For example: *https://mycompanyuuid123.api-eu-20.dws.workzone.ondemand.com/api/v2/auth/token*





    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `client_id`
    
    </td>
    <td valign="top">
    
    Valid if *ClientCertificateAuthentication* is configured as authentication method.

    Enter the OAuth Client id used for access token retrieval.
    
    </td>
    </tr>
    <tr>
    <td valign="top" align="center" colspan="2">
    
    **Optional Properties**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `workzone.group.filter`
    
    </td>
    <td valign="top">
    
    Enter a SCIM-based search criteria for filtering groups.

    Example: **displayName eq "Project123"** 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `workzone.user.filter`
    
    </td>
    <td valign="top">
    
    Enter a SCIM-based search criteria for filtering users.

    Example: **userName eq "SmithJ" and addresses.country eq "US"** 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.failed.request.retry.attempts`
    
    </td>
    <td valign="top">
    
    Predefined value: *2*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.failed.request.retry.attempts.interval`
    
    </td>
    <td valign="top">
    
    Predefined value: *30*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

6.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Build Work Zone, advanced edition* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Build Work Zone, advanced edition system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Build Work Zone SCIM API](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/user-and-user-list-provisioning-using-scim-api)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary== true)].value",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$.meta"
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.title",
    >                 "targetPath": "$.title",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.locale",
    >                 "targetPath": "$.locale",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "optional": true,
    >                 "targetPath": "$.timezone"
    >             },
    >             {
    >                 "sourcePath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.addresses"
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true
    >             }   
    >         ]
    >     },
    >     "group": {
    >         "ignore": true,
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']"
    >             }
    >         ]
    >     }
    > }
    > ```

7.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio647c5b5b59df4669ab21cc95d7b5fd1c__postreq_emv_vdb_kdb"/>

## Next Steps

1.  Before starting a provisioning job, you can first subscribe to the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during your jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
2.  Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

