<!-- loioc5af5f01352a411d93f554a2a1357463 -->

# SAP Jam Collaboration

Follow this procedure to set up SAP Jam Collaboration as a target system.



## Prerequisites

You get OAuth credentials for SAP Jam Collaboration. If your SAP Jam tenant is of "SCIM provisioning" type, an OAuth client is automatically created for it, with the name **SCIM API Client**. To find this client:

1.  Go to the SAP Jam Collaboration admin panel.
2.  Choose *Integrations* \> *OAuth Clients*.
3.  For *SCIM API Client*, choose *View*.
4.  Save the *Key* and *Secret* values – you'll need them later while configuring your SAP Jam Collaboration provisioning system.

To learn more, see: [SAP Jam: Add an OAuth Client](https://help.sap.com/viewer/9981b6fb8453459d8103a04d674ebe0f/LATEST/en-US/5eec65a0e0264ef693e8af8732926b60.html)



<a name="loioc5af5f01352a411d93f554a2a1357463__context_zhf_2vx_ybb"/>

## Context

After fulfilling the prerequisites, follow the procedure below to create a target SAP Jam Collaboration system to provision users and groups.

These target systems consume SCIM 2.0 API provided by SAP Jam Collaboration.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Jam Collaboration* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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

    When **set in the target system**, only groups containing the `SJC_` prefix in their display name will be provisioned to SAP Jam Collaboration. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Jam Collaboration.
    
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
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.groups`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of groups to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of groups, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.users`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of users to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of users, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Jam Collaboration* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Jam Collaboration. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Business Accelerator Hub: SAP Jam Collaboration](https://api.sap.com/package/SAPJam?section=Artifacts)

    -   **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target entity. If the entity has e-mail addresses, the first entry will be marked as primary.
    -   **User off-boarding**:
        -   Users can be deleted from the SAP Jam Collaboration system via the SCIM REST API. For more information, see [SCIM: Deleting Resources](https://tools.ietf.org/html/rfc7644#section-3.6).
        -   Users can be deactivated by setting the value of their `active` attribute to **false**. For more information, see [SCIM: Singular Attributes](https://tools.ietf.org/html/rfc7643#section-4.1.1) 


    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$",
    >                 "targetPath": "$"
    >             },
    >             {
    >                 "targetPath": "$.id",
    >                 "type": "remove"
    >             },
    >             {
    >                 "targetPath": "$.externalId",
    >                 "type": "remove"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id",
    >                 "scope": "deleteEntity"
    >             },
    >             {
    >                 "condition": "$.emails[0].length() > 0",
    >                 "constant": true,
    >                 "targetPath": "$.emails[0].primary"
    >             },
    >             {
    >                 "constant": false,
    >                 "targetPath": "$.active",
    >                 "scope": "deleteEntity"
    >             },
    >             {
    >                 "targetPath": "$.locale",
    >                 "type": "remove"
    >             },
    >             {
    >                 "condition": "($.locale EMPTY false) && ($.addresses[?(@.type == 'work')].country EMPTY false)",
    >                 "sourcePath": "$.locale",
    >                 "targetPath": "$.locale",
    >                 "functions": [
    >                     {
    >                         "function": "toLowerCaseString"
    >                     },
    >                     {
    >                         "function": "concatString",
    >                         "suffix": "_"
    >                     },
    >                     {
    >                         "function": "concatString",
    >                         "suffix": "$.addresses[?(@.type == 'work')].country"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "functions": [
    >                     {
    >                         "function": "resolveEntityIds"
    >                     }
    >                 ]
    >             }
    >         ]
    >     },
    >     "group": {
    >         "ignore": true,
    >         "condition": "('%jam.group.prefix%' === 'null') || ($.displayName =~ /%jam.group.prefix%.*/)",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$",
    >                 "targetPath": "$"
    >             },
    >             {
    >                 "targetPath": "$.id",
    >                 "type": "remove"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "('%jam.group.prefix%' !== 'null') && (@ =~ /%jam.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%jam.group.prefix%",
    >                         "replacement": ""
    >                     }
    >                 ]
    >             },
    >             {
    >                 "targetPath": "$.members",
    >                 "type": "remove"
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]",
    >                 "functions": [
    >                     {
    >                         "type": "resolveEntityIds"
    >                     }
    >                 ]
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loioc5af5f01352a411d93f554a2a1357463__postreq_emv_vdb_kdb"/>

## Next Steps

1.  Before starting a provisioning job, you can first subscribe to the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during your jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
2.  Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

> ### Restriction:  
> Bear in mind the following limitations for the number of sent requests during a provisioning job:
> 
> -   The **SAP Jam SCIM API** allows up to 13,000 requests per hour and up to 200 requests per minute.
> -   The Identity Provisioning service can handle the 200 requests per minute limit. If more requests are sent during the minute, the service will "wait" until it can execute them.

