<!-- loiocd6a0be649ef49e1807449324567a559 -->

# Microsoft Entra ID

Follow this procedure to set up Microsoft Entra ID \(formerly known as Microsoft Azure Active Directory\) as a proxy system.



<a name="loiocd6a0be649ef49e1807449324567a559__prereq_hcd_5cv_hz"/>

## Prerequisites

-   You've logged on to Microsoft Azure Portal, with credentials for a user with directory role **Global administrator**. For more information, see [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).
-   In *Azure Active Directory* \> *App registrations*, you've registered an application with a secret key and permissions for Microsoft Graph API. These permissions must be consented by an administrator. For more information, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).
-   \(Relevant to target systems\) Your registered application is assigned the **User Account Administrator** role. This role allows you to deprovision users. For more information, see [Add-MsolRoleMember](https://learn.microsoft.com/en-us/powershell/module/msonline/add-msolrolemember?view=azureadps-1.0).

    > ### Note:  
    > If this role isn't assigned, you can only disable users. To do that, set the `accountEnabled` property to **false**. For more information, see [MS Graph: user resource type](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/user)


> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.

**Permissions**

Assign the following permissions to your application, according to your scenario. Also, the permissions have to be of type *Application*.

-   Users – *User.ReadWrite.All*, *Directory.AccessAsUser.All*
-   Groups – *Group.ReadWrite.All*

For more information, see [MS Graph: Users](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/users) and [MS Graph: Groups](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/group)



<a name="loiocd6a0be649ef49e1807449324567a559__context_kcx_w1p_vdb"/>

## Context

When using it as a proxy system, you can write both users and groups, read from any source system you've added in the Identity Provisioning user interface. The Microsoft Entra ID proxy systems use Microsoft Graph API. For more information, see [Microsoft Graph](https://developer.microsoft.com/en-us/graph/docs/overview/overview).

If you've successfully finished with the initial setup \(described in the **Prerequisites** section\), continue with the procedure.

> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



<a name="loiocd6a0be649ef49e1807449324567a559__steps_trm_y1p_vdb"/>

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

5.  Add *Microsoft Entra ID* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter: **https://graph.microsoft.com**
    
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
    
    Enter the application ID registered in your Microsoft Entra ID subscription \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the secret key associated to your app registration.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `aad.domain.name`
    
    </td>
    <td valign="top">
    
    Enter one of the verified domain names from the corresponding Microsoft Entra ID tenant. On this domain, you perform the provisioning operations. For more information, see [Managing custom domain names in your Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/domains-manage).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `oauth.resource.name`
    
    </td>
    <td valign="top">
    
    Enter: **https://graph.microsoft.com**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter: **https://login.microsoftonline.com/<your\_domain\>/oauth2/token**, where `<your_domain>` is the domain name you have set in the `aad.domain.name` property.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.group.member.attributes`
    
    </td>
    <td valign="top">
    
    This property defines the attributes of a group member to be read by the Identity Provisioning. By default, it always reads the **type** and the **id** of a member.

    If you want the Identity Provisioning to read additional attributes, enter them as a single or a comma-separated value. For example:

    > ### Example:  
    > -   If you want to read the e-mails too, enter: `aad.group.member.attributes`=*mail*
    > 
    >     This will read a member's type, ID, and e-mail.
    > 
    > -   If you want to read multiple additional attributes, enter: `aad.group.member.attributes`=*mail,mobilePhone,displayName* 
    > 
    >     This will read a member's type, ID, e-mail, phone, and display name.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.user.attributes.membership.active`
    
    </td>
    <td valign="top">
    
    Use this property if you want to get information about all the groups to which the users are assigned \(if any\).

    -   If the property is missing, or is set to *false* – group membership details for the users will not be extracted.
    -   If the property is set to *true* – group membership details for the users will be extracted.

    To learn more, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.user.filter`
    
    </td>
    <td valign="top">
    
    Use this property to filter users by specific criteria, according to the [Microsoft Graph REST API](https://docs.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#properties).

    > ### Note:  
    > This property replaces the deprecated `msgraph-filter` property. To learn more, see: [List of Properties](list-of-properties-d6f3577.md) 


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.group.filter`
    
    </td>
    <td valign="top">
    
    Use this property to filter groups by specific criteria, according to the [Microsoft Graph REST API](https://docs.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.user.filter.group.filter.combine`
    
    </td>
    <td valign="top">
    
    Use this property to filter users based on their group assignments.

    When set to **true**, this property combines user and group filters defined on the `aad.user.filter` and `aad.group.filter` properties to further narrow the search results. This way, only users that meet the following filtering criteria are returned:

    -   Users that match the user filter and at the same time are members of groups that match the group filter.

    -   Members of the filtered groups that match the user filter.


    When set to **false**, user and group filters are not combined.

    To learn more, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.user.attributes`
    
    </td>
    <td valign="top">
    
    Defines which user attributes are read from Microsoft Entra ID system.

    The property is set during system creation with the following default value: *id,mail,userPrincipalName,displayName,mailNickname,givenName,surname,mobilePhone,businessPhones*

    This means that by default, Identity Provisioning will read from Microsoft Entra ID the user attributes defined in the property value. Those attributes are used in the default read transformation.

    To check the complete set of user attributes \(properties\) supported by Microsoft Entra ID, see: [Microsoft Graph: User Properties](https://docs.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#properties)

    To learn more, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.group.attributes`
    
    </td>
    <td valign="top">
    
    Defines which group attributes are read from Microsoft Entra ID system.

    The property is set during system creation with the following default value: *id,displayName,mailNickname*

    This means that by default, Identity Provisioning will read from Microsoft Entra ID the group attributes defined in the property value and will also return the *members* attribute. Those attributes are used in the default read transformation.

    To check the complete set of group attributes \(properties\) supported by Microsoft Entra ID, see: [Microsoft Graph: Group Properties](https://docs.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties)

    To learn more, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.entities.top`
    
    </td>
    <td valign="top">
    
    This property defines the number of entities to be read per page. Default value: *100* 
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

7.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Microsoft Entra ID* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Microsoft Entra ID. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [MS Graph: Users](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/users)

    [MS Graph: Groups](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/group)

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
    >     "condition": "$.userPrincipalName EMPTY false",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem",
    >         "targetPath": "$.id"
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
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.mail",
    >         "targetPath": "$.emails[0].value",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.userPrincipalName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "optional": true,
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.mailNickname",
    >         "optional": true,
    >         "targetPath": "$.externalId",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.givenName",
    >         "optional": true,
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.surname",
    >         "optional": true,
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.mobilePhone",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[0].value"
    >       },
    >       {
    >         "condition": "$.mobilePhone EMPTY false",
    >         "constant": "mobile",
    >         "targetPath": "$.phoneNumbers[0].type"
    >       },
    >       {
    >         "sourcePath": "$.businessPhones[0]",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[1].value"
    >       },
    >       {
    >         "condition": "$.businessPhones.length() > 0",
    >         "constant": "work",
    >         "targetPath": "$.phoneNumbers[1].type"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups"
    >       },
    >       {
    >         "sourcePath": "$.manager.id",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.manager.displayName",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem",
    >         "targetPath": "$.id"
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
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members"
    >       },
    >       {
    >         "targetPath": "$.members[*].id",
    >         "constant": "value",
    >         "type": "rename",
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
    >     "user": {
    >         "scimEntityEndpoint": "Users",
    >         "mappings": [
    >             {
    >                 "optional": true,
    >                 "sourcePath": "$.onPremisesImmutableId",
    >                 "targetPath": "$.onPremisesImmutableId"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "optional": true,
    >                 "targetPath": "$.accountEnabled"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true,
    >                 "targetPath": "$.mailNickname"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                  "sourcePath": "$.name.givenName",
    >                  "optional": true,
    >                  "targetPath": "$.givenName"
    >             },
    >             {
    >                  "sourcePath": "$.name.familyName",
    >                  "optional": true,
    >                  "targetPath": "$.surname"
    >             },
    >             {
    >                 "sourcePath": "$.addresses[0].locality",
    >                 "optional": true,
    >                 "targetPath": "$.city"
    >             },
    >             {
    >                 "sourcePath": "$.addresses[0].country",
    >                 "optional": true,
    >                 "targetPath": "$.country"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userPrincipalName",
    >                 "functions": [
    >                     {
    >                         "type": "concatString",
    >                         "suffix": "@%aad.domain.name%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "constant": "true",
    >                 "targetPath": "$.accountEnabled"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "sourcePath": "$.active",
    >                 "optional": true,
    >                 "targetPath": "$.accountEnabled"
    >             },
    >             {
    >                  "scope": "createEntity",
    >                  "sourcePath": "name.givenName",
    >                  "targetPath": "$.mailNickname"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "targetPath": "$.passwordProfile.password",
    >                 "functions": [
    >                     {
    >                         "type": "randomPassword",
    >                         "passwordLength": 16,
    >                         "minimumNumberOfLowercaseLetters": 1,
    >                         "minimumNumberOfUppercaseLetters": 1,
    >                         "minimumNumberOfDigits": 1,
    >                         "minimumNumberOfSpecialSymbols": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "constant": false,
    >                 "targetPath": "$.passwordProfile.forceChangePasswordNextSignIn"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "scimEntityEndpoint": "Groups",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "optional": true,
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.mailNickname"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "constant": true,
    >                 "targetPath": "$.mailEnabled"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "constant": false,
    >                 "targetPath": "$.securityEnabled"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "constant": "Unified",
    >                 "targetPath": "$.groupTypes[0]"
    >             }
    >         ]
    >     }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
    **Custom Configurations**


    <table>
    <tr>
    <th valign="top">

    Goal
    
    </th>
    <th valign="top">

    Action
    
    </th>
    <th valign="top">

    Result
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    You want Identity Provisioning to read the additional user attributes specified in property `aad.user.attributes` and write them successfully in the external back-end system.
    
    </td>
    <td valign="top">
    
    In the *Read Transformation*, extend the "*user*" mapping as follows:

    ```
    
    {
    	"user": {
    	   "condition": "$.userPrincipalName EMPTY false",
    	   "mappings": [
    		{
    		   "sourcePath": "$",
    		   "targetPath": "$"
    		},
    		{
    		   "sourcePath": "$.id",
    		   "targetVariable": "entityIdSourceSystem"
    		},
    ...
     
    ```


    
    </td>
    <td valign="top">
    
    For example, you specify the `aad.user.attributes` property and set its value to: *id,mail,userPrincipalName,city,department,companyName*

    As a result, every user in the external back-end system will have the following attributes populated – ID, e-mail, user principle name, city, department, and company name.

    Returned information of an exemplary user:

    ```
    ...
    {
       "Resources":[
    	{
    	   "id":"555-aaaa-333-abcd-111222333",
    	   "mail":"john.smith@domain.com",
    	   "userPrincipalName":"abc@something.onmicrosoft.com",
    	   "city": "Sofia",
    	   "department":"029",
    	   "companyName":"SAP"
    	}
    ...
       ]
    }
    
    ```


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    You want Identity Provisioning to read the additional group attributes specified in property `aad.group.attributes` and write them successfully in the target system.
    
    </td>
    <td valign="top">
    
    Extend the "*group*" mapping as follows:

    ```
    
    {
    	"group": {
    	   "ignore": false,
    	   "mappings": [
    		{
    		   "sourcePath": "$",
    		   "targetPath": "$"
    		},
    		{
    		   "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    		   "targetPath": "$.schemas[0]"
    		},
    ...
     
    ```


    
    </td>
    <td valign="top">
    
    Example: Specify the `aad.group.attributes` property and set its value to: *id,displayName,recommendation,isSubscribedByMail*

    As a result, every group in the target system will have the following attributes populated – ID, display name, date and time of the last renewal, and information if it's subscribed by e-mail or not.

    Returned information of an exemplary group:

    ```
    ...
    {
       "Resources":[
    	{
    	   "id":"12345-ccc-000-xyz-777888999",
    	   "displayName":"ImportantGroup3",
    	   "renewedDateTime":"2018-01-01T00:00:00Z",
    	   "isSubscribedByMail":"true"
    	}
    ...
       ]
    }
    
    ```


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    You want the returned value of a group member to be not the ID but a different attribute.
    
    </td>
    <td valign="top">
    
    Replace **id** with the new attribute. For example:

    If you replace *id* with *mail*, the transformation will look like this:

    ```
    
    ...
    	{
    	   "sourcePath": "$.members",
    	   "preserveArrayWithSingleElement": true,
    	   "optional": true,
    	   "targetPath": "$.members"
    	},
    	{
    	   "targetPath": "$.members[*].mail",
    	   "constant": "value",
    	   "type": "rename",
    	   "optional": true
    	}
    ...
    ```

    > ### Caution:  
    > Make sure that you've added this attribute as a value of property *aad.group.member.attributes*.


    
    </td>
    <td valign="top">
    
    Returned information of an exemplary group member:

    ```
    ...
    {
       "members":[
    	{
    	   "id":"5555555-aaaa-333-abcd-1111122223333",
    	   "type":"user",
    	   "value":"johnsmith@mail.acme.com"
    	}
      ]
    }
    ...
    ```


    
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




<a name="loiocd6a0be649ef49e1807449324567a559__postreq_cf4_lgj_kfb"/>

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

