<!-- loio0624f7d86913402dabc15249e9910fe4 -->

# Local Identity Directory

Follow this procedure to set up Local Identity Directory as a proxy system.



<a name="loio0624f7d86913402dabc15249e9910fe4__prereq_w2s_11g_fzb"/>

## Prerequisites

> ### Note:  
> The *Local Identity Directory* connector is available for both bundle and standalone tenants running on SAP Cloud Identity Services infrastructure.



<a name="loio0624f7d86913402dabc15249e9910fe4__context_pqw_bth_vdb"/>

## Context

Identity directory is the user store of SAP Cloud Identity Services. It provides a central place for storing and managing users, groups and custom schemas through the System for Cross-domain Identity Management 2.0 REST API, in short Identity Directory SCIM API.

You can use the identity directory for user and group provisioning with an external identity management system without making a direct connection between them. For this, you configure the Local Identity Directory connector as a proxy system in the SAP Cloud Identity Services administration console.

The entities are read and written to and from the identity directory of your current SAP Cloud Identity Services tenant. Therefore, you don't have to set up connectivity and authentication properties for the proxy system. In case you want to use the identity directory in another tenant, add Identity Authentication \(version 2\) as a proxy system with the respective connectivity set up.

The proxy systems consume [Identity Directory SCIM API](https://api.sap.com/api/IdDS_SCIM/resource). It supports patch operations for proxy systems only, paging for group members and user’s groups, custom attributes, delta read mode for users. Also, the group resource mapping in the transformation is not ignored by default.

By configuring the directory as a proxy system, you implement secure authentication, single sign-on \(SSO\), strong authentication, and mobile SSO so that the provisioned users to the directory have access to the business applications of your company.

To create Local Identity Directory as a proxy system, proceed as follows:



## Procedure

1.  Sign in to SAP Cloud Identity Services administration console and create a technical user with the necessary authorizations. It will later be used by the external consumer to connect to SAP Cloud Identity Services.

    If you already have a technical user, skip this step.

    -   For **Certificate-based authentication**, follow the procedure in [Manage Certificates for Inbound Connection](Operation-Guide/manage-certificates-for-inbound-connection-952e7c7.md) → *SAP Cloud Identity Infrastructure*

    -   For **Basic authentication**, navigate to *Users & Authorizations* \> *Administrators* and add an admin user of type **System**. Configure a client ID and secret for this user and enable the *Access Proxy System API* permission.


2.  Navigate to *Identity Provisioning* \> *Proxy Systems*.

3.  Add *Local Identity Directory* as a proxy system.

    For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  **Optional:** If needed, choose the *Properties* tab to configure filtering and paging.

    **Optional Properties**


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
    
    `idds.user.filter`
    
    </td>
    <td valign="top">
    
    This property filters users by particular attributes. You can set a single attribute or multiple ones as search criteria.

    -   Value pattern for single attribute: *<user\_attribute\> eq "<value\>"*

    -   Value pattern for multiple attributes: *<user\_attribute1\> eq "<value1\>" and/or <user\_attribute2\> eq "<value2\>"*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `idds.group.filter`
    
    </td>
    <td valign="top">
    
    This property filters groups by display name. You can set a single display name or multiple ones as filter criteria. If you enter multiple display names \(using `OR` operator\), the filter will search for any of them.

    -   Value pattern for single attribute: *displayName eq "<group\_name\>"*

    -   Value pattern for multiple attributes: *displayName eq "<group\_name1\>" or displayName eq "<group\_name2\>"*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `idds.user.groups.paging.enabled`
    
    </td>
    <td valign="top">
    
    This property enables paging of user’s groups.

    The maximum number of user’s groups returned per request is 1000. To read more than 1000 user’s groups, paging must be enabled.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `idds.group.members.paging.enabled`
    
    </td>
    <td valign="top">
    
    This property enables paging of group members.

    The maximum number of group members returned per request is 20 000. To read more than 20 000 group members, paging must be enabled.
    
    </td>
    </tr>
    </table>
    
    Local Identity Directory properties are prefixed with `idds`.*<property\_name\>*. For more information, see [List of Properties](list-of-properties-d6f3577.md).

    > ### Note:  
    > The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).

5.  **Optional:** Configure transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the Local Identity Directory proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Local Identity Directory. For more information, see:

    -   [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    -   SCIM API version 2: [Identity Directory SCIM API](https://api.sap.com/api/IdDS_SCIM/resource)


    Default read and write transformations:

    > ### Tip:  
    > The proxy *Read Transformation* is used when the external client application \(for example, SAP Identity Management\) makes initial load. That is, executing GET requests to the resource endpoints \(**/Users** or **/Groups**\) to retrieve the corresponding entities of the particular type. The external client application can also execute GET requests to a single resource endpoint \(querying a single resource is supported\). In this case, the proxy system acts as a *source* one.
    > 
    > The proxy *Write Transformation* is used when the external application manages the entities in the proxy system – creates new entities, updates existing ones, or deletes existing ones. In this case, the proxy system acts as a *target* one.
    > 
    > However, after a *Create* or *Update* operation is performed on the proxy system, the *Read Transformation* is applied to the result, so that the created or updated entity is sent back to the external application. This behavior demonstrates that the proxy *Read Transformation* is used for *write* cases, as well.

    **Default transformations for Local Identity Directory:**


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
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.emails[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.emails[?(@.value)]"
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.emails[0].value"
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "targetPath": "$.userType",
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
    >         "optional": true
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
    >         "sourcePath": "$.timezone",
    >         "targetPath": "$.timezone",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.sourceSystem",
    >         "targetPath": "$.sourceSystem",
    >         "ignore": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "condition": "$.displayName EMPTY true",
    >         "type": "remove",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.company",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
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
    >          "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >          "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
    >       },
    >       {
    >          "sourcePath": "$.displayName",
    >          "targetPath": "$.displayName"
    >       },
    >       {
    >          "sourcePath": "$.members",
    >          "targetPath": "$.members",
    >          "preserveArrayWithSingleElement": true,
    >          "optional": true
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
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
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": ["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User","urn:ietf:params:scim:schemas:extension:sap:2.0:User"],
    >         "targetPath": "$.schemas"
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
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "defaultValue": true,
    >         "optional": true
    >       },
    >       {
    >         "constant": false,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sendMail']",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails']",
    >         "scope": "createEntity",
    >         "functions": [
    >           {
    >             "function": "putIfAbsent",
    >             "key": "verified",
    >             "defaultValue": true
    >           }
    >         ]
    >       },
    >       {
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails'][*]['type']",
    >         "type": "remove"
    >       },
    >       {
    >         "constant": "disabled",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "constant": 39,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "constant": "employee",
    >         "targetPath": "$.userType"
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "targetPath": "$.timezone",
    >         "optional": true
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
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
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
    >       },
    >       {
    >         "constant": ["urn:ietf:params:scim:schemas:core:2.0:Group","urn:sap:cloud:scim:schemas:extension:custom:2.0:Group","urn:ietf:params:scim:schemas:extension:sap:2.0:Group"],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "scope": "createEntity",
    >         "functions": [
    >           {
    >             "type": "replaceAllString",
    >             "regex": "[\\s\\p{Punct}]",
    >             "replacement": "_"
    >           }
    >         ]
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
    >       },
    >       {
    >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       },
    >       {
    >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >       },
    >       {
    >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
    > ### Remember:  
    > If you set `$.userType` to "**public**", all passwords will be written by default in the Local Identity Directory. Thus, all provisioned users will successfully sign in to Local Identity Directory target system.
    > 
    > When `$.userType` is set to "**employee**", the sign-in behavior of the provisioned users depends on whether users have been created with or without a password, and where these passwords are stored. Thus, you need to modify the target transformations accordingly in order for the users to successfully sign in to the SAP Cloud Identity Services administration console.
    > 
    > To learn more, see *Guided Answers*: [Identity Authentication: Provisioned Users Can't Sign In](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:31549) 

6.  Connect the external consumer to SAP Cloud Identity Services with the technical user you have created in step 1.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.




<a name="loio0624f7d86913402dabc15249e9910fe4__postreq_dvl_h41_rxb"/>

## Next Steps

When a proxy system is connected to an external backend system \(in the case of SAP Identity Management this means the exported CSV file is imported into the Identity Management Admin UI and a repository is configured\), you can start managing the users and groups into this external system. Usually, the first operation is the initial load of the existing entities into your external system. When this load has finished, changes in the external system, such as creating new users or updating existing ones, can trigger CRUD requests back to the proxy system.

To see an example with SAP Identity Management, see [Hybrid Scenario: SAP Identity Management](https://help.sap.com/docs/identity-provisioning/identity-provisioning/hybrid-scenario-sap-identity-management?version=Cloud) → sections **Next Steps** and **Future Identity Lifecycle**.

