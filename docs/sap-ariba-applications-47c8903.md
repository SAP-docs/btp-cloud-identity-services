<!-- loio47c890311337469e8615de705c54b3f4 -->

# SAP Ariba Applications

Follow this procedure to set up SAP Ariba Applications as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   You have created a client application on [SAP Ariba APIs Portal](https://developer.ariba.com/api) that needs to be enabled for Identity Provisioning.

    > ### Note:  
    > If you don’t have an account on SAP Ariba Developer Portal, then ask your **Designated Support Contact** \(DSC\) to submit a [request for an account](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/f7dbeb26531140e7bab57170a24e3701.html). To find your DSC person, see: [How can I see my company's Basic users and Designated Support Contacts \(DSC\)](https://support.ariba.com/item/view/184249)

-   Provide your DSC person with your SAP Ariba **realm name**, **application name**, and **application key**. You have already created the application name along with the application key on *step 1*. To find your realm name, login to your SAP Ariba system – it's part of your login URL, as shown in the following examples.
    -   *SAP Ariba Buyer* example: `https://s1.ariba.com/Buyer/Main/ad/loginPage/...&realm=`*mycompany-t*
    -   *SAP Ariba Sourcing* example: `http://`*mycompany*`.sourcing.ariba.com/`

-   Ask your DSC person to submit a service request for you to *SAP Ariba Support* for component **BNS-ARI-SS-API**, requesting the client application to be enabled for Identity Provisioning. Request your DSC person to mention the following details in the service request:
    -   Application name
    -   Application key
    -   Realm name

-   When your application is enabled, you can login to [SAP Ariba APIs Portal](https://developer.ariba.com/api), find your application, and generate a new OAuth secret for it. To learn how, see: [How to generate the OAuth Secret and Base64 Encoded Client and secret](https://help.sap.com/viewer/b61dd8c7e22c4fe489f191f66b4c48d6/cloud/en-US/81f493759bbb42e5b7486bfdf8185fa3.html)
-   To configure your *SAP Ariba Applications* provisioning system \(see the procedure below\), you will need to map your SAP Ariba application parameters to the relevant Identity Provisioning properties. The property mapping between the two systems is as follows:


    <table>
    <tr>
    <th valign="top">

    SAP Ariba
    
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
    
    SCIM API URL
    
    </td>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    Examples:

    -   US: **https://openapi.ariba.com**
    -   Europe: **https://eu.openapi.ariba.com**
    -   UAE: **https://mn1.openapi.ariba.com**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    SAP Ariba OAuth 2.0 Token URL
    
    </td>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Examples:

    -   US: **https://api.ariba.com/v2/oauth/token** 
    -   Europe: **https://api-eu.ariba.com/v2/oauth/token**
    -   UAE: **https://api.mn1.ariba.com/v2/oauth/token**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    OAuth Client ID
    
    </td>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Alphanumeric string

    Example:**aaaa12345-1111-3333-cccc-1234567890**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    OAuth Secret
    
    </td>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    Alphanumeric string

    Example:**aaaGGG1eee12abcdefGHIJK123lmnopTTT**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Application key
    
    </td>
    <td valign="top">
    
    `ariba.applications.api.key`
    
    </td>
    <td valign="top">
    
    Alphanumeric string

    Example:**123abc123XYZ000abc123ABC012345**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    AN-ID
    
    </td>
    <td valign="top">
    
    `ariba.applications.realm.id`
    
    </td>
    <td valign="top">
    
    AN<numeric\_string\>

    Example: **AN000111222333**
    
    </td>
    </tr>
    </table>
    



<a name="loio47c890311337469e8615de705c54b3f4__context_zhf_2vx_ybb"/>

## Context

After fulfilling the prerequisites, you can create an SAP Ariba Applications target system to provision users and groups.

These target systems consume SCIM 2.0 API provided by SAP Ariba Applications. For more information about the SAP Ariba SCIM API scope of support, see [3228340](https://me.sap.com/notes/3228340).



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Ariba Applications* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the SCIM API URL for your SAP Ariba application \(see the **Prerequisites** section\).
    
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
    
    Enter the OAuth Client ID \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Secret \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.applications.api.key`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter your application key \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.applications.realm.id`
    
    </td>
    <td valign="top">
    
    Enter your AN-ID \(see the **Prerequisites** section\).
    
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
    
    Exemplary destination \(property configuration\):


    <table>
    <tr>
    <td valign="top">
    
    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `ProxyType`=*Internet*

    `URL`=*https://openapi.ariba.com*

    `User`=*aaaa12345-1111-3333-cccc-1234567890*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `OAuth2TokenServiceURL`=*https://api.ariba.com/v2/oauth/token*

    `ariba.applications.api.key`=*123abc123XYZ000abc123ABC012345*

    `ariba.applications.realm.id`=*AN000111222333*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Ariba Applications* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Ariba Applications. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Ariba APIs Portal](https://developer.ariba.com/api/apis) → *Discover* → *SUPPLIER MANAGEMENT*

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "('%ariba.applications.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%ariba.applications.group.prefix%.*/)] empty false)",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:sap:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User",
    >           "urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "condition": "$.emails[0].length() > 0",
    >         "constant": true,
    >         "targetPath": "$.emails[0].primary"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['companyCode']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['companyCode']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['costCenter']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['costCenter']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingGroup']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingGroup']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['generalLedgerAccount']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['generalLedgerAccount']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingOrganization']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingOrganization']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['currency']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['currency']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['deliverTo']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['deliverTo']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['purchasingUnit']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['purchasingUnit']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['network']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['network']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['addresses']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['addresses']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['passwordAdapter']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['passwordAdapter']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:User']['alternativeDisplayNames']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:User']['alternativeDisplayNames']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "optional": true,
    >         "targetPath": "$.locale"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "optional": true,
    >         "targetPath": "$.timezone"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers",
    >         "functions": [
    >           {
    >             "function": "putIfAbsent",
    >             "key": "type",
    >             "defaultValue": "work"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true,
    >         "functions": [
    >           {
    >             "function": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, ariba.applications.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], ariba.applications.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:Group",
    >           "urn:ietf:params:scim:schemas:extension:sap:2.0:Group",
    >           "urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:Group"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, ariba.applications.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%ariba.applications.group.prefix%",
    >             "replacement": ""
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
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:Group']['alternativeDisplayNames']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:Group']['alternativeDisplayNames']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "type": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio47c890311337469e8615de705c54b3f4__postreq_emv_vdb_kdb"/>

## Next Steps

1.  Before starting a provisioning job, you can first subscribe to the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during your jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
2.  Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

[The SAP Ariba developer portal](https://help.sap.com/viewer/b61dd8c7e22c4fe489f191f66b4c48d6/cloud/en-US/1d55722e669e4c6aaa4eda5a011519ac.html)

[Video: Create application and API approval process](https://www.youtube.com/watch?v=CQQlADnbM6w)

