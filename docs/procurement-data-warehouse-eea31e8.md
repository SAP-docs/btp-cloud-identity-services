<!-- loioeea31e8c7d094678bb77e8297d78d22d -->

# Procurement Data Warehouse

Follow this procedure to set up procurement data warehouse as a target system.



<a name="loioeea31e8c7d094678bb77e8297d78d22d__prereq_oky_mqb_gzb"/>

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

You can use Identity Provisioning to configure procurement data warehouse as a target system where you can provision users and groups. The target system consumes SCIM 2.0 API provided by procurement data warehouse.



<a name="loioeea31e8c7d094678bb77e8297d78d22d__steps_b5y_gll_cxb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *Procurement Data Warehouse* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    `pdw.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    It defines by which unique attribute\(s\) an existing user to be resolved in the event of conflicting users.

    Default value: **userName**

    Possible values:

    -   **emails\[0\].value**
    -   **userName,emails\[0\].value**

    > ### Note:  
    > If this property is missing, or you've deleted it, and the service does not find such a *userName*, it will try again to resolve the conflicting user – by *email*. If the second attempt for resolution is unsuccessful too, the creation of the conflicting user fails.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
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

    When **set in the target system**, only groups containing the `PDW_` prefix in their display name will be provisioned to procurement data warehouse. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to procurement data warehouse.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `pdw.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    Set this property to *true* if you want to enable SCIM bulk operations for provisioning users. That means, the Identity Provisioning service can write, update, and delete a potentially large collection of users in a single request. For more information, see: [SCIM Protocol: Bulk Operations](https://datatracker.ietf.org/doc/html/rfc7644#section-3.7)

    If not specified, the default value is *false*.

    > ### Note:  
    > SCIM bulk operations are not supported for provisioning groups to procurement data warehouse.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `pdw.bulk.operations.max.count`
    
    </td>
    <td valign="top">
    
    If you have enabled the SCIM bulk operations, you can use this property to set the number of users to be provisioned per request.

    Default value: `20`

    > ### Note:  
    > The value must not exceed the number of entities defined by the procurement data warehouse system as a SCIM service provider. Otherwise, the provisioning job will fail with HTTP response code 413 \(*Request Entity Too Large*\).


    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the procurement data warehouse target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your procurement data warehouse system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    > ### Note:  
    > To access the Procurement Data Warehouse API documentation, contact theProcurement Data Warehouse technical support.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "($.emails[0].value EMPTY false)",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:user-custom-parameters:1.0"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.emails[0].value",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "condition": "$.emails[?(@.primary == true)].value != []",
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "preserveArrayWithSingleElement": false,
    >                 "optional": true,
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.preferredLanguage",
    >                 "optional": true,
    >                 "targetPath": "$.preferredLanguage"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.name.givenName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "targetPath": "$.name.familyName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "condition": "$.emails[0].length() > 0",
    >                 "targetPath": "$.emails[0].primary",
    >                 "constant": true
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
    >                 "sourcePath": "$.roles",
    >                 "targetPath": "$.roles",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.photos",
    >                 "targetPath": "$.photos",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.groups[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups[?(@.value)]",
    >                 "functions": [
    >                     {
    >                       "entityType": "group",
    >                       "function": "resolveEntityIds"
    >                     }
    >                 ]
    >       }
    >         ]
    >     },
    >     "group": {
    >         "condition": "('%pdw.group.prefix%' === 'null') || ($.displayName =~ /%pdw.group.prefix%.*/)",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": [
    >                   "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                   "urn:ietf:params:scim:schemas:extension:sap:group-custom-parameters:1.0"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.id",
    >                 "scope": "createEntity",
    >                 "functions": [
    >                     {
    >                         "condition": "('%pdw.group.prefix%' !== 'null') && (@ =~ /%pdw.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%pdw.group.prefix%",
    >                         "replacement": ""
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "('%pdw.group.prefix%' !== 'null') && (@ =~ /%pdw.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%pdw.group.prefix%",
    >                         "replacement": ""
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]",
    >                 "functions": [
    >                     {
    >                         "function": "resolveEntityIds"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:group-custom-parameters:1.0']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:group-custom-parameters:1.0']",
    >                 "optional": true
    >             }
    >         ]
    >     }
    > }
    > ```

    If you try to provision groups that already exist in procurement data warehouse, your provisioning job may fail with: ‘*The group already exists on the target system and cannot be provisioned*’ error. This happens after a reset of the procurement data warehouse target system or if you create a new target system connected to an existing procurement data warehouse backend.

    To avoid this, you have the following options:

    -   Delete the existing group in procurement data warehouse target system.

    -   Adapt the procurement data warehouse write transformation. Either ignore provisioning of groups or add temporary the *skipOperations* expression for creating groups.

    -   Avoid provisioning of already existing groups.


6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)

    > ### Caution:  
    > The **email** attribute is unique for procurement data warehouse but it might not be unique for other systems, such as *SAP SuccessFactors*. That's why, when you choose a source system, make sure that there are no users with duplicate e-mails. If there are such, then after the provisioning job all users with the same e-mail address will be created as a single user in procurement data warehouse.
    > 
    > To learn more, see *Guided Answers*: [Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)
    > 
    > To learn more about excluding users from procurement data warehouse target, see: [Exclude Users from Provisioning to Target Systems](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:55088)




<a name="loioeea31e8c7d094678bb77e8297d78d22d__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Configure OAuth Certificate Authentication](Operation-Guide/configure-oauth-certificate-authentication-a40a3f3.md "You can use outbound certificates generated by Identity Provisioning for OAuth authentication with provisioning systems.")

