<!-- loioa78881b9cb5d4f5d8b458c2d5be277b7 -->

# SAP Application Server ABAP

Follow this procedure to set up SAP Application Server ABAP \(AS ABAP\) as a proxy system.



<a name="loioa78881b9cb5d4f5d8b458c2d5be277b7__prereq_tnm_v4j_y2b"/>

## Prerequisites

> ### Note:  
> If you have purchased the Identity Provisioning service between **September 1, 2020** and **October 20, 2020**, and you want to make a connection to this on-premise system, follow the procedure in: [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-authentication/identity-authentication/connect-to-on-premise-systems-in-sap-cloud-identity-infrastructure?version=Cloud).

-   You have installed the Cloud Connector in your corporate environment and have done the initial configuration. For more information, see: [Cloud Connector \(Neo\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d751d065774e45e1b6bdbfdfd541da13.html)
-   You have credentials of a technical user with read and write permissions for AS ABAP, which plays both the role of a user data source and a target system. Via this user, the Identity Provisioning service will call the ABAP public API in order to execute a number of function modules. These function modules are listed in **step 1** from the procedure below.
-   You have the following role, which provides all authorizations with read and write access to user data: **SAP\_BC\_JSF\_COMMUNICATION**

    For more information, see: [Configuring the UME to Use an AS ABAP as Data Source](https://help.sap.com/doc/saphelp_nw73/latest/en-US/9e/fdcf3d4f902d10e10000000a114084/frameset.htm)




<a name="loioa78881b9cb5d4f5d8b458c2d5be277b7__context_vdl_w4j_y2b"/>

## Context

SAP Application Server ABAP \(AS ABAP\) offers a user store and user administration capabilities for maintaining users and their authorizations for AS ABAP applications. You can configure AS ABAP as a proxy system so as to provision entities between AS ABAP and another on-premise system.

> ### Note:  
> During the *Initial Load*, only active ABAP users are read. That means, users that have been created before the initial load job is started, and whose expiration date is after the end of the job. To learn about initial load, see **step 8** below – Transformations.

> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



## Procedure

1.  Open Cloud Connector to add an access control system mapping for **AS ABAP**. This is needed to allow the Identity Provisioning service to access AS ABAP as a back-end system on the intranet. To learn how, see: [Configure Access Control \(RFC\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/ca5868997e48468395cf0ca4882f5783.html)

    Go to *Cloud To On-Premise* \> *Access Control* tab and select protocol *RFC SNC*. Then, expose the following *exact names* as accessible resources:

    -   `PRGN_ROLE_GETLIST`
    -   `BAPI_USER_GETLIST`
    -   `BAPI_USER_GET_DETAIL`
    -   `BAPI_USER_CREATE1`
    -   `BAPI_USER_ACTGROUPS_ASSIGN`
    -   `IDENTITY_MODIFY`
    -   `BAPI_USER_DELETE`
    -   `PRGN_ACTIVITY_GROUPS_LOAD_RFC`

    These are Business Application Programming Interface \(BAPI\) functional modules designed to perform certain tasks in the SAP AS ABAP system, such as retrieving, creating, updating or deleting user data.

    For more information about each function module and its parameters, refer to the documentation provided in the SAP system. Logon to your SAP system and run transaction code `SE37`. In the *Function Builder: Initial Screen*, enter the function name, choose *Display* and then *Functional Module Documentation*.

2.  Open SAP BTP cockpit, and in your Identity Provisioning subaccount create a destination for the AS ABAP system. To learn how, see: [Create RFC Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/848f2abb59664a719f7bac83b0021c1e.html)

    The destination configuration is required by the Identity Provisioning service to find the back-end system to be used for reading data. It also provides the credentials of the technical user, needed for the connection to the ABAP public API.

    Below are the fields you have to fill in the cockpit destination before using an AS ABAP client as a proxy system.

    > ### Note:  
    > In the RFC destination, you can set only JCo properties. Properties starting with `abap` are connector specific and must be set in the Identity Provisioning UI.


    <table>
    <tr>
    <th valign="top">

    Field/Property Name
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Name*
    
    </td>
    <td valign="top">
    
    Enter a destination name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Type*
    
    </td>
    <td valign="top">
    
    Select *RFC*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *User*
    
    </td>
    <td valign="top">
    
    Enter the user for AS ABAP.

    The *User* field corresponds to property `jco.client.user` in the exported RFC destination.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Password*
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for the AS ABAP user.

    The *Password* field corresponds to property `jco.client.passwd` in the exported RFC destination.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **`jco.client.client`**
    
    </td>
    <td valign="top">
    
    Provide the client to be used in the ABAP system. Valid format is a three-digit number.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **`jco.destination.proxy_type`**
    
    </td>
    <td valign="top">
    
    Defines the proxy type of the connection you need to provide for your ABAP system.

    The proxy type *OnPremise* requires the Cloud Connector to access resources within your on-premise network.

    Enter: *OnPremise*
    
    </td>
    </tr>
    <tr>
    <td valign="top" align="center" colspan="2">
    
    **Direct Connection** 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **`jco.client.ashost`**
    
    </td>
    <td valign="top">
    
    Provide the virtual host entry that you have configured in the Cloud Connector → *Access Control* configuration.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **`jco.client.sysnr`**
    
    </td>
    <td valign="top">
    
    Provide the "system number" of the ABAP system.
    
    </td>
    </tr>
    <tr>
    <td valign="top" align="center" colspan="2">
    
    **Load Balancing Connection** 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **`jco.client.mshost`**
    
    </td>
    <td valign="top">
    
    Represents the message server host to be used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **`jco.client.r3name`**
    
    </td>
    <td valign="top">
    
    Provide the three-character system ID of the ABAP system to be addressed.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **`jco.client.msservt`**
    
    </td>
    <td valign="top">
    
    Provide the port on which the message server is listening for incoming requests. You can use this property as an alternative to `jco.client.r3name`.
    
    </td>
    </tr>
    <tr>
    <td valign="top" align="center" colspan="2">
    
    **Optional Properties** 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.destination.peak_limit`
    
    </td>
    <td valign="top">
    
    The value represents the maximum number of active connections that can simultaneously be created for a destination. For example: *10*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jco.destination.pool_capacity`
    
    </td>
    <td valign="top">
    
    The value represents the maximum number of idle connections kept open by the destination. For example: *5*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `abap.user.name.filter`
    
    </td>
    <td valign="top">
    
    Filters user names by a regular expression. The regex can define any kind of search pattern.

    For example, `abap.user.name.filter` = **^MAR.\*** reads all user names that start with *MAR*, such as **MARK**, **MARTINA**, and so on.

    > ### Note:  
    > This property has a higher priority over `abap.user.filter`. That means, if you set both properties in a system, the value of **abap.user.name.filter** will be used. However, if the value of `abap.user.name.filter` is empty, then **abap.user.filter**’s value will be used instead.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `abap.role.name.filter`
    
    </td>
    <td valign="top">
    
    Filters user roles by a regular expression. The regex can define any kind of search pattern.

    For example, `abap.role.name.filter` = **^inter.\*** reads all roles which start with *inter*, such as **internal**, **internship**, and so on.

    > ### Note:  
    > This property has a higher priority over `abap.role.filter`. That means, if you set both properties in a system, the value of **abap.role.name.filter** will be used. However, if the value of `abap.role.name.filter` is empty, then **abap.role.filter**’s value will be used instead.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `abap.user.membership.filter`
    
    </td>
    <td valign="top">
    
    Filters users by a regular expression, based on their *Role* memberships in AS ABAP. The regex can define any kind of search pattern.

    For example, `abap.user.membership.filter` = **\(?i\)^new.\*** reads all users who have an assigned role which starts with *new*. This regex is case insensitive, which means the result can be roles starting with **new**, or **New**, or **NEW**, and so on.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > If connection properties, like `User` and `Password`, are configured both in the destination \(SAP BTP cockpit\) and on the *Properties* tab \(Identity Provisioning User Interface\), the values set in the destination are considered with higher priority.

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Users & Authorizations* \> *Administrators*.

4.  Create a technical user with the necessary authorizations. It will later be used by the external consumer to connect to Identity Provisioning.

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



5.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

6.  Add *SAP Application Server ABAP* as a proxy system. To learn how, see: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md)

7.  From the *Destination Name* dropdown, choose the RFC destination you have created in *step 2*.

8.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Application Server ABAP* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your AS ABAP. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    Default read and write transformations:

    > ### Tip:  
    > The proxy *Read Transformation* is used when the external client application \(for example, SAP Identity Management\) makes initial load. That is, executing GET requests to the resource endpoints \(**/Users** or **/Groups**\) to retrieve the corresponding entities of the particular type. The external client application can also execute GET requests to a single resource endpoint \(querying a single resource is supported\). In this case, the proxy system acts as a *source* one.
    > 
    > The proxy *Write Transformation* is used when the external application manages the entities in the proxy system – creates new entities, updates existing ones, or deletes existing ones. In this case, the proxy system acts as a *target* one.
    > 
    > However, after a *Create* or *Update* operation is performed on the proxy system, the *Read Transformation* is applied to the result, so that the created or updated entity is sent back to the external application. This behavior demonstrates that the proxy *Read Transformation* is used for *write* cases, as well.

    -   Use the default transformations if the version of your AS ABAP system is *7.40* or higher. If your system version is *7.31*, you can still use these transformations – just apply SAP Note [1695883](https://me.sap.com/notes/1695883).

        **NOTE:** If a user is *inactive* in the identity management system, the default Write Transformation creates it as *inactive* \(locked\) in AS ABAP too.


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
        >         "sourcePath": "$.USERNAME",
        >         "targetVariable": "entityIdSourceSystem",
        >         "targetPath": "$.id",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.USERNAME",
        >         "targetPath": "$.userName",
        >         "correlationAttribute": true
        >       },
        >       {
        >         "sourcePath": "$.ALIAS.USERALIAS",
        >         "optional": true,
        >         "targetPath": "$.externalId",
        >         "correlationAttribute": true
        >       },
        >       {
        >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
        >         "targetPath": "$.schemas[0]"
        >       },
        >       {
        >         "constant": "User",
        >         "targetPath": "$.meta.resourceType"
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
        >         "sourcePath": "$.ADDRESS.E_MAIL",
        >         "targetPath": "$.emails[0].value",
        >         "optional": true,
        >         "correlationAttribute": true
        >       },
        >       {
        >         "condition": "$.ADDRESS.E_MAIL EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.emails[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.E_MAIL EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.emails[0].type"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.FIRSTNAME",
        >         "optional": true,
        >         "targetPath": "$.name.givenName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.LASTNAME",
        >         "optional": true,
        >         "targetPath": "$.name.familyName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.MIDDLENAME",
        >         "optional": true,
        >         "targetPath": "$.name.middleName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.NICKNAME",
        >         "optional": true,
        >         "targetPath": "$.nickName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.TITLE_P",
        >         "optional": true,
        >         "targetPath": "$.name.honorificPrefix"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.COUNTRY",
        >         "optional": true,
        >         "targetPath": "$.addresses[0].country"
        >       },
        >       {
        >         "condition": "$.ADDRESS.COUNTRY EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.addresses[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.COUNTRY EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.addresses[0].type"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.TEL1_NUMBR",
        >         "optional": true,
        >         "targetPath": "$.phoneNumbers[0].value"
        >       },
        >       {
        >         "condition": "$.ADDRESS.TEL1_NUMBR EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.phoneNumbers[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.TEL1_NUMBR EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.phoneNumbers[0].type"
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.DEFAULTS.LANGU"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.locale",
        >         "defaultValue": "en",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "W"
        >             ],
        >             "mappedValue": "bg"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.ADDRESS.LANGUP_ISO"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.preferredLanguage",
        >         "functions": [
        >           {
        >             "function": "toLowerCaseString"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.LOGONDATA.TZONE"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.timezone",
        >         "defaultValue": "Europe/Berlin",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "EET"
        >             ],
        >             "mappedValue": "Europe/Sofia"
        >           }
        >         ]
        >       },
        >       {
        >         "constant": false,
        >         "targetPath": "$.active"
        >       },
        >       {
        >         "condition": "($.ISLOCKED.LOCAL_LOCK != 'L') && ($.ISLOCKED.NO_USER_PW != 'L') && ($.ISLOCKED.GLOB_LOCK != 'L') && ($.ISLOCKED.WRNG_LOGON != 'L') && ($.LOCK != 'L') && ($.LOCK_LOCALLY != 'X')",
        >         "constant": true,
        >         "targetPath": "$.active"
        >       },
        >       {
        >         "sourcePath": "$.ACTIVITYGROUPS[*].AGR_NAME",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.groups[?(@.value)]",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "direct",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.groups[*].type",
        >         "optional": true
        >       }
        >     ]
        >   },
        >   "group": {
        >     "scimEntityEndpoint": "Groups",
        >     "mappings": [
        >       {
        >         "sourcePath": "$.ROLE_NAME",
        >         "targetVariable": "entityIdSourceSystem",
        >         "targetPath": "$.id",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "Group",
        >         "targetPath": "$.meta.resourceType"
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
        >         "sourcePath": "$.ROLE_NAME",
        >         "targetPath": "$.displayName"
        >       },
        >       {
        >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
        >         "targetPath": "$.schemas[0]"
        >       },
        >       {
        >         "sourcePath": "$.USERLIST[*].USERNAME",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.members[?(@.value)]",
        >         "optional": true,
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "User",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.members[*].type",
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
        >     "mappings": [
        >       {
        >         "sourcePath": "$.userName",
        >         "targetPath": "$.USERNAME",
        >         "targetVariable": "entityIdTargetSystem"
        >       },
        >       {
        >         "scope": "deleteEntity",
        >         "sourceVariable": "entityIdTargetSystem",
        >         "targetVariable": "entityIdTargetSystem",
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.externalId",
        >         "optional": true,
        >         "targetPath": "$.ALIAS.USERALIAS"
        >       },
        >       {
        >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
        >         "optional": true,
        >         "targetPath": "$.SAPUSER_UUID.SAP_UID"
        >       },
        >       {
        >         "condition": "$.emails[?(@.primary == true)].value != []",
        >         "sourcePath": "$.emails[?(@.primary == true)].value",
        >         "preserveArrayWithSingleElement": false,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.E_MAIL"
        >       },
        >       {
        >         "condition": "$.emails[?(@.type == 'work')].value != []",
        >         "sourcePath": "$.emails[?(@.type == 'work')].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.E_MAIL",
        >         "functions": [
        >           {
        >             "function": "elementAt",
        >             "index": 0
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.emails[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDSMTP[?(@.E_MAIL)]"
        >       },
        >       {
        >         "sourcePath": "$.name.givenName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.FIRSTNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.familyName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.LASTNAME"
        >       },
        >       {
        >         "scope": "createEntity",
        >         "sourcePath": "$.name.familyName",
        >         "targetPath": "$.ADDRESS.LASTNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.middleName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.MIDDLENAME"
        >       },
        >       {
        >         "sourcePath": "$.nickName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.NICKNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.honorificPrefix",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TITLE_P"
        >       },
        >       {
        >         "condition": "$.phoneNumbers[?(@.primary == true)].value != []",
        >         "sourcePath": "$.phoneNumbers[?(@.primary == true)].value",
        >         "preserveArrayWithSingleElement": false,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TEL1_NUMBR"
        >       },
        >       {
        >         "condition": "$.phoneNumbers[?(@.type == 'work')].value != []",
        >         "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TEL1_NUMBR",
        >         "functions": [
        >           {
        >             "function": "elementAt",
        >             "index": 0
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.phoneNumbers[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDTEL[?(@.TELEPHONE)]"
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.locale"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.DEFAULTS.LANGU",
        >         "defaultValue": "E",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "bg"
        >             ],
        >             "mappedValue": "W"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.preferredLanguage",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.LANGUP_ISO",
        >         "functions": [
        >           {
        >             "function": "toUpperCaseString"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.timezone"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.LOGONDATA.TZONE",
        >         "defaultValue": "CET",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "Europe/Sofia"
        >             ],
        >             "mappedValue": "EET"
        >           }
        >         ]
        >       },
        >       {
        >         "scope": "createEntity",
        >         "targetPath": "$.PASSWORD.BAPIPWD",
        >         "functions": [
        >           {
        >             "type": "randomPassword",
        >             "passwordLength": 24,
        >             "minimumNumberOfLowercaseLetters": 1,
        >             "minimumNumberOfUppercaseLetters": 1,
        >             "minimumNumberOfDigits": 1,
        >             "minimumNumberOfSpecialSymbols": 0
        >           }
        >         ]
        >       },
        >       {
        >         "scope": "createEntity",
        >         "optional": true,
        >         "ignore": true,
        >         "sourcePath": "$.password",
        >         "targetPath": "$.PASSWORD.BAPIPWD"
        >       },
        >       {
        >         "constant": "updateEntity",
        >         "targetVariable": "operationTypeVariable"
        >       },
        >       {
        >         "constant": "createEntity",
        >         "targetVariable": "operationTypeVariable",
        >         "scope": "createEntity"
        >       },
        >       {
        >         "condition": "$.active == false && '${operationTypeVariable}' == 'createEntity'",
        >         "constant": "X",
        >         "targetPath": "$.LOCK_LOCALLY"
        >       },
        >       {
        >         "condition": "'${operationTypeVariable}' == 'updateEntity'",
        >         "constant": "U",
        >         "targetPath": "$.LOCK"
        >       },
        >       {
        >         "condition": "$.active == false && '${operationTypeVariable}' == 'updateEntity'",
        >         "constant": "L",
        >         "targetPath": "$.LOCK"
        >       }
        >     ]
        >   },
        >   "group": {
        >     "scimEntityEndpoint": "Groups",
        >     "mappings": [
        >       {
        >         "sourcePath": "$.displayName",
        >         "targetPath": "$.ROLE_NAME"
        >       },
        >       {
        >         "sourceVariable": "entityIdTargetSystem",
        >         "targetVariable": "entityIdTargetSystem",
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.members[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.USERLIST[?(@.USERNAME)]",
        >         "optional": true,
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString",
        >             "applyOnElements": true
        >           }
        >         ]
        >       }
        >     ]
        >   }
        > }
        > ```


        
        </td>
        </tr>
        </table>
        
    -   If your AS ABAP version is *7.30* or lower, use the transformations below.

        **NOTE:** The Write Transformation creates all users as *active* \(unlocked\) in AS ABAP, regardless if they are *active* or *inactive* in the identity management system.


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
        >         "sourcePath": "$.USERNAME",
        >         "targetVariable": "entityIdSourceSystem",
        >         "targetPath": "$.id",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.USERNAME",
        >         "targetPath": "$.userName",
        >         "correlationAttribute": true
        >       },
        >       {
        >         "sourcePath": "$.ALIAS.USERALIAS",
        >         "optional": true,
        >         "targetPath": "$.externalId",
        >         "correlationAttribute": true
        >       },
        >       {
        >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
        >         "targetPath": "$.schemas[0]"
        >       },
        >       {
        >         "constant": "User",
        >         "targetPath": "$.meta.resourceType"
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
        >         "sourcePath": "$.ADDRESS.E_MAIL",
        >         "targetPath": "$.emails[0].value",
        >         "optional": true,
        >         "correlationAttribute": true
        >       },
        >       {
        >         "condition": "$.ADDRESS.E_MAIL EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.emails[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.E_MAIL EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.emails[0].type"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.FIRSTNAME",
        >         "optional": true,
        >         "targetPath": "$.name.givenName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.LASTNAME",
        >         "optional": true,
        >         "targetPath": "$.name.familyName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.MIDDLENAME",
        >         "optional": true,
        >         "targetPath": "$.name.middleName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.NICKNAME",
        >         "optional": true,
        >         "targetPath": "$.nickName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.TITLE_P",
        >         "optional": true,
        >         "targetPath": "$.name.honorificPrefix"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.COUNTRY",
        >         "optional": true,
        >         "targetPath": "$.addresses[0].country"
        >       },
        >       {
        >         "condition": "$.ADDRESS.COUNTRY EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.addresses[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.COUNTRY EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.addresses[0].type"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.TEL1_NUMBR",
        >         "optional": true,
        >         "targetPath": "$.phoneNumbers[0].value"
        >       },
        >       {
        >         "condition": "$.ADDRESS.TEL1_NUMBR EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.phoneNumbers[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.TEL1_NUMBR EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.phoneNumbers[0].type"
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.DEFAULTS.LANGU"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.locale",
        >         "defaultValue": "en",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "W"
        >             ],
        >             "mappedValue": "bg"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.ADDRESS.LANGUP_ISO"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.preferredLanguage",
        >         "functions": [
        >           {
        >             "function": "toLowerCaseString"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.LOGONDATA.TZONE"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.timezone",
        >         "defaultValue": "Europe/Berlin",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "EET"
        >             ],
        >             "mappedValue": "Europe/Sofia"
        >           }
        >         ]
        >       },
        >       {
        >         "constant": false,
        >         "targetPath": "$.active"
        >       },
        >       {
        >         "condition": "($.ISLOCKED.LOCAL_LOCK != 'L') && ($.ISLOCKED.NO_USER_PW != 'L') && ($.ISLOCKED.GLOB_LOCK != 'L') && ($.ISLOCKED.WRNG_LOGON != 'L') && ($.LOCK != 'L') && ($.LOCK_LOCALLY != 'X')",
        >         "constant": true,
        >         "targetPath": "$.active"
        >       },
        >       {
        >         "sourcePath": "$.ACTIVITYGROUPS[*].AGR_NAME",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.groups[?(@.value)]",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "direct",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.groups[*].type",
        >         "optional": true
        >       }
        >     ]
        >   },
        >   "group": {
        >     "scimEntityEndpoint": "Groups",
        >     "mappings": [
        >       {
        >         "sourcePath": "$.ROLE_NAME",
        >         "targetVariable": "entityIdSourceSystem",
        >         "targetPath": "$.id",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "Group",
        >         "targetPath": "$.meta.resourceType"
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
        >         "sourcePath": "$.ROLE_NAME",
        >         "targetPath": "$.displayName"
        >       },
        >       {
        >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
        >         "targetPath": "$.schemas[0]"
        >       },
        >       {
        >         "sourcePath": "$.USERLIST[*].USERNAME",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.members[?(@.value)]",
        >         "optional": true,
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "User",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.members[*].type",
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
        >     "mappings": [
        >       {
        >         "sourcePath": "$.userName",
        >         "targetPath": "$.USERNAME",
        >         "targetVariable": "entityIdTargetSystem"
        >       },
        >       {
        >         "scope": "deleteEntity",
        >         "sourceVariable": "entityIdTargetSystem",
        >         "targetVariable": "entityIdTargetSystem",
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.externalId",
        >         "optional": true,
        >         "targetPath": "$.ALIAS.USERALIAS"
        >       },
        >       {
        >         "condition": "$.emails[?(@.primary == true)].value != []",
        >         "sourcePath": "$.emails[?(@.primary == true)].value",
        >         "preserveArrayWithSingleElement": false,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.E_MAIL"
        >       },
        >       {
        >         "condition": "$.emails[?(@.type == 'work')].value != []",
        >         "sourcePath": "$.emails[?(@.type == 'work')].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.E_MAIL",
        >         "functions": [
        >           {
        >             "function": "elementAt",
        >             "index": 0
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.emails[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDSMTP[?(@.E_MAIL)]"
        >       },
        >       {
        >         "sourcePath": "$.name.givenName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.FIRSTNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.familyName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.LASTNAME"
        >       },
        >       {
        >         "scope": "createEntity",
        >         "sourcePath": "$.name.familyName",
        >         "targetPath": "$.ADDRESS.LASTNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.middleName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.MIDDLENAME"
        >       },
        >       {
        >         "sourcePath": "$.nickName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.NICKNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.honorificPrefix",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TITLE_P"
        >       },
        >       {
        >         "condition": "$.phoneNumbers[?(@.primary == true)].value != []",
        >         "sourcePath": "$.phoneNumbers[?(@.primary == true)].value",
        >         "preserveArrayWithSingleElement": false,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TEL1_NUMBR"
        >       },
        >       {
        >         "condition": "$.phoneNumbers[?(@.type == 'work')].value != []",
        >         "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TEL1_NUMBR",
        >         "functions": [
        >           {
        >             "function": "elementAt",
        >             "index": 0
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.phoneNumbers[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDTEL[?(@.TELEPHONE)]"
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.locale"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.DEFAULTS.LANGU",
        >         "defaultValue": "E",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "bg"
        >             ],
        >             "mappedValue": "W"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.preferredLanguage",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.LANGUP_ISO",
        >         "functions": [
        >           {
        >             "function": "toUpperCaseString"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.timezone"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.LOGONDATA.TZONE",
        >         "defaultValue": "CET",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "Europe/Sofia"
        >             ],
        >             "mappedValue": "EET"
        >           }
        >         ]
        >       },
        >       {
        >         "scope": "createEntity",
        >         "targetPath": "$.PASSWORD.BAPIPWD",
        >         "functions": [
        >           {
        >             "type": "randomPassword",
        >             "passwordLength": 24,
        >             "minimumNumberOfLowercaseLetters": 1,
        >             "minimumNumberOfUppercaseLetters": 1,
        >             "minimumNumberOfDigits": 1,
        >             "minimumNumberOfSpecialSymbols": 0
        >           }
        >         ]
        >       },
        >       {
        >         "scope": "createEntity",
        >         "optional": true,
        >         "ignore": true,
        >         "sourcePath": "$.password",
        >         "targetPath": "$.PASSWORD.BAPIPWD"
        >       },
        >       {
        >         "scope": "createEntity",
        >         "sourcePath": "$.groups[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ACTIVITYGROUPS[?(@.AGR_NAME)]",
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString",
        >             "applyOnElements": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "updateEntity",
        >         "targetVariable": "operationTypeVariable"
        >       },
        >       {
        >         "constant": "createEntity",
        >         "targetVariable": "operationTypeVariable",
        >         "scope": "createEntity"
        >       },
        >       {
        >         "condition": "'${operationTypeVariable}' == 'updateEntity'",
        >         "constant": "U",
        >         "targetPath": "$.LOCK"
        >       },
        >       {
        >         "condition": "$.active == false && '${operationTypeVariable}' == 'updateEntity'",
        >         "constant": "L",
        >         "targetPath": "$.LOCK"
        >       }
        >     ]
        >   },
        >   "group": {
        >     "scimEntityEndpoint": "Groups",
        >     "mappings": [
        >       {
        >         "sourcePath": "$.displayName",
        >         "targetPath": "$.ROLE_NAME"
        >       },
        >       {
        >         "sourceVariable": "entityIdTargetSystem",
        >         "targetVariable": "entityIdTargetSystem",
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.members[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.USERLIST[?(@.USERNAME)]",
        >         "optional": true,
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString",
        >             "applyOnElements": true
        >           }
        >         ]
        >       }
        >     ]
        >   }
        > }
        > ```


        
        </td>
        </tr>
        </table>
        
    -   **Default transformations supporting User UUID attribute:**


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
        >         "sourcePath": "$.USERNAME",
        >         "targetVariable": "entityIdSourceSystem",
        >         "targetPath": "$.id",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.USERNAME",
        >         "targetPath": "$.userName",
        >         "correlationAttribute": true
        >       },
        >       {
        >         "sourcePath": "$.ALIAS.USERALIAS",
        >         "optional": true,
        >         "targetPath": "$.externalId",
        >         "correlationAttribute": true
        >       },
        >       {
        >         "sourcePath": "$.SAPUSER_UUID.SAP_UID",
        >         "optional": true,
        >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
        >       },
        >       {
        >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
        >         "targetPath": "$.schemas[0]"
        >       },
        >       {
        >         "constant": "User",
        >         "targetPath": "$.meta.resourceType"
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
        >         "sourcePath": "$.ADDRESS.E_MAIL",
        >         "targetPath": "$.emails[0].value",
        >         "optional": true,
        >         "correlationAttribute": true
        >       },
        >       {
        >         "condition": "$.ADDRESS.E_MAIL EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.emails[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.E_MAIL EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.emails[0].type"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.FIRSTNAME",
        >         "optional": true,
        >         "targetPath": "$.name.givenName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.LASTNAME",
        >         "optional": true,
        >         "targetPath": "$.name.familyName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.MIDDLENAME",
        >         "optional": true,
        >         "targetPath": "$.name.middleName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.NICKNAME",
        >         "optional": true,
        >         "targetPath": "$.nickName"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.TITLE_P",
        >         "optional": true,
        >         "targetPath": "$.name.honorificPrefix"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.COUNTRY",
        >         "optional": true,
        >         "targetPath": "$.addresses[0].country"
        >       },
        >       {
        >         "condition": "$.ADDRESS.COUNTRY EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.addresses[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.COUNTRY EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.addresses[0].type"
        >       },
        >       {
        >         "sourcePath": "$.ADDRESS.TEL1_NUMBR",
        >         "optional": true,
        >         "targetPath": "$.phoneNumbers[0].value"
        >       },
        >       {
        >         "condition": "$.ADDRESS.TEL1_NUMBR EMPTY false",
        >         "constant": true,
        >         "targetPath": "$.phoneNumbers[0].primary"
        >       },
        >       {
        >         "condition": "$.ADDRESS.TEL1_NUMBR EMPTY false",
        >         "constant": "work",
        >         "targetPath": "$.phoneNumbers[0].type"
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.DEFAULTS.LANGU"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.locale",
        >         "defaultValue": "en",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "W"
        >             ],
        >             "mappedValue": "bg"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.ADDRESS.LANGUP_ISO"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.preferredLanguage",
        >         "functions": [
        >           {
        >             "function": "toLowerCaseString"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.LOGONDATA.TZONE"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.timezone",
        >         "defaultValue": "Europe/Berlin",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "EET"
        >             ],
        >             "mappedValue": "Europe/Sofia"
        >           }
        >         ]
        >       },
        >       {
        >         "constant": false,
        >         "targetPath": "$.active"
        >       },
        >       {
        >         "condition": "($.ISLOCKED.LOCAL_LOCK != 'L') && ($.ISLOCKED.GLOB_LOCK != 'L') && ($.ISLOCKED.WRNG_LOGON != 'L') && ($.LOCK != 'L') && ($.LOCK_LOCALLY != 'X')",
        >         "constant": true,
        >         "targetPath": "$.active"
        >       },
        >       {
        >         "sourcePath": "$.ACTIVITYGROUPS[*].AGR_NAME",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.groups[?(@.value)]",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "direct",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.groups[*].type",
        >         "optional": true
        >       }
        >     ]
        >   },
        >   "group": {
        >     "scimEntityEndpoint": "Groups",
        >     "mappings": [
        >       {
        >         "sourcePath": "$.ROLE_NAME",
        >         "targetVariable": "entityIdSourceSystem",
        >         "targetPath": "$.id",
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "Group",
        >         "targetPath": "$.meta.resourceType"
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
        >         "sourcePath": "$.ROLE_NAME",
        >         "targetPath": "$.displayName"
        >       },
        >       {
        >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
        >         "targetPath": "$.schemas[0]"
        >       },
        >       {
        >         "sourcePath": "$.USERLIST[*].USERNAME",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.members[?(@.value)]",
        >         "optional": true,
        >         "functions": [
        >           {
        >             "type": "encode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "User",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.members[*].type",
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
        >     "mappings": [
        >       {
        >         "sourcePath": "$.userName",
        >         "targetPath": "$.USERNAME",
        >         "targetVariable": "entityIdTargetSystem"
        >       },
        >       {
        >         "scope": "deleteEntity",
        >         "sourceVariable": "entityIdTargetSystem",
        >         "targetVariable": "entityIdTargetSystem",
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.externalId",
        >         "optional": true,
        >         "targetPath": "$.ALIAS.USERALIAS"
        >       },
        >       {
        >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
        >         "optional": true,
        >         "targetPath": "$.SAPUSER_UUID.SAP_UID"
        >       },
        >       {
        >         "condition": "$.emails[?(@.primary == true)].value != []",
        >         "sourcePath": "$.emails[?(@.primary == true)].value",
        >         "preserveArrayWithSingleElement": false,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.E_MAIL"
        >       },
        >       {
        >         "condition": "$.emails[?(@.type == 'work')].value != []",
        >         "sourcePath": "$.emails[?(@.type == 'work')].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.E_MAIL",
        >         "functions": [
        >           {
        >             "function": "elementAt",
        >             "index": 0
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.emails[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDSMTP[?(@.E_MAIL)]"
        >       },
        >       {
        >         "sourcePath": "$.name.givenName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.FIRSTNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.familyName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.LASTNAME"
        >       },
        >       {
        >         "scope": "createEntity",
        >         "sourcePath": "$.name.familyName",
        >         "targetPath": "$.ADDRESS.LASTNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.middleName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.MIDDLENAME"
        >       },
        >       {
        >         "sourcePath": "$.nickName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.NICKNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.honorificPrefix",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TITLE_P"
        >       },
        >       {
        >         "condition": "$.phoneNumbers[?(@.primary == true)].value != []",
        >         "sourcePath": "$.phoneNumbers[?(@.primary == true)].value",
        >         "preserveArrayWithSingleElement": false,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TEL1_NUMBR"
        >       },
        >       {
        >         "condition": "$.phoneNumbers[?(@.type == 'work')].value != []",
        >         "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.TEL1_NUMBR",
        >         "functions": [
        >           {
        >             "function": "elementAt",
        >             "index": 0
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.phoneNumbers[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ADDTEL[?(@.TELEPHONE)]"
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.locale"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.DEFAULTS.LANGU",
        >         "defaultValue": "E",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "bg"
        >             ],
        >             "mappedValue": "W"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.preferredLanguage",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.LANGUP_ISO",
        >         "functions": [
        >           {
        >             "function": "toUpperCaseString"
        >           }
        >         ]
        >       },
        >       {
        >         "type": "valueMapping",
        >         "sourcePaths": [
        >           "$.timezone"
        >         ],
        >         "optional": true,
        >         "targetPath": "$.LOGONDATA.TZONE",
        >         "defaultValue": "CET",
        >         "valueMappings": [
        >           {
        >             "key": [
        >               "Europe/Sofia"
        >             ],
        >             "mappedValue": "EET"
        >           }
        >         ]
        >       },
        >       {
        >         "scope": "createEntity",
        >         "targetPath": "$.PASSWORD.BAPIPWD",
        >         "functions": [
        >           {
        >             "type": "randomPassword",
        >             "passwordLength": 24,
        >             "minimumNumberOfLowercaseLetters": 1,
        >             "minimumNumberOfUppercaseLetters": 1,
        >             "minimumNumberOfDigits": 1,
        >             "minimumNumberOfSpecialSymbols": 0
        >           }
        >         ]
        >       },
        >       {
        >         "scope": "createEntity",
        >         "optional": true,
        >         "ignore": true,
        >         "sourcePath": "$.password",
        >         "targetPath": "$.PASSWORD.BAPIPWD"
        >       },
        >       {
        >         "scope": "createEntity",
        >         "sourcePath": "$.groups[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "optional": true,
        >         "targetPath": "$.ACTIVITYGROUPS[?(@.AGR_NAME)]",
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString",
        >             "applyOnElements": true
        >           }
        >         ]
        >       },
        >       {
        >         "constant": "updateEntity",
        >         "targetVariable": "operationTypeVariable"
        >       },
        >       {
        >         "constant": "createEntity",
        >         "targetVariable": "operationTypeVariable",
        >         "scope": "createEntity"
        >       },
        >       {
        >         "condition": "$.active == false && '${operationTypeVariable}' == 'createEntity'",
        >         "constant": "X",
        >         "targetPath": "$.LOCK_LOCALLY"
        >       },
        >       {
        >         "condition": "'${operationTypeVariable}' == 'updateEntity'",
        >         "constant": "U",
        >         "targetPath": "$.LOCK"
        >       },
        >       {
        >         "condition": "$.active == false && '${operationTypeVariable}' == 'updateEntity'",
        >         "constant": "L",
        >         "targetPath": "$.LOCK"
        >       }
        >     ]
        >   },
        >   "group": {
        >     "scimEntityEndpoint": "Groups",
        >     "mappings": [
        >       {
        >         "sourcePath": "$.displayName",
        >         "targetPath": "$.ROLE_NAME"
        >       },
        >       {
        >         "sourceVariable": "entityIdTargetSystem",
        >         "targetVariable": "entityIdTargetSystem",
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString"
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.members[*].value",
        >         "preserveArrayWithSingleElement": true,
        >         "targetPath": "$.USERLIST[?(@.USERNAME)]",
        >         "optional": true,
        >         "functions": [
        >           {
        >             "type": "decode",
        >             "algorithm": "base32",
        >             "skipPadding": true
        >           },
        >           {
        >             "type": "toString",
        >             "applyOnElements": true
        >           }
        >         ]
        >       }
        >     ]
        >   }
        > }
        > ```


        
        </td>
        </tr>
        </table>
        

9.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.




<a name="loioa78881b9cb5d4f5d8b458c2d5be277b7__postreq_cf4_lgj_kfb"/>

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

