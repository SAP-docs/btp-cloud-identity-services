<!-- loio13f60ee7604b489eb87d15cd728e8b59 -->

# Procurement Data Warehouse

Follow this procedure to set up procurement data warehouse as a source system.



<a name="loio13f60ee7604b489eb87d15cd728e8b59__prereq_oky_mqb_gzb"/>

## Prerequisites

-   You obtain credentials to access the Procurement Data Warehouse API.

    > ### Note:  
    > To obtain credentials to access the Procurement Data Warehouse API, create a [case](https://support.sap.com/en/index.html) to the component *BNS-ARI-PRI*.
    > 
    > In response to the case, SAP provides the certificate needed to access the API as well as the URL for the procurement data warehouse enrollment service, which is landscape-specific and starts with `*.cloud.sap`.

-   You established trust between your SAP BTP subaccount and the SAP Cloud Identity Services - Identity Authentication service. For more information, see [Establishing Trust Automatically](https://help.sap.com/docs/btp/sap-business-technology-platform/establishing-trust-automatically?version=Cloud).

-   To configure your *Procurement Data Warehouse* provisioning system \(see the procedure below\), you will need to map your SAP Ariba application parameters to the relevant Identity Provisioning properties. The property mapping between the two systems is as follows:


    <table>
    <tr>
    <th valign="top">

    Procurement Data Warehouse Application
    
    </th>
    <th valign="top">

    Identity Provisioning
    
    </th>
    <th valign="top">

    Values
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    API URL
    
    </td>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    Examples:

    -   US: **https://openapi.ariba.com**
    -   Europe: **https://eu.openapi.ariba.com**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    procurement data warehouseOAuth Token URL
    
    </td>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Examples:

    -   US: **https://api.ariba.com/v2/oauth/token** 
    -   Europe: **https://api-eu.ariba.com/v2/oauth/token**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    OAuth Client ID
    
    </td>
    <td valign="top">
    
    `client_id`
    
    </td>
    <td valign="top">
    
    Enter the OAuth Client id used for access token retrieval.
    
    </td>
    </tr>
    </table>
    
-   To load transaction data into procurement data warehouse, you must have one or more of the following SAP Ariba applications:

    -   SAP Ariba Buying
    -   SAP Ariba Buying and Invoicing
    -   Guided sourcing capability for SAP Ariba Sourcing
    -   SAP Ariba Contracts
    -   SAP Ariba Spend Analysis




## Context

The procurement data warehouse is a capability that feeds analytics information from SAP Ariba applications, including guided sourcing capability for SAP Ariba Sourcing, SAP Ariba Buying and Invoicing, and SAP Spend Control Tower, to the embedded SAP Analytics Cloud. It provides data transfer, storage, loading, and reporting, and it drives visualization through advanced analytics dashboards.

You can use Identity Provisioning to configure procurement data warehouse as a source system where you can read users and groups and provision them to target systems of your choice for custom reporting. The source system consumes SCIM 2.0 API provided by procurement data warehouse.



<a name="loio13f60ee7604b489eb87d15cd728e8b59__steps_pl4_rlx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *Procurement Data Warehouse* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the SAP Analytics Cloud URL for your procurement data warehouse.
    
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
    
    `client_id`
    
    </td>
    <td valign="top">
    
    Enter the OAuth client id, generated for your procurement data warehouse. \(see the **Prerequisites** section\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your procurement data warehouse instance.

    This token URL is listed in the *OAuth Clients* section of the *App Integration* page.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `pdw.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those procurement data warehouse users matching the filter expression will be read. For example:

    -   *userName eq "Julie Armstrong"*

    -   *userName sw "J"*

    -   *emails eq "julie.armstrong@example.com"*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`pdw.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes procurement data warehouse groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `PDW_`

    You can use the example value or provide your own.

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the procurement data warehouse source system and will be provisioned to the target system with the following name pattern: <code>PDW_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way procurement data warehouse groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the procurement data warehouse groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *procurement data warehouse* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your procurement data warehouse system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    > ### Note:  
    > To access the Procurement Data Warehouse API documentation, contact theProcurement Data Warehouse technical support.

    **Default transformation:**

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
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.preferredLanguage",
    >                 "optional": true,
    >                 "targetPath": "$.preferredLanguage"
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
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
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:user-custom-parameters:1.0']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:user-custom-parameters:1.0']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:scim:schemas:extension:enterprise:1.0']",
    >                 "optional":true,
    >                 "targetPath": "$['urn:scim:schemas:extension:enterprise:1.0']"
    >             },
    >             {
    >                 "sourcePath": "$.roles",
    >                 "targetPath": "$.roles",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.photos",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.photos",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "functions": [
    >                     {
    >                         "condition": "'%pdw.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "applyOnElements": true,
    >                         "applyOnAttribute": "display",
    >                         "prefix": "%pdw.group.prefix%"
    >                     }
    >                 ]
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
    >                         "condition": "'%pdw.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "prefix": "%pdw.group.prefix%"
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
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:group-custom-parameters:1.0']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:group-custom-parameters:1.0']",
    >                 "optional": true
    >              },
    >             {
    >                 "condition": "'%ips.application.id%' !== 'null'",
    >                 "constant": "%ips.application.id%",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "optional": true
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio13f60ee7604b489eb87d15cd728e8b59__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Configure OAuth Certificate Authentication](Operation-Guide/configure-oauth-certificate-authentication-a40a3f3.md "You can use outbound certificates generated by Identity Provisioning for OAuth authentication with provisioning systems.")

