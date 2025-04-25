<!-- loio8c7d05e738844818b9a18661f8354482 -->

# Local Identity Directory

Follow this procedure to set up Local Identity Directory as a source system.



<a name="loio8c7d05e738844818b9a18661f8354482__prereq_w2s_11g_fzb"/>

## Prerequisites

> ### Note:  
> The *Local Identity Directory* connector is available for both bundle and standalone tenants running on SAP Cloud Identity Services infrastructure.



<a name="loio8c7d05e738844818b9a18661f8354482__context_uyq_djx_rdb"/>

## Context

Identity directory is the user store of SAP Cloud Identity Services. It provides a central place for storing and managing users, groups and custom schemas through the System for Cross-domain Identity Management 2.0 REST API, in short Identity Directory SCIM API.

You can read users and groups from the identity directory and provision them to various target systems by configuring the Local Identity Directory connector as a source system in the SAP Cloud Identity Services administration console. The entities are read from the identity directory of your current SAP Cloud Identity Services tenant. Therefore, you don't have to set up connectivity and authentication properties for the source system. In case you want to read entities from the identity directory in another tenant, add Identity Authentication \(version 2\) as a source system and configure the respective connectivity and authentication properties.

To create Local Identity Directory as a source system, proceed as follows:



## Procedure

1.  Sign in to SAP Cloud Identity Services administration console and navigate to *Identity Provisioning* \> *Source Systems*.

2.  Add *Local Identity Directory* as a source system.

    For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

3.  **Optional:** If needed, choose the *Properties* tab to configure filtering and paging.

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

4.  **Optional:** Configure transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the Local Identity Directory source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    When Local Identity Directory is configured as a source system, the default transformation logic reads the user attributes from the user store of SAP Cloud Identity Services. The logic is provided by the Identity Directory SCIM API, which then maps the attributes to the internal SCIM representation.

    **Handling Application-Specific Groups**

    In case you want to provision application-specific groups between the following pairs of provisioning systems:


    <table>
    <tr>
    <th valign="top">

    Source System
    
    </th>
    <th valign="top">

    Target System
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Identity Authentication \(SCIM API version 2\)
    
    </td>
    <td valign="top">
    
    Identity Authentication \(SCIM API version 2\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Identity Authentication \(SCIM API version 2\)
    
    </td>
    <td valign="top">
    
    Local Identity Directory
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Local Identity Directory
    
    </td>
    <td valign="top">
    
    Identity Authentication \(SCIM API version 2\)
    
    </td>
    </tr>
    </table>
    
    The Identity Provisioning will search and try to resolve the groups by the attribute values of `displayName`, `applicationId`, and `type`. To ensure successful provisioning, you must define value mappings for the attribute `applicationId` in the transformation mappings of the source or the target system. You should define to which `applicationId` in the target system will be mapped the `applicationId` read from the source system.

    For example:

    ```
    {
    "sourcePaths": [
    	"$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    ],
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']",
    "valueMappings": [
    	{
    		"key": [
    			"<your_source_system_applicationId>"
    		],
    		"mappedValue": "<your_target_system_applicationId>"
    	}
        ],
        "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
        "type": "valueMapping",
        "defaultValue": ""
    }
    ```

    For more information, see [Transformation Expressions](transformation-expressions-bb8537b.md) → section **valueMapping**.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Local Identity Directory. For more information, see:

    -   [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    -   SCIM API version 2: [Identity Directory SCIM API](https://api.sap.com/api/IdDS_SCIM/resource)


    **Default transformation for Local Identity Directory:**

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
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']",
    >                 "optional": true
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
    >             }
    >         ]
    >     }
    > }
    > ```

5.  Add a target system where to provision users and groups. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio8c7d05e738844818b9a18661f8354482__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

