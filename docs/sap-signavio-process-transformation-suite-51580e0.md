<!-- loio51580e0b464a46868881039fafac8f8a -->

# SAP Signavio Process Transformation Suite

Follow this procedure to set up SAP Signavio Process Transformation Suite as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.



<a name="loio51580e0b464a46868881039fafac8f8a__context_y2y_nxx_rdb"/>

## Context

SAP Signavio Process Transformation Suite helps you understand, improve, and transform your business processes – fast and at scale – with a cloud-based process management platform.

You can use Identity Provisioning to configure SAP Signavio Process Transformation Suite as a target system where you can provision users and groups from source systems.

> ### Note:  
> The initial setup of SAP Signavio Process Transformation Suite is performed in the Service Provider Cockpit - a central system for operational processes like system provisioning. This setup includes configuring the connection and certificate-based authentication between Identity Provisioning and the SAP Signavio Process Transformation Suite. If any changes are needed, they must be made through a support incident.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Signavio Process Transformation Suite* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    The URL to the SCIM API of your SAP Signavio Process Transformation Suite system.
    
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
    
    Enter: *ClientCertificateAuthentication* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sig.tenant.id`
    
    </td>
    <td valign="top">
    
    The identifier of SAP Signavio Process Transformation Suite tenant
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sig.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    This property defines by which unique attribute\(s\) an existing user in the target system will be searched and resolved in case Identity Provisioning tries to provision a conflicting user.

    According to your use case and system type, choose how to set up this property:

    -   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
    -   Value = *userName, urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*. If the service finds an existing user with both these *userName* and *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

    **Possible values:**

    -   *userName*
    -   *userName, urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*

    Default value: *userName*
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Signavio Process Transformation Suite* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Signavio Process Transformation Suite system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Business Accelerator Hub: SAP Signavio Process Transformation Suite](https://api.sap.com/api/SCIMService/overview)

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Signavio Process Transformation Suite entity.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "($.emails EMPTY false) && isValidEmail($.emails[*].value) && (('%sig.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%sig.group.prefix%.*/)] empty false))",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value == []",
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value != []",
    >         "sourcePath": "$.emails[?(@.primary == true)].value",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "targetPath": "$.name.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.honorificPrefix",
    >         "targetPath": "$.name.honorificPrefix",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.honorificSuffix",
    >         "targetPath": "$.name.honorificSuffix",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.nickName",
    >         "targetPath": "$.nickName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.profileUrl",
    >         "targetPath": "$.profileUrl",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.title",
    >         "targetPath": "$.title",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "targetPath": "$.userType",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.preferredLanguage",
    >         "targetPath": "$.preferredLanguage",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.locale",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "targetPath": "$.timezone",
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
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "targetPath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.ims",
    >         "targetPath": "$.ims",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.photos",
    >         "targetPath": "$.photos",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.addresses",
    >         "targetPath": "$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.entitlements",
    >         "targetPath": "$.entitlements",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "targetPath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.x509Certificates",
    >         "targetPath": "$.x509Certificates",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
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
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuidHistory']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuidHistory']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['status']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['status']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mfaEnabled']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mfaEnabled']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['totpEnabled']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['totpEnabled']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['loginTime']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['loginTime']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['contactPreferences']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['contactPreferences']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sncName']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sncName']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['groupDomains']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['groupDomains']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, sig.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], sig.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:Group",
    >           "urn:ietf:params:scim:schemas:extension:sap:2.0:Group"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, sig.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%sig.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "targetPath": "$.members[?(@.value)]",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >           {
    >             "function": "resolveEntityIds"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
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
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio51580e0b464a46868881039fafac8f8a__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Signavio Process Transformation Suite](https://help.sap.com/docs/signavio-process-transformation-suite)

