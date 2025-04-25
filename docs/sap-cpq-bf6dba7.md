<!-- loiobf6dba7c48564118bb8a46fa0b2597cc -->

# SAP CPQ

Follow this procedure to set up SAP CPQ \(Configure, Price, and Quote\) as a proxy system.



<a name="loiobf6dba7c48564118bb8a46fa0b2597cc__prereq_gvh_45y_rdb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created a technical user with administrator permissions that will be used to call the API of SAP CPQ for reading, creating and updating user and group information.
-   Make sure all users from the external consumer system that have been not provisioned via Identity Provisioning and you would like later to be written in SAP CPQ, have an organization unit name. This unit name must correspond to an existing company system ID in SAP CPQ. The *organization unit* and the *company system ID* must be exactly the same. Users with empty \(missing\) organization units will not be provisioned, as well as users whose organization units don't match any of the SAP CPQ company system IDs for the relevant tenant.
-   In order for a created user to be active in SAP CPQ, it should be assigned to an SAP CPQ target group, whose ID ends with suffix *–USERTYPE*. To learn more, see [SAP CPQ: SCIM API](https://help.sap.com/viewer/08a7929ad06d4680b4f18cb57bc1a1d3/latest/en-US/7cf5d969d59a4723bcfd01cc38322a00.html) → section **Mappings between SCIM API and SAP CPQ** → `groups`.

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



## Context

SAP CPQ is a highly configurable system designated to help sales representatives to configure products, apply pricing and generate quotes. SAP CPQ is part of the SAP Sales Cloud portfolio.

Create an SAP CPQ proxy connector to execute hybrid scenarios. That means, it can provision its entities to another \(external\) back-end system by request, and then can continue executing CRUD operations back to the SAP CPQ system, whenever the external back-end requests such. This scenario supports provisioning **users** and **groups**.

> ### Caution:  
> You can't create or delete groups on SAP CPQ. That means:
> 
> -   On the attempt to create a group on SAP CPQ, Identity Provisioning will only add new members or update existing ones. Also, if you read a group from the external back-end system, there must be a group with the exact same display name \(case sensitive\) in the SAP CPQ system. Otherwise, an error will be thrown and the group members will not be updated.
> -   On the attempt to delete a group on SAP CPQ, Identity Provisioning will only remove its members \(group assignments\). And this can happen only if the relevant group assignments have been provisioned/are present in the target system.

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

5.  Add *SAP CPQ* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

6.  Set up the communication between Identity Provisioning and SAP CPQ and configure the authentication method \(basic or OAuth certificate-based\).

    > ### Note:  
    > We recommend that you use OAuth certificate-based authentication.

    1.  In your newly added SAP CPQ proxy system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](Operation-Guide/generate-and-manage-certificates-for-outbound-connection-76867db.md).

        Skip this step if you use basic authentication. The next steps are relevant for OAuth certificate-based authentication only. For more information, see [Configure OAuth Certificate Authentication](Operation-Guide/configure-oauth-certificate-authentication-a40a3f3.md).

    2.  Convert your certificate file from `.crt` to `.cer`.

    3.  Login to SAP CPQ and navigate to *Security* \> *Certificate Management* \> *User Certificates* \> *New Certificate* and upload the certificate to the technical user of SAP CPQ.

        Make sure the *Enable User Certificates* option is turned on. Additionally, the technical user must be set to *Active*.


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

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    Enter your authentication method:

    -   *BasicAuthentication*

    -   *ClientCertificateAuthentication*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cpq.user.filter`
    
    </td>
    <td valign="top">
    
    \(Optional\) When specified, only those SAP CPQ users matching the filter expression will be read.

    Example: **name.familyName eq "Smith" and addresses.country eq "US"**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Valid if *ClientCertificateAuthentication* is configured as authentication method.

    Enter the OAuth 2.0 Token Service URL.

    For example: `https://<cpq_url>/oauth2/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    \(Credential\) Specify the password for your technical user.
    
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
    
    Enter the URL to the API of your SAP CPQ system. It is the same as your SAP CPQ tenant URL. It must contain the domain name.

    For example: **https://sample1234.mycpqdomain.com**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    Enter the Username of your SAP CPQ technical user.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

8.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP CPQ* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP CPQ system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    [SAP CPQ: SCIM API](https://help.sap.com/viewer/08a7929ad06d4680b4f18cb57bc1a1d3/latest/en-US/7cf5d969d59a4723bcfd01cc38322a00.html)

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
    >         "scimEntityEndpoint": "Users",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
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
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.addresses"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.phoneNumbers"
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.groups"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "scimEntityEndpoint": "Groups",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
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
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.members"
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
    >         "mappings": [
    >             {
    >                 "targetPath": "$.id",
    >                 "sourceVariable": "entityIdTargetSystem"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >                 "targetPath": "$.schemas[1]"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.addresses"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.phoneNumbers"
    >             },
    >             {
    >                 "constant": [],
    >                 "targetPath": "$.groups",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']"
    >             },
    >             {
    >                 "constant": false,
    >                 "targetPath": "$['urn:sap:cpq:scim:schemas:extension:custom:2.0:User']['IsSsoUser']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "scimEntityEndpoint": "Groups",
    >         "mappings": [
    >             {
    >                 "targetPath": "$.id",
    >                 "sourceVariable": "entityIdTargetSystem"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
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
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]"
    >             }
    >         ]
    >     }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
9.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PATCH**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PATCH**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PATCH** method for modifying entities.




<a name="loiobf6dba7c48564118bb8a46fa0b2597cc__postreq_vc3_v5g_5nb"/>

## Next Steps

After the proxy connector is configured, a consumer application can start sending CRUD requests to it. That means, initially reading all \(or a filtered set of\) entities, and creating them in the SCIM 2.0 back-end of the consumer application. The proxy connector can continue read newly created or updated entities and provision them to the proxy system's back-end.

To see an example with SAP Identity Management, see [Hybrid Scenario: SAP Identity Management](https://help.sap.com/docs/identity-provisioning/identity-provisioning/hybrid-scenario-sap-identity-management?version=Cloud) → sections **Next Steps** and **Future Identity Lifecycle**.

**REMEMBER!** When creating a new user in the consumer application, you have to do the following mandatory settings:

-   Enter *organization unit* for the user, because this is a mandatory attribute for SAP CPQ. An organization with that exact name must already exist in SAP CPQ, otherwise the new user will not be provisioned.
-   In order the new user to be active, add a group privilege for it of type *–USERTYPE*. To learn more, see [SAP CPQ: SCIM API](https://help.sap.com/viewer/08a7929ad06d4680b4f18cb57bc1a1d3/2011/en-US/7cf5d969d59a4723bcfd01cc38322a00.html) → section **Mappings between SCIM API and SAP CPQ** → `groups`.

> ### Caution:  
> Effective September 2020, Neo tenants from Shanghai \(China\) can be only accessed on the following domain: `dispatcher.cn1.platform.sapcloud.cn`
> 
> So make sure you use the correct domain when you construct your REST API requests.
> 
> For example: **GET** *https://ipsproxyabcd12345-xyz789.dispatcher.cn1.platform.sapcloud.cn/ipsproxy/api/v1/scim/bbb111aa-1234-aaaa-7777-1234567abcde/Users/s123456789*
> 
> To learn more, see: [Proxy Systems](proxy-systems-b10d68a.md)

