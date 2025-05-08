<!-- loiobeeeebf189dc4a5aa0e0e289653f4f17 -->

# SAP Advanced Financial Closing

Follow this procedure to set up SAP Advanced Financial Closing as a target system.



<a name="loiobeeeebf189dc4a5aa0e0e289653f4f17__prereq_gfl_gvx_rdb"/>

## Prerequisites

You have created an instance and generated a service key for the standard service plan of SAP Advanced Financial Closing. For more information, see: [How to Manage User Access Using the SCIM API Provided](https://help.sap.com/docs/AFC/b021b34a2c2d4943abc3a31008c7bdfc/49376ed8c58f41e0b84d141824698721.html).

The service key contains the API URL and the OAuth credentials \(`clientid` and `clientsecret`\) under the `uaa` property.



<a name="loiobeeeebf189dc4a5aa0e0e289653f4f17__context_y2y_nxx_rdb"/>

## Context

SAP Advanced Financial Closing allows you to define, automate, process, and monitor the financial closing tasks for the entities of your organization. It is an SAP BTP application that runs in an SAP BTP subaccount.

You can use Identity Provisioning to configure SAP Advanced Financial Closing as a target system for provisioning users and user groups from various source systems.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Advanced Financial Closing* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    `s4hana.afc.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a user that already exists in the target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

    Possible values:

    -   *userName*
    -   *emails\[0\].value*
    -   *userName,emails\[0\].value*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.afc.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a group that already exists in the target system \(a conflicting group\), this property defines the unique attributes by which the existing group will be searched and resolved.

    The default value is *displayName*.
    
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

    Transformations are used to map user and group attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Advanced Financial Closing* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Advanced Financial Closing system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    [How to Manage User Access Using the SCIM API Provided](https://help.sap.com/docs/AFC/b021b34a2c2d4943abc3a31008c7bdfc/49376ed8c58f41e0b84d141824698721.html)

    [SAP Business Accelerator Hub: SAP Advanced Financial Closing](https://api.sap.com/package/SAPS4HANACloudforadvancedfinancialclosing/rest)

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Advanced Financial Closing entity.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "('%s4hana.afc.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%s4hana.afc.group.prefix%.+/)] empty false)",
    >     "mappings": [
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
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
    >         "condition": "$.emails[0].length() > 0",
    >         "targetPath": "$.emails[0].primary",
    >         "constant": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails",
    >         "functions": [
    >           {
    >             "function": "putIfAbsent",
    >             "key": "type",
    >             "defaultValue": "work"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "targetPath": "$.phoneNumbers",
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
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, s4hana.afc.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], s4hana.afc.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:Group",
    >           "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, s4hana.afc.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%s4hana.afc.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, s4hana.afc.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%s4hana.afc.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, s4hana.afc.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%s4hana.afc.group.prefix%",
    >             "replacement": ""
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
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "function": "resolveEntityIds"
    >           }
    >         ]
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

6.  Add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loiobeeeebf189dc4a5aa0e0e289653f4f17__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

