<!-- loioe4e25f1fae094c2a89ad62159e1cd230 -->

# Identity Authentication

Follow this procedure to set up SAP Cloud Identity Service – Identity Authentication as a source system.



<a name="loioe4e25f1fae094c2a89ad62159e1cd230__prereq_ezp_nrh_vdb"/>

## Prerequisites

To establish the connection between Identity Provisioning and Identity Authentication, you need to set up the technical user \(of type *System*\) in Identity Authentication and assign this user the necessary authorizations. You have the option to do it either now, as a prerequisite, or while configuring Identity Authentication as a source system, as described in step 3.



<a name="loioe4e25f1fae094c2a89ad62159e1cd230__context_uyq_djx_rdb"/>

## Context

Identity Authentication provides authentication and single sign-on for users in the cloud. The user store of Identity Authentication can manage different type of users \(employees, partners, customers and public\) as well as groups. Using Identity Provisioning, you can read those users \(self-registered, imported, or manually created\) and groups and provision them to various target systems.

For this, you need to configure the Identity Authentication as a source system in the Identity Provisioning UI. This source system consumes SCIM 2.0 API provided by Identity Authentication.

There are two versions of the Identity Authentication SCIM API. They are handled by the `ias.api.version` property as follows:

-   When the value is set to `1` or the property is not defined \(typical for systems created before versioning was introduced on July 9, 2021\) - Identity Authentication SCIM API \(in short, SCIM API version 1\) is used.

    For more information on how to update to version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md)

-   When the value is set to `2` - Identity Directory SCIM API \(in short, SCIM API version 2\) is used. This value is set automatically for all manually created systems in the as a source system. For more information, see Identity Provisioning UI after versioning was introduced on July 9, 2021.

    SCIM API version 2 is enhanced to support paging for group members and user’s groups, custom attributes, delta read mode for users. Also, the group resource mapping in the transformation is not ignored by default, as it is in SCIM API version 1.

    > ### Note:  
    > Identity Authentication \(using SCIM API version 2\) and Identity Directory are sometimes used interchangeably. Identity Directory is the persistency layer of SAP Cloud Identity Services – Identity Authentication.


To create Identity Authentication as a source system, proceed as follows:



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *Identity Authentication* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning as a source system and Identity Authentication and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added Identity Authentication source system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Manage Certificates](Operation-Guide/manage-certificates-86d06a0.md).

        Skip step **a.** if you want to use basic authentication.

        In SAP Cloud Identity Services administration console, perform the next steps. They are relevant for both basic and certificate-based authentication.

    2.  [Add System as administrator](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/bbbdbdd3899942ce874f3aae9ba9e21d.html#loiocefb742a36754b18bbe5c3503ac6d87c) and provide the respective credentials.

        For basic authentication, provide a password. The user ID will be generated automatically when you set the password for the first time.

        For certificate-based authentication, upload the certificate you have generated in SAP Cloud Identity Services administration console on the previous step.

    3.  Save your changes.

    4.  Make sure *Manage Users* \(or at least *Read Users*\) and *Manage Groups* authorization roles are enabled for the technical user. This way, you can read users and groups from the Identity Authentication user store.


5.  Choose the *Properties* tab to configure the connection settings for your system.

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

    The Identity Authentication service is a cloud solution and is outside of your company on-premise infrastructure.
    
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
    
    `ias.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those users matching the filter expression will be read.

    For example: **name.familyName eq "Smith" and addresses.country eq "US"**

    This filter will read only users whose name is "*Smith*" and are living in the *United States*.

    For more information, see [Identity Directory SCIM API: User Search](https://api.sap.com/api/IdDS_SCIM/resource/Users).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ias.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those groups matching the filter expression will be read.

    For example: **displayName eq "ProjectTeam1"**

    This filter will read only groups, whose display name is "*ProjectTeam1*".

    For more information, see [Identity Directory SCIM API: Group Search](https://api.sap.com/api/IdDS_SCIM/resource/Groups).
    
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
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Identity Authentication* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    When Identity Authentication is configured as a source system, the default transformation logic reads all the user attributes from the Identity Authentication user store. The logic is provided by the Identity Authentication SCIM REST API, which then maps the attributes to the internal SCIM representation.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Identity Authentication system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    SCIM API version 1: [Identity Authentication: SCIM REST API](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/2f215687fcf34170b0bbc8b36b60f2e9.html)

    SCIM API version 2: [Identity Directory SCIM API](https://api.sap.com/api/IdDS_SCIM/resource)

    > ### Note:  
    > When a user is deleted from the Identity Authentication, the deletion status is considered by it during the read processes. Depending on the off-boarding user handling in the target system, a user can be deleted, or can be set to *inactive*.

    **Default transformation for SCIM API version 1:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['userId']"
    >             },
    >             {
    >                 "sourcePath": "$.userUuid",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.name.givenName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.middleName",
    >                 "targetPath": "$.name.middleName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "targetPath": "$.name.familyName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificPrefix",
    >                 "targetPath": "$.name.honorificPrefix",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary== true)].value",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true,
    >                 "defaultValue": true
    >             },
    >             {
    >                 "sourcePath": "$.userType",
    >                 "targetPath": "$.userType",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.addresses",
    >                 "targetPath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.locale",
    >                 "targetPath": "$.locale",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "targetPath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.timeZone",
    >                 "targetPath": "$.timezone",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.sourceSystemId",
    >                 "targetPath": "$.sourceSystemId",
    >                 "ignore": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "condition": "$.displayName EMPTY true",
    >                 "type": "remove",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.company",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "optional": true
    >             }
    >         ]
    >     },
    > 	
    > 	// By default, the group mapping is inactive (ignored) but groups are supported. 
    > 	// To start reading groups, either delete the statement "ignore": true, or set its value to false.
    >     "group": {
    >         "ignore": true,
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true,
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members"
    >             },
    >             {
    >                 "ignore": true,
    >                 "constant": "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group",
    >                 "targetPath": "$.schemas[1]"
    >             },
    >             {
    >                 "ignore": true,
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
    >             },
    >             {
    >                 "ignore": true,
    >                 "optional": true,
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']"
    >             }
    >         ]
    >     }
    > }
    > ```

    **Default transformation for SCIM API version 2:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['userId']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.name.givenName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.middleName",
    >                 "targetPath": "$.name.middleName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "targetPath": "$.name.familyName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificPrefix",
    >                 "targetPath": "$.name.honorificPrefix",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary== true)].value",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.userType",
    >                 "targetPath": "$.userType",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.addresses",
    >                 "targetPath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.locale",
    >                 "targetPath": "$.locale",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "targetPath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "targetPath": "$.timezone",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "condition": "$.displayName EMPTY true",
    >                 "type": "remove",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.company",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "optional": true
    >             }
    >         ]
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             }
    >         ]
    >     }
    > }
    > ```

7.  Add a target system where to provision users and groups. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loioe4e25f1fae094c2a89ad62159e1cd230__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Identity Authentication: Documentation](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html)

[Identity Authentication: SCIM REST API](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/2f215687fcf34170b0bbc8b36b60f2e9.html)

