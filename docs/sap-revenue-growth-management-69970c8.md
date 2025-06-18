<!-- loio69970c83bbc84862ac205b8c0b525198 -->

# SAP Revenue Growth Management

Follow this procedure to set up SAP Revenue Growth Management as a proxy system.



<a name="loio69970c83bbc84862ac205b8c0b525198__prereq_qcc_vk2_2cb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created an SAP Revenue Growth Management consumer application in your SAP Cloud Identity Services tenant and defined a dependency to its API, as described in [Configure Integration Between Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/communicate-between-applications?locale=en-US&version=Cloud). *UserImport* must be selected for the dependency *API*.

-   You have generated API credentials for the consumer application, as described in [Generate Credentials to Access the APIs of an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/quick-start-dependent-applications?version=Cloud).




<a name="loio69970c83bbc84862ac205b8c0b525198__context_wrv_lyn_vdb"/>

## Context

SAP Revenue Growth Management is an SAP BTP SaaS application that provides customers in the Consumer Products industry an easy way to efficiently create, monitor, and maintain account plans.

You can use Identity Provisioning to configure SAP Revenue Growth Management as a proxy system in hybrid scenarios. For example, when SAP Revenue Growth Management is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management, without making a direct connection between both systems. You can provision users and groups to the external backend system, which can trigger CRUD \(create, read, update, delete\) operations on users and group back to the SAP Revenue Growth Management.

> ### Note:  
> Support for groups is intended for future use.

> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



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

5.  Add *SAP Revenue Growth Management* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

6.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Enter the value of the dependency name used in the configuration of the SAP Revenue Growth Management consumer application, created in the SAP Cloud Identity Services tenant. It is used for access token retrieval from Identity Authentication. For more information, see [Integrating Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/integrating-applications?locale=en-US&version=Cloud).
    
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
    
    \(Optional\) `rgm.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those users matching the filter expression will be read. You can filter users by `userName`, `emails[0].value`, and `externalId`, according to the API syntax of SAP Revenue Growth Management.

    For example:

    -   *userName eq "johnbrown" and externalId eq "c167254d-25fd-5fac-af32-0b8c35e0de27"*
    -   *userName sw "J" and externalId eq "c167254d-25fd-5fac-af32-0b8c35e0de27"*
    -   *userName eq "johnbrown" and emails.value eq "johnbrown@email.com"*
    -   *userName eq "johnbrown" and emails.value eq "johnbrown@email.com" and externalId eq "c167254d-25fd-5fac-af32-0b8c35e0de27"*

        > ### Note:  
        > These combinations are valid for both 'or' and 'and' operators.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `rgm.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those groups matching the filter expression will be read.

    For example:

    *urn:sap:cloud:scim:schemas:extension:custom:2.0:Group:name eq "ProjectTeam1" or "Students2018"*
    
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


    Default value for proxy systems: *true*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

7.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Revenue Growth Management* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Revenue Growth Management. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **[SAP Revenue Growth Management SCIM API](https://hub.sap.com/api/RGM_USER_SCIM/overview)**

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
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath":"$.userName",
    >         "targetPath":"$.userName",
    >         "correlationAttribute":true
    >       },
    >       {
    >         "sourcePath": "$.meta",
    >         "targetPath": "$.meta"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >            "type": "concatString",
    >            "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary == true)].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath":"$.externalId",
    >         "targetPath":"$.externalId",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.givenName",
    >         "targetPath":"$.name.givenName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.familyName",
    >         "targetPath":"$.name.familyName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.displayName",
    >         "targetPath":"$.displayName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.userType",
    >         "targetPath":"$.userType",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.preferredLanguage",
    >         "targetPath":"$.preferredLanguage",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.locale",
    >         "targetPath":"$.locale",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.timezone",
    >         "targetPath":"$.timezone",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.active",
    >         "targetPath":"$.active",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath":"$.addresses"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       }
    >     ]
    >   },
    >    "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.meta",
    >         "targetPath": "$.meta"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >            {
    >                "type": "concatString",
    >                "suffix": "${entityIdSourceSystem}"
    >            }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >        {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true
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


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "user":{
    >     "scimEntityEndpoint": "Users",
    >     "mappings":[
    >      {
    >        "constant": [
    >          "urn:ietf:params:scim:schemas:core:2.0:User",
    >          "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:api:messages:2.0:PatchOp",
    >         "targetPath": "$.schemas[0]",
    >         "scope": "patchEntity"
    >       },
    >       {
    >         "sourcePath": "$.Operations",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.Operations",
    >         "scope": "patchEntity"
    >       },
    >       {
    >         "sourceVariable":"entityIdTargetSystem",
    >         "targetPath": "$.id"
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
    >         "sourcePath":"$.name.familyName",
    >         "targetPath":"$.name.familyName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.displayName",
    >         "targetPath":"$.displayName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.userType",
    >         "targetPath":"$.userType",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.preferredLanguage",
    >         "targetPath":"$.preferredLanguage",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.locale",
    >         "targetPath":"$.locale",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.timezone",
    >         "targetPath":"$.timezone",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.active",
    >         "targetPath":"$.active",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath":"$.addresses"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       }
    >     ]
    >   },
    >    "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
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
    >         "sourcePath": "$.Operations",
    >         "targetPath": "$.Operations",
    >         "preserveArrayWithSingleElement": true,
    >         "scope": "patchEntity"
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "scope": "patchEntity"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
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

9.  Run an initial load job.




<a name="loio69970c83bbc84862ac205b8c0b525198__postreq_cf4_lgj_kfb"/>

## Next Steps

When a proxy system is connected to an external backend system \(in the case of SAP Identity Management this means the exported CSV file is imported into the Identity Management Admin UI and a repository is configured\), you can start managing the users and groups into this external system. Usually, the first operation is the initial load of the existing entities into your external system. When this load has finished, changes in the external system, such as creating new users or updating existing ones, can trigger CRUD requests back to the proxy system.

To see an example with SAP Identity Management, see [Hybrid Scenario: SAP Identity Management](Integrating-the-Service/hybrid-scenario-sap-identity-management-6fa419a.md) → sections **Next Steps** and **Future Identity Lifecycle**.

> ### Caution:  
> Effective **September 2020**, Shanghai \(China\) tenants that reside on SAP BTP, Neo environment can be only accessed on the following domain: `dispatcher.cn1.platform.sapcloud.cn`
> 
> So make sure you use the correct domain when you construct your REST API requests.
> 
> For example: **GET** *https://ipsproxyabcd12345-xyz789.dispatcher.cn1.platform.sapcloud.cn/ipsproxy/api/v1/scim/bbb111aa-1234-aaaa-7777-1234567abcde/Users/s123456789*
> 
> To learn more, see: [Proxy Systems](proxy-systems-b10d68a.md)

**Related Information**  


[SAP Revenue Growth Management](https://help.sap.com/docs/rgm?locale=en-US&task=all_tasks)

