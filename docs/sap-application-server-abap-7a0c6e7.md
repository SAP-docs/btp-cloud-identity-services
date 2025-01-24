<!-- loio7a0c6e7f67f5456fab32a34a252f4399 -->

# SAP Application Server ABAP

Follow this procedure to set up SAP Application Server ABAP \(AS ABAP\) as a target system.



<a name="loio7a0c6e7f67f5456fab32a34a252f4399__prereq_tnm_v4j_y2b"/>

## Prerequisites

> ### Note:  
> If you have purchased the Identity Provisioning service between **September 1, 2020** and **October 20, 2020**, and you want to make a connection to this on-premise system, follow the procedure in: [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-authentication/identity-authentication/connect-to-on-premise-systems-in-sap-cloud-identity-infrastructure?version=Cloud).

-   You have installed the Cloud Connector in your corporate environment and have done the initial configuration. For more information, see: [Cloud Connector \(Neo\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d751d065774e45e1b6bdbfdfd541da13.html)
-   You have credentials of a technical user with write permissions for AS ABAP. Via this user, the Identity Provisioning service will call the ABAP public API in order to execute a number of function modules. These function modules are listed in **step 1** from the procedure below.
-   You have the following role, which provides all authorizations with read and write access to user data: **SAP\_BC\_JSF\_COMMUNICATION**

    For more information, see: [Requirements for the System User for UME-ABAP Communication](https://help.sap.com/docs/SAP_NETWEAVER_750/a42446bded624585958a36a71903a4a7/8f67d27676ace84080964d4c4223bb3c.html?locale=en-US)




<a name="loio7a0c6e7f67f5456fab32a34a252f4399__context_vdl_w4j_y2b"/>

## Context

SAP Application Server ABAP \(AS ABAP\) offers a user store and user administration capabilities for maintaining users and their authorizations for AS ABAP applications. You can configure AS ABAP as a target system so as to provision new entities from another on-premise or cloud system.

> ### Caution:  
> You can't create or delete groups in AS ABAP. That means:
> 
> -   On the attempt to create a group in AS ABAP, Identity Provisioning will only add new members or update existing ones. Also, when the service reads a group from a source system, there must be a group with the exact same display name \(case sensitive\) in the AS ABAP target system. Otherwise, an error will be thrown and the group members will not be updated.
> 
>     If group names in the source system defer from the ones in AS ABAP, you can define value mappings for these group names so the provisioning will still work. To learn how, see [Transformation Expressions](transformation-expressions-bb8537b.md) → section **valueMapping**.
> 
> -   On the attempt to delete a group in AS ABAP, Identity Provisioning will only remove its members \(group assignments\). And this can happen only if the relevant group assignments have been provisioned/are present in the target system.

Groups in source systems are mapped to roles in AS ABAP target systems.

> ### Note:  
> Role unassignments are handled differently in AS ABAP version 7.31 and lower, and versions higher than 7.31. For example: If a child role R2 is assigned to a user – first, indirectly through a parent role R1, and then directly to the user, when the parent role is unassigned, expect the following results:
> 
> AS ABAP **7.31 and lower**: Directly assigned parent role R1 and indirectly assigned child role R2 are unassigned. Directly assigned child role R2 is still assigned to the user.
> 
> AS ABAP **higher than 7.31**: All roles are unassigned from the user.



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

    The destination configuration is required by the Identity Provisioning service to find the back-end system to be used for writing data. It also provides the credentials of the technical user, needed for the connection to the ABAP public API.

    Below are the fields you have to fill in the cockpit destination before using an AS ABAP client as a target system.

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
    
    `ips.overwrite.existedbefore.assignments`
    
    </td>
    <td valign="top">
    
    This property defines whether or not the Identity Provisioning service to overwrite user/group assignments that have existed in the target system before you start provisioning entities to that system.

    -   If you start a provisioning job without setting this property \(by default, it's *true*\), all assignments from the source group will overwrite the ones from the target group.
    -   If you set the property to *false*, all existing assignments will be kept in the target system group, and the new ones will just be added.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.groups`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of group assignments to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of group assignments, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.delete.threshold.users`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of users to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of users, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > If connection properties, like `User` and `Password`, are configured both in the destination \(SAP BTP cockpit\) and on the *Properties* tab \(Identity Provisioning User Interface\), the values set in the destination are considered with higher priority.

3.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

4.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

5.  Add *SAP Application Server ABAP* as a target system. To learn how, see: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md)

6.  From the *Destination Name* dropdown, choose the RFC destination you have created in *step 2*.

7.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Application Server ABAP* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in AS ABAP. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    When AS ABAP is configured as a target system for the Identity Provisioning service, the ABAP public API is used to write the identity data retrieved from the relevant source system. During the writing process, the JSON data is following the structure of the export parameters and will turn them into list and tables. Therefore, every JSON array from the intermediate transformation will be represented as a BAPI table, and every child JSON object will be represented as a BAPI structure.

    **Default transformation:**

    -   Use the default transformation if the version of your AS ABAP system is *7.40* or higher. If your system version is *7.31*, you can still use this transformation – just apply SAP Note [1695883](https://me.sap.com/notes/1695883).

        **Note:** If a user is *inactive* in the source system, the default transformation creates it as *inactive* \(locked\) in AS ABAP too.

        > ### Code Syntax:  
        > ```
        > 
        > // The value of attribute entityIdTargetSystem stores the entity's unique ID, and then 
        > // it's written in the target system as a username. Do not delete this statement!
        > 
        > {
        >     "user": {
        >         "mappings": [
        >             {
        >                 "sourceVariable": "entityIdTargetSystem",
        >                 "targetPath": "$.USERNAME"
        >             },
        > 			
        > // The userName attribute is used also as USERNAME value for the internal JSON representation. 
        >             {
        >                 "sourcePath": "$.userName",
        >                 "targetPath": "$.USERNAME"
        >             },
        >             {
        >                 "sourcePath": "$.externalId",
        >                 "optional": true,
        >                 "targetPath": "$.ALIAS.USERALIAS",
        >                 "defaultValue": ""
        >             },
        >             {
        >                 "condition": "$.emails[?(@.primary == true)].value != []",
        >                 "sourcePath": "$.emails[?(@.primary == true)].value",
        >                 "preserveArrayWithSingleElement": false,
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.E_MAIL"
        >             },
        >             {
        >                 "condition": "$.emails[?(@.type == 'work')].value != []",
        >                 "sourcePath": "$.emails[?(@.type == 'work')].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.E_MAIL",
        >                 "functions": [
        >                     {
        >                         "function": "elementAt",
        >                         "index": 0
        >                     }
        >                 ]
        >             },
        >             {
        >                 "sourcePath": "$.emails[*].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.ADDSMTP[?(@.E_MAIL)]"
        >             },
        >             {
        >                 "sourcePath": "$.name.familyName",
        >                 "targetPath": "$.ADDRESS.LASTNAME"
        >             },
        >             {
        >                 "sourcePath": "$.name.givenName",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.FIRSTNAME"
        >             },
        >             {
        >                 "sourcePath": "$.name.middleName",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.MIDDLENAME"
        >             },
        >             {
        >                 "sourcePath": "$.nickName",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.NICKNAME"
        >             },
        >             {
        >                 "sourcePath": "$.name.honorificPrefix",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.TITLE_P"
        >             },
        >             {
        >                 "condition": "$.phoneNumbers[?(@.primary == true)].value != []",
        >                 "sourcePath": "$.phoneNumbers[?(@.primary == true)].value",
        >                 "preserveArrayWithSingleElement": false,
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.TEL1_NUMBR"
        >             },
        >             {
        >                 "condition": "$.phoneNumbers[?(@.type == 'work')].value != []",
        >                 "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.TEL1_NUMBR",
        >                 "functions": [
        >                     {
        >                         "function": "elementAt",
        >                         "index": 0
        >                     }
        >                 ]
        >             },
        >             {
        >                 "sourcePath": "$.phoneNumbers[*].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.ADDTEL[?(@.TELEPHONE)]"
        >             },
        > 
        > // The Identity Provisioning reads the locales from the source system and map them as specific ABAP language codes in the target ABAP system.
        > // The transformation provides an example with key = "bg", which in the ABAP system is mapped as "W". The default language is en. 
        > // To see all languages and codes supported by AS ABAP, see the Related Information section below.
        >             {
        >                 "optional": true,
        >                 "targetPath": "$.DEFAULTS.LANGU",
        >                 "type": "valueMapping",
        >                 "sourcePaths": [
        >                     "$.locale"
        >                 ],
        >                 "defaultValue": "E",
        >                 "valueMappings": [
        >                     {
        >                         "key": [
        >                             "bg"
        >                         ],
        >                         "mappedValue": "W"
        >                     }
        >                 ]
        >             },
        >             {
        >                 "sourcePath": "$.preferredLanguage",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.LANGUP_ISO",
        >                 "functions": [
        >                     {
        >                         "function": "toUpperCaseString"
        >                     }
        >                 ]
        >             },
        > 
        > 
        > // The Identity Provisioning writes standard timezone codes, which are supported by the AS ABAP BAPI.
        > // However, the standard SCIM API does not support these codes, thus the source system can only provide values in format "<region>/<city>".
        > // The transformation provides an example with key = "Europe/Sofia", which in the target system is mapped as "EET". The default timezone is CET. 
        >             {
        >                 "optional": true,
        >                 "targetPath": "$.LOGONDATA.TZONE",
        >                 "type": "valueMapping",
        >                 "sourcePaths": [
        >                     "$.timezone"
        >                 ],
        >                 "defaultValue": "CET",
        >                 "valueMappings": [
        >                     {
        >                         "key": [
        >                             "Europe/Sofia"
        >                         ],
        >                         "mappedValue": "EET"
        >                     }
        >                 ]
        >             },
        >              {
        >                 "targetPath": "$.PASSWORD.BAPIPWD",
        >                 "scope": "createEntity",
        >                 "functions": [
        >                     {
        >                         "function": "randomPassword",
        >                         "passwordLength": 24,
        >                         "minimumNumberOfLowercaseLetters": 1,
        >                         "minimumNumberOfUppercaseLetters": 1,
        >                         "minimumNumberOfDigits": 1,
        >                         "minimumNumberOfSpecialSymbols": 0
        >                     }
        >                 ]
        >             },
        >             {
        >               "constant": "updateEntity",
        >               "targetVariable": "operationTypeVariable"
        >             },
        >             {
        >               "constant": "createEntity",
        >               "targetVariable": "operationTypeVariable",
        >               "scope": "createEntity"
        >             },
        >             {
        >               "condition": "$.active == false && '${operationTypeVariable}' == 'createEntity'",
        >               "constant": "X",
        >               "targetPath": "$.LOCK_LOCALLY"
        >             },
        >             {
        >               "condition": "'${operationTypeVariable}' == 'updateEntity'",
        >               "constant": "U",
        >               "targetPath": "$.LOCK"
        >             },
        >             {
        >               "condition": "$.active == false && '${operationTypeVariable}' == 'updateEntity'",
        >               "constant": "L",
        >               "targetPath": "$.LOCK"
        >             }
        >        ]
        >   },
        >     "group": {
        >         "mappings": [
        >             {
        >                 "sourcePath": "$.displayName",
        >                 "targetVariable": "entityIdTargetSystem",
        >                 "scope": "createEntity"
        >             },
        >             {
        >                 "sourcePath": "$.displayName",
        >                 "targetPath": "$.ROLE_NAME"
        >             },
        >             {
        >                 "sourcePath": "$.members[*].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.USERLIST[?(@.USERNAME)]"
        >             }
        >         ]
        >     }
        > }
        > ```

    -   If your AS ABAP version is *7.30* or lower, use the transformation below.

        **Note:** This transformation creates all users as *active* \(unlocked\) in AS ABAP, regardless if they are *active* or *inactive* in the source system.

        > ### Code Syntax:  
        > ```
        > 
        > {
        >     "user": {
        >         "mappings": [
        >             {
        >                 "sourceVariable": "entityIdTargetSystem",
        >                 "targetPath": "$.USERNAME"
        >             },			
        >             {
        >                 "sourcePath": "$.userName",
        >                 "targetPath": "$.USERNAME"
        >             },
        >             {
        >                 "sourcePath": "$.externalId",
        >                 "optional": true,
        >                 "targetPath": "$.ALIAS.USERALIAS",
        >                 "defaultValue": ""
        >             },
        >             {
        >                 "condition": "$.emails[?(@.primary == true)].value != []",
        >                 "sourcePath": "$.emails[?(@.primary == true)].value",
        >                 "preserveArrayWithSingleElement": false,
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.E_MAIL"
        >             },
        >             {
        >                 "condition": "$.emails[?(@.type == 'work')].value != []",
        >                 "sourcePath": "$.emails[?(@.type == 'work')].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.E_MAIL",
        >                 "functions": [
        >                     {
        >                         "function": "elementAt",
        >                         "index": 0
        >                     }
        >                 ]
        >             },
        >             {
        >                 "sourcePath": "$.emails[*].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.ADDSMTP[?(@.E_MAIL)]"
        >             },
        >             {
        >                 "sourcePath": "$.name.familyName",
        >                 "targetPath": "$.ADDRESS.LASTNAME"
        >             },
        >             {
        >                 "sourcePath": "$.name.givenName",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.FIRSTNAME"
        >             },
        >             {
        >                 "sourcePath": "$.name.middleName",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.MIDDLENAME"
        >             },
        >             {
        >                 "sourcePath": "$.nickName",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.NICKNAME"
        >             },
        >             {
        >                 "sourcePath": "$.name.honorificPrefix",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.TITLE_P"
        >             },
        >             {
        >                 "condition": "$.phoneNumbers[?(@.primary == true)].value != []",
        >                 "sourcePath": "$.phoneNumbers[?(@.primary == true)].value",
        >                 "preserveArrayWithSingleElement": false,
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.TEL1_NUMBR"
        >             },
        >             {
        >                 "condition": "$.phoneNumbers[?(@.type == 'work')].value != []",
        >                 "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.TEL1_NUMBR",
        >                 "functions": [
        >                     {
        >                         "function": "elementAt",
        >                         "index": 0
        >                     }
        >                 ]
        >             },
        >             {
        >                 "sourcePath": "$.phoneNumbers[*].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.ADDTEL[?(@.TELEPHONE)]"
        >             },
        >             {
        >                 "optional": true,
        >                 "targetPath": "$.DEFAULTS.LANGU",
        >                 "type": "valueMapping",
        >                 "sourcePaths": [
        >                     "$.locale"
        >                 ],
        >                 "defaultValue": "E",
        >                 "valueMappings": [
        >                     {
        >                         "key": [
        >                             "bg"
        >                         ],
        >                         "mappedValue": "W"
        >                     }
        >                 ]
        >             },
        >             {
        >                 "sourcePath": "$.preferredLanguage",
        >                 "optional": true,
        >                 "targetPath": "$.ADDRESS.LANGUP_ISO",
        >                 "functions": [
        >                     {
        >                         "function": "toUpperCaseString"
        >                     }
        >                 ]
        >             },
        >             {
        >                 "optional": true,
        >                 "targetPath": "$.LOGONDATA.TZONE",
        >                 "type": "valueMapping",
        >                 "sourcePaths": [
        >                     "$.timezone"
        >                 ],
        >                 "defaultValue": "CET",
        >                 "valueMappings": [
        >                     {
        >                         "key": [
        >                             "Europe/Sofia"
        >                         ],
        >                         "mappedValue": "EET"
        >                     }
        >                 ]
        >             },
        >              {
        >                 "targetPath": "$.PASSWORD.BAPIPWD",
        >                 "scope": "createEntity",
        >                 "functions": [
        >                     {
        >                         "function": "randomPassword",
        >                         "passwordLength": 24,
        >                         "minimumNumberOfLowercaseLetters": 1,
        >                         "minimumNumberOfUppercaseLetters": 1,
        >                         "minimumNumberOfDigits": 1,
        >                         "minimumNumberOfSpecialSymbols": 0
        >                     }
        >                 ]
        >             },
        >             {
        >               "constant": "updateEntity",
        >               "targetVariable": "operationTypeVariable"
        >             },
        >             {
        >               "constant": "createEntity",
        >               "targetVariable": "operationTypeVariable",
        >               "scope": "createEntity"
        >             },
        >             {
        >               "condition": "'${operationTypeVariable}' == 'updateEntity'",
        >               "constant": "U",
        >               "targetPath": "$.LOCK"
        >             },
        >             {
        >               "condition": "$.active == false && '${operationTypeVariable}' == 'updateEntity'",
        >               "constant": "L",
        >               "targetPath": "$.LOCK"
        >             }
        >        ]
        >   },
        >     "group": {
        >         "mappings": [
        >             {
        >                 "sourcePath": "$.displayName",
        >                 "targetVariable": "entityIdTargetSystem",
        >                 "scope": "createEntity"
        >             },
        >             {
        >                 "sourcePath": "$.displayName",
        >                 "targetPath": "$.ROLE_NAME"
        >             },
        >             {
        >                 "sourcePath": "$.members[*].value",
        >                 "preserveArrayWithSingleElement": true,
        >                 "optional": true,
        >                 "targetPath": "$.USERLIST[?(@.USERNAME)]"
        >             }
        >         ]
        >     }
        > }
        > ```

    -   Default transformation supporting User UUID attribute:

        The following SAP Note must be implemented in the SAP AS ABAP [3003462](https://me.sap.com/notes/3003462) *Interface enhancement for global user ID*.

        > ### Code Syntax:  
        > ```
        > {
        >   "user": {
        >     "condition": "($.emails EMPTY true) || isValidEmail($.emails[0].value)",
        >     "mappings": [
        >       {
        >         "sourceVariable": "entityIdTargetSystem",
        >         "targetPath": "$.USERNAME"
        >       },
        >       {
        >         "sourcePath": "$.userName",
        >         "targetPath": "$.USERNAME"
        >       },
        >       {
        >         "sourcePath": "$.externalId",
        >         "optional": true,
        >         "targetPath": "$.ALIAS.USERALIAS",
        >         "defaultValue": ""
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
        >         "sourcePath": "$.name.familyName",
        >         "targetPath": "$.ADDRESS.LASTNAME"
        >       },
        >       {
        >         "sourcePath": "$.name.givenName",
        >         "optional": true,
        >         "targetPath": "$.ADDRESS.FIRSTNAME"
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
        >         "targetPath": "$.PASSWORD.BAPIPWD",
        >         "scope": "createEntity",
        >         "functions": [
        >           {
        >             "function": "randomPassword",
        >             "passwordLength": 24,
        >             "minimumNumberOfLowercaseLetters": 1,
        >             "minimumNumberOfUppercaseLetters": 1,
        >             "minimumNumberOfDigits": 1,
        >             "minimumNumberOfSpecialSymbols": 0
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
        >     "condition": "('%abap.role.prefix%' === 'null') || ($.displayName =~ /%abap.role.prefix%.*/)",
        >     "mappings": [
        >       {
        >         "scope": "createEntity",
        >         "sourcePath": "$.displayName",
        >         "targetVariable": "entityIdTargetSystem",
        >         "functions": [
        >           {
        >             "condition": "('%abap.role.prefix%' !== 'null') && (@ =~ /%abap.role.prefix%.*/)",
        >             "function": "replaceFirstString",
        >             "regex": "%abap.role.prefix%",
        >             "replacement": ""
        >           }
        >         ]
        >       },
        >       {
        >         "sourcePath": "$.displayName",
        >         "targetPath": "$.ROLE_NAME",
        >         "functions": [
        >           {
        >             "condition": "('%abap.role.prefix%' !== 'null') && (@ =~ /%abap.role.prefix%.*/)",
        >             "function": "replaceFirstString",
        >             "regex": "%abap.role.prefix%",
        >             "replacement": ""
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
        >             "function": "resolveEntityIds"
        >           }
        >         ]
        >       }
        >     ]
        >   }
        > }
        > 
        > ```


8.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio7a0c6e7f67f5456fab32a34a252f4399__postreq_qv1_mqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[ABAP: Supported Languages and Code Pages](https://help.sap.com/saphelp_nw73ehp1/helpdata/en/c1/ae563cd2ad4f0ce10000000a11402f/frameset.htm)

