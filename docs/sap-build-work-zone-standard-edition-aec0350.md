<!-- loioaec0350202e9473db153d3fd54f93b29 -->

# SAP Build Work Zone, standard edition

Follow this procedure to set up SAP Build Work Zone, standard edition as a proxy system.



<a name="loioaec0350202e9473db153d3fd54f93b29__prereq_gvh_45y_rdb"/>

## Prerequisites

-   You have created an instance and generated a service key for the standard service plan of SAP Build Work Zone, standard edition. For more information, see: [Initial Setup](https://help.sap.com/viewer/8c8e1958338140699bd4811b37b82ece/Cloud/en-US/fd79b232967545569d1ae4d8f691016b.html).

    The service key contains the API URL and the OAuth credentials \(`clientid` and `clientsecret`\) under the `uaa` property.

-   > ### Note:  
    > Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.




## Context

The SAP Build Work Zone, standard edition

You can use the Identity Provisioning UI to configure SAP Build Work Zone, standard edition simplifies access to SAP, custom-built, and third party applications and extensions \(both on the cloud and on premise\) by establishing a central launchpad. as a proxy system and configure it in hybrid scenarios. For example, when SAP Build Work Zone, standard edition is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management and SAP Cloud Identity Access Governance, without making a direct connection between both systems. You can provision users, groups and users’ group assignments to the external backend system, which can trigger CRUD \(create, read, update, delete\) operations on users, groups and users’ group assignments back to the SAP Build Work Zone, standard edition.



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

5.  Add *SAP Build Work Zone, standard edition* simplifies access to SAP, as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the SAP Build Work Zone, standard edition API URL from the service key of your SAP Build Work Zone, standard edition instance under `endpoints [portal-service]`. It follows the pattern:

    `https://portal-service.cfapps.sap.hana.ondemand.com`
    
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
    
    Enter the OAuth Client Id, from the service key of your SAP Build Work Zone, standard edition instance under `uaa.clientid`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, from the service key of your SAP Build Work Zone, standard edition instance under `uaa.clientsecret`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL from the service key of your SAP Build Work Zone, standard edition instance. It follows the pattern: `<uaa.url>/oauth/token`.

    For example: `https://ips-cflp-woaealle.authentication.sap.hana.ondemand.com/oauth/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cflp.providerId`
    
    </td>
    <td valign="top">
    
    Enter a valid providerID value.

    The provider ID is specified in the Channel Manager of the SAP Build Work Zone, standard edition when defining a new content provider. For more information about configuring the content provider to use the Identity Provisioning service, see: [Manage Content Providers \(Cloud\)](https://help.sap.com/docs/build-work-zone-standard-edition/sap-build-work-zone-standard-edition/manage-content-providers-cloud), [Manage Content Providers \(On Premise\)](https://help.sap.com/docs/build-work-zone-standard-edition/sap-build-work-zone-standard-edition/manage-content-providers-on-premise).

    > ### Note:  
    > All users and groups are provisioned to the proxy SAP Build Work Zone, standard edition system with the providerID defined for this proxy system. If you want to use different providerIDs, you need to create separate proxy systems for every providerID.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cflp.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Build Work Zone, standard edition users matching the filter expression will be read.

    By default, users are always filtered by the providerId. If another filtering attribute is defined, for example the email of the user, both filters are combined.

    Possible values:

    -   `emails.value eq 'john.smith@example.com'`

        > ### Note:  
        > Although, the email is supported as a filtering attribute, it is not returned when searching for the user.

    -   `urn:ietf:params:scim:schemas:extension:2.0:mapping.providerId eq 'ABC123'`



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cflp.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Build Work Zone, standard edition groups matching the filter expression will be read. By default, groups are always filtered by the providerId.

    Possible values:

    -   `externalId eq 12345678`

    -   `urn:ietf:params:scim:schemas:extension:2.0:mapping.providerId eq 'ABC123'`

    -   `meta.isIAG eq true`

        This filtering attribute indicates whether the group will be used in a hybrid scenario with SAP Cloud Identity Access Governance.



    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    > ### Note:  
    > The Identity Provisioning implementation of the SCIM Proxy API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).

7.  Configure the transformations.

    Transformations are used to map user and group attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Build Work Zone, standard edition* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Build Work Zone, standard edition system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    **User Update and Uniqueness**

    The proxy write transformation of SAP Build Work Zone, standard edition supports three user unique attributes: *externalId*, *email* and *providerId*. Only providerId is mandatory in combination with at least one of the other attributes. Based on the combinations of these attributes, there can be distinguished three types of users:

    -   User 1 - with *email* and *providerId*, but no *externalId*

    -   User 2 - with *externalId* and *providerId*, but no *email*

    -   User 3 - with all three attributes: *externalId*, *email* and *providerId*


    The uniqueness of the user is ensured by the combination of two unique attributes: the *providerId* and *externalId* or the *providerId* and the *email*.

    Updating an existing user in the proxy system depends on how the user is identified there \(its combination of unique attributes\) and whether Identity Provisioning is aware of this user:

    -   The existing user was created by a provisioning job \(that is, the service is aware of this user\).

        If the following attributes are changed in the source system: the *email* of user 1, the *externalId* of user 2, or the *email* or *externalId* of user 3, after running a new job, Identity Provisioning will update the existing user.

    -   The existing user was not created by a provisioning job or was created by one but afterwards the source and the proxy systems have been reset \(that is, the service is not aware of this user\).

        If the following attributes are changed in the source system, expect the subsequent results after running a new job:

        -   Changing the *email* of user 1 will result in creating a new user in the proxy system, because the user won’t match the combination of two unique attributes: *email* and *providerId*.

        -   Changing the *externalId* of user 2 will result in creating a new user in the proxy system, because the user won’t match the combination of two unique attributes: *externalId* and *providerId*.

        -   Changing the *email* or the *externalId* of user 3 will result in updating the user in the proxy system, because the user will still match a combination of two unique attributes. However, changing both, the *email* and the *externalId*, of user 3 will result in creating a new user in the proxy system, because the user will match only one unique attribute - the *providerId*.



    Default read and write transformations:


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
    >                 "targetVariable": "entityIdSourceSystem",
    >                 "correlationAttribute": true
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
    >                 "sourcePath": "$.emails.value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails.value"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']"
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
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']"
    >             },
    >             {
    >                 "sourcePath": "$.meta.isIAG",
    >                 "targetPath": "$.meta.isIAG"
    >             },
    >             {
    >                 "condition": " '%cflp.providerId%' != 'null' ",
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "condition": " '%cflp.providerId%' == 'null' ",
    >                 "sourcePath": "$.externalId",
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
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:2.0:mapping"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']"
    >             },
    >             {
    >                 "condition": "($['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId'] EMPTY true)",
    >                 "constant": "%cflp.providerId%",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.groups[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups[?(@.value)]"
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
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                     "urn:ietf:params:scim:schemas:extension:2.0:mapping"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.meta.isIAG",
    >                 "optional": true,
    >                 "targetPath": "$.meta.isIAG"
    >             },
    >             {
    >                 "constant": "%cflp.providerId%",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]"
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




<a name="loioaec0350202e9473db153d3fd54f93b29__postreq_cf4_lgj_kfb"/>

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


[Configure Integration with the Identity Provisioning Service](https://help.sap.com/docs/build-work-zone-standard-edition/sap-build-work-zone-standard-edition/configure-integration-with-identity-provisioning-service)

