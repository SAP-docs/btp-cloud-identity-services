<!-- loio59557aec028d4eae9720bf89abd110bf -->

# Local Identity Directory

Follow this procedure to set up Local Identity Directory as a target system.



<a name="loio59557aec028d4eae9720bf89abd110bf__prereq_w2s_11g_fzb"/>

## Prerequisites

> ### Note:  
> The *Local Identity Directory* connector is available for both bundle and standalone tenants running on SAP Cloud Identity Services infrastructure.



## Context

Identity directory is the user store of SAP Cloud Identity Services. It provides a central place for storing and managing users, groups and custom schemas through the System for Cross-domain Identity Management 2.0 REST API, in short Identity Directory SCIM API.

You can provision users and groups to the identity directory from various source systems by configuring the Local Identity Directory connector as a target system in the SAP Cloud Identity Services administration console. The entities are written to the identity directory of your current SAP Cloud Identity Services tenant. Therefore, you don't have to set up connectivity and authentication properties for the target system. In case you want to write entities to the identity directory in another tenant, add Identity Authentication \(version 2\) as a target system and configure the respective connectivity and authentication properties.

To create Local Identity Directory as a target system, proceed as follows:



## Procedure

1.  Sign in to SAP Cloud Identity Services administration console and navigate to *Identity Provisioning* \> *Target Systems*.

2.  Add *Local Identity Directory* as a target system.

    For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

3.  **Optional:** If needed, choose the *Properties* tab to configure patch and bulk operations.

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
    
    `idds.bulk.operations.max.count`
    
    </td>
    <td valign="top">
    
    This property sets the number of operations to be performed in one bulk request.

    -   Default value: *20*

    -   Maximum value: *100* 



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `idds.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    This property enables bulk operations for users and groups.

    -   When bulk operations are enabled, Identity Provisioning creates, updates, and deletes multiple users and groups in one request.

    -   When bulk operations are not enabled, Identity Provisioning creates, updates, and deletes one user at a time.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `idds.patch.group.members.above.threshold`
    
    </td>
    <td valign="top">
    
    Defines the threshold number of group members above which they are provisioned on batches with `PATCH` requests, and below which they are provisioned with `PUT` request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

    -   Default value: *20 000*

    -   Minimum value: *1*

    -   Maximum value: *200 000*



    
    </td>
    </tr>
    </table>
    
    Local Identity Directory properties are prefixed with `idds`.*<property\_name\>*. For more information, see [List of Properties](list-of-properties-d6f3577.md).

4.  **Optional:** Configure transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the Local Identity Directory target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    When Local Identity Directory is configured as a target system, the default transformation logic writes the user attributes in the user store of SAP Cloud Identity Services. The logic is provided by the Identity Directory SCIM API, which then maps the attributes to the internal SCIM representation.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Local Identity Directory. For more information, see:

    -   [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    -   SCIM API version 2: [Identity Directory SCIM API](https://api.sap.com/api/IdDS_SCIM/resource)


    **Default transformation for Local Identity Directory:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)",
    >         "mappings": [
    >             {
    >                 "targetPath": "$.id",
    >                 "sourceVariable": "entityIdTargetSystem"
    >             },
    >             {
    >                 "targetPath": "$.schemas",
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:User",
    >                     "urn:sap:cloud:scim:schemas:extension:custom:2.0:User"
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails']",
    >                 "preserveArrayWithSingleElement": true,
    >                 "scope": "createEntity",
    >                 "functions": [
    >                     {
    >                         "function": "putIfAbsent",
    >                         "key": "verified",
    >                         "defaultValue": true
    >                     }
    >                 ]
    >             },
    >             {
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['emails'][*]['type']",
    >                 "type": "remove"
    >             },
    >             {
    >                 "sourcePath": "$.emails[*].value",
    >                 "targetPath": "$.emails[?(@.value)]",
    >                 "preserveArrayWithSingleElement": true
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
    >                 "sourcePath": "$.addresses",
    >                 "targetPath": "$.addresses",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true,
    >                 "functions": [
    >                     {
    >                         "function": "putIfAbsent",
    >                         "key": "type",
    >                         "defaultValue": "work"
    >                     },
    >                     {
    >                         "function": "putIfPresent",
    >                         "condition": "(@.type NIN ['work', 'home'])",
    >                         "key": "type",
    >                         "defaultValue": "work"
    >                     }
    >                 ],
    >                 "defaultValue": []
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "targetPath": "$.phoneNumbers",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.userType",
    >                 "targetPath": "$.userType",
    >                 "optional": true,
    >                 "defaultValue": "employee"
    >             },
    >             {
    >                 "sourcePath": "$.locale",
    >                 "targetPath": "$.locale",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "targetPath": "$.timezone",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true,
    >                 "defaultValue": true
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
    >                 "optional": true,
    >                 "functions": [
    >                     {
    >                         "function": "resolveEntityIds"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "optional": true
    >             },
    >             {
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sendMail']",
    >                 "constant": false,
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
    >                 "constant": true,
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']",
    >                 "constant": "disabled",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['attributes']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['attributes']",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "targetPath": "$.password",
    >                 "ignore": true,
    >                 "constant": "<your-initial-password>",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    >                 "ignore": true,
    >                 "constant": "<your-source-system-type-code>",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
    >                 "ignore": true,
    >                 "constant": "<your-source-system-id>",
    >                 "scope": "createEntity"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "targetPath": "$.id",
    >                 "sourceVariable": "entityIdTargetSystem"
    >             },
    >             {
    >                 "targetPath": "$.schemas",
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                     "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:Group"
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "targetPath": "$.members[?(@.value)]",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true,
    >                 "functions": [
    >                     {
    >                         "function": "resolveEntityIds",
    >                         "entityType": "user"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "targetPath": "$.members[?(@.value)]",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true,
    >                 "functions": [
    >                     {
    >                         "function": "resolveEntityIds",
    >                         "entityType": "group"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >                 "optional": true,
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']",
    >                 "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
    >                 "optional": true
    >             }
    >         ]
    >     }
    > }
    > ```

5.  Add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)

    > ### Caution:  
    > By default, the **email** attribute is unique for Local Identity Directory but it might not be unique for other systems, such as *SAP SuccessFactors*. That's why, when you choose a source system, make sure that there are no users with duplicate e-mails. If there are such, then after the provisioning job all users with the same e-mail address will be created as a single user in Local Identity Directory.
    > 
    > To learn more about how to fix this issue or prevent it from happening, see *Guided Answers*: [Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)
    > 
    > To learn more about excluding users from Local Identity Directory target, see: [Exclude Users from Provisioning to Target Systems](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:55088)

    If you have configured the **email** attribute to NOT be unique in Local Identity Directory, then ignore this **Caution** note and the guided answer. For more information about configurable attributes, see: [Configure User Identifier Attributes](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/8b9fa88649ae4d86a4ab4baf8fb0e007.html)




<a name="loio59557aec028d4eae9720bf89abd110bf__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[\(Guided Answers\) Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)

[\(Guided Answers\) Identity Authentication: Provisioned Users Can't Sign In](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:31549)

