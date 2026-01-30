<!-- loiofd9895dcbcc84e47b1378cda4e26372c -->

# SAP Advanced Financial Closing

Follow this procedure to set up a SAP Advanced Financial Closing as а source system.



<a name="loiofd9895dcbcc84e47b1378cda4e26372c__prereq_gfl_gvx_rdb"/>

## Prerequisites

You have created an instance and generated a service key for the standard service plan of SAP Advanced Financial Closing. For more information, see: [How to Manage User Access Using the SCIM API Provided](https://help.sap.com/docs/AFC/b021b34a2c2d4943abc3a31008c7bdfc/49376ed8c58f41e0b84d141824698721.html).

The service key contains the API URL and the OAuth credentials \(`clientid` and `clientsecret`\) under the `uaa` property.



## Context

SAP Advanced Financial Closing allows you to define, automate, process, and monitor the financial closing tasks for the entities of your organization. It is an SAP BTP application that runs in an SAP BTP subaccount.

You can use Identity Provisioning to configure SAP Advanced Financial Closing as a source system where you can read users, user groups and user roles from, and provision them to a target system.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Advanced Financial Closing* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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

    Value
    
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
    
    Enter the URL provided by the service key under *endpoints* \> *scim2* without adding the path information.

    For example: `https://afc-production-afc-api.cfapps.eu10.hana.ondemand.com`
    
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
    
    Enter the user ID provided by the service key under *uaa* \> *clientid*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password provided by the service key under *uaa* \> *clientsecret*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL provided by the service key of your SAP Advanced Financial Closing instance. It follows the pattern: <code><i class="varname">&lt;uaa.url&gt;</i>/oauth/token</code>, where:

    -   *<uaa.url\>* is the URL provided by the service key under *uaa* \> *url*.

    -   `/oauth/token` is the suffix you need to add.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.afc.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Advanced Financial Closing users matching the filter expression will be read.

    Supported operators: `eq` \(equal\), `sw` \(starts with\) and `co` \(contains\)

    For example:

    -   *userName eq "Julie Armstrong"*

    -   *emails eq "julie.armstrong@example.com"*

    -   *name.familyName sw "A"*

    -   *name.givenName co "Ju"*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.afc.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Advanced Financial Closing groups matching the filter expression will be read.

    Supported operators: `eq` \(equal\), `sw` \(starts with\) and `co` \(contains\)

    For example: *displayName eq "Administrators"*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the SAP Advanced Financial Closing source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Advanced Financial Closing. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    [How to Manage User Access Using the SCIM API Provided](https://help.sap.com/docs/AFC/b021b34a2c2d4943abc3a31008c7bdfc/49376ed8c58f41e0b84d141824698721.html)

    [SAP Business Accelerator Hub: SAP Advanced Financial Closing](https://api.sap.com/package/SAPS4HANACloudforadvancedfinancialclosing/rest)

    > ### Note:  
    > When configuring SAP Advanced Financial Closing as a source system, there may be a mismatch between optional user attributes in the source system and required user attributes in the target system. For example, the email is an optional attribute in SAP Advanced Financial Closing but a required one in Identity Authentication. In such cases, you need to review and adapt your source and/or target system transformations and configurations to reflect your needs.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.name.formatted",
    >         "targetPath": "$.name.formatted",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.locale",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >           {
    >             "condition": "'%s4hana.afc.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "display",
    >             "prefix": "%s4hana.afc.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "targetPath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "targetPath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "'%s4hana.afc.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%s4hana.afc.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >           {
    >             "condition": "'%s4hana.afc.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%s4hana.afc.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    >       }
    >     ]
    >   }
    > }
    > ```

6.  [Target Systems](target-systems-ab3f641.md)




<a name="loiofd9895dcbcc84e47b1378cda4e26372c__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

