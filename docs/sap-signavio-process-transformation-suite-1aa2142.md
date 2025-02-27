<!-- loio1aa2142a011745728491f7e20f8cbb19 -->

# SAP Signavio Process Transformation Suite

Follow this procedure to set up SAP Signavio Process Transformation Suite as а source system.



<a name="loio1aa2142a011745728491f7e20f8cbb19__prereq_gfl_gvx_rdb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.



## Context

SAP Signavio Process Transformation Suite helps you understand, improve, and transform your business processes – fast and at scale – with a cloud-based process management platform.

You can use Identity Provisioning to configure SAP Signavio Process Transformation Suite as a source system where you can read users and groups from and provision them to a target system.

> ### Note:  
> The initial setup of SAP Signavio Process Transformation Suite is performed in the Service Provider Cockpit - a central system for operational processes like system provisioning. This setup includes configuring the connection and certificate-based authentication between Identity Provisioning and the SAP Signavio Process Transformation Suite. If any changes are needed, they must be made through a support incident.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Signavio Process Transformation Suite* as a source system. See: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the identifier of your SAP Signavio Process Transformation Suite tenant.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sig.group.members.paging.enabled`
    
    </td>
    <td valign="top">
    
    This property enables paging of group members.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sig.user.groups.paging.enabled`
    
    </td>
    <td valign="top">
    
    This property enables paging of user’s groups.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sig.group.members.page.size`
    
    </td>
    <td valign="top">
    
    The number of group members that SAP Signavio Process Transformation Suite returns per request when reading a group.

    Default value = 1000
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sig.user.groups.page.size`
    
    </td>
    <td valign="top">
    
    The number of user groups that SAP Signavio Process Transformation Suite returns per request when reading a user.

    Default value = 1000
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sig.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Signavio Process Transformation Suite users matching the filter expression will be read.

    Supported operators: eq \(equal\) and sw \(starts with\).

    For example:

    -   Value = *userName eq "JohnSmith"*

    -   Value = *userName sw "J"*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sig.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Signavio Process Transformation Suite groups matching the filter expression will be read.

    Supported operators: eq \(equal\) and sw \(starts with\).

    For example:

    -   Value = *displayName eq "ProjectTeam1"*

    -   Value = *displayName sw "P"*



    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Signavio Process Transformation Suite* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **Mapping logic** – the behavior of the default transformation logic is to read all user attributes from the source SAP Signavio Process Transformation Suite system, and then map them to the internal SCIM representation. It uses `entityIdSourceSystem` to store the unique ID of the identity.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "optional": true,
    >         "targetPath": "$.name.middleName"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.name.honorificPrefix",
    >         "optional": true,
    >         "targetPath": "$.name.honorificPrefix"
    >       },
    >       {
    >         "sourcePath": "$.name.honorificSuffix",
    >         "optional": true,
    >         "targetPath": "$.name.honorificSuffix"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "optional": true,
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.nickName",
    >         "optional": true,
    >         "targetPath": "$.nickName"
    >       },
    >       {
    >         "sourcePath": "$.profileUrl",
    >         "optional": true,
    >         "targetPath": "$.profileUrl"
    >       },
    >       {
    >         "sourcePath": "$.title",
    >         "optional": true,
    >         "targetPath": "$.title"
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "optional": true,
    >         "targetPath": "$.userType"
    >       },
    >       {
    >         "sourcePath": "$.preferredLanguage",
    >         "optional": true,
    >         "targetPath": "$.preferredLanguage"
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "optional": true,
    >         "targetPath": "$.locale"
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "optional": true,
    >         "targetPath": "$.timezone"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "optional": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails']"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers"
    >       },
    >       {
    >         "sourcePath": "$.ims",
    >         "optional": true,
    >         "targetPath": "$.ims"
    >       },
    >       {
    >         "sourcePath": "$.photos",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.photos"
    >       },
    >       {
    >         "sourcePath": "$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.addresses"
    >       },
    >       {
    >         "sourcePath": "$.entitlements",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.entitlements"
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.roles"
    >       },
    >       {
    >         "sourcePath": "$.x509Certificates",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.x509Certificates"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuidHistory']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuidHistory']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['status']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['status']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mfaEnabled']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mfaEnabled']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['totpEnabled']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['totpEnabled']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['loginTime']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['loginTime']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['contactPreferences']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['contactPreferences']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sncName']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sncName']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['groupDomains']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['groupDomains']"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups"
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
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "'%sig.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%sig.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
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
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members"
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Add a target system to provision users to it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio1aa2142a011745728491f7e20f8cbb19__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Signavio Process Transformation Suite](https://help.sap.com/docs/signavio-process-transformation-suite)

