<!-- loiodac4ec8c4ffc4aad9077623d885a03ef -->

# SAP BTP Java/HTML5 apps \(Neo\)

Follow this procedure to set up SAP Business Technology Platform as a proxy system, from and to which you can provision user-to-groups assignments for Java/HTML5 applications that run on SAP BTP, Neo environment.



<a name="loiodac4ec8c4ffc4aad9077623d885a03ef__prereq_n1b_khq_h2b"/>

## Prerequisites

-   You have created a new Platform API OAuth client, with *Authorization Management* scopes. Save the *Client ID* and *Client Secret* as you'll need them when you configure your proxy system. Make sure you save the client secret as you cannot retrieve it later.

    To learn how to create a Platform API client and what are the required platform service roles, see: [Create a Platform API Client](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/392af9d162694d6595499f1549978aa6.html)


> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loiodac4ec8c4ffc4aad9077623d885a03ef__context_cz4_d3n_j2b"/>

## Context

The Identity Provisioning service helps companies to automatically manage the user-to-groups assignments for Java/HTML5 applications running on the SAP Business Technology Platform. For this aim, the service reuses data from an active company user store.

For this scenario, SAP Business Technology Platform is a proxy system. That is, the Identity Provisioning service represents the various authorization mappings managed by Authorization Management REST API of SAP BTP as one generic SCIM 2.0 system, with some limitations. For more information, see: [Using the Authorization Management REST API](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dbea343ebe184c26b6067daaabaa9ac6.html)

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

5.  Add *SAP BTP Java/HTML5 apps \(Neo\)* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter: `https://api.<SAP_BTP_host>/authorization/v1/accounts/<SAP_BTP_account>` 

    Examples:

    -   \(Europe – Rot\) *https://api.hana.ondemand.com/authorization/v1/accounts/abc123xyz*
    -   \(Japan – Tokyo\) *https://api.jp1.hana.ondemand.com/authorization/v1/accounts/abc123xyz*


    
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
    
    Enter the Client ID of the new Platform API OAuth client created for the Authorization Management API \(see the prerequisites\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the Client Secret of the new Platform API OAuth client created for the Authorization Management API \(see the prerequisites\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter: `https://api.<SAP_BTP_host>/oauth2/apitoken/v1`

    Examples:

    -   \(Europe – Rot\) *https://api.hana.ondemand.com/oauth2/apitoken/v1*
    -   \(US East – Sterling\) *https://api.us3.hana.ondemand.com/oauth2/apitoken/v1*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `hcp.read.group.roles`
    
    </td>
    <td valign="top">
    
    If you set this property to *true*, the Identity Provisioning will read the following additional attributes for a SAP BTP group:

    -   Application roles
    -   Group mappings, defined by your identity provider

    > ### Restriction:  
    > This property and the relevant functionality is applicable only if SAP BTP and the external SCIM-based system belong to one and the same region.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `hcp.patch.response.with.resource`
    
    </td>
    <td valign="top">
    
    Use this property when you execute hybrid scenarios with SAP BTP as a SCIM proxy system, and you update an entity \(mostly relevant to groups, like when you change the members of a group\) via a PATCH request.

    Set this property to *true*. This way, the successful PATCH request will return a response code 200 \(*OK*\) back to the consumer client application with a payload body containing the updated attributes of the relevant group.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

7.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP Java/HTML5 apps \(Neo\)* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your proxy system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP BTP: Authorization Management API](https://api.hana.ondemand.com/authorization/v1/documentation)

    The *SAP BTP Java/HTML5 apps \(Neo\)* proxy connector supports SCIM PATCH operation.

    The read transformation takes the group name from the source system. However, SAP BTP groups names sometimes contain characters that do not fit the SCIM URI specification. As Identity Provisioning service cannot directly use these characters as a SCIM resource ID, it needs to first encode them into base32 ASCII format. The intermediate JSON logic of the proxy system will then use the new encoded ID and write it to the target system. That means, the ID will be decoded in the proxy write transformation during the **patchEntity** operation. For more information, see: [Transformation Expressions](transformation-expressions-bb8537b.md) → *patchEntity*

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
    > 
    > {
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem",
    >         "functions": [
    >           {
    >             "type": "encode",
    >             "algorithm": "base32",
    >             "skipPadding": true
    >           }
    >         ]
    >       },
    >       {
    >         "targetPath": "$.displayName",
    >         "sourcePath": "$.name"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "targetPath": "$.meta.location",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       },
    >       {
    >         "targetPath": "$.schemas[0]",
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "targetPath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.idpGroupMappings",
    >         "targetPath": "$.idpGroupMappings",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "constant": "User",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[*].type",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "targetPath": "$.displayName",
    >         "sourcePath": "$.name"
    >       },
    >       {
    >         "targetPath": "$.userName",
    >         "sourcePath": "$.name",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "targetPath": "$.meta.location",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       },
    >       {
    >         "targetPath": "$.schemas[0]",
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.groups[?(@.value)]",
    >         "optional": true,
    >         "functions": [
    >           {
    >             "type": "encode",
    >             "algorithm": "base32",
    >             "skipPadding": true
    >           }
    >         ]
    >       },
    >       {
    >         "constant": "direct",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.groups[*].type",
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
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.name",
    >         "targetVariable": "entityIdTargetSystem"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.name",
    >         "targetVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "scope": "deleteEntity",
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetVariable": "entityIdTargetSystem",
    >         "functions": [
    >           {
    >             "type": "decode",
    >             "algorithm": "base32",
    >             "skipPadding": true
    >           },
    >           {
    >             "type": "toString"
    >           }
    >         ]
    >       },
    >       {
    >         "scope": "patchEntity",
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetVariable": "entityIdTargetSystem",
    >         "functions": [
    >           {
    >             "type": "decode",
    >             "algorithm": "base32",
    >             "skipPadding": true
    >           },
    >           {
    >             "type": "toString"
    >           }
    >         ]
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
    >         "sourcePath": "$.members[*].value",
    >         "optional": true,
    >         "targetPath": "$.users"
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




<a name="loiodac4ec8c4ffc4aad9077623d885a03ef__postreq_cf4_lgj_kfb"/>

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

