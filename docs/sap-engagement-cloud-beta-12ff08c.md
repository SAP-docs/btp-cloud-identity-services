<!-- loio12ff08ca313d409986524d7a88fe00e0 -->

# SAP Engagement Cloud \(Beta\)

Follow this procedure to set up SAP Engagement Cloud \(Beta\) as a target system.



<a name="loio12ff08ca313d409986524d7a88fe00e0__prereq_gfl_gvx_rdb"/>

## Prerequisites

-   You have created API credentials for one of the two scenarios, as described in:
    -   [API Credentials for SAP Engagement Cloud | SAP Emarsys](https://help.sap.com/docs/SAP_ENGAGEMENT_CLOUD/c68c0f660ecd456195d98c00a678e04e/fdf4b58974c110149353957a3e7ef453.html?version=CLOUD#openid-connect)
    -   [API Credentials for SAP Engagement Cloud, enterprise edition](https://help.sap.com/docs/SAP_ENGAGEMENT_CLOUD/c68c0f660ecd456195d98c00a678e04e/fdf4b58974c110149353957a3e7ef453.html?version=CLOUD#openid-connect-(sap-cloud-identity))

-   You have enabled SCIM permissions:
    -   In the **Permissions** section search for **scim**.
    -   Turn on **all 15 SCIM permissions** \(required to use all API endpoints\).




<a name="loio12ff08ca313d409986524d7a88fe00e0__context_y2y_nxx_rdb"/>

## Context

> ### Note:  
> This connector is currently in beta state. Features and behavior may change in future releases.

SAP Engagement Cloud \(Beta\) is SAP's customer engagement platform for creating personalized, omnichannel customer experiences and automating marketing across email, mobile, web, SMS, and other digital channels.

-   SAP Engagement Cloud | SAP Emarsys delivers the core marketing automation and customer engagement capabilities.
-   SAP Engagement Cloud, enterprise edition is a solution that connects enterprise data and artificial intelligence to securely orchestrate real-time, personalized interactions across the entire business.

You can use Identity Provisioning to configure SAP Engagement Cloud \(Beta\) as a source system where you can read users, user groups and user roles from, and provision them to a target system.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Engagement Cloud \(Beta\)* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the *API Basepath*, generated from your API Credentials.
    
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
    
    Enter the *OAuth Client Id*, created for your SAP Engagement Cloud \(Beta\) system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    Enter the *Oauth Client Secret*, created from your API Credentials.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the *Token Endpoint*, created from your API Credentials.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map user and group attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Engagement Cloud \(Beta\)* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Engagement Cloud \(Beta\) system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Engagement Cloud \(Beta\) entity.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "('%ec.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%ec.group.prefix%.+/)] empty false)",
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
    >         "targetPath": "$.emails",
    >         "functions": [
    >           {
    >             "function": "putIfAbsent",
    >             "key": "type",
    >             "defaultValue": "work"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, ec.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], ec.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
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
    >             "condition": "isAttributeWithMandatoryPrefix(@, ec.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%ec.group.prefix%",
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




<a name="loio12ff08ca313d409986524d7a88fe00e0__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

