<!-- loiof5466e64372347d78b8fdaf2efa6ebe6 -->

# SAP Ariba Applications

Follow this procedure to set up SAP Ariba Applications as a proxy system.



<a name="loiof5466e64372347d78b8fdaf2efa6ebe6__prereq_bns_xn4_vdb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created a client application on [SAP Ariba APIs Portal](https://developer.ariba.com/api) that needs to be enabled for Identity Provisioning.

    > ### Note:  
    > If you don’t have an account on SAP Ariba Developer Portal, then ask your **Designated Support Contact** \(DSC\) to submit a [request for an account](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/f7dbeb26531140e7bab57170a24e3701.html). To find your DSC person, see: [How can I see my company's Basic users and Designated Support Contacts \(DSC\)](https://support.ariba.com/item/view/184249)

-   Provide your DSC person with your SAP Ariba **realm name**, **application name**, and **application key**. You have already created the application name along with the application key on *step 2*. To find your realm name, login to your SAP Ariba system – it's part of your login URL, as shown in the following examples.
    -   *SAP Ariba Buyer* example: `https://s1.ariba.com/Buyer/Main/ad/loginPage/...&realm=`*mycompany-t*
    -   *SAP Ariba Sourcing* example: `http://`*mycompany*`.sourcing.ariba.com/`

-   Ask your DSC person to submit a service request for you to *SAP Ariba Support* for component **BNS-ARI-SS-API**, requesting the client application to be enabled for Identity Provisioning. Request your DSC person to mention the following details in the service request:
    -   Application name
    -   Application key
    -   Realm name

-   When your application is enabled, you can login to [SAP Ariba APIs Portal](https://developer.ariba.com/api), find your application, and generate a new OAuth secret for it. To learn how, see: [How to generate the OAuth Secret and Base64 Encoded Client and secret](https://help.sap.com/viewer/b61dd8c7e22c4fe489f191f66b4c48d6/cloud/en-US/81f493759bbb42e5b7486bfdf8185fa3.html)
-   To configure your *SAP Ariba Applications* provisioning system \(see the procedure below\), you will need to map your SAP Ariba application parameters to the relevant Identity Provisioning properties. The property mapping between the two systems is as follows:


    <table>
    <tr>
    <th valign="top">

    SAP Ariba
    
    </th>
    <th valign="top">

    Identity Provisioning
    
    </th>
    <th valign="top">

    Values
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    SCIM API URL
    
    </td>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    Examples:

    -   US: **https://openapi.ariba.com**
    -   Europe: **https://eu.openapi.ariba.com**
    -   UAE: **https://mn1.openapi.ariba.com**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    SAP Ariba OAuth 2.0 Token URL
    
    </td>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Examples:

    -   US: **https://api.ariba.com/v2/oauth/token** 
    -   Europe: **https://api-eu.ariba.com/v2/oauth/token**
    -   UAE: **https://api.mn1.ariba.com/v2/oauth/token**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    OAuth Client ID
    
    </td>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Alphanumeric string

    Example:**aaaa12345-1111-3333-cccc-1234567890**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    OAuth Secret
    
    </td>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    Alphanumeric string

    Example:**aaaGGG1eee12abcdefGHIJK123lmnopTTT**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Application key
    
    </td>
    <td valign="top">
    
    `ariba.applications.api.key`
    
    </td>
    <td valign="top">
    
    Alphanumeric string

    Example:**123abc123XYZ000abc123ABC012345**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    AN-ID
    
    </td>
    <td valign="top">
    
    `ariba.applications.realm.id`
    
    </td>
    <td valign="top">
    
    AN<numeric\_string\>

    Example: **AN000111222333**
    
    </td>
    </tr>
    </table>
    

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loiof5466e64372347d78b8fdaf2efa6ebe6__context_zhf_2vx_ybb"/>

## Context

After fulfilling the prerequisites, you can create an SAP Ariba Applications proxy system to load its users into an on-premise system and provision groups and new users back to SAP Ariba Applications.

These proxy systems consume SCIM 2.0 API provided by SAP Ariba Applications. For more information about the SAP Ariba SCIM API scope of support, see [3228340](https://me.sap.com/notes/3228340).

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

5.  Add *SAP Ariba Applications* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the SCIM API URL for your SAP Ariba application \(see the **Prerequisites** section\).
    
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
    
    Enter the OAuth Client ID \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Secret \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.applications.api.key`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter your application key \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.applications.realm.id`
    
    </td>
    <td valign="top">
    
    Enter your AN-ID \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ariba.applications.group.flatten`
    
    </td>
    <td valign="top">
    
    This property allows or forbids reading "nested groups" \(group structures\) from SAP Ariba Applications. If enabled \(**true**\), group members of type *group* will be ignored during read in order not to be provisioned to target systems that do not support nested groups. Thus, leave the default/predefined **false** value only if you are sure that the consuming external application \(identity management system\) supports nested groups.

    Default value: *false*

    Predefined value \(during system creation\): *false*

    Leave the default/predefined value only if you are sure that the consuming external application \(identity management system\) supports nested groups.

    > ### Note:  
    > If you set this property to *true* in your proxy system, the execution of requests with parameter `membersType=group` will not be supported.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ariba.applications.support.patch.operation`
    
    </td>
    <td valign="top">
    
    Default value: *true*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.applications.group.members.page.size`
    
    </td>
    <td valign="top">
    
    SAP Ariba Applications has a hardcoded limit of the number of group members returned per request when reading the group SCIM resources.

    When the Identity Provisioning reads a group, it compares the number of group members with the value configured for `ariba.applications.group.members.page.size`. Depending on the value you defined for `ariba.applications.group.members.paging.enabled`, you can expect the following results:

    -   In case the number of group members equals or exceeds the configured limit and the property `ariba.applications.group.members.paging.enabled` is enabled, the Identity Provisioning will perform full read of all group members via subsequent requests.

    -   In case the number of group members is less than the configured limit or the property `ariba.applications.group.members.paging.enabled` is disabled, the Identity Provisioning will get the returned group members from the target system.


    Setting the property `ariba.applications.group.members.paging.enabled` allows you to read groups with a large number of group members. For more information, see ariba.applications.group.members.paging.enabled.

    Default value: *50*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.applications.group.members.paging.enabled`
    
    </td>
    <td valign="top">
    
    This property enables the full read of group members.

    When it is set to *true*, all groups with members count exceeding the value defined in `ariba.applications.group.members.page.size` will be fully read by the Identity Provisioning via subsequent requests.

    **Possible values:**

    -   *true* - Full read of group members is enabled.
    -   *false* - Full read of group members is disabled.

    Default value: *true*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.applications.user.groups.paging.enabled`
    
    </td>
    <td valign="top">
    
    SAP Ariba Applications has a hardcoded limitation over the number of user's groups returned per request.

    This limit is specified by the property `ariba.applications.group.members.page.size`.

    To trigger a full read of a user with *'groups'* attribute over the configured value, set `ariba.applications.user.groups.paging.enabled` to *true*.

    **Possible values:**

    -   *true* - the full read of user's groups is enabled.

    -   *false* - the full read of user's groups is disabled.


    Default value: *true*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.applications.user.groups.page.size`
    
    </td>
    <td valign="top">
    
    The nuber of user groups that SAP Ariba Application returns per request when reading a user.

    When the Identity Provisioning reads a user, it compares the number groups assigned with the value configured for `ariba.applications.user.groups.page.size`. Depending on the number of groups assigned to the user, you can expect the following results:

    -   If the number of assigned groups is equal or exceeds the configured value, and the `ariba.applications.user.groups.paging.enabled` property is set to *true*, Identity Provisioning will read all user groups in separate requests.

        For example, if a user has 6 groups assigned and the value of the page size is set to *2*, Identity Provisioning will send 3 requests to read the user groups.

    -   If the number of assigned groups is less than the configured value for `ariba.applications.user.groups.page.size` or the property `ariba.applications.user.groups.paging.enabled` is disabled, the Identity Provisioning will read all user groups via one request.

        For example, if a user has 2 groups assigned and the value of the page size is set to *6*, Identity Provisioning will read all user groups via one request.


    Setting the property `ariba.applications.user.groups.paging.enabled` allows you to read users with a large number of groups assigned. For more information, see `ariba.applications.user.groups.paging.enabled`.

    Default value: *50*
    
    </td>
    </tr>
    </table>
    
    Exemplary destination \(property configuration\):


    <table>
    <tr>
    <td valign="top">
    
    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `ProxyType`=*Internet*

    `URL`=*https://openapi.ariba.com*

    `User`=*aaaa12345-1111-3333-cccc-1234567890*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `OAuth2TokenServiceURL`=*https://api.ariba.com/v2/oauth/token*

    `ariba.applications.group.flatten`=*false*

    `ariba.applications.support.patch.operation`=*true*

    `ariba.applications.api.key`=*123abc123XYZ000abc123ABC012345*

    `ariba.applications.realm.id`=*AN000111222333*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

7.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Ariba Applications* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Ariba Applications. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Ariba APIs Portal](https://developer.ariba.com/api/apis) → *Discover* → *SUPPLIER MANAGEMENT*

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
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
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
    >                 "sourcePath": "$.emails[0].value",
    >                 "targetPath": "$.emails[0].value",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['companyCode']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['companyCode']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['costCenter']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['costCenter']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingGroup']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingGroup']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['generalLedgerAccount']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['generalLedgerAccount']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingOrganization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingOrganization']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['plant']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['plant']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['currency']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['currency']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['deliverTo']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['deliverTo']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['purchasingUnit']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['purchasingUnit']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['network']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['network']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['addresses']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['addresses']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['passwordAdapter']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['passwordAdapter']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:User']['alternativeDisplayNames']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:User']['alternativeDisplayNames']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "optional": true,
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.title",
    >                 "optional": true,
    >                 "targetPath": "$.title"
    >             },
    >             {
    >                 "sourcePath": "$.locale",
    >                 "optional": true,
    >                 "targetPath": "$.locale",
    >                 "functions": [
    >                     {
    >                         "type": "substring",
    >                         "beginIndex": 0,
    >                         "endIndex": 2
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "optional": true,
    >                 "targetPath": "$.timezone"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.phoneNumbers"
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "optional": true
    >             }
    >         ]
    >     },
    >     "group": {
    >         "scimEntityEndpoint": "Groups",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
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
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:Group']['alternativeDisplayNames']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:Group']['alternativeDisplayNames']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
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
    > {
    >     "user": {
    >         "scimEntityEndpoint": "Users",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
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
    >                 "targetPath": "$.id",
    >                 "type": "remove",
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User",
    >                     "urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:User"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['companyCode']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['companyCode']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['costCenter']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['costCenter']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingGroup']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingGroup']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['generalLedgerAccount']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['generalLedgerAccount']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingOrganization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['purchasingOrganization']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['plant']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User']['plant']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['currency']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['currency']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['deliverTo']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['deliverTo']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['purchasingUnit']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['purchasingUnit']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['network']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['network']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['addresses']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['addresses']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['passwordAdapter']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:ariba:2.0:User']['passwordAdapter']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:User']['alternativeDisplayNames']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:User']['alternativeDisplayNames']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "condition": "$.emails[0].length() > 0",
    >                 "constant": true,
    >                 "targetPath": "$.emails[0].primary"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             },
    >             {
    >                 "sourcePath": "$.locale",
    >                 "optional": true,
    >                 "targetPath": "$.locale"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "optional": true,
    >                 "targetPath": "$.timezone"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.phoneNumbers",
    >                 "functions": [
    >                     {
    >                         "function": "putIfAbsent",
    >                         "key": "type",
    >                         "defaultValue": "work"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "optional": true
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
    >                 "targetPath": "$.id",
    >                 "type": "remove",
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:Group",
    >                     "urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:Group"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:Group']['alternativeDisplayNames']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:profile:Group']['alternativeDisplayNames']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.members",
    >                 "optional": true
    >             }
    >         ]
    >     }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
8.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PATCH**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PATCH**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PATCH** method for modifying entities.


**Related Information**  


[The SAP Ariba developer portal](https://help.sap.com/viewer/b61dd8c7e22c4fe489f191f66b4c48d6/cloud/en-US/1d55722e669e4c6aaa4eda5a011519ac.html)

[Video: Create application and API approval process](https://www.youtube.com/watch?v=CQQlADnbM6w)

