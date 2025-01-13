<!-- loioc4d3fd59a4dd4e7eac783107991afb57 -->

# SAP Fieldglass

Follow this procedure to set up a target connector for SAP Fieldglass.



<a name="loioc4d3fd59a4dd4e7eac783107991afb57__prereq_wvj_nhz_fpb"/>

## Prerequisites

You have created an API application key and a web service. To do that, follow the steps on page: [Create API Application Key or Web Service](https://help.sap.com/docs/SAP_FIELDGLASS_INTEGRATION/73c0a1be6aaa46ef9b66b1c3f28a77f4/ea00dcbe002748d09cc1fef57668bcc1.html) and [Web Services Setup](https://help.sap.com/docs/SAP_FIELDGLASS_INTEGRATION/73c0a1be6aaa46ef9b66b1c3f28a77f4/b61abedb5df34f138d9e479d15f97364.html?locale=en-US)

You will need the values of *Virtual Person Name \(Username\)* and *License Key* for the configuration of your target system \(**step 3** below\).



## Context

After fulfilling the prerequisites, follow the procedure below to add a target system for SAP Fieldglass to write users to it. This target system consumes SCIM 2.0 API provided by SAP Fieldglass.

> ### Note:  
> The system transformation supports groups but cannot directly create new groups. However, you can map groups from the source system to groups from SAP Fieldglass by display name.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Fieldglass* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify your SAP Fieldglass environment URL.

    For example: *https://abc123.fgvms.com*
    
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
    
    Enter your *Virtual Person Name \(Username\)* – see the **Prerequisites** section above.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter your *License Key* – see the **Prerequisites** section above.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter your OAuth token URL in the following format:

    <code>https://<i class="varname">&lt;Environment_URL&gt;</i>/api/oauth2/v2.0/token</code>

    For example: *https://abc123.fgvms.com/api/oauth2/v2.0/token*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)

    `fg.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Fieldglass groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `FG_`

    You can use the example value or provide your own.

    -   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Fieldglass source system and will be provisioned to the target system with the following name pattern: <code>FG_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Fieldglass groups in the target system will be distinguished from groups provisioned from other applications.

        If the property is not set, the SAP Fieldglass groups will be read and provisioned to the target system with their actual display names.

    -   When **set in the target system**, only groups containing the `FG_` prefix in their display name will be provisioned to SAP Fieldglass. Groups without this prefix in the display name won't be provisioned.

        If the property is not set, all groups will be be provisioned to SAP Fieldglass.



    
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

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Fieldglass* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Fieldglass. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Business Accelerator Hub: SAP Fieldglass](https://api.sap.com/package/FieldglassAPI/rest)

    -   **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target entity. If the entity has e-mail addresses, the first entry will be marked as primary.
    -   **User off-boarding** – Users can be deleted from the target system. Depending on the implementation, this could be done through a user interface \(if such exists\) or the SCIM REST API. Users could be deactivated, depending on the SAP Fieldglass system implementation. The SCIM core schema defines an attribute “**active**”, whose definition depends on the service provider. For more information, see [SCIM: Singular Attributes](https://tools.ietf.org/html/rfc7643#section-4.1.1) 

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "scope": "createEntity",
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.honorificPrefix",
    >         "targetPath": "$.name.honorificPrefix",
    >         "condition": "$.name.honorificPrefix IN ['Mr.', 'Mrs.', 'Ms.', 'Dr.']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.title",
    >         "targetPath": "$.title",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.locale",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.emails[0].value"
    >       },
    >       {
    >         "optional": true,
    >         "defaultValue": "work",
    >         "sourcePath": "$.emails[0].type",
    >         "targetPath": "$.emails[0].type"
    >       },
    >       {
    >         "defaultValue": true,
    >         "optional": true,
    >         "sourcePath": "$.emails[0].primary",
    >         "targetPath": "$.emails[0].primary"
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "optional": true,
    >         "targetPath": "$.timezone"
    >       },
    >       {
    >         "sourcePath": "$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.addresses"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >         "targetPath": "$.schemas[1]"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "optional": true
    >       },
    >       {
    >         "scope": "createEntity",
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "optional": true
    >       },
    >       {
    >         "scope": "createEntity",
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       }
    >     ]
    >   },
    > 
    > // You cannot create groups but instead, you can map groups from the source system to groups from SAP Fieldglass by display name. 
    > // The group deletion operation is skipped. 
    > 
    >   "group": {
    >     "skipOperations": [
    >       "delete"
    >     ],
    >     "condition": "('%fg.group.prefix%' === 'null') || ($.displayName =~ /%fg.group.prefix%.*/)",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >             {
    >                 "condition": "('%fg.group.prefix%' !== 'null') && (@ =~ /%fg.group.prefix%.*/)",
    >                 "function": "replaceFirstString",
    >                 "regex": "%fg.group.prefix%",
    >                 "replacement": ""
    >             }
    >         ]
    >       },
    >       {
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true,
    >         "sourcePath": "$.members[*].value",
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "function": "resolveEntityIds"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       }
    >     ]
    >   }
    > }
    > 
    > ```

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loioc4d3fd59a4dd4e7eac783107991afb57__postreq_lvw_bqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

