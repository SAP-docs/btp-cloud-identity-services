<!-- loio7e2b54ec36344dc1983d5f8a6437b11b -->

# SAP HANA Cloud, SAP HANA Database

Follow this procedure to set up SAP HANA Cloud, SAP HANA Database as a target system.



## Prerequisites

You have created a technical user for Identity Provisioning in the SAP HANA database with the OPERATOR and ROLE ADMIN system privileges. For more information, see [SAP Identity Provisioning Service](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/sap-identity-provisioning-service) → *Prerequisites*.



<a name="loio7e2b54ec36344dc1983d5f8a6437b11b__context_y2y_nxx_rdb"/>

## Context

SAP HANA Cloud allows you to consume the SAP HANA database from cloud applications running on SAP Business Technology Platform, as well as from applications running elsewhere using the standard SAP HANA clients. Every instance of SAP HANA Cloud has its own single SAP HANA database.

You can use the Identity Provisioning user interface \(UI\) to configure SAP HANA Cloud, SAP HANA Database as a target system where you can provision users and group members.

> ### Caution:  
> You cannot create or delete groups in SAP HANA Cloud, SAP HANA Database. In this case, you can expect the following behavior:
> 
> -   If a new group is created in the source system \(for example, Identity Authentication\) and you run the provisioning job to SAP HANA Cloud, SAP HANA Database, the job will fail and no group will be created in the target system.
> 
> -   If a group exists both in the source system \(for example, Identity Authentication\) and the target system - SAP HANA Cloud, SAP HANA Database, running a provisioning job will only add new members or update existing ones. In this case, groups in the source and target systems must have the same display name \(case sensitive\). Otherwise, the job will fail, and no group members will be updated.
> 
> -   If a group exists in the target SAP HANA Cloud, SAP HANA Database system and you try to delete it, Identity Provisioning will only remove its group members. In this case, the relevant group members must exist in the target system.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP HANA Cloud, SAP HANA Database* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Choose the *Properties* tab to configure the connection settings for your system.

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

    Value
    
    </th>
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
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL.

    For example: `https://demo-hc-3-test.authentication.sap.hana.ondemand.com`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.authenticationType`
    
    </td>
    <td valign="top">
    
    Specifies the method by which users authenticate when connecting to the database.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.instance.type`
    
    </td>
    <td valign="top">
    
    Refers to the type of instance being configured or used within the SAP HANA Cloud.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.instance.id`
    
    </td>
    <td valign="top">
    
    Refers to a unique identifier associated with a specific database instance within the SAP HANA Cloud.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.providerName`
    
    </td>
    <td valign="top">
    
    Specifies the identity provider \(IdP\) that is responsible for handling authentication requests.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.group.prefix`
    
    </td>
    <td valign="top">
    
    \(Optional\) This property distinguishes SAP HANA Cloud, SAP HANA Database groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `HANA_Cloud_DB_`

    You can use the example value or provide your own.

    -   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP HANA Cloud, SAP HANA Database source system and will be provisioned to the target system with the following name pattern: <code>HANA_Cloud_DB_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP HANA Cloud, SAP HANA Database groups in the target system will be distinguished from groups provisioned from other applications.

        If the property is not set, the SAP HANA Cloud, SAP HANA Database groups will be read and provisioned to the target system with their actual display names.

    -   When **set in the target system**, only groups containing the `HANA_Cloud_DB_` prefix in their display name will be provisioned to SAP HANA Cloud, SAP HANA Database. Groups without this prefix in the display name won't be provisioned.

        If the property is not set, all groups will be be provisioned to SAP HANA Cloud, SAP HANA Database.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    This property defines by which unique attribute\(s\) an existing user in the target system will be searched and resolved in case Identity Provisioning tries to provision a conflicting user.

    Default value: *userName*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.delete.threshold.groups`
    
    </td>
    <td valign="top">
    
    \(Optional\) Use this property to control the number of group assignments to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of group assignments, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.delete.threshold.users`
    
    </td>
    <td valign="top">
    
    \(Optional\) Use this property to control the number of users to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of users, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, created for your SAP HANA Database system.
    
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
    
    Enter the SAP HANA Cloud, SAP HANA Database API URL.

    For example: `https://api.gateway.orchestration.<cluster>-<datacenter>.hanacloud.ondemand.com`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the OAuth Client Id, created for your SAP HANA Database system.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP HANA Cloud, SAP HANA Database* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP HANA Cloud, SAP HANA Database system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    > ### Note:  
    > Given that the SAP HANA Database username attribute is immutable and the email is not supported, refer to [Handling Specific Attributes](handling-specific-attributes-e957782.md) for your provisioning scenarios, particularly with Identity Authentication.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "targetPath": "$.id",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:sap:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >         "optional": true
    >       },
    >       {
    >         "condition": "'%hana.cloud.db.providerName%' !== 'null'",
    >         "constant": "%hana.cloud.db.providerName%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User']['authenticationDetails']['providerName']"
    >       },
    >       {
    >         "condition": "'%hana.cloud.db.authenticationType%' !== 'null'",
    >         "constant": "%hana.cloud.db.authenticationType%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User']['authenticationDetails']['authenticationType']"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "('%hana.cloud.db.group.prefix%' === 'null') || ($.displayName =~ /%hana.cloud.db.group.prefix%.*/)",
    >     "mappings": [
    >       {
    >         "targetPath": "$.id",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "('%hana.cloud.db.group.prefix%' !== 'null') && (@ =~ /%hana.cloud.db.group.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%hana.cloud.db.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "function": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio7e2b54ec36344dc1983d5f8a6437b11b__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[User Provisioning](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-administration-guide/user-provisioning)

