<!-- loiof29ee52ea67647e4bef362d42631cbc3 -->

# SAP Intelligent Agriculture

Follow this procedure to set up SAP Intelligent Agriculture as a target system.



<a name="loiof29ee52ea67647e4bef362d42631cbc3__prereq_zxm_qw3_pzb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   You have onboarded your SAP Intelligent Agriculture tenant as described in the [Onboarding with the SAP BTP Cockpit](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/ba2d9265332a4682b019b92689500fa3/0ad81c4430c54cac8746ebe44ec5b850.html) section of the *Administration Guide for SAP Intelligent Agriculture*.

-   You have OAuth credentials for SAP Intelligent Agriculture. For more information, see: [Getting the Credentials from the SAP Intelligent Agriculture Instance](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/724d45c4d2934012a35cc9982b81d9a8/9cbec11fa6434df396cfc918aed7ecde.html#getting-the-credentials-from-the-sap-intelligent-agriculture-instance).




## Context

SAP Intelligent Agriculture enables agribusinesses to sustainably increase farming efficiency by digitizing their farming processes and services from plan-to-harvest, taking advantage of data science and machine learning capabilities.

You can use Identity Provisioning to configure SAP Intelligent Agriculture as a target system where you can provision users and update group members.

> ### Caution:  
> You can't create or delete groups on SAP Intelligent Agriculture. That means:
> 
> -   On the attempt to create a group on SAP Intelligent Agriculture, Identity Provisioning will only add new members or update existing ones. Also, if you read a group from the external back-end system, there must be a group with the exact same display name \(case sensitive\) in the SAP Intelligent Agriculture system. Otherwise, an error will be thrown and the group members will not be updated.
> -   On the attempt to delete a group on SAP Intelligent Agriculture, Identity Provisioning will only remove its members \(group assignments\). And this can happen only if the relevant group assignments have been provisioned/are present in the target system.



<a name="loiof29ee52ea67647e4bef362d42631cbc3__steps_y2v_1m3_rzb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Intelligent Agriculture* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    `Type`
    
    </td>
    <td valign="top">
    
    Enter: **
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    Enter the URL related to your SAP Intelligent Agriculture system, in format: `https://*.prod-<region>.ia.agribusiness.cloud.sap`

    , where *\*.* is the name of your subaccount.

    For example: `https://custom-domain.prod-eu10.ia.agribusiness.cloud.sap`
    
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
    
    Enter: *BasicAuthentication* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the OAuth Client Id, created for your SAP Intelligent Agriculture instance \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, created for your SAP Intelligent Agriculture instance \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Intelligent Agriculture instance, in format: `https://<TENANT>.authentication.<REGION>.hana.ondemand.com/oauth/token` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ia.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    When Identity Provisioning attempts to provision a user for the first time, it may detect that this user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

    This property defines by which unique attribute\(s\) the existing user will be searched and resolved. If the service finds a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find a user on the target system via this filter, the creation will fail.

    **Default behavior**: The property is automatically added during system creation. Its default value is *userName*. This means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such *userName* is not found, the creation of the conflicting user fails.

    **Possible values:**

    -   *userUuid*
    -   *emails*
    -   *userName*
    -   *externalId*

    Default value: *userName*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ia.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If the service tries to create a group that already exists in the target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\).

    *displayName*. Currently, it is the only unique attribute that is supported. When set, you can expect the following behavior:

    -   If a group with the given This property defines by which unique attribute\(s\) the existing group will be searched and resolved. The default value is *displayName* is found in the target system, the group that you try to provision will overwrite the existing one.

    -   This property defines by which unique attribute\(s\) theIf a group with the given *displayName* is not found in the target system, the group that you try to provision will not be created in the target system.


    **Possible values:**

    If the property is not specified, the search is done by the default attribute: `displayName`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ia.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

    -   If set to *true*, `PATCH` operations are used to update users and groups in the target system. This means, for example, that if a group member is removed from a group, only these changes will be provisioned and applied in the target system.

    -   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ia.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Intelligent Agriculture groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `IA_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `IA_` prefix in their display name will be provisioned to SAP Intelligent Agriculture. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Intelligent Agriculture.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ia.include.if.match.wildcard.header` 
    
    </td>
    <td valign="top">
    
    Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Intelligent Agriculture system for entity versioning.

    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false*
    
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
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Intelligent Agriculture* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Intelligent Agriculture system. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Intelligent Agriculture entity.

    > ### Note:  
    > When а user is deleted from the SAP Intelligent Agriculture target system, depending on the off-boarding user handling it can be deleted or set to anonymized.
    > 
    > If you try to read such user, you get only its *id* and the other attributes have value `ANONYMOUS`.
    > 
    > If you try to create again a user with the same unique attributes \(`userUuid`, `externalId`, `userName`, and `email`l\) during the configured retention period, the existed entity is restored to its active state. If the create operation requests changes in the values of the attributes, they will be executed after triggering a resync job.
    > 
    > For more information, see [Data Retention Manager](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/ba2d9265332a4682b019b92689500fa3/e55cbc4d42aa4059a835711c5fba1c44.html?locale=en-US).

    [SAP Intelligent Agriculture SCIM API](https://help.sap.com/docs/SAP_INTELLIGENT_AGRICULTURE/724d45c4d2934012a35cc9982b81d9a8/1919b94dc2c84711ab65fd63002b9bce.html)

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "($.emails EMPTY false) && ($.userName EMPTY false) && ($['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid'] EMPTY false)",
    >     "mappings": [
    >       {
    >         "targetPath": "$.id",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$.userUuid"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.emails[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.emails[?(@.value)]"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "('%ia.group.prefix%' === 'null') || ($.displayName =~ /%ia.group.prefix%.*/)",
    >     "mappings": [
    >       {
    >         "targetPath": "$.id",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schema[0]"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "('%ia.group.prefix%' !== 'null') && (@ =~ /%ia.group.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%ia.group.prefix%",
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

    > ### Note:  
    > When Identity Authentication is configured as a source system, the default transformation logic:
    > 
    > -   Provisions only groups and user group assignments if they are part of the following predefined group list:
    >     -   *intagri\_Data\_Scientist*
    > 
    >     -   *intagri\_Farm\_Manager*
    > 
    >     -   *intagri\_Operator*
    > 
    >     -   *intagri\_Operations\_Planner*
    > 
    >     -   *intagri\_Master\_Data\_Manager*
    > 
    >     -   *intagri\_Administrator*
    > 
    > 
    > -   Skips some of the attributes from the identity records.
    > 
    > This way, the transformation logic ensures that the identity data, sent to the Identity Provisioning SCIM REST API, is consistent.




<a name="loiof29ee52ea67647e4bef362d42631cbc3__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

