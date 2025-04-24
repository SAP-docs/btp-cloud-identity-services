<!-- loiofef74f6574214bec980c4ee2fb4d107a -->

# SAP BTP XS Advanced UAA \(Cloud Foundry\)

Follow this procedure to set up the SAP BTP XS Advanced UAA \(running on SAP BTP, Cloud Foundry environment\) as а proxy system.



<a name="loiofef74f6574214bec980c4ee2fb4d107a__prereq_tcl_4r3_kfb"/>

## Prerequisites

You have created credentials to call the REST APIs of the SAP Authorization and Trust Management service on global account, subaccount, or directory level. For more information, see: [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis) and [btp create security/api-credential](https://help.sap.com/docs/btp/btp-cli-command-reference/btp-create-security-api-credential).

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loiofef74f6574214bec980c4ee2fb4d107a__context_jgv_gc1_123"/>

## Context

You can use Identity Provisioning to configure SAP BTP XS Advanced UAA as a proxy system in hybrid scenarios. For example, when SAP BTP XS Advanced UAA is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management, without making a direct connection between both systems. Upon provisioning platform users, business users and groups \(considered role collections in SAP BTP\) to the external backend system, it will trigger CRUD \(create, read, update, delete\) operations on users back to the SAP BTP XS Advanced UAA.

Create a separate proxy system for each global account, multi-environment subaccount and directory on SAP BTP, and configure the respective credentials and connectivity properties. Depending on where you want to provision your entities, you need to:

-   Create a proxy system for the global account to provision **platform users** and groups.

-   Create a proxy system for the directory to provision **platform users** and groups.

-   Create a proxy system for the subaccount to provision **platform users**, **business users** and groups.


> ### Note:  
> Provisioning of platform users as **org members** and **space members** requires the usage of a different connector: SAP BTP Platform Members \(Cloud Foundry\). For more information, see [SAP BTP Platform Members \(Cloud Foundry\)](sap-btp-platform-members-cloud-foundry-93807cf.md).

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

5.  Add *SAP BTP XS Advanced UAA \(Cloud Foundry\)* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

6.  Choose the *Properties* tab to configure the connection settings for your system.

    > ### Note:  
    > If your Identity Provisioning tenant is running on SAP BTP, Neo environment, you can create a [connectivity destination](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/72696d6d06c0490394ac3069da600278.html) in your subaccount in the SAP BTP cockpit, and then select it from the *Destination Name* combo box in your Identity Provisioning User Interface.
    > 
    > If one and the same property exists both in the cockpit and in the *Properties* tab, the value set in the *Properties* tab is considered with higher priority.
    > 
    > We recommend that you use the *Properties* tab. Use a connectivity destination only if you need to reuse one and the same configuration for multiple provisioning systems.

    **Properties**


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
    
    Enter the API URL in the following format:

    <code>https://api.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com</code> or

    <code>https://api.authentication.<i class="varname">&lt;region&gt;</i>.accounts.cloud.sap</code>

    For more information, see [Call an API](https://help.sap.com/docs/btp/sap-business-technology-platform/call-api?version=Cloud).

    > ### Restriction:  
    > The `accounts.cloud.sap` domain is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.


    
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
    
    Enter the URL to the OAuth2 token service in the following format:

    -   <code>https://<i class="varname">&lt;global_account_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code> or

        <code>https://<i class="varname">&lt;global_account_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.accounts.cloud.sap/oauth/token</code>

    -   <code>https://<i class="varname">&lt;subaccount_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code> or

        <code>https://<i class="varname">&lt;subaccount_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.accounts.cloud.sap/oauth/token</code>

    -   <code>https://<i class="varname">&lt;directory_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code> or

        <code>https://<i class="varname">&lt;directory_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.accounts.cloud.sap/oauth/token</code>


    For more information, see [Call an API](https://help.sap.com/docs/btp/sap-business-technology-platform/call-api?version=Cloud).

    > ### Restriction:  
    > The `accounts.cloud.sap` domain is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the respective OAuth client ID that was generated when you created credentials for each global account, subaccount and directory.

    For more information, see [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the respective OAuth client secret that was generated when you created credentials for each global account, subaccount and directory.

    For more information, see [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `xsuaa.origin`
    
    </td>
    <td valign="top">
    
    Enter the Origin Key of your identity provider.

    -   Identity provider for platform users:

        In the SAP BTP cockpit, go to your global account \(see [Navigate in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-in-cockpit?version=Cloud)\), choose *Security* \> *Trust Configuration* and copy the *Origin Key* value used for platform users. This origin key always ends with `-platform`.

    -   Identity provider for business users:

        In the SAP BTP cockpit, go to your subaccount \(see [Navigate in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-in-cockpit?version=Cloud)\), choose *Security* \> *Trust Configuration* and copy the *Origin Key* value used for business \(application\) users. For example: sap.custom


    For more information about users with multiple origins, see [Configure Single and Multiple Origins](configure-single-and-multiple-origins-e5c5900.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `xsuaa.origin.filter.enabled`
    
    </td>
    <td valign="top">
    
    This flag property depends on `xsuaa.origin`. Possible values: **true** or **false**

    -   If set to *true*, the Identity Provisioning service will read only users whose identity provider is set as a value of `xsuaa.origin`.
    -   If set to *false*, the Identity Provisioning service will read all users, regardless of their origin.
    -   If set to *true* but the `xsuaa.origin` property is missing, the provisioning will fail.


    
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
    
    `xsuaa.patch.response.with.resource`
    
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

    `URL`=*https://api.authentication.eu10.hana.ondemand.com*

    `OAuth2TokenServiceURL`=*https://myaccount.authentication.eu10.hana.ondemand.com/oauth/token*

    `User`=*sb-full-access!a76125*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `xsuaa.origin`=*sap.custom*

    `xsuaa.origin.filter.enabled`=*true*

    `scim.support.patch.operation`=*true*

    `xsuaa.patch.response.with.resource`=*false*
    
    </td>
    </tr>
    </table>
    
7.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP XS Advanced UAA* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP BTP XS Advanced UAA system. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md) and the API documentation.

    -   [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/resource/SCIM_groups_role_collections)- SCIM groups - role collections

    -   [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/resource/SCIM_users_shadow_users) - SCIM users - shadow users


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
    >    "user": {
    >       "mappings": [
    >          {
    >             "sourcePath": "$.id",
    >             "targetPath": "$.id",
    >             "targetVariable": "entityIdSourceSystem"
    >          },
    >          {
    >             "sourceVariable": "entityBaseLocation",
    >             "targetPath": "$.meta.location",
    >             "targetVariable": "entityLocationSourceSystem",
    >             "functions": [
    >                {
    >                   "type": "concatString",
    >                   "suffix": "${entityIdSourceSystem}"
    >                }
    >             ]
    >          },
    >          {
    >             "sourcePath": "$.userName",
    >             "targetPath": "$.userName",
    >             "correlationAttribute": true
    >          },
    >          {
    >             "sourcePath": "$.name",
    >             "targetPath": "$.name",
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.emails",
    >             "targetPath": "$.emails",
    >             "preserveArrayWithSingleElement": true
    >          },
    >          {
    >             "sourcePath": "$.emails[?(@.primary== true)].value",
    >             "correlationAttribute": true
    >          },
    >          {
    >             "sourcePath": "$.groups",
    >             "targetPath": "$.groups",
    >             "preserveArrayWithSingleElement": true,
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.phoneNumbers",
    >             "targetPath": "$.phoneNumbers",
    >             "preserveArrayWithSingleElement": true,
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.active",
    >             "targetPath": "$.active",
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.meta",
    >             "targetPath": "$.meta",
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.externalId",
    >             "targetPath": "$.externalId",
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.origin",
    >             "targetPath": "$.origin",
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.zoneId",
    >             "targetPath": "$.zoneId",
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.verified",
    >             "targetPath": "$.verified",
    >             "optional": true
    >          },
    >          {
    >             "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >             "targetPath": "$.schemas[0]"
    >          }
    >       ],
    >       "scimEntityEndpoint": "Users"
    >    },
    >    "group": {
    >       "mappings": [
    >          {
    >             "sourcePath": "$.id",
    >             "targetPath": "$.id",
    >             "targetVariable": "entityIdSourceSystem"
    >          },
    >          {
    >             "sourceVariable": "entityBaseLocation",
    >             "targetPath": "$.meta.location",
    >             "targetVariable": "entityLocationSourceSystem",
    >             "functions": [
    >                {
    >                   "function": "concatString",
    >                   "suffix": "${entityIdSourceSystem}"
    >                }
    >             ]
    >          },
    >          {
    >             "sourcePath": "$.displayName",
    >             "targetPath": "$.displayName"
    >          },
    >          {
    >             "sourcePath": "$.description",
    >             "targetPath": "$.description",
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.members",
    >             "targetPath": "$.members",
    >             "preserveArrayWithSingleElement": true,
    >             "optional": true
    >          },
    >          {
    >             "sourcePath": "$.zoneId",
    >             "targetPath": "$.zoneId"
    >          },
    >          {
    >             "sourcePath": "$.meta",
    >             "targetPath": "$.meta",
    >             "optional": true
    >          },
    >          {
    >             "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >             "targetPath": "$.schemas[0]"
    >          },
    >          {
    >             "constant": "authorization",
    >             "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >          },
    >          {
    >             "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >             "optional": true,
    >             "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >          }
    >       ],
    >       "scimEntityEndpoint": "Groups"
    >    }
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
    >         "constant": "xsuaa-dummy-value",
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
    >         "targetPath": "$.phoneNumbers",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.verified",
    >         "targetPath": "$.verified",
    >         "optional": true
    >       },
    >       {
    >         "constant": "%xsuaa.origin%",
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
    >         "optional": true
    >       },
    >       {
    >         "constant": "USER",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[*].type",
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
    
8.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.




<a name="loiofef74f6574214bec980c4ee2fb4d107a__postreq_cf4_lgj_kfb"/>

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

**Related Information**  


[SAP Authorization and Trust Management Service](https://help.sap.com/docs/authorization-and-trust-management-service?locale=en-US&version=Cloud)

[btp CLI Command Reference](https://help.sap.com/docs/btp/btp-cli-command-reference/btp-cli-command-reference)

[SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario?version=Cloud)

