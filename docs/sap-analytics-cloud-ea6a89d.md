<!-- loioea6a89de7a8242a497f42655bef9bef1 -->

# SAP Analytics Cloud

Follow this procedure to set up SAP Analytics Cloud as a target system.



<a name="loioea6a89de7a8242a497f42655bef9bef1__prereq_qcc_vk2_2cb"/>

## Prerequisites

-   In SAP Analytics Cloud, you have enabled a custom SAML Identity Provider, for which *User Attribute* is set to **Custom SAML User Mapping**. To learn how, see: [Enabling a Custom SAML Identity Provider](https://help.sap.com/doc/00f68c2e08b941f081002fd3691d86a7/release/en-US/3651184dad944aa2b361ad029a7a8cae.html)

-   Add an OAuth client with authorization grant **Client Credentials**. To learn how, see: [Managing OAuth Clients and Trusted Identity Providers](https://help.sap.com/doc/00f68c2e08b941f081002fd3691d86a7/release/en-US/4f43b54398fc4acaa5efa32badfe3df6.html)




## Context

SAP Analytics Cloud is an all-in-one cloud product offered as software as a service for business intelligence, planning, and predictive analytics.

You can use Identity Provisioning to configure SAP Analytics Cloud as a target system where you can provision users and groups. The target system consumes SCIM 2.0 API provided by SAP Analytics Cloud. For more information, see [SAP Analytics Cloud: User and Team Provisioning API](https://help.sap.com/viewer/298f82da4b184d1fb825b7ffe365e94a/release/en-US/36c9929c050e428ba6b391bf16b018fc.html).

There are two versions of the SAP Analytics Cloud SCIM API. They are handled by the`sac.api.version` property as follows:

-   When the value is set to `1` or the property is not defined \(typical for systems created before versioning was introduced on April 10, 2023\), SAP Analytics Cloud SCIM API version 1 is used. This is the default value.

-   When the value is set to `2` - SAP Analytics Cloud SCIM API version 2 is used. This version is released with enhancements, such as: support for patch operations.


For more information on the differences between SAP Analytics Cloud SCIM API version 1 and 2, see [Managing Users and Teams](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/ee11077e8a344ce99dfb77033eace581.html).

For more information on how to update to version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Analytics Cloud* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    `sac.api.csrf.protection`
    
    </td>
    <td valign="top">
    
    Specifies whether to fetch a CSRF token when sending requests to the system.

    This property is automatically added to the system, with default value: **enabled**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `csrf.token.path`
    
    </td>
    <td valign="top">
    
    Path which is appended to the URL to retrieve the CSRF token.

    The property is automatically added during system creation, when the system in use is SAP Analytics Cloud consuming SCIM API version 2.

    Based on the version of the SCIM API consumed, the default value for the property is:

    -   SAP Analytics Cloud SCIM API version 1: `/api/v1/scim/Users?count=1`

        > ### Note:  
        > The property is present only for systems created before December 3, 2024. Systems created after this date use the default value for the connector version without adding the property.

    -   SAP Analytics Cloud SCIM API version 2: `/api/v1/scim2/Users?count=1`

        > ### Note:  
        > If you delete the property, the Identity Provisioning will use the default value for the property for SAP Analytics Cloud using SCIM API**version 1**.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sac.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Analytics Cloud. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

    According to your use case, choose how to set up this property:

    -   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
    -   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
    -   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

    > ### Note:  
    > If this property is missing, or you've deleted it, and the service does not find such a *userName*, it will try again to resolve the conflicting user – by *email*. If the second attempt for resolution is unsuccessful too, the creation of the conflicting user fails.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
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
    <tr>
    <td valign="top">
    
    \(Optional\) `sac.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    Set this property to *true* if you want to enable SCIM bulk operations for provisioning users. That means, the Identity Provisioning service can write, update, and delete a potentially large collection of users in a single request. For more information, see: [SCIM Protocol: Bulk Operations](https://datatracker.ietf.org/doc/html/rfc7644#section-3.7)

    If not specified, the default value is *false*.

    > ### Note:  
    > SCIM bulk operations are not supported for provisioning groups to SAP Analytics Cloud.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sac.bulk.operations.max.count`
    
    </td>
    <td valign="top">
    
    If you have enabled the SCIM bulk operations, you can use this property to set the number of users to be provisioned per request.

    Default value:

    -   `100` - when using SAP Analytics Cloud SCIM API version 1.

    -   `30` - when using SAP Analytics Cloud SCIM API version 2.


    > ### Note:  
    > The value must not exceed the number of entities defined by the SAP Analytics Cloud system as a SCIM service provider. Otherwise, the provisioning job will fail with HTTP response code 413 \(*Payload Too Large*\).


    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Analytics Cloud* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Analytic Cloud system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Analytics Cloud REST API: Managing Users and Teams](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/ee11077e8a344ce99dfb77033eace581.html)

    [Managing Users and Teams → api/v1/scim](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/42d90beb6337476984fcc7c54ec146dd.html)

    [Managing Users and Teams → api/v1/scim2](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/e34d2555509548028b76a7862cc5b84a.html)

    **Default transformation for SAP Analytics Cloud SCIM API version 1:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "($.emails[0].value EMPTY false) && isValidEmail($.emails[0].value)",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
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
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "condition": "$.emails[0].length() > 0",
    >                 "targetPath": "$.emails[0].primary",
    >                 "constant": true
    >             },
    >             {
    >                 "sourcePath": "$.roles",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.roles"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:scim:schemas:extension:enterprise:1.0']['manager']['managerId']",
    >                 "functions": [
    >                     {
    >                         "type": "resolveEntityIds"
    >                     }
    >                 ]
    >             }
    >         ]
    >     },
    >     "group": {
    >         "condition": "('%sac.group.prefix%' === 'null') || ($.displayName =~ /%sac.group.prefix%.*/)",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.id",
    >                 "scope": "createEntity",
    >                 "functions": [
    >                     {
    >                         "condition": "('%sac.group.prefix%' !== 'null') && (@ =~ /%sac.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%sac.group.prefix%",
    >                         "replacement": ""
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "('%sac.group.prefix%' !== 'null') && (@ =~ /%sac.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%sac.group.prefix%",
    >                         "replacement": ""
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.roles",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.roles"
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

    **Default transformation for SAP Analytics Cloud SCIM API version 2:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "($.emails[0].value EMPTY false) && isValidEmail($.emails[0].value)",
    >     "mappings": [
    >       {
    >         "constant": [
    >           "urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters",
    >           "urn:ietf:params:scim:schemas:core:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value != []",
    >         "sourcePath": "$.emails[?(@.primary == true)].value",
    >         "preserveArrayWithSingleElement": false,
    >         "optional": true,
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "optional": true,
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "optional": true,
    >         "targetPath": "$.name.middleName"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "optional": true,
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "optional": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "condition": "$.emails[0].length() > 0",
    >         "constant": true,
    >         "targetPath": "$.emails[0].primary"
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
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']"
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']['idpUserId']"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value != []",
    >         "sourcePath": "$.emails[?(@.primary == true)].value",
    >         "preserveArrayWithSingleElement": false,
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']['idpUserId']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']['idpUserId']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']['idpUserId']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "functions": [
    >           {
    >             "type": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "('%sac.group.prefix%' === 'null') || ($.displayName =~ /%sac.group.prefix%.*/)",
    >     "mappings": [
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:Group",
    >           "urn:sap:params:scim:schemas:extension:sac:2.0:group-roles",
    >           "urn:sap:params:scim:schemas:extension:sac:2.0:group-custom-parameters"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.id",
    >         "scope": "createEntity",
    >         "functions": [
    >           {
    >             "condition": "('%sac.group.prefix%' !== 'null') && (@ =~ /%sac.group.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%sac.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "('%sac.group.prefix%' !== 'null') && (@ =~ /%sac.group.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%sac.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.roles"
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
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-roles']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-roles']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-custom-parameters']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-custom-parameters']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-custom-parameters']['description']"
    >       }
    >     ]
    >   }
    > }
    > ```

    > ### Caution:  
    > When provisioning users and groups between a source system and SAP Analytics Cloud, groups are mapped to teams in SAP Analytics Cloud. Those teams can then get role assignments in SAP Analytics Cloud.
    > 
    > If you then run another provisioning job \(**Read** or **Resync**\), role assignments of SAP Analytics Cloud teams will be removed as a result of an update operation being executed. This behavior \(causing permission issues for users\) is expected, as SAP Analytics Cloud role assignments are not available as group parameters in some source systems, for example – Identity Authentication. To avoid this, you need to change the transformation of the *SAP Analytics Cloud* target system, as described in SAP Note [3027079](https://me.sap.com/notes/3027079).

    > ### Note:  
    > Updating a user in SAP Analytics Cloud using SCIM API version 2 depends on whether user attributes in SAP Analytics Cloud are mapped to SAML attributes in your identity provider. If this is the case, the values of those attributes are populated by the identity provider and cannot be changed by the SAP Analytics SCIM API or the UI. For more information, see [Map SAML Attributes to Users](https://help.sap.com/doc/00f68c2e08b941f081002fd3691d86a7/2021.20/en-US/5e917dc3fc8f42828d4dfa850e78c913.html)

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)

    > ### Caution:  
    > The **email** attribute is unique for *SAP Analytics Cloud* but it might not be unique for other systems, such as *SAP SuccessFactors*. That's why, when you choose a source system, make sure that there are no users with duplicate e-mails. If there are such, then after the provisioning job all users with the same e-mail address will be created as a single user in *SAP Analytics Cloud*.
    > 
    > To learn more, see *Guided Answers*: [Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)
    > 
    > To learn more about excluding users from SAP Analytics Cloud target, see: [Exclude Users from Provisioning to Target Systems](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:55088)




<a name="loioea6a89de7a8242a497f42655bef9bef1__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[\(Guided Answers\) Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)

