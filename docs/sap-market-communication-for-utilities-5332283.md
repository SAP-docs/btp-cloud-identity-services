<!-- loio5332283ea239409e91cc7ad682fd7341 -->

# SAP Market Communication for Utilities

Follow this procedure to set up SAP Market Communication for Utilities as a proxy system.



<a name="loio5332283ea239409e91cc7ad682fd7341__prereq_tcl_4r3_kfb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have user credentials for an external back-end system with read and write permissions.

-   To establish the connection between Identity Provisioning and SAP Market Communication for Utilities, you need to set up the communication user in SAP Market Communication for Utilities. You can do it now \(as a prerequisite\) or in the process of configuring SAP Market Communication for Utilities as a proxy system, as described in step 5.

-   > ### Note:  
    > Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.




<a name="loio5332283ea239409e91cc7ad682fd7341__context_tjq_xs3_kfb"/>

## Context

The SAP Market Communication for Utilities application is based on SAP BTP ABAP environment. You can use Identity Provisioning to configure SAP Market Communication for Utilities as a proxy system to execute *hybrid* scenarios. That means, it can provision its entities to another \(external\) back-end system by request, and then continue executing CRUD operations back to SAP Market Communication for Utilities, whenever the external back-end requests such. This scenario supports:

-   Reading of **business users** \(Employee\) and **business roles** \(which are considered as *groups*\)

-   Writing of **users** and **assignments**


> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



<a name="loio5332283ea239409e91cc7ad682fd7341__steps_ujq_xs3_kfb"/>

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

5.  Add *SAP Market Communication for Utilities* as a proxy system. For more information, see: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

6.  Set up the communication between Identity Provisioning and SAP Market Communication for Utilities and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP Market Communication for Utilities proxy system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](Operation-Guide/generate-and-manage-certificates-for-outbound-connection-76867db.md).

        Skip step **a.** if you want to use basic authentication.

        The next steps are performed in SAP Market Communication for Utilities backend system and are relevant for both basic and certificate-based authentication.

    2.  [Create a communication user](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/0377adea0401467f939827242c1f4014.html?version=Cloud) and provide the respective credentials.

        For basic authentication, provide *User Name* and *Password*.

        For certificate-based authentication, upload the certificate you have generated in the Identity Provisioning UI on the previous step.

    3.  [Create a communication system](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/c2234acd55774ebcbedb66744199273e.html?version=Cloud) and assign the created user to the communication system.

        For your Identity Provisioning scenario, provide *System ID*, *System Name* and *Host Name*.

    4.  [Create a communication arrangement](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/a0771f6765f54e1c8193ad8582a32edb.html?version=Cloud) with the created system.

        For your Identity Provisioning scenario, choose *Scenario ID* SAP\_COM\_0193 \(SAP Cloud Identity Provisioning Integration\).

        For more information, see [Maintain a Communication Arrangement for Inbound Communication](https://developers.sap.com/tutorials/abap-environment-communication-arrangement.html)

        > ### Note:  
        > The communication scenario *SAP\_COM\_0193* is enhanced to support the User UUID attribute which is generated by Identity Authentication at user creation.
        > 
        > The User UUID is universally unique identifier. This attribute is immutable and unique across technology layers, such as user interface, APIs, and security tokens, as well as across products and lines of business contributing to a business process in the Intelligent Enterprise.


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
    
    Specify the API URL to your SAP Market Communication for Utilities system.
    
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
    
    Enter your authentication method:

    -   *BasicAuthentication*

    -   *ClientCertificateAuthentication*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    Enter the *User Name* from the communication arrangement.

    > ### Restriction:  
    > Do not use special symbol '**,**' \(comma\) as it is not supported.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Valid if *BasicAuthentication* is configured as authentication method.

    Enter the *Password* for the user name from the communication arrangement.

    > ### Restriction:  
    > Do not use special symbol '**,**' \(comma\) as it is not supported.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `maco.skip.read.archived`
    
    </td>
    <td valign="top">
    
    In the event of archived \(disabled\) entities in your SAP Market Communication for Utilities system, choose whether the provisioning jobs to continue reading such entities or to skip them.

    This property is enabled by default. If you want to always read disabled entities, set the property to **false**, or delete it.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.date.variable.format`
    
    </td>
    <td valign="top">
    
    *yyyy-MM-dd*

    \(needed for the *Read Transformation*\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `maco.user.roles.overwrite`
    
    </td>
    <td valign="top">
    
    This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP Market Communication for Utilities proxy system in a hybrid scenario.

    -   **true** – the current user roles will be deleted in the proxy system, and the user will be updated only with the roles provisioned by the service.
    -   **false** – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the proxy system.

    See also: [Extended Explanation of the \*user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `maco.roles.filter`
    
    </td>
    <td valign="top">
    
    Enter OData filtering for reading roles in the SAP Market Communication for Utilities system.

    To learn what criteria you can use, see: [OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → **4.5 Filter System Query Option**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `maco.roles.page.size`
    
    </td>
    <td valign="top">
    
    Indicate how many business roles \(considered as *groups*\) per page to be read from your SAP Market Communication for Utilities system.

    The value must be an integer number.
    
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

    `URL`=*https://12345-aaaaa-3333.abap.hana.ondemand.com*

    `User`=*MyMaCoUser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `ips.date.variable.format`=*yyyy-MM-dd*

    `maco.skip.read.archived`=*true*

    `maco.user.roles.overwrite` = *false*

    `maco.roles.filter`=*startswith\(ID, 'EMPLOYEE\_LEVEL\_3'\) eq true*

    `maco.roles.page.size`=*30*
    
    </td>
    </tr>
    </table>
    
8.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Market Communication for Utilities* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Market Communication for Utilities system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP S/4HANA Cloud API: Business User](https://help.sap.com/viewer/f1531d40f450474dbf95f0404cb62007/latest/en-US/640fb5fa26664a7486de073b1882405c.html)

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
    >     "mappings": [
    >       {
    >         "sourcePath": "$.personID",
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
    >         "sourcePath": "$.personalInformation.firstName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.personalInformation.lastName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.personalInformation.middleName",
    >         "targetPath": "$.name.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.personalInformation.personFullName",
    >         "targetPath": "$.name.formatted",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.user.userName",
    >         "targetPath": "$.userName",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "targetPath": "$.schemas[0]",
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User"
    >       },
    >       {
    >         "targetPath": "$.schemas[1]",
    >         "constant": "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >       },
    >       {
    >         "constant": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "condition": "$.user.lockedIndicator == 'true'",
    >         "constant": false,
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "condition": "($.user.validityPeriod.startDate > '${currentDate}') || ('${currentDate}' > $.user.validityPeriod.endDate)",
    >         "constant": false,
    >         "optional": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.workplaceInformation.emailAddress",
    >         "targetPath": "$.emails[0].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.user.logonLanguageCode",
    >         "optional": true,
    >         "targetPath": "$.locale"
    >       },
    >       {
    >         "sourcePath": "$.PersonExternalID",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.user.role[*].roleName",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups[?(@.value)]"
    >       },
    >       {
    >         "sourcePath": "$.user.globalUserID",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "type": "valueMapping",
    >         "sourcePaths": [
    >           "$.user.timeZoneCode"
    >         ],
    >         "targetPath": "$.timezone",
    >         "defaultValue": "Europe/Berlin",
    >         "valueMappings": [
    >           {
    >             "key": [
    >               "WDFT"
    >             ],
    >             "mappedValue": "Europe/Berlin"
    >           },
    >           {
    >             "key": [
    >               "ISRAEL"
    >             ],
    >             "mappedValue": "Asia/Jerusalem"
    >           },
    >           {
    >             "key": [
    >               "RUS03"
    >             ],
    >             "mappedValue": "Europe/Moscow"
    >           },
    >           {
    >             "key": [
    >               "AUSNSW"
    >             ],
    >             "mappedValue": "Australia/Sydney"
    >           },
    >           {
    >             "key": [
    >               "UTC+4"
    >             ],
    >             "mappedValue": "Asia/Dubai"
    >           },
    >           {
    >             "key": [
    >               "BRAZIL"
    >             ],
    >             "mappedValue": "America/Sao_Paulo"
    >           },
    >           {
    >             "key": [
    >               "BRZLEA"
    >             ],
    >             "mappedValue": "America/Sao_Paulo"
    >           },
    >           {
    >             "key": [
    >               "MSTNO"
    >             ],
    >             "mappedValue": "America/Phoenix"
    >           },
    >           {
    >             "key": [
    >               "EST"
    >             ],
    >             "mappedValue": "America/New_York"
    >           },
    >           {
    >             "key": [
    >               "UTC"
    >             ],
    >             "mappedValue": "Etc/UTC"
    >           },
    >           {
    >             "key": [
    >               "UTC+3"
    >             ],
    >             "mappedValue": "Asia/Riyadh"
    >           },
    >           {
    >             "key": [
    >               "EST_"
    >             ],
    >             "mappedValue": "America/Toronto"
    >           },
    >           {
    >             "key": [
    >               "UTC+8"
    >             ],
    >             "mappedValue": "Asia/Shanghai"
    >           },
    >           {
    >             "key": [
    >               "JAPAN"
    >             ],
    >             "mappedValue": "Asia/Tokyo"
    >           }
    >         ]
    >       },
    >       {
    >         "type": "valueMapping",
    >         "sourcePaths": [
    >           "$.businessPartnerRoleCode"
    >         ],
    >         "targetPath": "$.userType",
    >         "defaultValue": "Employee",
    >         "valueMappings": [
    >           {
    >             "key": [
    >               "BUP003"
    >             ],
    >             "mappedValue": "Employee"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.ID",
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
    >         "sourcePath": "$.ID",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.to_BusinessUserAssignment.results",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members"
    >       },
    >       {
    >         "type": "remove",
    >         "targetPath": "$.members[*].__metadata"
    >       },
    >       {
    >         "type": "remove",
    >         "targetPath": "$.members[*].UserName"
    >       },
    >       {
    >         "type": "rename",
    >         "constant": "value",
    >         "targetPath": "$.members[*].PersonID"
    >       },
    >       {
    >         "constant": "User",
    >         "targetPath": "$.members[*].type"
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
    >     "mappings": [
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.personExternalID"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true,
    >         "targetPath": "$.personExternalID"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$.user.globalUserID"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.personID"
    >       },
    >       {
    >         "targetPath": "$.businessPartnerRoleCode",
    >         "type": "valueMapping",
    >         "sourcePaths": [
    >           "$.userType"
    >         ],
    >         "defaultValue": "BUP003",
    >         "valueMappings": [
    >           {
    >             "key": [
    >               "Employee"
    >             ],
    >             "mappedValue": "BUP003"
    >           }
    >         ]
    >       },
    >       {
    >         "scope": "createEntity",
    >         "sourceVariable": "currentDate",
    >         "targetPath": "$.validityPeriod.startDate"
    >       },
    >       {
    >         "scope": "createEntity",
    >         "constant": "9999-12-31",
    >         "targetPath": "$.validityPeriod.endDate"
    >       },
    >       {
    >         "scope": "createEntity",
    >         "sourceVariable": "currentDate",
    >         "targetPath": "$.user.validityPeriod.startDate"
    >       },
    >       {
    >         "scope": "createEntity",
    >         "constant": "9999-12-31",
    >         "targetPath": "$.user.validityPeriod.endDate"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.personalInformation.firstName"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.personalInformation.lastName"
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "optional": true,
    >         "targetPath": "$.personalInformation.middleName"
    >       },
    >       {
    >         "sourcePath": "$.name.formatted",
    >         "optional": true,
    >         "targetPath": "$.personalInformation.personFullName"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.user.userName"
    >       },
    >       {
    >         "sourcePath": "$.nickName",
    >         "optional": true,
    >         "targetPath": "$.user.nickName"
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "optional": true,
    >         "targetPath": "$.user.logonLanguageCode"
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "optional": true,
    >         "targetPath": "$.workplaceInformation.emailAddress"
    >       },
    >       {
    >         "condition": "$.active == false",
    >         "constant": "true",
    >         "targetPath": "$.user.lockedIndicator"
    >       }
    >     ],
    >     "scimEntityEndpoint": "Users"
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]"
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
    
    By default, Identity Provisioning reads group IDs and members. If you want the service to also read group descriptions, you can add an extra mapping to the *"group"* resource in the *Read Transformation*. To learn how, see [Guided Answers: Business Role Description](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:39660:40191).

9.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PATCH**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PATCH**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PATCH** method for modifying entities.




<a name="loio5332283ea239409e91cc7ad682fd7341__postreq_cf4_lgj_kfb"/>

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

