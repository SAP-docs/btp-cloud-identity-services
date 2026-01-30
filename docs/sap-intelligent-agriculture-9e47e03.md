<!-- loio9e47e033b01f4dc993fd2af08776f15f -->

# SAP Intelligent Agriculture

Follow this procedure to set up SAP Intelligent Agriculture as a source system.



<a name="loio9e47e033b01f4dc993fd2af08776f15f__prereq_zxm_qw3_pzb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have onboarded your SAP Intelligent Agriculture tenant as described in the [Onboarding with the SAP BTP Cockpit](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/ba2d9265332a4682b019b92689500fa3/0ad81c4430c54cac8746ebe44ec5b850.html) section of the *Administration Guide for SAP Intelligent Agriculture*.

-   You have OAuth credentials for SAP Intelligent Agriculture. For more information, see: [Getting the Credentials from the SAP Intelligent Agriculture Instance](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/724d45c4d2934012a35cc9982b81d9a8/9cbec11fa6434df396cfc918aed7ecde.html#getting-the-credentials-from-the-sap-intelligent-agriculture-instance).




## Context

SAP Intelligent Agriculture enables agribusinesses to sustainably increase farming efficiency by digitizing their farming processes and services from plan-to-harvest, taking advantage of data science and machine learning capabilities.

After fulfilling the prerequisites, follow the procedure below to create a source SAP Intelligent Agriculture system to read users and groups.

These source systems consume SCIM 2.0 API provided by SAP Intelligent Agriculture.



<a name="loio9e47e033b01f4dc993fd2af08776f15f__steps_b2z_wmx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Intelligent Agriculture* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Choose the *Properties* tab to configure the connection settings for your system.

    > ### Note:  
    > If your Identity Provisioning tenant is running on SAP BTP, Neo environment, you can create a [connectivity destination](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/72696d6d06c0490394ac3069da600278.html) in your subaccount in the SAP BTP cockpit, and then select it from the *Destination Name* combo box in your Identity Provisioning User Interface.
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
    
    Enter the URL related to your SAP Intelligent Agriculture system, in format: `https://*.prod-<region>.ia.agribusiness.cloud.sap` 

    , where *\*.* is the name of your subaccount.

    For example: `https://custom-domain.prod-eu10.ia.agribusiness.cloud.sap`
    
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
    
    Enter: *BasicAuthentication*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the OAuth Client Id, created for your SAP Intelligent Agriculture instance \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, created for your SAP Intelligent Agriculture instance \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Intelligent Agriculture instance, in format: `https://<TENANT>.authentication.<REGION>.hana.ondemand.com/oauth/token` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ia.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Intelligent Agriculture groups matching the filter expression will be read.

    **Possible values:**

    -   *intagri\_Data\_Scientist*

    -   *intagri\_Farm\_Manager*

    -   *intagri\_Operator*

    -   *intagri\_Operations\_Planner*

    -   *intagri\_Master\_Data\_Manager*

    -   *intagri\_Administrator*


    For example: *displayName eq "intagri\_Master\_Data\_Manager"*

    For more information, see [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ia.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Intelligent Agriculture users matching the filter expression will be read.

    For example: *userName eq "Smith.J"*

    For more information, see [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`ia.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Intelligent Agriculture groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `IA_`

    You can use the example value or provide your own.

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Intelligent Agriculture source system and will be provisioned to the target system with the following name pattern: <code>IA_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Intelligent Agriculture groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Intelligent Agriculture groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Intelligent Agriculture* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Intelligent Agriculture system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Intelligent Agriculture SCIM API](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/724d45c4d2934012a35cc9982b81d9a8/1919b94dc2c84711ab65fd63002b9bce.html)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "($.userName != 'ANONYMOUS' && $.userUuid != 'ANONYMOUS' && $.externalId != 'ANONYMOUS' )",
    > //When a user is deleted from the SAP Intelligent Agriculture system, its unique attributes are set to value 'ANONYMOUS'. Such users are skipped by the read provisioning jobs.
    > 
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true
    >             },
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
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.userUuid",
    >                 "targetPath": "$.userUuid"
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.emails[0].value",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true,
    >                 "functions": [
    >                     {
    >                         "function": "concatString",
    >                         "condition": "'%ia.group.prefix%' !== 'null'",
    >                         "applyOnElements": true,
    >                         "applyOnAttribute": "display",
    >                         "prefix": "%ia.group.prefix%"
    >                     }
    >                 ]
    >             }
    >         ]
    >     },
    >     "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "function": "concatString",
    >             "condition": "'%ia.group.prefix%' !== 'null'",
    >             "prefix": "%ia.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    >       },
    >       {
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio9e47e033b01f4dc993fd2af08776f15f__postreq_emv_vdb_kdb"/>

## Next Steps

1.  Before starting a provisioning job, you can first subscribe to the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during your jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
2.  Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

