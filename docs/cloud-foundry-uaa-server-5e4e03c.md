<!-- loio5e4e03c94a11448ab8fa682394a6aaea -->

# Cloud Foundry UAA Server

Follow this procedure to set up the Cloud Foundry UAA server as а proxy system.



<a name="loio5e4e03c94a11448ab8fa682394a6aaea__prereq_tcl_4r3_kfb"/>

## Prerequisites

> ### Restriction:  
> This system is available for standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on SAP Cloud Identity Services infrastructure and Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have a technical user with administrator permissions for Cloud Foundry UAA to read, create, and update user account information. You need Cloud Foundry UAA version **4.2** or higher.
-   \(Optional\) You have installed the Cloud Connector in your corporate environment and have done the initial configuration. You need to do this only if the Cloud Foundry UAA server is exposed in a private corporate network. For more information, see [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loio5e4e03c94a11448ab8fa682394a6aaea__context_jgv_gc1_123"/>

## Context

User Account and Authentication Service \(UAA\) is an OAuth2 server that you can use for centralized identity management. It owns the user accounts and authentication sources, and supports standard protocols \(such as *SAML*, *LDAP*, and *OpenID Connect*\) to provide SSO and delegated authorization to Web applications. For more information, see [Cloud Foundry UAA: Overview](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#overview).

Cloud Foundry UAA is responsible for the SAP ID service to create and manage platform users \(platform administrators and platform developers\) in Cloud Foundry.

> ### Tip:  
> This connector is meant for provisioning users and groups from/to **general** Cloud Foundry systems \(they could be non-SAP ones\). If you want to trigger provisioning of entities from/to SAP Business Technology Platform Cloud Foundry applications, you'd better use [SAP BTP XS Advanced UAA \(Cloud Foundry\)](sap-btp-xs-advanced-uaa-cloud-foundry-fef74f6.md) proxy system.

These proxy systems consume SCIM 1.1 API provided by Cloud Foundry UAA.

> ### Remember:  
> You can manage users and groups to Cloud Foundry on **application** level only. You cannot manage them on a *subaccount* level.

> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).

Follow the steps below to create a SCIM 2.0 representation of your proxy Cloud Foundry UAA system. You can then provision on demand new users and groups back to Cloud Foundry UAA.



## Procedure

1.  \(Optional\) Open Cloud Connector to add an access control system mapping for the **Cloud Foundry UAA Server**. This is needed to allow the Identity Provisioning service to access the Cloud Foundry UAA system as a back-end system on the intranet. To learn how, see: [Configure Access Control \(HTTP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e7d4927dbb571014af7ef6ebd6cc3511.html)

2.  Open your subaccount in SAP BTP cockpit \(valid for OAuth authentication to the Identity Provisioning proxy system\).

    > ### Note:  
    > If you have a bundle tenant, then in the cockpit → *Neo* → *Overview*, you can see the Global account, which SAP provides for your bundle in the corresponding Identity Provisioning region. Then, in the global account, you can see your subaccount, where the Identity Provisioning is enabled as a service for the bundle. The display name of the subaccount starts with **SAP\_BUNDLE**.

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Users & Authorizations* \> *Administrators*.

4.  Create a technical user with the necessary authorizations. It will later be used by the external consumer to connect to Identity Provisioning.

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



5.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

6.  Add *Cloud Foundry UAA Server* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

7.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Specify the URL to the Cloud Foundry UAA SCIM API.

    If not sure about the exact URL, ask your Cloud Foundry UAA administrator.
    
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
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    As you need to make OAuth authentication to the UAA system, enter the URL to the OAuth2 token service.

    If not sure about the exact URL, ask your Cloud Foundry UAA administrator.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the OAuth client ID of the Cloud Foundry UAA technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth client secret of the technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `uaa.origin`
    
    </td>
    <td valign="top">
    
    Enter the location of your Cloud Foundry identity provider. If not sure about the value, ask your Cloud Foundry UAA administrator.

    The value of this property is a string, which will be used as the *origin* attribute in the system transformations.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `uaa.origin.filter.enabled`
    
    </td>
    <td valign="top">
    
    This flag property depends on `uaa.origin`. Possible values: **true** or **false**

    -   If set to *true*, the Identity Provisioning service will read only users whose identity provider is set as a value of `uaa.origin`.
    -   If set to *false*, the Identity Provisioning service will read all users, regardless of their origin.
    -   If set to *true* but the `uaa.origin` property is missing, the provisioning will fail.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `scim.support.patch.operation`
    
    </td>
    <td valign="top">
    
    Use this property if you want to modify the members of a group.

    Possible values:

    -   **true** – the Identity Provisioning service will modify the group membership via the *PATCH /Groups* endpoint of UAA. To learn how, see [Patch](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#patch-2) 
    -   **false** – the Identity Provisioning service will modify the group membership via the *POST /Groups* or *DELETE /Groups* endpoints of UAA. To learn how, see [Add Member](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#add-member) and [Remove Member](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#remove-member).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `uaa.patch.response.with.resource`
    
    </td>
    <td valign="top">
    
    Use this property if you want to retrieve a group whose membership was modified.

    > ### Note:  
    > This property is usable only when you have configured membership modifications via *Add/Remove Member* UAA endpoints. That is, when the `scim.support.patch.operation` property is set to **false**.

    Possible values:

    -   **true** – the Identity Provisioning service will return the modified group via the *GET /Groups* endpoint of UAA. To learn how, see [Retrieve](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#retrieve-2).
    -   **false** – no modified groups will be returned by the service.


    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    Exemplary destination:


    <table>
    <tr>
    <td valign="top">
    
    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `ProxyType`=*Internet*

    `URL`=*https://api.authentication.hana.ondemand.com*

    `OAuth2TokenServiceURL`=*https://MyCFaccount.authentication.hana.ondemand.com/oauth/token*

    `User`=*MyCFuser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `uaa.origin`=*my\_UAA\_location*

    `uaa.origin.filter.enabled`=*true*

    `scim.support.patch.operation`=*true*

    `uaa.patch.response.with.resource`=*false*
    
    </td>
    </tr>
    </table>
    
8.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Cloud Foundry UAA Server* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Cloud Foundry UAA server. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [Cloud Foundry UAA API: Users](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#users)

    [Cloud Foundry UAA API: Groups](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#groups)

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
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "targetPath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.meta",
    >         "targetPath": "$.meta",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.origin",
    >         "targetPath": "$.origin",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.zoneId",
    >         "targetPath": "$.zoneId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.verified",
    >         "targetPath": "$.verified",
    >         "optional": true
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       }
    >     ],
    >     "scimEntityEndpoint": "Users"
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.description",
    >         "targetPath": "$.description",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.zoneId",
    >         "targetPath": "$.zoneId"
    >       },
    >       {
    >         "sourcePath": "$.meta",
    >         "targetPath": "$.meta",
    >         "optional": true
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       }
    >     ],
    >     "scimEntityEndpoint": "Groups"
    >   }
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "constant": "uaa-dummy-value",
    >         "targetPath": "$.id",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value == []",
    >         "targetPath": "$.emails[0].primary",
    >         "constant": true
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.verified",
    >         "targetPath": "$.verified",
    >         "optional": true
    >       },
    >       {
    >         "constant": "%uaa.origin%",
    >         "targetPath": "$.origin"
    >       },
    >       {
    >         "constant": "urn:scim:schemas:core:1.0",
    >         "targetPath": "$.schemas[0]"
    >       }
    >     ],
    >     "scimEntityEndpoint": "Users"
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.description",
    >         "targetPath": "$.description",
    >         "optional": true
    >       },
    >       {
    >         "constant": "urn:scim:schemas:core:1.0",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >           {
    >             "condition": "@.type EMPTY false",
    >             "function": "toUpperCaseString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "type",
    >             "locale": "en_EN"
    >           }
    >         ]
    >       },
    >       {
    >         "constant": "%uaa.origin%",
    >         "targetPath": "$.members[*].origin",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
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
    >       }
    >     ],
    >     "scimEntityEndpoint": "Groups"
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
9.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.




<a name="loio5e4e03c94a11448ab8fa682394a6aaea__postreq_cf4_lgj_kfb"/>

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


[Cloud Foundry UAA: Users](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#users)

[Cloud Foundry UAA: Groups](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#groups)

