<!-- loiob9800f8c5fe2461eb5625f41898ebc6f -->

# SAP HANA Database \(Beta\)

Follow this procedure to set up SAP HANA Database \(Beta\) as a target system.



<a name="loiob9800f8c5fe2461eb5625f41898ebc6f__prereq_rl2_ldn_cbb"/>

## Prerequisites

> ### Restriction:  
> This system is available for standalone tenants running on SAP BTP, Neo environment.

-   You have credentials for a tenant in SAP Business Technology Platform. For more information, see: [Accounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8ed4a705efa0431b910056c0acdbf377)
-   You have the necessary connection settings to reach an SAP HANA database.
-   \(Optional\) You have installed the Cloud Connector in your corporate environment and have done the initial configuration. You need this only when your SAP HANA DB resides in a remote on-premise system, outside your Neo environment. For more information, see [Cloud Connector](https://help.hana.ondemand.com/help/frameset.htm?e6c7616abb5710148cfcf3e75d96d596.html).

> ### Note:  
> This is a beta feature available on SAP Business Technology Platform. For more information, see: *Enable beta features* in [Change Subaccount Details](https://help.sap.com/docs/btp/sap-business-technology-platform/change-subaccount-details?version=Cloud)



## Context

**SAP HANA Database** is a system \(connector\) in beta state, which allows you to log into remote systems that have SAP HANA installed. Only provisioning of entity type **user** is currently supported by this connector. That includes user assignments to roles and all types of catalog and repository privileges \(*schema*, *analytic*, *application*\). For more information about SAP HANA privileges, see:

[SAP HANA: GRANT Statement \(Access Control\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/2.0.02/en-US/20f674e1751910148a8b990d33efbdc5.html)

[SAP HANA: Stored Procedures Used to Grant/Revoke Privileges on Activated Repository Objects](https://help.sap.com/viewer/102d9916bf77407ea3942fef93a47da8/1.0.11/en-US/f1b28c0904cd4b70bebcfa187831b30f.html)

When using this connector, what you actually need is to connect to the JDBC SQL port of SAP HANA. Depending on whether this port is visible or hidden, you have the following use cases:

**Case 1** – The JDBC port is directly accessible by the enabled Identity Provisioning NEO account. That mostly happens when it resides in the same Neo environment as your Identity Provisioning service.

**Case 2** – The JDBC port is not directly accessible by your Neo environment. There are two subcases:

-   JDBC port of SAP HANA DB is accessible by a system, which is publicly reachable through SSH protocol. You have to configure your *SAP HANA Database \(Beta\)* connector so as to open an SSH tunnel to this system. Set the proxy type to **Internet**.
-   JDBC port of SAP HANA DB is accessible by a system, which is reachable through SSH protocol only from an internal network. You need to have the Cloud Connector installed in that network and configure it to allow SSH connections from the Identity Provisioning service account. You have to create an SSH tunnel by using TCP protocol connection configuration from the Cloud Connector. When configuring the access control, specify the SSH host and port to reach the system that has access to the JDBC port. Set the proxy type to **OnPremise**.

**Case 3** – SAP HANA DB is installed in the Cloud Foundry environment. You need to enable SSH access on both space and application level. To do this, execute the relevant console commands in the Cloud Foundry command line tool \(see: [Cloud Foundry: Accessing Apps with SSH](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html)\). The *SAP HANA Database \(Beta\)* connector will open an SSH tunnel to a running application container on the Cloud Foundry space. The space configuration of the security groups allows access to the JDBC port of SAP HANA MDC. You need to have the *Space Developer* role. Again, there are two subcases:

-   Cloud Foundry landscape is publicly accessible through SSH protocol. Set the proxy type to **Internet**.
-   Cloud Foundry landscape is accessible through SSH protocol, which is allowed only from a particular network. You need to have the Cloud Connector installed in that network and configure it to allow SSH connections from the Identity Provisioning service account. Set the proxy type to **OnPremise**.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP HANA Database \(Beta\)* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    This property is applicable if you use an SSH tunnel \(`hana.jdbc.access.type`=*ssh.tunnel|cf.app.ssh.tunnel*\). Possible values:

    -   **Internet** – if the SSH port is visible in your Neo environment
    -   **OnPremise** – if the SSH port is not directly accessible, and you have to use the Cloud Connector. You have to configure TCP protocol connection to the SSH host and port \(specify the configuration properties `hana.jdbc.ssh.tunnel.host` and `hana.jdbc.ssh.tunnel.port`\).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `CloudConnectorLocationId`
    
    </td>
    <td valign="top">
    
    Relevant when the proxy type is *OnPremise*. Use it only if your SAP Business Technology Platform account uses more than one Cloud Connector.
    
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
    
    30015
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.access.type`
    
    </td>
    <td valign="top">
    
    There are three types of SAP HANA access:

    -   **direct** – It requires only *hana.jdbc.db.\** properties
    -   **ssh.tunnel** – it requires *hana.jdbc.db.\** and *hana.jdbc.ssh.tunnel.\** properties.
    -   **cf.app.ssh.tunnel** – It requires *hana.jdbc.ssh.tunnel.cf.\** properties to establish an SSH tunnel to the Cloud Foundry application, from which to access the JDBC SQL port of SAP HANA.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.username`
    
    </td>
    <td valign="top">
    
    The username used for opening the SSH Tunnel
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.host`
    
    </td>
    <td valign="top">
    
    SSH Tunnel’s host
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.port`
    
    </td>
    <td valign="top">
    
    22
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.auth.type`
    
    </td>
    <td valign="top">
    
    Supported SSH authentication types:

    -   **key**
    -   **pwd**
    -   **otp**
    -   **key+otp**
    -   **key+pwd**
    -   **pwd+otp**
    -   **key+pwd+otp**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.cf.api.url`
    
    </td>
    <td valign="top">
    
    The URL of the Cloud Foundry API.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.cf.oauth.token.url`
    
    </td>
    <td valign="top">
    
    The URL of the OAuth token endpoint.

    > ### Remember:  
    > Remove the */oauth/token* part at the end of the URL.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.cf.org`
    
    </td>
    <td valign="top">
    
    This is the Cloud Foundry organization.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.cf.space`
    
    </td>
    <td valign="top">
    
    This is the Cloud Foundry space.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.cf.app`
    
    </td>
    <td valign="top">
    
    This is the Cloud Foundry application to which the *SAP HANA Database \(Beta\)* system opens an SSH tunnel. For more information, see: [Cloud Foundry: Accessing Apps with SSH](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html) 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.cf.app.instance`
    
    </td>
    <td valign="top">
    
    This is the instance number of the Cloud Foundry application.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.cf.username`
    
    </td>
    <td valign="top">
    
    This is the Cloud Foundry user. It has the role **Developer** for the space where the application is deployed.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.cf.password`
    
    </td>
    <td valign="top">
    
    \(Credential\) The password for property `hana.jdbc.ssh.tunnel.cf.username` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Taken into account only if the authentication type includes **pwd**. That means any of the following:

    -   `hana.jdbc.ssh.tunnel.auth.type` = *pwd*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *pwd+otp*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd+otp*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.totp.secret.key`
    
    </td>
    <td valign="top">
    
    \(Credential\) Taken into account only if the authentication type includes **otp**. That means any of the following:

    -   `hana.jdbc.ssh.tunnel.auth.type` = *otp*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *key+otp*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *pwd+otp*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd+otp*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.jdbc.ssh.tunnel.private.key`
    
    </td>
    <td valign="top">
    
    \(Credential\) Taken into account only if the authentication type includes **key**. That means any of the following:

    -   `hana.jdbc.ssh.tunnel.auth.type` = *key*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *key+otp*
    -   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd+otp*


    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP HANA Database \(Beta\)* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

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

