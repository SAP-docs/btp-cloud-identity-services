<!-- loioea2147de6e9f4cef8a2c3a6bc2d53d71 -->

# SAP Ariba Central Invoice Management

Follow this procedure to set up SAP Ariba Central Invoice Management as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

You have created an instance and generated a service key for the scim service plan of SAP Ariba Central Invoice Management. This step is automated by the booster *Set Up SAP Ariba Central Invoice Management*. For more information, see [Setting Up Invoice Processing with SAP Ariba Central Invoice Management \(4N6\)](https://support.sap.com/content/dam/SAAP/Sol_Pack/S4C/Library/Setup/4N6_Set-Up_EN_XX.pdf) –\> *Set up Configuration Using Booster in SAP BTP Cockpit*.



<a name="loioea2147de6e9f4cef8a2c3a6bc2d53d71__context_y2y_nxx_rdb"/>

## Context

SAP Ariba Central Invoice Management is an SAP BTP SaaS application running on SAP BTP, Cloud Foundry environment. This application enables central management of supplier invoices from multiple connected systems, such as SAP S/4HANA Cloud systems. You can use Identity Provisioning to configure SAP Ariba Central Invoice Management as a target system where you can provision users and groups from source systems.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Ariba Central Invoice Management* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL provided by the service key under the *ips-connector* field without adding the path information.

    For example: `https://eu10.cim.cloud.sap`
    
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
    
    Enter the value from the *clientid* field of the service key.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the value from the *clientsecret* field of the service key.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL. This is the value from the *url* field of the service key plus `/oauth/token`

    For example: <code>https://<i class="varname">&lt;my tenant&gt;</i>.authentication.eu10.hana.ondemand.com/oauth/token</code>
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cim.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a user that already exists in the target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved. The property is not added automatically at system creation.

    **Possible values:**

    -   *userName* - default value
    -   *emails\[\*\].value*
    -   *userName,emails\[\*\].value*

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)

    `cim.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Ariba Central Invoice Management groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `CIM_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `CIM_` prefix in their display name will be provisioned to SAP Ariba Central Invoice Management. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Ariba Central Invoice Management.
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Ariba Central Invoice Management* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Ariba Central Invoice Management system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [User Management \(SCIM\) for SAP Ariba Central Invoice Management](https://api.sap.com/api/UserServiceV1/resource/)

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Ariba Central Invoice Management entity.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "(($.emails EMPTY true) || (isValidEmail($.emails[*].value))) && (('%cim.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%cim.group.prefix%.*/)] empty false))",
    >     "mappings": [
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:User"
    >         ],
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
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
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
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
    >         "sourcePath": "$.name.formatted",
    >         "targetPath": "$.name.formatted",
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
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)] empty true",
    >         "constant": true,
    >         "targetPath": "$.emails[0].primary"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
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
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, cim.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], cim.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:Group"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, cim.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%cim.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
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
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loioea2147de6e9f4cef8a2c3a6bc2d53d71__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Ariba Central Invoice Management](https://help.sap.com/docs/CENTRAL_INVOICE_MANAGEMENT)

