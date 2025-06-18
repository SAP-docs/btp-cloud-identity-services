<!-- loio85ea2ea0c94b428db5059acd002a7269 -->

# SAP Revenue Growth Management

Follow this procedure to set up SAP Revenue Growth Management as a target system.



<a name="loio85ea2ea0c94b428db5059acd002a7269__prereq_qcc_vk2_2cb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   You have created an SAP Revenue Growth Management consumer application in your SAP Cloud Identity Services tenant and defined a dependency to its API, as described in [Configure Integration Between Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/communicate-between-applications?locale=en-US&version=Cloud). *UserImport* must be selected for the dependency *API*.

-   You have generated API credentials for the consumer application, as described in [Generate Credentials to Access the APIs of an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/quick-start-dependent-applications?version=Cloud).




<a name="loio85ea2ea0c94b428db5059acd002a7269__context_l2v_ypw_y2c"/>

## Context

SAP Revenue Growth Management is an SAP BTP SaaS application that provides customers in the Consumer Products industry an easy way to efficiently create, monitor, and maintain account plans.

You can use Identity Provisioning to configure SAP Revenue Growth Management as a target system to provision users and groups. These target systems consume SCIM 2.0 API provided by SAP Revenue Growth Management. For more information, see [SAP Revenue Growth Management SCIM API](https://hub.sap.com/api/RGM_USER_SCIM/overview).

> ### Note:  
> Support for groups is intended for future use.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Revenue Growth Management* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the base URL of your SAP Revenue Growth Management system's SCIM API, excluding any path information.
    
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
    
    Enter the client ID generated when creating API credentials for the consumer application. For more information, see [Generate Credentials to Access the APIs of an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/quick-start-dependent-applications?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the client secret generated when creating API credentials for the consumer application. For more information, see [Generate Credentials to Access the APIs of an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/quick-start-dependent-applications?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `rgm.userImport.api.dependency.name`
    
    </td>
    <td valign="top">
    
    Enter the value of the dependency name used in the configuration of the SAP Revenue Growth Management consumer application, created in the SAP Cloud Identity Services tenant. It is used for access token retrieval from Identity Authentication.

    For more information, see [Integrating Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/integrating-applications?locale=en-US&version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `rgm.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    This property defines by which unique attribute\(s\) an existing user in the target system will be searched and resolved in case Identity Provisioning tries to provision a conflicting user.

    SAP Revenue Growth Management supports the following unique attributes which are automatically filled in during system creation: `userName,emails[0].value,externalId`.

    If the service finds an existing user by at least one of the unique attributes, it updates this user with the data of the conflicting one. If such a user is not found, the update of the conflicting user fails. If more than one users with these unique attributes are found, the update fails.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `rgm.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If you try to provision a group that already exists in a target system, the group creation will fail. In this case, the existing group only needs to be updated.

    This property defines by which unique attribute\(s\) the existing group will be searched and resolved. The default value is `['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']`. Currently, it is the only unique attribute that is supported.

    If the service finds an existing group by this unique attribute, the group that you try to provision will overwrite the existing one. If such a group is not found, the group that you try to provision will not be created in the target system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `rgm.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Revenue Growth Management groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `RGM_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `RGM_` prefix in their display name will be provisioned to SAP Revenue Growth Management. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be provisioned to SAP Revenue Growth Management.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `rgm.support.patch.operation`
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Revenue Growth Management* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Revenue Growth Management system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    **[SAP Revenue Growth Management SCIM API](https://hub.sap.com/api/RGM_USER_SCIM/overview)**

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user":{
    >     "condition": "(('%rgm.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%rgm.group.prefix%.*/)] empty false))",
    >     "mappings":[
    >       {
    >        "constant": [
    >          "urn:ietf:params:scim:schemas:core:2.0:User",
    >          "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['userId']",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "targetPath": "$.userType",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.preferredLanguage",
    >         "targetPath": "$.preferredLanguage",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.locale",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "targetPath": "$.timezone",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.addresses"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$.groups[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups[?(@.value)]",
    >         "functions": [
    >           {
    >             "entityType": "group",
    >             "type": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >    "condition": "isAttributeWithOptionalPrefix($.displayName, rgm.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], rgm.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings":[
    >       {
    >         "targetPath": "$.id",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >        "constant": [
    >          "urn:ietf:params:scim:schemas:core:2.0:Group",
    >          "urn:ietf:params:scim:schemas:extension:sap:2.0:Group",
    >          "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "optional": true,
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, rgm.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%rgm.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, rgm.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%rgm.group.prefix%",
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
    >             "entityType": "user",
    >             "type": "resolveEntityIds"
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

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md).


**Related Information**  


[SAP Revenue Growth Management](https://help.sap.com/docs/rgm?locale=en-US&task=all_tasks)

