<!-- loioeeeb2464be88423aaefc06c63e720ceb -->

# SAP Jam Collaboration

Follow this procedure to set up SAP Jam Collaboration as a source system.



<a name="loioeeeb2464be88423aaefc06c63e720ceb__prereq_ih3_smx_rdb"/>

## Prerequisites

You get OAuth credentials for SAP Jam Collaboration. If your SAP Jam tenant is of "SCIM provisioning" type, an OAuth client is automatically created for it, with the name **SCIM API Client**. To find this client:

1.  Go to the SAP Jam Collaboration admin panel.
2.  Choose *Integrations* \> *OAuth Clients*.
3.  For *SCIM API Client*, choose *View*.
4.  Save the *Key* and *Secret* values – you'll need them later while configuring your SAP Jam Collaboration provisioning system.

To learn more, see: [SAP Jam: Add an OAuth Client](https://help.sap.com/viewer/9981b6fb8453459d8103a04d674ebe0f/LATEST/en-US/5eec65a0e0264ef693e8af8732926b60.html)



<a name="loioeeeb2464be88423aaefc06c63e720ceb__context_zhf_2vx_ybb"/>

## Context

After fulfilling the prerequisites, follow the procedure below to create a source SAP Jam Collaboration system to read users and groups.

These source systems consume SCIM 2.0 API provided by SAP Jam Collaboration.



<a name="loioeeeb2464be88423aaefc06c63e720ceb__steps_b2z_wmx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Jam Collaboration* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Enter the URL related to your SAP Jam system, in format: `https://<SAP_Jam_datacenter>.sapjam.com`

    For example: *https://jam4.sapjam.com*
    
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
    
    Enter the OAuth client key, created for your SAP Jam tenant \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth client secret, created for your SAP Jam tenant \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Jam instance, in format: `https://<SAP_Jam_datacenter>/api/v1/auth/token` 

    For example: *https://jam4.sapjam.com/api/v1/auth/token*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `jam.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Jam Collaboration groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `SJC_`

    You can use the example value or provide your own.

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Jam Collaboration source system and will be provisioned to the target system with the following name pattern: <code>SJC_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Jam Collaboration groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Jam Collaboration groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Jam Collaboration* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Jam Collaboration system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Business Accelerator Hub: SAP Jam Collaboration](https://api.sap.com/package/SAPJam?section=Artifacts)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "targetPath": "$",
    >                 "sourcePath": "$"
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "correlationAttribute": true
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
    >             }
    >         ]
    >     },
    >     "group": {
    >         "ignore": true,
    >         "mappings": [
    >             {
    >                 "targetPath": "$",
    >                 "sourcePath": "$"
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "'%jam.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "prefix": "%jam.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$.meta"
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loioeeeb2464be88423aaefc06c63e720ceb__postreq_emv_vdb_kdb"/>

## Next Steps

1.  Before starting a provisioning job, you can first subscribe to the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during your jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
2.  Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

