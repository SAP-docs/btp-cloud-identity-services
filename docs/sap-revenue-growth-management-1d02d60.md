<!-- loio1d02d60fdad84d39a8a5643942b40a80 -->

# SAP Revenue Growth Management

Follow this procedure to set up SAP Revenue Growth Management as a source system.



<a name="loio1d02d60fdad84d39a8a5643942b40a80__prereq_qcc_vk2_2cb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created an SAP Revenue Growth Management consumer application in your SAP Cloud Identity Services tenant and defined a dependency to its API, as described in [Configure Integration Between Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/communicate-between-applications?locale=en-US&version=Cloud). *UserImport* must be selected for the dependency *API*.

-   You have generated API credentials for the consumer application, as described in [Generate Credentials to Access the APIs of an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/quick-start-dependent-applications?version=Cloud).




<a name="loio1d02d60fdad84d39a8a5643942b40a80__context_w5f_nlx_rdb"/>

## Context

SAP Revenue Growth Management is an SAP BTP SaaS application that provides customers in the Consumer Products industry an easy way to efficiently create, monitor, and maintain account plans.

You can use Identity Provisioning to configure SAP Revenue Growth Management as a source system to read users and groups. These source systems consume SCIM 2.0 API provided by SAP Revenue Growth Management. For more information, see [SAP Revenue Growth Management SCIM API](https://hub.sap.com/api/RGM_USER_SCIM/overview).

> ### Note:  
> Support for groups is intended for future use.



<a name="loio1d02d60fdad84d39a8a5643942b40a80__steps_pl4_rlx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Revenue Growth Management* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the base URL of your SAP Revenue Growth Management system's SCIM API, excluding any path information.
    
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
    
    Enter the client ID generated when creating API credentials for the consumer application. For more information, see [Generate Credentials to Access the APIs of an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/quick-start-dependent-applications?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the client secret generated when creating API credentials for the consumer application. For more information, see [Generate Credentials to Access the APIs of an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/quick-start-dependent-applications?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `rgm.userImport.api.dependency.name`
    
    </td>
    <td valign="top">
    
    Enter the value of the dependency name used in the configuration of the SAP Revenue Growth Management consumer application, created in the SAP Cloud Identity Services tenant. It is used for access token retrieval from Identity Authentication.

    For more information, see [Integrating Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/integrating-applications?locale=en-US&version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `rgm.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those users matching the filter expression will be read. You can filter users by `userName`, `emails[0].value`, and `externalId`, according to the API syntax of SAP Revenue Growth Management.

    For example:

    -   *userName eq "johnbrown" and externalId eq "c167254d-25fd-5fac-af32-0b8c35e0de27"*
    -   *userName sw "J" and externalId eq "c167254d-25fd-5fac-af32-0b8c35e0de27"*
    -   *userName eq "johnbrown" and emails.value eq "johnbrown@email.com"*
    -   *userName eq "johnbrown" and emails.value eq "johnbrown@email.com" and externalId eq "c167254d-25fd-5fac-af32-0b8c35e0de27"*

        > ### Note:  
        > These combinations are valid for both 'or' and 'and' operators.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `rgm.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those groups matching the filter expression will be read.

    For example:

    *urn:sap:cloud:scim:schemas:extension:custom:2.0:Group:name eq "ProjectTeam1" or "Students2018"*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `rgm.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Revenue Growth Management groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `RGM_`

    You can use the example value or provide your own.

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Revenue Growth Management source system and will be provisioned to the target system with the following name pattern: <code>RGM_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Revenue Growth Management groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Revenue Growth Management groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Revenue Growth Management* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Revenue Growth Management system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **[SAP Revenue Growth Management SCIM API](https://hub.sap.com/api/RGM_USER_SCIM/overview)**

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user":{
    >     "mappings":[
    >       {
    >         "sourcePath":"$.id",
    >         "targetVariable":"entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath":"$.schemas",
    >         "targetPath":"$.schemas",
    >         "preserveArrayWithSingleElement":true
    >       },
    >       {
    >         "sourcePath":"$.userName",
    >         "targetPath":"$.userName",
    >         "correlationAttribute":true
    >       },
    >       {
    >         "sourcePath":"$.emails",
    >         "targetPath":"$.emails",
    >         "optional":true,
    >         "preserveArrayWithSingleElement":true
    >       },
    >       {
    >         "sourcePath":"$.emails[?(@.primary == true)].value",
    >         "correlationAttribute":true
    >       },
    >       {
    >         "sourcePath":"$.externalId",
    >         "targetPath":"$.externalId",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.givenName",
    >         "targetPath":"$.name.givenName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.familyName",
    >         "targetPath":"$.name.familyName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.displayName",
    >         "targetPath":"$.displayName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.userType",
    >         "targetPath":"$.userType",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.preferredLanguage",
    >         "targetPath":"$.preferredLanguage",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.locale",
    >         "targetPath":"$.locale",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.timezone",
    >         "targetPath":"$.timezone",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.active",
    >         "targetPath":"$.active",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath":"$.addresses"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >             {
    >                 "function": "concatString",
    >                 "condition": "'%rgm.group.prefix%' !== 'null'",
    >                 "applyOnElements": true,
    >                 "applyOnAttribute": "display",
    >                 "prefix": "%rgm.group.prefix%"
    >             }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings":[
    >       {
    >         "sourcePath":"$.id",
    >         "targetVariable":"entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath":"$.schemas",
    >         "targetPath":"$.schemas",
    >         "preserveArrayWithSingleElement":true
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >             {
    >                 "condition": "'%rgm.group.prefix%' !== 'null'",
    >                 "function": "concatString",
    >                 "prefix": "%rgm.group.prefix%"
    >             }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >             {
    >                 "condition": "'%rgm.group.prefix%' !== 'null'",
    >                 "function": "concatString",
    >                 "prefix": "%rgm.group.prefix%"
    >             }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true
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
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Now, add a target system to provision users and groups into it. Choose from:[Target Systems](target-systems-ab3f641.md).




<a name="loio1d02d60fdad84d39a8a5643942b40a80__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Revenue Growth Management](https://help.sap.com/docs/rgm?locale=en-US&task=all_tasks)

