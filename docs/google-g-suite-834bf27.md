<!-- loio834bf27567a24f86a97846d7a28844d8 -->

# Google G Suite

Follow this procedure to set up Google G Suite as a proxy system.



<a name="loio834bf27567a24f86a97846d7a28844d8__prereq_oq2_tx4_vdb"/>

## Prerequisites

1.  Sign in to the Google API console \([https://console.developers.google.com](https://console.developers.google.com)\) and create a project.
2.  Enable the Admin SDK. To do this, go to *Dashboard* \> *ENABLE API* \> *Admin SDK* \> *ENABLE*.
3.  Create a service account for your project. We recommend that you select *Enable G Suite Domain-wide Delegation* during the creation. If you skip this option, you can set it later. For more information, see [Creating a service account](https://developers.google.com/identity/protocols/OAuth2ServiceAccount?hl=en_US#creatinganaccount).
4.  Then, in the Google admin console \([https://admin.google.com](https://admin.google.com)\), a user with **Super Admin** role can delegate domain-wide authority to your service account. This way, it will have access to the Google Admin SDK on behalf of your user. For more information, see [Delegating domain-wide authority](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#delegatingauthority).

    **NOTE:** When specifying the scopes, the administrator has to enter the following:

    `https://www.googleapis.com/auth/admin.directory.user, https://www.googleapis.com/auth/admin.directory.group`


> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loio834bf27567a24f86a97846d7a28844d8__context_e3b_5x4_vdb"/>

## Context

A Google service account with delegated domain-wide authority is required for authentication and authorization of the Identity Provisioning service to G Suite domain. The authentication is based on OAuth 2.0 protocol with JSON Web Token \(JWT\). The private key for the signature is distributed by Google via one-time downloadable JSON data, which is accessible by the domain administrator. The private key is encoded in PKCS8 format and is in the *private\_key* field of the JSON data. For more information, see [JSON Web Token \(JWT\)](https://tools.ietf.org/html/rfc7519).

-   When using it as a source system, you can read both users and groups from Google G Suite and provision them to any target system you have added in the Identity Provisioning user interface.
-   When using it as a target system, you can write both users and groups, read from any source system you have added in the Identity Provisioning user interface. Google G Suite can automatically create accounts for your users in the Google Cloud Datastore.

The Identity Provisioning service supports user and group operations based on the following Google Directory API. See the table below.


<table>
<tr>
<th valign="top">

User Operations

</th>
<th valign="top">

Group Operations

</th>
</tr>
<tr>
<td valign="top">

[Create a user](https://developers.google.com/admin-sdk/directory/v1/reference/users/insert) 

</td>
<td valign="top">

[Create a group](https://developers.google.com/admin-sdk/directory/v1/reference/groups/insert) 

</td>
</tr>
<tr>
<td valign="top">

[Retrieve a user](https://developers.google.com/admin-sdk/directory/v1/reference/users/get) 

</td>
<td valign="top">

[Retrieve a group's properties](https://developers.google.com/admin-sdk/directory/v1/reference/groups/get) 

</td>
</tr>
<tr>
<td valign="top">

[Update a user](https://developers.google.com/admin-sdk/directory/v1/reference/users/update) 

</td>
<td valign="top">

[Update a group's properties](https://developers.google.com/admin-sdk/directory/v1/reference/groups/update) 

</td>
</tr>
<tr>
<td valign="top">

[Delete a user](https://developers.google.com/admin-sdk/directory/v1/reference/users/delete) 

</td>
<td valign="top">

[Delete a group](https://developers.google.com/admin-sdk/directory/v1/reference/groups/delete) 

</td>
</tr>
</table>

> ### Caution:  
> You can only provision users whose e-mails are from verified domains.

If you have successfully finished with the initial setup \(described in the **Prerequisites** section\), continue with the procedure below.



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

5.  Add *Google G Suite* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify the service URL:

    `https://www.googleapis.com/admin/directory`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Enter: `Internet`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    Enter: *BasicAuthentication*

    The authentication type in use is actually **OAuth** with JWT. But for any provisioning system based on OAuth, **BasicAuthentication** is used along with the `OAuth2TokenServiceURL` additional property.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the service account’s ID. You can take it from the *"client\_email"* field in the JSON data, downloaded during the setup of Google service account.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the service account’s private key, which represents a long string in PKCS8 format. You can take it from the *"private key"* field in the JSON data, downloaded during the setup of Google service account.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    To make OAuth authentication to the Google G Suite system, enter the URL to the access token provider service. For more information, see Using [OAuth 2.0 to Access Google APIs](https://developers.google.com/identity/protocols/OAuth2).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jwt.subject`
    
    </td>
    <td valign="top">
    
    Enter the Google G Suite user on behalf of which the Google Directory API is called. This user has been assigned the role **User Management Admin**.

    This property corresponds to “sub” claim in JWT being generated during access token request: [JWT: "sub" \(Subject\) Claim](https://tools.ietf.org/html/rfc7519#section-4.1.2)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `jwt.scope`
    
    </td>
    <td valign="top">
    
    Enter space-separated Google Directory API authorization scopes. For example:

    `https://www.googleapis.com/auth/admin.directory.user`
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    **Exemplary Configuration:**


    <table>
    <tr>
    <td valign="top">
    
    `ProxyType`=*Internet*

    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `URL`=*https://www.googleapis.com/admin/directory*

    `User`=*1234567890-compute@developer.gserviceaccount.com*

    `Password`=*\-----BEGIN PRIVATE KEY-----\\n123ABCDEFG123456789...*

    *… /123456789ABCDEFG123=\\n-----END PRIVATE KEY-----\\n*

    `OAuth2TokenServiceURL`=*https://www.googleapis.com/oauth2/v4/token*

    `jwt.subject`=*john.smith@me123.accounts.ondemand.com*

    `jwt.scope`=*https://www.googleapis.com/auth/admin.directory.user*
    
    </td>
    </tr>
    </table>
    
7.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Google G Suite* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    > ### Caution:  
    > An initial password setup is mandatory for all newly provisioned users. This is required by the Google G Suite API and must be provided when new accounts are created. The constant value that you see as configuration for the password attribute in the default transformation is generated by SAP. You have to change the constant value with another one, known only by the representatives of your company, before starting to use the Identity Provisioning service for creating users in your corporate Google G Suite system automatically.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Google G Suite. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [Google Directory API: Users](https://developers.google.com/admin-sdk/directory/v1/reference/users)

    [Google Directory API: Groups](https://developers.google.com/admin-sdk/directory/v1/reference/groups)

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
    >     "user": {
    >         "scimEntityEndpoint": "Users",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourceVariable": "entityBaseLocation",
    >                 "targetVariable": "entityLocationSourceSystem",
    >                 "targetPath": "$.meta.location",
    >                 "functions": [
    >                     {
    >                         "type": "concatString",
    >                         "suffix": "${entityIdSourceSystem}"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.primaryEmail",
    >                 "targetPath": "$.emails[0].value",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.primaryEmail",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "targetPath": "$.emails[0].primary",
    >                 "constant": true
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name"
    >             },
    >             {
    >                 "constant": true,
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "condition": "$.suspended == true",
    >                 "constant": false,
    >                 "targetPath": "$.active"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "scimEntityEndpoint": "Groups",
    >         "mappings": [
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourceVariable": "entityBaseLocation",
    >                 "targetVariable": "entityLocationSourceSystem",
    >                 "targetPath": "$.meta.location",
    >                 "functions": [
    >                     {
    >                         "type": "concatString",
    >                         "suffix": "${entityIdSourceSystem}"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members[?((@.type == 'USER') && (@.status == 'ACTIVE'))]",
    >                 "targetPath": "$.members",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "targetPath": "$.members[*].status",
    >                 "type": "remove"
    >             },
    >             {
    >                 "constant": "value",
    >                 "targetPath": "$.members[*].id",
    >                 "type": "rename"
    >             },
    >             {
    >                 "targetPath": "$.members[*].kind",
    >                 "type": "remove"
    >             },
    >             {
    >                 "targetPath": "$.members[*].etag",
    >                 "type": "remove"
    >             },
    >             {
    >                 "targetPath": "$.members[*].role",
    >                 "type": "remove"
    >             },
    >             {
    >                 "constant": "display",
    >                 "targetPath": "$.members[*].email",
    >                 "type": "rename"
    >             }
    >         ]
    >     }
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
    >         "condition": "($.emails.length() > 0) && ($.name.familyName EMPTY false)",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name"
    >             },
    >             {
    >                 "sourcePath": "$.emails[0].value",
    >                 "targetPath": "$.primaryEmail"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "targetPath": "$.phones",
    >                 "optional": true
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "targetPath": "$.password",
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
    >                 "constant": "false",
    >                 "targetPath": "$.suspended"
    >             },
    >             {
    >                 "condition": "$.active == false",
    >                 "constant": true,
    >                 "targetPath": "$.suspended"
    >             },
    >             {
    >                 "constant": "true",
    >                 "targetPath": "$.changePasswordAtNextLogin"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "scimEntityEndpoint": "Groups",
    >         "mappings": [
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.email",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.name"
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "targetPath": "$.members[*].value",
    >                 "type": "rename",
    >                 "constant": "id"
    >             },
    >             {
    >                 "targetPath": "$.members[*].display",
    >                 "type": "remove"
    >             }
    >         ]
    >     }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
    If the **displayName** attribute in the source system transformation does not provide group e-mails, you can modify the transformation the following ways:

    -   Map **email** to another attribute that contains a unique group e-mail.
    -   Concatenate the **displayName** attribute with your domain. For example:

        > ### Sample Code:  
        > ```
        > 
        >        {
        >            "sourcePath": "$.displayName",
        >            "targetPath": "$.email",
        >            "scope": "createEntity",
        >            "functions": [
        >                {
        >                    "type": "concatString",
        >                    "suffix": "@test.myaccount.ondemand.com"
        >                }
        >            ]
        >        }
        > 
        > 
        > ```


8.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.




<a name="loio834bf27567a24f86a97846d7a28844d8__postreq_cf4_lgj_kfb"/>

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

