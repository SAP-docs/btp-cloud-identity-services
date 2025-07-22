<!-- loio77e07a7b508d4d3da02bceb463925b4a -->

# Cloud Foundry UAA Server

Follow this procedure to set up the Cloud Foundry UAA server as а source system.



<a name="loio77e07a7b508d4d3da02bceb463925b4a__prereq_rjs_2yp_wy"/>

## Prerequisites

> ### Restriction:  
> This system is available for standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on SAP Cloud Identity Services infrastructure and Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have technical user credentials for a Cloud Foundry system with read access permissions.

    In case OAuth is used for authentication, client ID and secret are required when creating a destination for access token retrieval. You need Cloud Foundry UAA version **4.2** or higher.

-   \(Optional\) You have installed the Cloud Connector in your corporate environment and have done the initial configuration. You need to do this only if the Cloud Foundry UAA server is exposed in a private corporate network. For more information, see [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).




<a name="loio77e07a7b508d4d3da02bceb463925b4a__context_jgv_gc1_123"/>

## Context

User Account and Authentication Service \(UAA\) is an OAuth2 server that you can use for centralized identity management. It owns the user accounts and authentication sources, and supports standard protocols \(such as *SAML*, *LDAP*, and *OpenID Connect*\) to provide SSO and delegated authorization to Web applications. For more information, see [Cloud Foundry: Overview](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#overview).

Cloud Foundry UAA is responsible for the SAP ID service to create and manage platform users \(platform administrators and platform developers\) in Cloud Foundry.

> ### Tip:  
> This connector is meant for reading users and groups from **general** Cloud Foundry systems \(they could be non-SAP ones\). If you want to trigger provisioning of entities from SAP Business Technology Platform Cloud Foundry applications, you'd better use [SAP BTP XS Advanced UAA \(Cloud Foundry\)](sap-btp-xs-advanced-uaa-cloud-foundry-c135a52.md) source system.

These source systems consume SCIM 1.1 API provided by Cloud Foundry UAA.

> ### Remember:  
> You can read Cloud Foundry users and groups on **application** level only. You cannot read or manage them on a *subaccount* level.

Follow the steps below to create Cloud Foundry UAA as a source system to read users and groups, which can then be provisioned to a certain target system.



<a name="loio77e07a7b508d4d3da02bceb463925b4a__steps_cyl_j21_qfb"/>

## Procedure

1.  \(Optional\) If the Cloud Foundry UAA server is exposed in a private corporate network, add an access control system mapping in Cloud Connector. For more information, see [Configure Access Control \(HTTP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e7d4927dbb571014af7ef6ebd6cc3511.html).

2.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

4.  Add *Cloud Foundry UAA Server* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

5.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Specify the URL to the Cloud Foundry UAA SCIM API.

    If not sure about the exact URL, ask your Cloud Foundry UAA administrator.
    
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
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    As you need to make OAuth authentication to the UAA system, enter the URL to the OAuth2 token service.

    If not sure about the exact URL, ask your Cloud Foundry UAA administrator.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the OAuth client ID of the Cloud Foundry UAA technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth client secret of the technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `uaa.origin`
    
    </td>
    <td valign="top">
    
    Enter the location of your Cloud Foundry identity provider. If not sure about the value, ask your Cloud Foundry UAA administrator.

    The value of this property is a string, which will be used as the *origin* attribute in the system transformation.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `uaa.origin.filter.enabled`
    
    </td>
    <td valign="top">
    
    This flag property depends on `uaa.origin`. Possible values: **true** or **false**

    -   If set to *true*, the Identity Provisioning service will read only users whose identity provider is set as a value of `uaa.origin`.
    -   If set to *false*, the Identity Provisioning service will read all users, regardless of their origin.
    -   If set to *true* but the `uaa.origin` property is missing, the provisioning job will fail.


    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    Exemplary destination:


    <table>
    <tr>
    <td valign="top">
    
    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `ProxyType`=*Internet*

    `URL`=*https://api.authentication.hana.ondemand.com*

    `OAuth2TokenServiceURL`=*https://MyCFaccount.authentication.hana.ondemand.com/oauth/token*

    `User`=*MyCFuser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `uaa.origin`=*my\_UAA\_location*

    `uaa.origin.filter.enabled`=*true*
    
    </td>
    </tr>
    </table>
    
6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Cloud Foundry UAA Server* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    -   **Mapping logic** – The behavior of the default transformation logic is to map all attributes from a Cloud Foundry UAA entity to the intermediate Identity Provisioning representation.
    -   **User offboarding** – If a user or group has been deleted from the Cloud Foundry UAA server, this change is recognized, and the user/group is deleted from the target system too.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Cloud Foundry UAA server. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [Cloud Foundry UAA API: Users](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#users)

    [Cloud Foundry UAA API: Groups](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#groups)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
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
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.verified",
    >         "targetPath": "$.verified",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.origin",
    >         "targetPath": "$.origin",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.zoneId",
    >         "targetPath": "$.zoneId",
    >         "optional": true
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
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
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "'%uaa.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%uaa.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
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
    >         "sourcePath": "$.description",
    >         "targetPath": "$.description",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.zoneId",
    >         "targetPath": "$.zoneId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       }
    >     ]
    >   }
    > }
    > ```

7.  Now, add a target system to which to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio77e07a7b508d4d3da02bceb463925b4a__postreq_krz_xpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Cloud Foundry UAA: Users](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#users)

[Cloud Foundry UAA: Groups](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#groups)

