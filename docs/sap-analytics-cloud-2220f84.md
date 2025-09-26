<!-- loio2220f847ef8642d18f4ecc59a943ff4d -->

# SAP Analytics Cloud

Follow this procedure to set up SAP Analytics Cloud as a proxy system.



<a name="loio2220f847ef8642d18f4ecc59a943ff4d__prereq_qcc_vk2_2cb"/>

## Prerequisites

-   In SAP Analytics Cloud, you have enabled a custom SAML Identity Provider, for which *User Attribute* is set to **Custom SAML User Mapping**. To learn how, see: [Enabling a Custom SAML Identity Provider](https://help.sap.com/doc/00f68c2e08b941f081002fd3691d86a7/release/en-US/3651184dad944aa2b361ad029a7a8cae.html)
-   In SAP Analytics Cloud, you have added an OAuth client with authorization grant **Client Credentials**. To learn how, see: [Managing OAuth Clients and Trusted Identity Providers](https://help.sap.com/doc/00f68c2e08b941f081002fd3691d86a7/release/en-US/4f43b54398fc4acaa5efa32badfe3df6.html)

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loio2220f847ef8642d18f4ecc59a943ff4d__context_wrv_lyn_vdb"/>

## Context

SAP Analytics Cloud is an all-in-one cloud product offered as software as a service for business intelligence, planning, and predictive analytics.

You can use Identity Provisioning to configure SAP Analytics Cloud as a proxy system in hybrid scenarios. For example, when SAP Analytics Cloud is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management, without making a direct connection between both systems. You can provision users and groups to the external backend system, which can trigger CRUD \(create, read, update, delete\) operations on users and groups back to the SAP Analytics Cloud.

There are two versions of the SAP Analytics Cloud SCIM API. They are handled by the`sac.api.version` property as follows:

-   When the value is set to `1` or the property is not defined \(typical for systems created before versioning was introduced on April 10, 2023\), SAP Analytics Cloud SCIM API version 1 is used. This is the default value.

-   When the value is set to `2` - SAP Analytics Cloud SCIM API version 2 is used. This version is released with enhancements, among which the support for patch operations.


For more information on the differences between SAP Analytics Cloud SCIM API version 1 and 2, see [Managing Users and Teams](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/ee11077e8a344ce99dfb77033eace581.html).

For more information on how to update to version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).

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

5.  Add *SAP Analytics Cloud* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    \(Optional\) `sac.csrf.token.path`
    
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
    
    \(Optional\) `sac.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Analytics Cloud groups matching the filter expression will be read.

    > ### Note:  
    > You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

    **Possible values:**

    For example: *displayName eq "ProjectTeam1"*
    
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
    
    \(Optional\) `ips.http.header.x-ignore-roles-if-missing`
    
    </td>
    <td valign="top">
    
    Use this property to control whether users or teams \(referred to as groups\) should keep their role assignments in SAP Analytics Cloud \(SCIM API version 1\) when no roles are provisioned.

    Possible values:

    -   true - Users or teams will keep their role assignments when no roles are provisioned.

    -   false - Users or teams will lose their role assignments when no roles are provisioned. This is the default value.


    For more information, see SAP note [3092730](https://me.sap.com/notes/3092730).

    In SAP Analytics Cloud \(SCIM API version 2\), this behavior is managed by `sac.support.patch.operation` property.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

7.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Analytics Cloud* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Analytic Cloud. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Analytics Cloud REST API: Managing Users and Teams](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/ee11077e8a344ce99dfb77033eace581.html)

    [Managing Users and Teams → api/v1/scim](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/42d90beb6337476984fcc7c54ec146dd.html)

    [Managing Users and Teams → api/v1/scim2](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/14cac91febef464dbb1efce20e3f1613/e34d2555509548028b76a7862cc5b84a.html)

    Default read and write transformations:

    > ### Tip:  
    > The proxy *Read Transformation* is used when the external client application \(for example, SAP Identity Management\) makes initial load. That is, executing GET requests to the resource endpoints \(**/Users** or **/Groups**\) to retrieve the corresponding entities of the particular type. The external client application can also execute GET requests to a single resource endpoint \(querying a single resource is supported\). In this case, the proxy system acts as a *source* one.
    > 
    > The proxy *Write Transformation* is used when the external application manages the entities in the proxy system – creates new entities, updates existing ones, or deletes existing ones. In this case, the proxy system acts as a *target* one.
    > 
    > However, after a *Create* or *Update* operation is performed on the proxy system, the *Read Transformation* is applied to the result, so that the created or updated entity is sent back to the external application. This behavior demonstrates that the proxy *Read Transformation* is used for *write* cases, as well.

    **Default read and write transformations for SAP Analytics Cloud SCIM API version 1:**


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
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
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
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.emails[0].value"
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "targetPath": "$.roles",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$['urn:scim:schemas:extension:enterprise:1.0']['manager']['managerId']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
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
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "targetPath": "$.roles",
    >         "preserveArrayWithSingleElement": true
    >      },
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
    > 
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "condition": "($.emails[0].value EMPTY false)",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
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
    >         "sourcePath": "$.name",
    >         "optional": true,
    >         "targetPath": "$.name"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "optional": true,
    >         "targetPath": "$.displayName"
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
    >         "sourcePath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.roles"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true,
    >         "targetPath": "$['urn:scim:schemas:extension:enterprise:1.0']['manager']['managerId']"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.id",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.roles"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
    **Default read and write transformations for SAP Analytics Cloud SCIM API version 2:**


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
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
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
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.emails[0].value"
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "targetPath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']",
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
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
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-roles']",
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-roles']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-custom-parameters']",
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:group-custom-parameters']",
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
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "condition": "($.emails[0].value EMPTY false)",
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
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
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
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members",
    >         "optional": true
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


    
    </td>
    </tr>
    </table>
    
    > ### Caution:  
    > When running a provisioning job to update users or teams \(referred to as groups\) with role assignments in SAP Analytics Cloud, these role assignments will be removed as a result of the update. This behavior, which can lead to permission issues, is expected because role assignments in SAP Analytics Cloud are not available as group parameters in some source systems, such as Identity Authentication. To preserve existing role assignments when updating users or teams, proceed as follows based on the version of the SAP Analytics Cloud SCIM API:
    > 
    > -   For SCIM API version 1, set the`ips.http.header.x-ignore-roles-if-missing` property to *true* in the SAP Analytics Cloud target system. For more information, see the properties table above and the SAP note [3092730](https://me.sap.com/notes/3092730).
    > 
    > -   For SCIM API version 2, set the `sac.support.patch.operation` property to *true* in the SAP Analytics Cloud target system.

    > ### Note:  
    > Updating a user in SAP Analytics Cloud using SCIM API version 2 depends on whether user attributes in SAP Analytics Cloud are mapped to SAML attributes in your identity provider. If this is the case, the values of those attributes are populated by the identity provider and cannot be changed by the SAP Analytics SCIM API or the UI. For more information, see [Mapping SAML Attributes to Users](https://help.sap.com/docs/SAP_ANALYTICS_CLOUD/00f68c2e08b941f081002fd3691d86a7/b385d1af93444e9fbc6439d2c6b3c1a7.html#map-saml-attributes-to-users).

8.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.

9.  Run an initial load job.




<a name="loio2220f847ef8642d18f4ecc59a943ff4d__postreq_cf4_lgj_kfb"/>

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

