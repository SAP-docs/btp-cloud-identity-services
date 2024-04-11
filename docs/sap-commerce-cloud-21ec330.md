<!-- loio21ec330fca35475fbedc0a6b8edda55a -->

# SAP Commerce Cloud

Follow this procedure to set up SAP Commerce Cloud as a target system.



<a name="loio21ec330fca35475fbedc0a6b8edda55a__prereq_qcc_vk2_2cb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   In SAP Commerce Cloud, you have added an OAuth client with authorization grant **Client Credentials**. To learn how, see: [Configuring OAuth Client](https://help.sap.com/docs/SAP_COMMERCE_INTEGRATIONS/b6a1e8b75222421a8faf0269e8fbd0dc/e16a6e289ec84a68b8ea2e21fcb79ed5.html?locale=en-US&version=2108).




## Context

SAP Commerce Cloud is a highly flexible and modular platform for delivering modern customer experiences. It provides a standardized, automated, end-to-end solution that allows your projects to release code from repository to cloud.

You can use Identity Provisioning to configure SAP Commerce Cloud as a target system to provision users and groups. These target systems consume SCIM 2.0 API provided by SAP Commerce Cloud. For more information, see [Commerce Cloud SCIM Web Services API Documentation](https://help.sap.com/docs/SAP_COMMERCE_CLOUD_PUBLIC_CLOUD/452dcbb0e00f47e88a69cdaeb87a925d/baaa605b6a6f4907a2fc1cc917d8c6c7.html).



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Commerce Cloud* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    \(Optional\) `cc.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    This property defines by which unique attribute\(s\) an existing user in the target system will be searched and resolved in case Identity Provisioning tries to provision a conflicting user.

    SAP Commerce Cloud supports the following unique attributes which are automatically filled in during system creation: `emails[0].value, userName, externalId`.

    If the service finds an existing user by at least one of the unique attributes, it updates this user with the data of the conflicting one. If such a user is not found, the update of the conflicting user fails. If more than one users with these unique attributes are found, the update fails.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cc.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If you try to provision a group that already exists in a target system, the group creation will fail. In this case, the existing group only needs to be updated.

    This property defines by which unique attribute\(s\) the existing group will be searched and resolved. The default value is `displayName`.

    If the service finds an existing group by this unique attribute, the group that you try to provision will overwrite the existing one. If such a group is not found, the group that you try to provision will not be created in the target system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cc.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

    -   If set to *true*, `PATCH` operations are used to update users and groups in the target system.

    -   If set to *false*, `PUT` operations are used to update users and groups in the target system.


    Default value for target systems: *false*
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Commerce Cloud* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    > ### Note:  
    > Users that are created in SAP Commerce Cloud through the UI, don’t have an ID and a username. When synchronizing such users from a source system to SAP Commerce Cloud target system, Identity Provisioning detects that they already exist. To resolve the conflict, the service tries to retrieve them from the target, but as they have no IDs, the users are skipped.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Commerce Cloud system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    [Commerce Cloud SCIM Web Services API Documentation](https://help.sap.com/docs/SAP_COMMERCE_CLOUD_PUBLIC_CLOUD/452dcbb0e00f47e88a69cdaeb87a925d/baaa605b6a6f4907a2fc1cc917d8c6c7.html)

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "$.userName EMPTY false",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
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
    >                 "condition": "($.addresses[*].region EMPTY false) && ($.addresses[*].country EMPTY false)",
    >                 "sourcePath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.addresses",
    >                 "functions": [
    >                     {
    >                         "type": "convertCountryRegion",
    >                         "outputFormat": "alpha2",
    >                         "inputAttributes": [
    >                             "region",
    >                             "country"
    >                         ],
    >                         "outputAttribute": "region"
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
    >                 "condition": "$.emails[?(@.primary == true)].value == []",
    >                 "sourcePath": "$.emails[0].value",
    >                 "optional": true,
    >                 "targetPath": "$.emails[0].value"
    >             },
    >             {
    >                 "condition": "$.emails[?(@.primary == true)].value != []",
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails[0].value",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "condition": "$.emails[0].length() > 0",
    >                 "constant": true,
    >                 "targetPath": "$.emails[0].primary"
    >             }
    >         ]
    >     },
    >     "group": {
    >          "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "condition": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'] EMPTY false",
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >                 "targetPath": "$.displayName"
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
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md).


**Related Information**  


[SAP Cloud Identity Services Integration Architecture → cloudscimwebservices extension](https://help.sap.com/docs/SAP_COMMERCE_CLOUD_PUBLIC_CLOUD/403d43bf9c564f5a985913d1fbfbf8d7/e328e37a72924a50a12329a93949d286.html)

