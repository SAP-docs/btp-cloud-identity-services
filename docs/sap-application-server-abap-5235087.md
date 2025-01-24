<!-- loio5235087c8a6e4860aac36a8c3675fb9d -->

# SAP Application Server ABAP

Follow this procedure to set up SAP Application Server ABAP \(AS ABAP\) as a source system.



## Prerequisites

> ### Note:  
> If you have purchased the Identity Provisioning service between **September 1, 2020** and **October 20, 2020**, and you want to make a connection to this on-premise system, follow the procedure in: [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-authentication/identity-authentication/connect-to-on-premise-systems-in-sap-cloud-identity-infrastructure?version=Cloud).

-   You have installed the Cloud Connector in your corporate environment and have done the initial configuration. For more information, see: [Cloud Connector \(Neo\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d751d065774e45e1b6bdbfdfd541da13.html)
-   You have credentials of a technical user with read permissions for AS ABAP, which plays the role of a user data source. Via this user, the Identity Provisioning service will call the ABAP public API in order to execute a number of function modules. These function modules are listed in **step 1** from the procedure below.
-   You have the following role, which provides all authorizations with read-only access to user data: **SAP\_BC\_JSF\_COMMUNICATION\_RO**

    For more information, see: [Requirements for the System User for UME-ABAP Communication](https://help.sap.com/docs/SAP_NETWEAVER_750/a42446bded624585958a36a71903a4a7/8f67d27676ace84080964d4c4223bb3c.html?locale=en-US)




## Context

SAP Application Server ABAP \(AS ABAP\) offers a user store and user administration capabilities for maintaining users and their authorizations for AS ABAP applications. You can configure AS ABAP as a source system for your identity provisioning process, in the following cases:

-   Use AS ABAP as a central store for the identity data of your business users.
-   Reuse the permission model, implemented in your AS ABAP client, as a permission model for cloud applications. For example, you can provision roles and permission assignments to SAP BTP.

> ### Note:  
> During a provisioning job \(*Read* or *Resync*\), only active ABAP users are read. That means, users that have been created before the job is started, and whose expiration date is after the end of the job.



## Procedure

1.  Open the Cloud Connector to add an access control system mapping for **AS ABAP**. This is needed to allow the Identity Provisioning service to access AS ABAP as a back-end system on the intranet. To learn how, see: [Configure Access Control \(RFC\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/ca5868997e48468395cf0ca4882f5783.html)

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

    Below are the fields you have to fill in the cockpit destination before using an AS ABAP client as a source system.

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
    
    **`jco.client.msserv`**
    
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

3.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

4.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

5.  Add *SAP Application Server ABAP* as a source system. To learn how, see: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md)

6.  From the *Destination Name* dropdown, choose the RFC destination you have created in *step 2*.

7.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Application Server ABAP* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in AS ABAP. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    When AS ABAP is configured as a source system for the Identity Provisioning service, the ABAP public API is used to retrieve the identity data from the AS ABAP system. During the reading process, the JSON data generated by the Identity Provisioning service, is following the structure of the API export parameters list and tables. Every BAPI table is represented as a JSON array and every BAPI structure is represented as a child JSON object.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > // The value of attribute entityIdSourceSystem stores the unique ID of the identity. Do not delete this statement! 
    > // You can exchange the default attribute USERNAME (which is used as a source) with another one, but make sure it is unique. 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.USERNAME",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    > 			
    > // The USERNAME attribute is also used as userName value for the internal JSON representation. 
    >             {
    >                 "sourcePath": "$.USERNAME",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.ALIAS.USERALIAS",
    >                 "optional": true,
    >                 "targetPath": "$.externalId",
    >                 "correlationAttribute": true
    >             },
    > 			
    > // The constant urn:ietf:params:scim:schemas:core:2.0:User is required as a value for the 
    > // schemas definition in the Identity Authentication SCIM REST API. 
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >                 "targetPath": "$.schemas[0]"
    >             },
    > 			
    > // The ADDRESS.E_MAIL attribute is used also as a first array value in the emails JSON array. 
    >             {
    >                 "sourcePath": "$.ADDRESS.E_MAIL",
    >                 "optional": true,
    >                 "targetPath": "$.emails[0].value",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "condition": "$.ADDRESS.E_MAIL EMPTY false",
    >                 "constant": true,
    >                 "targetPath": "$.emails[0].primary"
    >             },
    >             {
    >                 "condition": "$.ADDRESS.E_MAIL EMPTY false",
    >                 "constant": "work",
    >                 "targetPath": "$.emails[0].type"
    >             },
    > 			
    >             {
    >                 "sourcePath": "$.ADDRESS.FIRSTNAME",
    >                 "optional": true,
    >                 "targetPath": "$.name.givenName"
    >             },		
    >             {
    >                 "sourcePath": "$.ADDRESS.LASTNAME",
    >                 "optional": true,
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.ADDRESS.MIDDLENAME",
    >                 "optional": true,
    >                 "targetPath": "$.name.middleName"
    >             },
    >             {
    >                 "sourcePath": "$.ADDRESS.NICKNAME",
    >                 "optional": true,
    >                 "targetPath": "$.nickName"
    >             },
    >             {
    >                 "sourcePath": "$.ADDRESS.TITLE_P",
    >                 "optional": true,
    >                 "targetPath": "$.name.honorificPrefix"
    >             },
    >             {
    >                 "sourcePath": "$.ADDRESS.COUNTRY",
    >                 "optional": true,
    >                 "targetPath": "$.addresses[0].country"
    >             },
    >             {
    >                 "condition": "$.ADDRESS.COUNTRY EMPTY false",
    >                 "constant": true,
    >                 "targetPath": "$.addresses[0].primary"
    >             },
    >             {
    >                 "condition": "$.ADDRESS.COUNTRY EMPTY false",
    >                 "constant": "work",
    >                 "targetPath": "$.addresses[0].type"
    >             },
    >             {
    >                 "sourcePath": "$.ADDRESS.TEL1_NUMBR",
    >                 "optional": true,
    >                 "targetPath": "$.phoneNumbers[0].value"
    >             },
    >             {
    >                 "condition": "$.ADDRESS.TEL1_NUMBR EMPTY false",
    >                 "constant": true,
    >                 "targetPath": "$.phoneNumbers[0].primary"
    >             },
    >             {
    >                 "condition": "$.ADDRESS.TEL1_NUMBR EMPTY false",
    >                 "constant": "work",
    >                 "targetPath": "$.phoneNumbers[0].type"
    >             },
    > 
    > // The Identity Provisioning reads the specific ABAP language codes and mapped them as locales in the target system.
    > // The transformation provides an example with key = "W", which in the target system is mapped as "bg". The default language is en. 
    > // To see all languages and codes supported by AS ABAP, see the Related Information section below.
    >             {
    >                 "optional": true,
    >                 "targetPath": "$.locale",
    >                 "type": "valueMapping",
    >                 "sourcePaths": [
    >                     "$.DEFAULTS.LANGU"
    >                 ],
    >                 "defaultValue": "en",
    >                 "valueMappings": [
    >                     {
    >                         "key": [
    >                             "W"
    >                         ],
    >                         "mappedValue": "bg"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "optional": true,
    >                 "targetPath": "$.preferredLanguage",
    >                 "type": "valueMapping",
    >                 "functions": [
    >                     {
    >                         "function": "toLowerCaseString"
    >                     }
    >                 ],
    >                 "sourcePaths": [
    >                     "$.ADDRESS.LANGUP_ISO"
    >                 ]
    >             },
    > 
    > // The Identity Provisioning reads standard timezone codes, which are supported by the AS ABAP BAPI.
    > // However, the standard SCIM API does not support these codes, thus the target system can only accept values in format "<region>/<city>".
    > // The transformation provides an example with key = "EET", which in the target system is mapped as "Europe/Sofia". The default timezone is Berlin. 
    >             {
    >                 "optional": true,
    >                 "targetPath": "$.timezone",
    >                 "type": "valueMapping",
    >                 "sourcePaths": [
    >                     "$.LOGONDATA.TZONE"
    >                 ],
    >                 "defaultValue": "Europe/Berlin",
    >                 "valueMappings": [
    >                     {
    >                         "key": [
    >                             "EET"
    >                         ],
    >                         "mappedValue": "Europe/Sofia"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "constant": false,
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "condition": "($.ISLOCKED.LOCAL_LOCK != 'L') && ($.ISLOCKED.NO_USER_PW != 'L') && ($.ISLOCKED.GLOB_LOCK != 'L') && ($.ISLOCKED.WRNG_LOGON != 'L')",
    >                 "constant": true,
    >                 "targetPath": "$.active"
    >             },
    > 			
    > // The attribute ACTIVITYGROUPS (SAP ABAP roles) is transformed by default into groups attribute of the SCIM internal representation.
    >             {
    >                 "sourcePath": "$.ACTIVITYGROUPS[*].AGR_NAME",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups[?(@.value)]"
    >             }
    >         ]
    >      },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.ROLE_NAME",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.ROLE_NAME",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.USERLIST[*].USERNAME",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]"
    >             }
    >         ]
    >     }
    > }
    > }
    > ```

    **Default transformation supporting User UUID attribute:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.USERNAME",
    >         "targetVariable": "entityIdSourceSystem"
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
    >         "sourcePath": "$.ADDRESS.E_MAIL",
    >         "optional": true,
    >         "targetPath": "$.emails[0].value",
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
    >         "condition": "($.ISLOCKED.LOCAL_LOCK != 'L') && ($.ISLOCKED.GLOB_LOCK != 'L') && ($.ISLOCKED.WRNG_LOGON != 'L')",
    >         "constant": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.ACTIVITYGROUPS[*].AGR_NAME",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups[?(@.value)]"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.ROLE_NAME",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.ROLE_NAME",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "'%abap.role.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%abap.role.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.USERLIST[*].USERNAME",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "optional": true
    >       }
    >     ]
    >   }
    > }
    > ```

8.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




## Example

**How to transform roles, assigned to AS ABAP users, into corporate groups in the Identity Authentication?**

The AS ABAP roles are represented as groups in your Identity Authentication tenant. That is, when you configure AS ABAP as a source and Identity Authentication as a target system, the default transformations helps you to use the ABAP roles assignment of the users as source data and to automatically create corporate group assignments for the users in the Identity Authentication. When a user is assigned to one or more AS ABAP roles, the technical names of these roles \(their ABAP attribute name is **AGR\_NAME**\) will become corporate groups value in the Identity Authentication.

1.  Transforming source data into the intermediate JSON representation.

    The following example demonstrates how the sample roles, read from the AS ABAP system, will become groups in the intermediate JSON data, as a result from the transformation statement:


    <table>
    <tr>
    <th valign="top">

    Data read from AS ABAP user store
    
    </th>
    <th valign="top">

    Intermediate JSON data
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > 
    > …
    > "ACTIVITYGROUPS": [
    >     {
    >       "AGR_TEXT": "FICO 03",
    >       "AGR_NAME": "ZFICO_03",
    >       "FROM_DAT": "27.04.2016",
    >       "TO_DAT": "31.12.9999"
    >     },
    >     {
    >       "AGR_TEXT": "CASH 01",
    >       "AGR_NAME": "ZCASH_01",
    >       "FROM_DAT": "16.05.2016",
    >       "TO_DAT": "31.12.9999"
    >     }
    >   ]
    > …
    > 
    > ```


    
    </td>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > 
    > … 
    > "groups":[ 
    > { 
    > "value": "ZFICO_03" 
    > }, 
    > { 
    > "value": “ZCASH_01” 
    > },
    > ] …
    > 
    > ```


    
    </td>
    </tr>
    </table>
    
2.  The mapping statement in the default transformation, available when the Identity Authentication service is configured as a target system:

    > ### Sample Code:  
    > ```
    > 
    > { 
    > "sourcePath": "$.groups", 
    > "preserveArrayWithSingleElement": true, 
    > "optional": true, 
    > "targetPath": "$.corporateGroups" 
    > } 
    > 
    > ```

3.  The following example demonstrates how the groups from the intermediate JSON are transformed into corporate groups, using the transformation statement:


    <table>
    <tr>
    <th valign="top">

    Intermediate JSON Data
    
    </th>
    <th valign="top">

    Transformation output result
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > 
    > … 
    > "groups":[ 
    > { 
    > "value": "ZFICO_03" 
    > }, 
    > { 
    > "value": “ZCASH_01” 
    > },
    > ] …
    > 
    > ```


    
    </td>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > 
    > … 
    > "corporateGroups":[ 
    > { 
    > "value": "ZFICO_03" 
    > }, 
    > { 
    > "value": “ZCASH_01”  
    > },
    > ] …
    > 
    > ```


    
    </td>
    </tr>
    </table>
    



<a name="loio5235087c8a6e4860aac36a8c3675fb9d__postreq_qv1_mqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[ABAP: Supported Languages and Code Pages](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/c1/ae563cd2ad4f0ce10000000a11402f/frameset.htm)

