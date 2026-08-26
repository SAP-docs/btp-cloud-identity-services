<!-- loiob9800f8c5fe2461eb5625f41898ebc6f -->

# SAP HANA Database

Follow this procedure to set up SAP HANA Database as a target system.



<a name="loiob9800f8c5fe2461eb5625f41898ebc6f__prereq_rl2_ldn_cbb"/>

## Prerequisites

-   You have credentials for a tenant in SAP Business Technology Platform. For more information, see: [Accounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8ed4a705efa0431b910056c0acdbf377)
-   You have the necessary connection settings to reach an SAP HANA database.
-   \(Optional\) You have installed the Cloud Connector in your corporate environment and have done the initial configuration. You need this only when your SAP HANA DB resides in a remote on-premise system, outside your Neo environment. For more information, see [Cloud Connector](https://help.hana.ondemand.com/help/frameset.htm?e6c7616abb5710148cfcf3e75d96d596.html).



## Context

> ### Note:  
> SAP HANA Database is only available as a target system.

**SAP HANA Database** is a target system \(connector\), which allows you to log into remote systems that have SAP HANA installed. Only provisioning of entity type **user** is currently supported by this connector. That includes user assignments to roles and all types of catalog and repository privileges \(*schema*, *analytic*, *application*\). For more information about SAP HANA privileges, see:

[SAP HANA: GRANT Statement \(Access Control\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/2.0.02/en-US/20f674e1751910148a8b990d33efbdc5.html)

[SAP HANA: Stored Procedures Used to Grant/Revoke Privileges on Activated Repository Objects](https://help.sap.com/viewer/102d9916bf77407ea3942fef93a47da8/1.0.11/en-US/f1b28c0904cd4b70bebcfa187831b30f.html)



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP HANA Database* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Choose the *Properties* tab to configure the connection settings for your system.

    > ### Note:  
    > If your Identity Provisioning tenant is running on SAP BTP, Neo environment, you can create a [connectivity destination](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/72696d6d06c0490394ac3069da600278.html) in your subaccount in the SAP BTP cockpit, and then select it from the *Destination Name* combo box in your Identity Provisioning User Interface.
    > 
    > If one and the same property exists both in the cockpit and in the *Properties* tab, the value set in the *Properties* tab is considered with higher priority.
    > 
    > We recommend that you use the *Properties* tab. Use a connectivity destination only if you need to reuse one and the same configuration for multiple provisioning systems.

    Below are listed all available SAP HANA properties. Some of them can be mandatory and others – optional, depending on your scenario.

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
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Possible values:

    -   **Internet**
    -   **OnPremise**

    The proxy type **OnPremise** requires you to provide mappings to your host and port to the Cloud Connector.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `Type`
    
    </td>
    <td valign="top">
    
    Enter: **HTTP**

    > ### Note:  
    > This property is mandatory only when your **ProxyType** is **OnPremise**.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.db.user`
    
    </td>
    <td valign="top">
    
    Name of the SAP HANA Database user
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.db.password`
    
    </td>
    <td valign="top">
    
    \(Credential\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.db.host`
    
    </td>
    <td valign="top">
    
    SAP HANA Database host
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.db.port`
    
    </td>
    <td valign="top">
    
    Default value: **30015** 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.db.encrypt`
    
    </td>
    <td valign="top">
    
    This property enables or disables TLS encryption.

    Possible values:

    -   true \(Default value\)

    -   false


    > ### Note:  
    > For existing systems, the property value defaults to false.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.db.validateCertificate`
    
    </td>
    <td valign="top">
    
    When set to true, this property specifies that the server certificate is validated. When set to false, the certificate is not validated.

    Possible values:

    -   true \(Default value\)

    -   false



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `CloudConnectorLocationId`
    
    </td>
    <td valign="top">
    
    Relevant when the proxy type is *OnPremise*. Use it only if your SAP Business Technology Platform account uses more than one Cloud Connector.
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP HANA Database* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP HANA Database. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "condition": "$.userName EMPTY false",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.username"
    >             },
    >             {
    >                 "targetPath": "$.password_option.password",
    >                 "scope": "createEntity",
    >                 "functions": [
    >                     {
    >                         "type": "randomPassword",
    >                         "passwordLength": 24,
    >                         "minimumNumberOfLowercaseLetters": 1,
    >                         "minimumNumberOfUppercaseLetters": 1,
    >                         "minimumNumberOfDigits": 1,
    >                         "minimumNumberOfSpecialSymbols": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": true,
    >                 "targetPath": "$.password_option.no_force_first_password_change",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "constant": true,
    >                 "targetPath": "$.deactivate",
    >                 "scope": "deleteEntity"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.username",
    >                 "scope": "deleteEntity"
    >             },
    >             {
    >                 "constant": false,
    >                 "targetPath": "$.deactivate"
    >             },
    >             {
    >                 "constant": true,
    >                 "targetPath": "$.reset_connect_attempts"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": true,
    >                 "targetPath": "$.force_password_change"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": true,
    >                 "targetPath": "$.enable_password_lifetime"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": true,
    >                 "targetPath": "$.disable_client_connect"
    >             },
    >             {
    >                 "constant": "NOW",
    >                 "targetPath": "$.valid_from"
    >             },
    >             {
    >                 "constant": "FOREVER",
    >                 "targetPath": "$.valid_to"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "1970-01-01 00:00:00.0",
    >                 "targetPath": "$.valid_from"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "1970-01-01 00:00:00.0",
    >                 "targetPath": "$.valid_to"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "role",
    >                 "targetPath": "$.catalog_permissions[0].type"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "MONITORING",
    >                 "targetPath": "$.catalog_permissions[0].name"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "ADMIN",
    >                 "targetPath": "$.catalog_permissions[0].option"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "object_privilege",
    >                 "targetPath": "$.catalog_permissions[1].type"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "SELECT CDS METADATA",
    >                 "targetPath": "$.catalog_permissions[1].name"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "SYS.USERS",
    >                 "targetPath": "$.catalog_permissions[1].on"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "role",
    >                 "targetPath": "$.repository_permissions[0].type"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "sap.appcore.auth.p::select_ACCESS_VIEWS_BY_USER",
    >                 "targetPath": "$.repository_permissions[0].name"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "application_privilege",
    >                 "targetPath": "$.repository_permissions[1].type"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "sap.hana.ide::Catalog",
    >                 "targetPath": "$.repository_permissions[1].name"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": true,
    >                 "targetPath": "$.repository_permissions[2].revoke"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "analytic_privilege",
    >                 "targetPath": "$.repository_permissions[2].type"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "_SYS_BI_CP_ALL",
    >                 "targetPath": "$.repository_permissions[2].name"
    >             }
    >         ]
    >     }
    > }
    > 
    > ```

6.  Now, add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loiob9800f8c5fe2461eb5625f41898ebc6f__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

