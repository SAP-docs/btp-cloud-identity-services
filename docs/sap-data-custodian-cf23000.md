<!-- loiocf23000cff3643f793de18c43ddbdd84 -->

# SAP Data Custodian

Follow this procedure to set up SAP Data Custodian as a target system.



<a name="loiocf23000cff3643f793de18c43ddbdd84__prereq_c5f_nrh_dwb"/>

## Prerequisites

> ### Restriction:  
> This system is available for all standalone tenants and bundle tenants running on SAP Cloud Identity Services infrastructure. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   You have created an SAP Data Custodian tenant.

-   You have created a user within your tenant with the required roles for your scenario.

-   You have added your user to SAP Identity Service Management \(SAP ISM\).

-   You have completed the Transparency and Control Service Onboarding Process or the Key Management Service Onboarding Process, depending on the scenario you want to implement. For more information, see [Transparency and Control Service Onboarding Process](https://help.sap.com/docs/SAP_DATA_CUSTODIAN/538dde61cf134c89bda1c31100a6c0e1/22a3ec71c2314004b87d8a4d1df01492.html?locale=en-US&version=2210) and [Key Management Service Onboarding Process](https://help.sap.com/docs/SAP_DATA_CUSTODIAN/538dde61cf134c89bda1c31100a6c0e1/21ec63132e22411c9308894d397e3901.html?locale=en-US&version=2210).




<a name="loiocf23000cff3643f793de18c43ddbdd84__context_zhf_2vx_ybb"/>

## Context

> ### Note:  
> Currently, SAP Data Custodian connector is only available for selected customers who are approached by SAP. For more information, see [3319946](https://me.sap.com/notes/3319946).

SAP Data Custodian is a robust Software as a Service \(SaaS\) solution that protects sensitive data stored in public, private, hybrid, and multicloud environments. This solution integrates with partnered public hyperscalers, SAP applications, and SAP managed clouds.

After fulfilling the prerequisites, follow the procedure below to create a target SAP Data Custodian system to provision users and groups.

These target systems consume SCIM 2.0 API provided by SAP Data Custodian.

SCIM API 2.0 does not support managing of group assignments via the SCIM user resource. The "groups" attribute of the user is read-only. This means that the user group assignments should be managed via the SCIM group resources using the "members" attribute \(as it is defined by the SCIM standard\).



<a name="loiocf23000cff3643f793de18c43ddbdd84__steps_mwn_wrh_dwb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Data Custodian* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify the URL to the SAP Data Custodian SCIM API portal.
    
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
    
    Enter the OAuth client key, created for your SAP Data Custodian tenant.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth client secret, created for your SAP Data Custodian tenant.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Data Custodian instance, in format: `https://<SAP_Data_Custodian_datacenter>/api/v1/auth/token` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dc.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Data Custodian groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `DC_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `DC_` prefix in their display name will be provisioned to SAP Data Custodian. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Data Custodian.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dc.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If the service tries to create a group that already exists in the target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\).

    To make the search filter by a specific attribute, specify this attribute as a value for the `dc.group.unique.attribute` property.

    If the property is not specified, the search is done by the default attribute: *displayName*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dc.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    When Identity Provisioning attempts to provision a user for the first time, it may detect that this user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

    This property defines by which unique attribute\(s\) the existing user will be searched and resolved. If the service finds a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find a user on the target system via this filter, the creation will fail.

    **Default behavior**: The property is automatically added during system creation. Its default value is *userName*. This means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such *userName* is not found, the creation of the conflicting user fails.

    **Possible values:**

    Default value: *userName*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dc.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified users in the source system are updated in the target system.

    -   If set to *true*, `PATCH` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, only this change will be provisioned and applied in the target system.

    -   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


    Users can be updated in the target system in various cases, such as:

    -   In the source system, some user attributes are modified, or new attributes are added.

    -   In the source system, a condition or a filter is set for users not to be read anymore.

    -   A user is deleted from the source system.


    In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Data Custodian* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Jam Collaboration. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Data Custodian SCIM 2.0 API](https://api-kms-devel.datacustodian.cloud.sap/kms/scim/v1/ui/)

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "($.emails EMPTY false) && (('%dc.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%dc.group.prefix%.+/)] empty false))",
    >         // This condition filters the users by the group display name of their assigned groups. 
    >         // If the dc.group.prefix is set, only users assigned to groups that contain in their display name the set specific prefix will be provisioned.
    >         //In case the property is not set, all users are provisioned to SAP Data Custodian, regardless of the group display name of their assigned groups.
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": ["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User","urn:ietf:params:scim:schemas:extension:sap:2.0:User","urn:sap:cloud:scim:schemas:extension:custom:2.0:User"],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "condition": "$.externalId EMPTY false",
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "condition": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['userId'] EMPTY false",
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['userId']",
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "condition": "$.emails[?(@.primary == true)].value == []",
    >                 "sourcePath": "$.emails[0].value",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "condition": "$.emails[?(@.primary == true)].value != []",
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.userName",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional":true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "optional":true,
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional":true,
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.name.formatted",
    >                 "optional":true,
    >                 "targetPath": "$.name.formatted"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificPrefix",
    >                 "optional":true,
    >                 "targetPath": "$.name.honorificPrefix"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificSuffix",
    >                 "optional":true,
    >                 "targetPath": "$.name.honorificSuffix"
    >             },
    >             {
    >                 "sourcePath": "$.name.middleName",
    >                 "optional":true,
    >                 "targetPath": "$.name.middleName"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "optional":true,
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "condition": "('%dc.group.prefix%' === 'null') || ($.displayName =~ /%dc.group.prefix%.*/)",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "('%dc.group.prefix%' !== 'null') && (@ =~ /%dc.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%dc.group.prefix%",
    >                         "replacement": ""
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]",
    >                 "functions": [
    >                     {
    >                         "function": "resolveEntityIds"
    >                     }
    >                 ]
    >             }
    >         ]
    >     }
    > } 
    > ```

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)

    > ### Note:  
    > When Identity Authentication is configured as a source system, the default transformation logic:
    > 
    > -   Provisions only groups and user group assignments if they are part of the following predefined group list:
    >     -   *SAP\_Data\_Custodian\_Auditor*
    > 
    >     -   *SAP\_Data\_Custodian\_Service\_Admin*
    > 
    >     -   *SAP\_Data\_Custodian\_Key\_Admin*
    > 
    >     -   *SAP\_Data\_Custodian\_Key\_User*
    > 
    > 
    > -   Skips some of the attributes from the identity records.
    > -   Sets primary email for `userName` of the user.
    > 
    > This way, the transformation logic ensures that the identity data, sent to the Identity Provisioning SCIM REST API, is consistent.




<a name="loiocf23000cff3643f793de18c43ddbdd84__postreq_emv_vdb_kdb"/>

## Next Steps

1.  Before starting a provisioning job, you can first subscribe to the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during your jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
2.  Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Data Custodian](https://help.sap.com/docs/SAP_DATA_CUSTODIAN?version=2210&locale=en-US)

