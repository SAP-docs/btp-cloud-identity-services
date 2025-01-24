<!-- loiof217bd39c17d47cdb4f89ed19cb2c701 -->

# Identity Authentication

Follow this procedure to set up SAP Cloud Identity Service – Identity Authentication as a target system.



<a name="loiof217bd39c17d47cdb4f89ed19cb2c701__prereq_ezp_nrh_vdb"/>

## Prerequisites

To establish the connection between Identity Provisioning and Identity Authentication, you need to set up the technical user \(of type *System*\) in Identity Authentication and assign this user the necessary authorizations. You have the option to do it either now, as a prerequisite, or while configuring Identity Authentication as a target system, as described in step 3.



## Context

Identity Authentication provides authentication and single sign-on for users in the cloud.

Using Identity Provisioning, you can read corporate users from on-premise or cloud systems, and provision them to the Identity Authentication user store. This way, you can implement secure authentication, single sign-on \(SSO\), strong authentication and mobile SSO so that the provisioned users have access to the business applications of your company. For example, you can implement two-factor authentication and mobile SSO for SAP SuccessFactors users.

You can use the Identity Provisioning UI to configure Identity Authentication as a target system where you can provision users, groups and group members. The target system consumes SCIM 2.0 API provided by Identity Authentication.

There are two versions of the Identity Authentication SCIM API. They are controlled by the `ias.api.version` property as follows:

-   When the value is set to `1` or the property is not defined \(typical for systems created before versioning was introduced on July 9, 2021\) - Identity Authentication SCIM API \(in short, SCIM API version 1\) is used.

    For more information on how to update to version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md)

-   When the value is set to `2` - Identity Directory SCIM API \(in short, SCIM API version 2\) is used. This value is set automatically for all manually created systems in the Identity Provisioning UI after versioning was introduced on July 9, 2021.

    SCIM API version 2 does not support managing of group assignments via the SCIM user resource. The "groups" attribute of the user is read-only. This means that the user group assignments should be managed via the SCIM group resources using the "members" attribute \(as it is defined by the SCIM standard\). Also, the group resource mapping in the transformation is not ignored by default, as it is in SCIM API version 1.

    > ### Note:  
    > Identity Authentication \(using SCIM API version 2\) and Identity Directory are sometimes used interchangeably. Identity Directory is the persistency layer of SAP Cloud Identity Services – Identity Authentication.


To create Identity Authentication as a target system, proceed as follows:



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *Identity Authentication* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and Identity Authentication and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added Identity Authentication target system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Manage Certificates](Operation-Guide/manage-certificates-86d06a0.md).

        Skip step **a.** if you want to use basic authentication.

        In SAP Cloud Identity Services administration console, perform the next steps. They are relevant for both basic and certificate-based authentication.

    2.  [Add System as administrator](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/bbbdbdd3899942ce874f3aae9ba9e21d.html#loiocefb742a36754b18bbe5c3503ac6d87c) and provide the respective credentials.

        For basic authentication, provide a password. The user ID will be generated automatically when you set the password for the first time.

        For certificate-based authentication, upload the certificate you have generated in the Identity Provisioning UI on the previous step.

    3.  Save your changes.

    4.  Make sure *Manage Users* and *Manage Groups* authorization roles are enabled for the technical user. This way, you can create, edit and delete users and groups in the Identity Authentication user store.


5.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Specify the URL of the Identity Authentication tenant of your company.

    For example: **https://mytenant.accounts.ondemand.com**

    > ### Note:  
    > If your Identity Authentication Shanghai \(China\) tenants reside on SAP BTP, Neo environment, you should use the following URL pattern: *https://<tenant\_ID\>.accounts.sapcloud.cn/*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Enter: *Internet*

    The Identity Authentication is a cloud solution and is outside of your company on-premise infrastructure.
    
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

    Enter the Client ID \(previously User ID\) of the Identity Authentication technical user. It is generated automatically for the administrator of type system, when choosing *Secrets* \> *Add* \> *Save*. For example: *1ab7c243-5de5-4530-8g14-1234h26373ab*

    If your technical user was created before *January 2020*, enter the T-user. For example: *T000003*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Valid if *BasicAuthentication* is configured as authentication method.

    Enter the Client Secret \(previously Password\) of the Identity Authentication technical user. It is generated automatically for the administrator of type system, when choosing *Secrets* \> *Add* \> *Save*.
    
    </td>
    </tr>
    </table>
    
    **Optional Properties**


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
    
    -   `ias.<property_name>`

    -   `scim.<property_name>`



    
    </td>
    <td valign="top">
    
    When using SCIM API version 2, property names start with `ias` prefix, for example: `ias.user.unique.attribute`.

    When using SCIM API version 1, property names start with `scim` prefix, for example: `scim.user.unique.attribute`.

    For more information, see [List of Properties](list-of-properties-d6f3577.md). Use the main search or filter properties by *Name* or *System Type* columns.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ias.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    This property defines by which unique attribute\(s\) an existing user will be resolved in the event of conflicting users. It appears by default when the system is created, and its value is set to *userName*.

    Other possible values:

    -   *emails\[0\].value*

    -   *userName,emails\[0\].value*

    -   *phoneNumbers\[0\].value*

    -   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes


    If the service finds a user on the target system through this filter, then the conflicting user will overwrite the existing one. If the service does not find a user on the target system through this filter, the creation will fail.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.failed.request.retry.attempts`
    
    </td>
    <td valign="top">
    
    Predefined value: *2*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.failed.request.retry.attempts.interval`
    
    </td>
    <td valign="top">
    
    Predefined value: *60*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.groups`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of groups to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of groups, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.users`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of users to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of users, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    </table>
    
6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Identity Authentication* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    When Identity Authentication is configured as a target system, the default transformation logic writes all the user attributes in the Identity Authentication user store. The logic is provided by the Identity Authentication SCIM REST API, which then maps the attributes to the internal SCIM representation.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Identity Authentication system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    SCIM API version 1: [Identity Authentication: SCIM REST API](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/2f215687fcf34170b0bbc8b36b60f2e9.html)

    SCIM API version 2: [Identity Directory SCIM API](https://api.sap.com/api/IdDS_SCIM/resource)

    When Identity Authentication is configured as a target system, the default transformation logic:

    -   Reads all user attributes from the intermediate SCIM representation.

    -   Skips some of the attributes from the identity records.


    This way, the transformation logic ensures that the identity data, sent to the Identity Provisioning SCIM REST API, is consistent.

    **Default transformation for SCIM API version 1:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "condition": "($.emails.length() > 0) && ($.name.familyName EMPTY false) && isValidEmail($.emails[0].value)",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.corporateGroups"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >         "targetPath": "$.schemas[1]"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.emails[?(@.value)]"
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "targetPath": "$.userType",
    >         "defaultValue": "employee",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "targetPath": "$.name.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.honorificPrefix",
    >         "targetPath": "$.name.honorificPrefix",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.addresses",
    >         "targetPath": "$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "defaultValue": [],
    >         "optional": true,
    >         "functions": [
    >           {
    >             "function": "putIfAbsent",
    >             "key": "type",
    >             "defaultValue": "work"
    >           },
    >           {
    >             "condition": "(@.type NIN ['work', 'home'])",
    >             "function": "putIfPresent",
    >             "key": "type",
    >             "defaultValue": "work"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.locale",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "targetPath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional" : true,
    >         "functions": [
    >             {
    >                 "function": "resolveEntityIds"
    >             }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "defaultValue": true,
    >         "optional": true
    >       },
    >       {
    >         "constant": "false",
    >         "targetPath": "$.sendMail",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "constant": "true",
    >         "targetPath": "$.mailVerified",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "constant": "disabled",
    >         "targetPath": "$.passwordStatus",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "constant": "39",
    >         "targetPath": "$.sourceSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "targetPath": "$.timeZone",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "ignore": true,
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "scope": "createEntity",
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >           {
    >             "type": "replaceAllString",
    >             "regex": "[\\s\\p{Punct}]",
    >             "replacement": "_"
    >           }
    >         ]
    >       },
    >       {
    >         "scope": "createEntity",
    >         "optional": true,
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
    >       },
    >       {
    >         "optional": true,
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']"
    >       },
    >       {
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true,
    >         "sourcePath": "$.members[*].value",
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "type": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   }
    > }
    > ```

    **Default transformation for SCIM API version 2:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": ["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User","urn:ietf:params:scim:schemas:extension:sap:2.0:User","urn:sap:cloud:scim:schemas:extension:custom:2.0:User"],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails']",
    >         "scope": "createEntity",
    >         "functions": [
    >            {
    >                  "function": "putIfAbsent",
    >                  "key": "verified",
    >                  "defaultValue": true
    >            }
    >          ]
    >       },
    >       {
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails'][*]['type']",
    >         "type": "remove"
    >       },
    >       {
    >         "sourcePath": "$.emails[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.emails[?(@.value)]"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "targetPath": "$.name.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.honorificPrefix",
    >         "targetPath": "$.name.honorificPrefix",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.addresses",
    >         "targetPath": "$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "defaultValue": [],
    >         "optional": true,
    >         "functions": [
    >           {
    >             "function": "putIfAbsent",
    >             "key": "type",
    >             "defaultValue": "work"
    >           },
    >           {
    >             "condition": "(@.type NIN ['work', 'home'])",
    >             "function": "putIfPresent",
    >             "key": "type",
    >             "defaultValue": "work"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "targetPath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "targetPath": "$.userType",
    >         "defaultValue": "employee",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.locale",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "targetPath": "$.timezone",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "defaultValue": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "optional" : true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional" : true,
    >         "functions": [
    >             {
    >               "function": "resolveEntityIds"
    >             }
    >           ]
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "optional" : true
    >       },
    >       {
    >         "constant": false,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sendMail']",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "constant": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "constant": "disabled",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['attributes']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['attributes']"
    >       },
    >       {
    >         "constant": "<your-initial-password>",
    >         "targetPath": "$.password",
    >         "scope": "createEntity",
    >         "ignore": "true"
    >       },
    >       {
    >         "constant": "<your-source-system-type-code>",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    >         "scope": "createEntity",
    >         "ignore": true
    >       },
    >       {
    >         "constant": "<your-source-system-id>",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
    >         "scope": "createEntity",
    >         "ignore": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": ["urn:ietf:params:scim:schemas:core:2.0:Group","urn:sap:cloud:scim:schemas:extension:custom:2.0:Group"],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >             {
    >               "entityType": "user",
    >               "type": "resolveEntityIds"
    >             }
    >           ]
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >             {
    >               "entityType": "group",
    >               "type": "resolveEntityIds"
    >             }
    >           ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']"
    >       }
    >     ]
    >   }
    > }
    >  
    > ```

    > ### Remember:  
    > If you set `$.userType` to "**public**", all passwords will be written by default in the Identity Authentication. Thus, all provisioned users will successfully sign in to Identity Authentication target system.
    > 
    > When `$.userType` is set to "**employee**", the sign-in behavior of the provisioned users depends on whether users have been created with or without a password, and where these passwords are stored. Thus, you need to modify the target transformations accordingly in order for the users to successfully sign in to the Identity Authentication console.
    > 
    > To learn more, see *Guided Answers*: [Identity Authentication: Provisioned Users Can't Sign In](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:31549) 

7.  Add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)

    > ### Caution:  
    > By default, the **email** attribute is unique for *Identity Authentication* but it might not be unique for other systems, such as *SAP SuccessFactors*. That's why, when you choose a source system, make sure that there are no users with duplicate e-mails. If there are such, then after the provisioning job all users with the same e-mail address will be created as a single user in *Identity Authentication*.
    > 
    > To learn more about how to fix this issue or prevent it from happening, see *Guided Answers*: [Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)
    > 
    > To learn more about excluding users from Identity Authentication target, see: [Exclude Users from Provisioning to Target Systems](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:55088)

    If you have configured the **email** attribute to NOT be unique in *Identity Authentication*, then ignore this **Caution** note and the guided answer. For more information about configurable attributes, see: [Identity Authentication: Configure User Identifier Attributes](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/8b9fa88649ae4d86a4ab4baf8fb0e007.html)




<a name="loiof217bd39c17d47cdb4f89ed19cb2c701__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Identity Authentication: Documentation](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html)

[Identity Authentication: SCIM REST API](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/2f215687fcf34170b0bbc8b36b60f2e9.html)

[\(Guided Answers\) Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)

[\(Guided Answers\) Identity Authentication: Provisioned Users Can't Sign In](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:31549)

