<!-- loio624fff62fe994e749788cc214e8c3e80 -->

# Intelligent Opportunity Analyzer

Follow this procedure to set up intelligent opportunity analyzer as a proxy system.



<a name="loio624fff62fe994e749788cc214e8c3e80__prereq_wby_s2m_22c"/>

## Prerequisites

-   You have added *Intelligent Opportunity Analyzer* with *scim* plan in the *Entitlements* page of your subaccount as described in.

-   You have created an instance and generated a service key for the *scim* service plan of *Intelligent Opportunity Analyzer*. For more information, see [Assigning the Entitlements for Intelligent Opportunity Analyzer to Your Subaccounts](https://help.sap.com/docs/categories/sap-ariba-category-management-configuration-guide/assigning-entitlement-for-intelligent-opportunity-analyzer?locale=en-US&version=2411).

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.



## Context

Intelligent opportunity analyzer is a service that comes integrated with SAP Ariba Category Management for identifying and managing opportunities that lead to improving the performance of a purchasing category.

You can use Identity Provisioning to configure intelligent opportunity analyzer as a proxy system in hybrid scenarios. For example, when intelligent opportunity analyzer is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management, without making a direct connection between both systems. You can provision users to the external backend system, which can trigger CRUD \(create, read, update, delete\) operations on users back to the intelligent opportunity analyzer.

> ### Note:  
> Intelligent opportunity analyzer does not support groups.



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

5.  Add *Intelligent Opportunity Analyzer* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL provided by the service key under the *scim-v1* field without adding the path information.
    
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
    
    Enter the value from the *clientid* field of the service key.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the value from the *clientsecret* field of the service key.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL. This is the value from the *url* field of the service key. Ensure to append the value `/oauth/token?grant_type=client_credentials`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ioa.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those intelligent opportunity analyzer users matching the filter expression will be read. For example:

    -   *userName eq "SmithJ"*

    -   *emails.value eq "john.doe@example.com"*



    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    > ### Note:  
    > The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).

7.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Intelligent Opportunity Analyzer* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your intelligent opportunity analyzer system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    > ### Note:  
    > The documentation for the Intelligent Opportunity Analyzer API and its integration with Identity Provisioning is still under development. Refer to the [Intelligent Opportunity Analyzer Setup](https://help.sap.com/docs/categories/sap-ariba-category-management-configuration-guide/intelligent-opportunity-analyzer-setup?version=2502) for updates.

    **Default read and write transformations**

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
    >         "sourcePath": "$.meta",
    >         "targetPath": "$.meta"
    >       },
    >       {
    >         "sourcePath":"$.userName",
    >         "targetPath":"$.userName",
    >         "correlationAttribute":true
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
    >         "sourcePath":"$.loginName",
    >         "targetPath":"$.loginName",
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
    >         "sourcePath":"$.name.formatted",
    >         "targetPath":"$.name.formatted",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.middleName",
    >         "targetPath":"$.name.middleName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.honorificPrefix",
    >         "targetPath":"$.name.honorificPrefix",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.honorificSuffix",
    >         "targetPath":"$.name.honorificSuffix",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.emails",
    >         "targetPath":"$.emails",
    >         "preserveArrayWithSingleElement":true
    >       },
    >       {
    >         "sourcePath":"$.emails[?(@.primary== true)].value",
    >         "correlationAttribute":true
    >       },
    >       {
    >         "sourcePath":"$.active",
    >         "targetPath":"$.active"
    >       },
    >       {
    >         "sourcePath":"$.displayName",
    >         "targetPath":"$.displayName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       }
    >     ],
    >     "scimEntityEndpoint": "Users"
    >   }
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "user":{
    >     "mappings":[
    >      {
    >        "constant": [
    >          "urn:ietf:params:scim:schemas:core:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
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
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath":"$.loginName",
    >         "targetPath":"$.loginName",
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
    >         "sourcePath":"$.name.formatted",
    >         "targetPath":"$.name.formatted",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.middleName",
    >         "targetPath":"$.name.middleName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.honorificPrefix",
    >         "targetPath":"$.name.honorificPrefix",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.name.honorificSuffix",
    >         "targetPath":"$.name.honorificSuffix",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath":"$.active",
    >         "targetPath":"$.active"
    >       },
    >       {
    >         "sourcePath":"$.displayName",
    >         "targetPath":"$.displayName",
    >         "optional":true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       }
    >     ],
    >     "scimEntityEndpoint": "Users"
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




<a name="loio624fff62fe994e749788cc214e8c3e80__postreq_cf4_lgj_kfb"/>

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

