<!-- loio9e9cf6f5e39b4ce680897de47ea843c7 -->

# SAP Field Service Management

Follow this procedure to set up SAP Field Service Management as a proxy system.



<a name="loio9e9cf6f5e39b4ce680897de47ea843c7__prereq_gvh_45y_rdb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

You have OAuth credentials for SAP Field Service Management. For more information, see: [Generating Client ID & Secret](https://help.sap.com/viewer/fsm_admin/Cloud/en-US/generating-client-id.html)

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



## Context

SAP Field Service Management is a cloud-based solution that is used to resolve customers issues with end-to-end field service management. For example, it helps customers overcome resource limitations, such as having enough skilled technicians in all locations.

You can use the Identity Provisioning user interface \(UI\) to configure SAP Field Service Management as a proxy system in hybrid scenarios. For example, when SAP Field Service Management is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management, without making a direct connection between both systems. You can provision users and groups to the external backend system, which can trigger CRUD \(create, read, update, delete\) operations on users and group members back to the SAP Field Service Management.

This scenario supports provisioning **users** and **group members**. When integrated with Identity Provisioning, SAP Field Service Management supports the following group concept:

-   A user is created with а default group assigned. A group is mapped to a company \(one of the key organizational units in SAP Field Service Management\). When using the Identity Provisioning service API, the group is returned as follows:

    ```
    <GroupName>_<CompanyName>
    ```

-   A user can have one group assignment for each company. As in SAP Field Service Management a user can be assigned to multiple companies, this requires a group assignment for each of the companies the user can access. A user cannot be assigned to different groups mapped to one and the same company.


> ### Caution:  
> You cannot create or delete groups in SAP Field Service Management. In this case, you can expect the following behavior:
> 
> -   If a new group is created in the source system \(for example, Identity Authentication\) and you run the provisioning job to SAP Field Service Management, the job will fail and no group will be created in the target system.
> 
> -   If a group exists both in the source system \(for example, Identity Authentication\) and the target system - SAP Field Service Management, running a provisioning job will only add new members or update existing ones. In this case, groups in the source and target systems must have the same display name \(case sensitive\). Otherwise, the job will fail, and no group members will be updated.
> 
> -   If a group exists in the target SAP Field Service Management system and you try to delete it, Identity Provisioning will only remove its group members. In this case, the relevant group members must exist in the target system.



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

5.  Add *SAP Field Service Management* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify the URL to the API of your SAP Field Service Management system. It follows the pattern:

    <code>https://<i class="varname">&lt;cluster&gt;</i>.coresystems.net</code>
    
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
    
    Enter the OAuth Client Id, created for your SAP Field Service Management system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, created for your SAP Field Service Management system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL.

    For example: `https://<cluster>.coresuite.com/api/oauth2/v1/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `fsm.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Field Service Management users matching the filter expression will be read.

    Example: **name.familyName eq "Smith" and addresses.country eq "US"**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `fsm.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Field Service Management groups matching the filter expression will be read.

    Example: **displayName eq "ProjectTeam1" or "Employees2020"**
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    > ### Note:  
    > The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).

7.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Field Service Management* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Field Service Management system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    [SAP Field Service Management - SCIM API](https://help.sap.com/viewer/fsm_scim_api/Cloud/en-US/scim-api.html)

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
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
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
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true,
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional": true,
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.active",
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
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             }
    >         ],
    >         "scimEntityEndpoint": "Users"
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
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
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
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
    >     "user":  {
    >         "mappings":  [
    >             {
    >                 "sourceVariable":  "entityIdTargetSystem",
    >                 "targetPath":  "$.id"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath":  "$.userName",
    >                 "targetPath":  "$.userName"
    >             },
    >             {
    >                 "sourcePath":  "$.name.givenName",
    >                 "targetPath":  "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath":  "$.name.familyName",
    >                 "targetPath":  "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath":  "$.active",
    >                 "targetPath":  "$.active"
    >             },
    >             {
    >                 "sourcePath":  "$.emails",
    >                 "preserveArrayWithSingleElement":  true,
    >                 "optional":  true,
    >                 "targetPath":  "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             }
    >         ],
    >         "scimEntityEndpoint":  "Users"
    >     },
    >     "group":  {
    >         "mappings":  [
    >             {
    >                 "sourceVariable":  "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.Operations",
    >                 "targetPath": "$.Operations",
    >                 "preserveArrayWithSingleElement": true,
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "targetPath":  "$.id",
    >                 "type":  "remove",
    >                 "scope":  "patchEntity"
    >             },
    >             {
    >                 "constant":  "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath":  "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath":  "$.displayName",
    >                 "targetPath":  "$.displayName"
    >             },
    >             {
    >                 "sourcePath":  "$.members[*].value",
    >                 "preserveArrayWithSingleElement":  true,
    >                 "optional":  true,
    >                 "targetPath":  "$.members[?(@.value)]"
    >             }
    >         ],
    >         "scimEntityEndpoint":  "Groups"
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




<a name="loio9e9cf6f5e39b4ce680897de47ea843c7__postreq_cf4_lgj_kfb"/>

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

