<!-- loioa0988e363c4646cc863ba6eed65b7fef -->

# SAP Analytics Cloud

Follow this procedure to set up SAP Analytics Cloud as a source system.



<a name="loioa0988e363c4646cc863ba6eed65b7fef__prereq_qcc_vk2_2cb"/>

## Prerequisites

-   In SAP Analytics Cloud, you have enabled a custom SAML Identity Provider, for which *User Attribute* is set to **Custom SAML User Mapping**. To learn how, see: [Enabling a Custom SAML Identity Provider](https://help.sap.com/doc/00f68c2e08b941f081002fd3691d86a7/release/en-US/3651184dad944aa2b361ad029a7a8cae.html)

-   Add an OAuth client with authorization grant **Client Credentials**. To learn how, see: [Managing OAuth Clients and Trusted Identity Providers](https://help.sap.com/doc/00f68c2e08b941f081002fd3691d86a7/release/en-US/4f43b54398fc4acaa5efa32badfe3df6.html)




<a name="loioa0988e363c4646cc863ba6eed65b7fef__context_w5f_nlx_rdb"/>

## Context

SAP Analytics Cloud is an all-in-one cloud product offered as software as a service for business intelligence, planning, and predictive analytics.

You can use Identity Provisioning to configure SAP Analytics Cloud as a source system where you can read users and groups and provision them to target systems of your choice. The source system consumes SCIM 2.0 API provided by SAP Analytics Cloud.

There are two versions of the SAP Analytics Cloud SCIM API. They are handled by the`sac.api.version` property as follows:

-   When the value is set to `1` or the property is not defined \(typical for systems created before versioning was introduced on April 10, 2023\), SAP Analytics Cloud SCIM API version 1 is used. This is the default value.

-   When the value is set to `2` - SAP Analytics Cloud SCIM API version 2 is used. This version is released with enhancements, such as: reading groups is not ignored in the default read transformation.


For more information on the differences between SAP Analytics Cloud SCIM API version 1 and 2, see [Managing Users and Teams](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/ee11077e8a344ce99dfb77033eace581.html).

For more information on how to update to version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).



<a name="loioa0988e363c4646cc863ba6eed65b7fef__steps_pl4_rlx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Analytics Cloud* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL to your SAP Analytics Cloud system without adding the path information.
    
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
    
    Enter the client ID to retrieve the OAuth access token for SAP Analytics Cloud.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the client secret to retrieve the OAuth access token for SAP Analytics Cloud.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Analytics Cloud instance.

    This token URL is listed in the *OAuth Clients* section of the *App Integration* page. For more information, refer to *Authorize API Access for OAuth Clients* in [Manage OAuth Clients](https://help.sap.com/viewer/00f68c2e08b941f081002fd3691d86a7/release/en-US/4f43b54398fc4acaa5efa32badfe3df6.html)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sac.api.version`
    
    </td>
    <td valign="top">
    
    Handles the version of SAP Analytics Cloud SCIM API.

    **Possible values:**

    -   *1* - Indicates that SAP Analytics Cloud SCIM API version 1 is used.

    -   *2* - Indicates that SAP Analytics Cloud SCIM API version 2 is used.


    Default value: *1*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Analytic Cloud* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Analytic Cloud system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Analytics Cloud REST API: Managing Users and Teams](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/ee11077e8a344ce99dfb77033eace581.html)

    [Managing Users and Teams → api/v1/scim](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/42d90beb6337476984fcc7c54ec146dd.html)

    [Managing Users and Teams → api/v1/scim2](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/e34d2555509548028b76a7862cc5b84a.html)

    **Default transformation for SAP Analytic Cloud SCIM API version 1:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary== true)].value",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.roles",
    >                 "targetPath": "$.roles",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "functions": [
    >                     {
    >                         "condition": "'%sac.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "applyOnElements": true,
    >                         "applyOnAttribute": "display",
    >                         "prefix": "%sac.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:scim:schemas:extension:enterprise:1.0']['manager']['managerId']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "ignore": true,
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "'%sac.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "prefix": "%sac.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.roles",
    >                 "targetPath": "$.roles",
    >                 "preserveArrayWithSingleElement": true
    >             }
    >         ]
    >     }
    > }
    > ```

    **Default transformation for SAP Analytic Cloud SCIM API version 2:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary== true)].value",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']",
    >                 "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.roles",
    >                 "targetPath": "$.roles",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "functions": [
    >                     {
    >                         "condition": "'%sac.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "applyOnElements": true,
    >                         "applyOnAttribute": "display",
    >                         "prefix": "%sac.group.prefix%"
    >                     }
    >                 ]
    >             }
    >         ]
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "'%sac.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "prefix": "%sac.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-roles']",
    >                 "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-roles']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-custom-parameters']",
    >                 "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-custom-parameters']",
    >                 "optional": true
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loioa0988e363c4646cc863ba6eed65b7fef__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

