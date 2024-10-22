<!-- loio202d95e7361541d994c23395d1a6a2eb -->

# SAP Intelligent Agriculture

Follow this procedure to set up SAP Intelligent Agriculture as a proxy system.



<a name="loio202d95e7361541d994c23395d1a6a2eb__prereq_zxm_qw3_pzb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have onboarded your SAP Intelligent Agriculture tenant as described in the [Onboarding with the SAP BTP Cockpit](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/ba2d9265332a4682b019b92689500fa3/0ad81c4430c54cac8746ebe44ec5b850.html) section of the *Administration Guide for SAP Intelligent Agriculture*.

-   You have OAuth credentials for SAP Intelligent Agriculture. For more information, see: [Getting the Credentials from the SAP Intelligent Agriculture Instance](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/724d45c4d2934012a35cc9982b81d9a8/9cbec11fa6434df396cfc918aed7ecde.html#getting-the-credentials-from-the-sap-intelligent-agriculture-instance).




## Context

SAP Intelligent Agriculture enables agribusinesses to sustainably increase farming efficiency by digitizing their farming processes and services from plan-to-harvest, taking advantage of data science and machine learning capabilities.

You can use Identity Provisioning to configure SAP Intelligent Agriculture as a proxy system in hybrid scenarios. For example, when SAP Intelligent Agriculture is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management, without making a direct connection between both systems. You can provision users and groups to the external backend system, which can trigger CRUD \(create, read, update, delete\) operations on users and group members back to the SAP Intelligent Agriculture.

> ### Caution:  
> You can't create or delete groups on SAP Intelligent Agriculture. That means:
> 
> -   On the attempt to create a group on SAP Intelligent Agriculture, Identity Provisioning will only add new members or update existing ones. Also, if you read a group from the external back-end system, there must be a group with the exact same display name \(case sensitive\) in the SAP Intelligent Agriculture system. Otherwise, an error will be thrown and the group members will not be updated.
> -   On the attempt to delete a group on SAP Intelligent Agriculture, Identity Provisioning will only remove its members \(group assignments\). And this can happen only if the relevant group assignments have been provisioned/are present in the target system.



<a name="loio202d95e7361541d994c23395d1a6a2eb__steps_ymg_b43_rzb"/>

## Procedure

1.  Open your subaccount in SAP BTP cockpit \(valid for OAuth authentication to the Identity Provisioning proxy system\).

    > ### Note:  
    > If you have a bundle tenant, then in the cockpit → *Neo* → *Overview*, you can see the Global account, which SAP provides for your bundle in the corresponding Identity Provisioning region. Then, in the global account, you can see your subaccount, where the Identity Provisioning is enabled as a service for the bundle. The display name of the subaccount starts with **SAP\_BUNDLE**.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Users & Authorizations* \> *Administrators*.

3.  Create a technical user with the necessary authorizations. It will later be used by the external consumer to connect to Identity Provisioning.

    -   For **Certificate-based authentication**, follow the procedure in [Manage Certificates for Inbound Connection](Operation-Guide/manage-certificates-for-inbound-connection-952e7c7.md) → *SAP BTP, Neo Environment*

    -   For **OAuth authentication**, proceed as follows:

        1.  Go to *Security* \> *OAuth* \> *Clients* and choose *Register New Client*.

        2.  From the *Subscription* combo box, select **<provider\_subaccount\>/ipsproxy**.

        3.  From the *Authorization Grant* combo box, select **Client Credentials**.

        4.  In the *Secret* field, enter a password \(client secret\) and remember it. You will need it later, for the repository configuration in the external system.

        5.  Copy/paste and save \(in a notepad\) the generated *Client ID*. You will need it later, too.

        6.  From the left-side navigation, choose *Subscriptions* \> *Java Applications* \> *ipsproxy* .

        7.  From the left-side navigation, choose *Roles* \> *IPS\_PROXY\_USER*.

        8.  Choose *Assign* and enter **oauth\_client\_<client\_ID\>**.

            For *<client\_ID\>*, enter the one you have saved in the previous main step.


    -   For **Certificate-based authentication**, upload the certificate for the technical user of type *System*, as described in [Add System as Administrator](https://help.sap.com/docs/identity-authentication/identity-authentication/add-administrators?version=Cloud#add-system-as-administrator) and enable the *Access Proxy System API* permission.

    -   For **Basic authentication**, proceed as follows:

        1.  Add an administrator user of type **System** and configure the basic authentication method for this user.

            If you already have a technical user, skip this step.

        2.  Save your changes.

        3.  Select your administrator user of type **System** and enable the *Access Proxy System API* permission.

        4.  Save your changes.



4.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

5.  Add *SAP Intelligent Agriculture* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

6.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Enter the URL related to your SAP Intelligent Agriculture system, in format: `https://*.prod-<region>.ia.agribusiness.cloud.sap`

    , where *\*.* is the name of your subaccount.

    For example: `https://custom-domain.prod-eu10.ia.agribusiness.cloud.sap`
    
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
    
    Enter the OAuth Client Id, created for your SAP Intelligent Agriculture instance \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, created for your SAP Intelligent Agriculture instance \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Intelligent Agriculture instance, in format: `https://<TENANT>.authentication.<REGION>.hana.ondemand.com/oauth/token` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ia.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Intelligent Agriculture users matching the filter expression will be read.

    For example: *userName eq "Smith.J"*

    For more information, see [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ia.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Intelligent Agriculture groups matching the filter expression will be read.

    **Possible values:**

    -   *intagri\_Data\_Scientist*

    -   *intagri\_Farm\_Manager*

    -   *intagri\_Operator*

    -   *intagri\_Operations\_Planner*

    -   *intagri\_Master\_Data\_Manager*

    -   *intagri\_Administrator*


    For example: *displayName eq "intagri\_Master\_Data\_Manager"*

    For more information, see [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ia.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    When Identity Provisioning attempts to provision a user for the first time, it may detect that this user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

    This property defines by which unique attribute\(s\) the existing user will be searched and resolved. If the service finds a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find a user on the target system via this filter, the creation will fail.

    **Default behavior**: The property is missing during system creation. Its default value is *userName*. This means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such *userName* is not found, the creation of the conflicting user fails.

    **Possible values:**

    -   *userUuid*
    -   *emails*
    -   *userName*
    -   *externalId*

    Default value: *userName*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ia.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    When Identity Provisioning attempts to provision a user for the first time, it may detect that this user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

    This property defines by which unique attribute\(s\) the existing user will be searched and resolved. If the service finds a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find a user on the target system via this filter, the creation will fail.

    **Default behavior**: The property is automatically added during system creation. Its default value is *userUuid*. This means, if the service finds an existing user by a *userUuid*, it updates this user with the data of the conflicting one. If a user with such *userUuid* is not found, the creation of the conflicting user fails.

    **Possible values:**

    -   *userUuid*
    -   *emails*
    -   *userName*
    -   *externalId*

    Default value: *userUuid*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ia.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

    -   If set to *true*, `PATCH` operations are used to update users and groups in the target system. This means, for example, that if a group member is removed from a group, only these changes will be provisioned and applied in the target system.

    -   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ia.include.if.match.wildcard.header` 
    
    </td>
    <td valign="top">
    
    Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Intelligent Agriculture system for entity versioning.

    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    > ### Note:  
    > The Identity Provisioning implementation of the SCIM Proxy API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).

7.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Intelligent Agriculture* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    > ### Note:  
    > When Identity Authentication is configured as a source system, the default transformation logic:
    > 
    > -   Provisions only groups and user group assignments if they are part of the following predefined group list:
    >     -   *intagri\_Data\_Scientist*
    > 
    >     -   *intagri\_Farm\_Manager*
    > 
    >     -   *intagri\_Operator*
    > 
    >     -   *intagri\_Operations\_Planner*
    > 
    >     -   *intagri\_Master\_Data\_Manager*
    > 
    >     -   *intagri\_Administrator*
    > 
    > 
    > -   Skips some of the attributes from the identity records.
    > 
    > This way, the transformation logic ensures that the identity data, sent to the Identity Provisioning SCIM REST API, is consistent.

    > ### Note:  
    > When а user is deleted from the SAP Intelligent Agriculture target system, depending on the off-boarding user handling it can be deleted or set to anonymized.
    > 
    > If you try to read such user, you get only its *id* and the other attributes have value `ANONYMOUS`.
    > 
    > If you try to create again a user with the same unique attributes \(`userUuid`, `externalId`, `userName`, and `email`l\) during the configured retention period, the existed entity is restored to its active state. If the create operation requests changes in the values of the attributes, they will be executed after triggering a resync job.
    > 
    > For more information, see [Data Retention Manager](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/ba2d9265332a4682b019b92689500fa3/e55cbc4d42aa4059a835711c5fba1c44.html?locale=en-US).

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Intelligent Agriculture system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    [SAP Intelligent Agriculture SCIM API](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/724d45c4d2934012a35cc9982b81d9a8/1919b94dc2c84711ab65fd63002b9bce.html)

    Default read and write transformations:

    > ### Tip:  
    > The proxy *Read Transformation* is used when the external client application \(for example, SAP Identity Management\) makes initial load. That is, executing GET requests to the resource endpoints \(**/Users** or **/Groups**\) to retrieve the corresponding entities of the particular type. The external client application can also execute GET requests to a single resource endpoint \(querying a single resource is supported\). In this case, the proxy system acts as a *source* one.
    > 
    > The proxy *Write Transformation* is used when the external application manages the entities in the proxy system – creates new entities, updates existing ones, or deletes existing ones. In this case, the proxy system acts as a *target* one.
    > 
    > However, after a *Create* or *Update* operation is performed on the proxy system, the *Read Transformation* is applied to the result, so that the created or updated entity is sent back to the external application. This behavior demonstrates that the proxy *Read Transformation* is used for *write* cases, as well.


    <table>
    <tr>
    <th valign="top">

    Read Transformation
    
    </th>
    <th valign="top">

    Write Transformation
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.meta",
    >                 "targetPath": "$.meta"
    >             },
    >             {
    >                 "sourceVariable": "entityBaseLocation",
    >                 "targetPath": "$.meta.location",
    >                 "targetVariable": "entityLocationSourceSystem",
    >                 "functions": [
    >                     {
    >                         "type": "concatString",
    >                         "suffix": "${entityIdSourceSystem}"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.userUuid",
    >                 "targetPath": "$.userUuid"
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "optional": true,
    >                 "targetPath": "$.name"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.emails[0].value",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']"
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups"
    >             }
    >         ],
    >         "scimEntityEndpoint": "Users"
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.meta",
    >                 "targetPath": "$.meta"
    >             },
    >             {
    >                 "sourceVariable": "entityBaseLocation",
    >                 "targetPath": "$.meta.location",
    >                 "targetVariable": "entityLocationSourceSystem",
    >                 "functions": [
    >                     {
    >                         "type": "concatString",
    >                         "suffix": "${entityIdSourceSystem}"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members"
    >             }
    >         ],
    >         "scimEntityEndpoint": "Groups"
    >     }
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
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
    >                 "sourcePath": "$.userUuid",
    >                 "targetPath": "$.userUuid"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.Operations",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.Operations",
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas",
    >                 "scope": "patchEntity"
    >             }
    >         ],
    >         "scimEntityEndpoint": "Users"
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schema[0]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]"
    >             },
    >             {
    >                 "sourcePath": "$.Operations",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.Operations",
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas",
    >                 "scope": "patchEntity"
    >             }
    >         ],
    >         "scimEntityEndpoint": "Groups"
    >     }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
8.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.




<a name="loio202d95e7361541d994c23395d1a6a2eb__postreq_cf4_lgj_kfb"/>

## Next Steps

When a proxy system is connected to an external backend system \(in the case of SAP Identity Management this means the exported CSV file is imported into the Identity Management Admin UI and a repository is configured\), you can start managing the users and groups into this external system. Usually, the first operation is the initial load of the existing entities into your external system. When this load has finished, changes in the external system, such as creating new users or updating existing ones, can trigger CRUD requests back to the proxy system.

To see an example with SAP Identity Management, see [Hybrid Scenario: SAP Identity Management](https://help.sap.com/docs/identity-provisioning/identity-provisioning/hybrid-scenario-sap-identity-management?version=Cloud) → sections **Next Steps** and **Future Identity Lifecycle**.

> ### Caution:  
> Effective **September 2020**, Shanghai \(China\) tenants that reside on SAP BTP, Neo environment can be only accessed on the following domain: `dispatcher.cn1.platform.sapcloud.cn`
> 
> So make sure you use the correct domain when you construct your REST API requests.
> 
> For example: **GET** *https://ipsproxyabcd12345-xyz789.dispatcher.cn1.platform.sapcloud.cn/ipsproxy/api/v1/scim/bbb111aa-1234-aaaa-7777-1234567abcde/Users/s123456789*
> 
> To learn more, see: [Proxy Systems](proxy-systems-b10d68a.md)

