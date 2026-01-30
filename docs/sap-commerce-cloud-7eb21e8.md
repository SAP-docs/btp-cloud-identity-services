<!-- loio7eb21e8ad805466f98a1d12ba8f97a73 -->

# SAP Commerce Cloud

Follow this procedure to set up SAP Commerce Cloud as a source system.



<a name="loio7eb21e8ad805466f98a1d12ba8f97a73__prereq_qcc_vk2_2cb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   In SAP Commerce Cloud, you have added an OAuth client with authorization grant **Client Credentials**. To learn how, see: [Configuring OAuth Client](https://help.sap.com/docs/SAP_COMMERCE_INTEGRATIONS/b6a1e8b75222421a8faf0269e8fbd0dc/e16a6e289ec84a68b8ea2e21fcb79ed5.html?locale=en-US&version=2108).




<a name="loio7eb21e8ad805466f98a1d12ba8f97a73__context_w5f_nlx_rdb"/>

## Context

SAP Commerce Cloud is a highly flexible and modular platform for delivering modern customer experiences. It provides a standardized, automated, end-to-end solution that allows your projects to release code from repository to cloud.

You can use Identity Provisioning to configure SAP Commerce Cloud as a source system to read users and groups. These source systems consume SCIM 2.0 API provided by SAP Commerce Cloud. For more information, see [Commerce Cloud SCIM Web Services API Documentation](https://help.sap.com/docs/SAP_COMMERCE_CLOUD_PUBLIC_CLOUD/452dcbb0e00f47e88a69cdaeb87a925d/baaa605b6a6f4907a2fc1cc917d8c6c7.html).



<a name="loio7eb21e8ad805466f98a1d12ba8f97a73__steps_pl4_rlx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Commerce Cloud* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL to your SAP Commerce Cloud system.

    The URL follows the pattern: `https://backoffice.<tenant>. model-t.cc.commerce.ondemand.com`

    You can find the correct URL in the *Environments* section of SAP Cloud Portal.
    
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
    
    Enter the client ID to retrieve the OAuth access token for SAP Commerce Cloud.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the client secret to retrieve the OAuth access token for SAP Commerce Cloud.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Commerce Cloud instance.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cc.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those users matching the filter expression will be read. You can filter users by `userName`, `emails.value`, and `externalId`, according to the API syntax of SAP Commerce Cloud.

    For example:

    -   *userName eq "johnbrown" and externalId eq "P000252"*
    -   *userName eq "johnbrown" and emails.value eq "johnbrown@email.com"*
    -   *userName eq "johnbrown" and emails.value eq "johnbrown@email.com" and externalId eq "P000252"*

        > ### Note:  
        > These combinations are valid for both 'or' and 'and' operators.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cc.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those groups matching the filter expression will be read.

    For example:

    *displayName eq "ProjectTeam1" or "Students2018"*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Commerce Cloud* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Commerce Cloud system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [Commerce Cloud SCIM Web Services API Documentation](https://help.sap.com/docs/SAP_COMMERCE_CLOUD_PUBLIC_CLOUD/452dcbb0e00f47e88a69cdaeb87a925d/baaa605b6a6f4907a2fc1cc917d8c6c7.html)

    > ### Note:  
    > When configuring SAP Commerce Cloud as a source system, note that there may be mismatches between optional and required user attributes in the given target systems. For example, the email is an optional attribute in SAP Commerce Cloud but a required one in Identity Authentication. In such cases, you need to review and adapt your source and/or target system transformations and configurations to reflect your needs.

    > ### Note:  
    > Users that are created in SAP Commerce Cloud through the UI, don’t have an ID and a username. As the ID is a mandatory attribute by SCIM specification, provisioning of those users to target systems will fail.
    > 
    > To solve this, create the users in SAP Commerce Cloud through API or implement ImpEx \(import and export\) for user ID provisioning, as described in [Configuring SAP Commerce Cloud](https://help.sap.com/docs/SAP_COMMERCE_INTEGRATIONS/f5c1fa314b8e434291c1cf71034c8132/ef1a66dcb9df4e9ebaa2ec8985cdad29.html).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "optional": true,
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.nickName",
    >                 "optional": true,
    >                 "targetPath": "$.nickName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional": true,
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.name.middleName",
    >                 "optional": true,
    >                 "targetPath": "$.name.middleName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true,
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificSuffix",
    >                 "optional": true,
    >                 "targetPath": "$.name.honorificSuffix"
    >             },
    >             {
    >                 "sourcePath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.addresses",
    >                 "functions": [
    >                     {
    >                         "type": "convertCountryCode",
    >                         "outputFormat": "alpha2",
    >                         "inputAttributes": [
    >                             "country"
    >                         ],
    >                         "outputAttribute": "country"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.userType",
    >                 "optional": true,
    >                 "targetPath": "$.userType"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "optional": true,
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "condition": "'%ips.application.id%' !== 'null'",
    >                 "constant": "%ips.application.id%",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >             },
    >             {
    >                 "constant": "authorization",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                    {
    >                         "function": "concatString",
    >                         "condition": "'%cc.group.prefix%' !== 'null'",
    >                         "prefix": "%cc.group.prefix%"
    >                    }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members"
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a target system to provision users and groups into it. Choose from:[Target Systems](target-systems-ab3f641.md).




<a name="loio7eb21e8ad805466f98a1d12ba8f97a73__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Cloud Identity Services Integration Architecture → cloudscimwebservices extension](https://help.sap.com/docs/SAP_COMMERCE_CLOUD_PUBLIC_CLOUD/403d43bf9c564f5a985913d1fbfbf8d7/e328e37a72924a50a12329a93949d286.html)

