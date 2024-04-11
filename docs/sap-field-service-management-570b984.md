<!-- loio570b984678e74af1924386ba551e45c6 -->

# SAP Field Service Management

Follow this procedure to set up SAP Field Service Management as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

You have OAuth credentials for SAP Field Service Management. For more information, see: [Generating Client ID & Secret](https://help.sap.com/viewer/fsm_admin/Cloud/en-US/generating-client-id.html)



<a name="loio570b984678e74af1924386ba551e45c6__context_y2y_nxx_rdb"/>

## Context

SAP Field Service Management is a cloud-based solution that is used to resolve customers issues with end-to-end field service management. For example, it helps customers overcome resource limitations, such as having enough skilled technicians in all locations.

You can use the Identity Provisioning user interface \(UI\) to configure SAP Field Service Management as a target system where you can provision users and group members. When integrated with Identity Provisioning, the cloud solution supports the following group concept:

-   A user is created with а default group assigned. A group is mapped to a company \(one of the key organizational units in SAP Field Service Management\). When using the Identity Provisioning service API, the group is returned as follows:

    ```
    <GroupName>_<CompanyName>
    ```

-   A user can have one group assignment for each company. As in SAP Field Service Management a user can be assigned to multiple companies, this requires a group assignment for each of the companies the user can access. A user cannot be assigned to different groups mapped to one and the same company.


> ### Caution:  
> You cannot create or delete groups in SAP Field Service Management. In this case, you can expect the following behavior:
> 
> -   If a new group is created in the source system \(for example, Identity Authentication\) and you run the provisioning job to SAP Field Service Management, the job will fail and no group will be created in the target system.
> 
> -   If a group exists both in the source system \(for example, Identity Authentication\) and the target system - SAP Field Service Management, running a provisioning job will only add new members or update existing ones. In this case, groups in the source and target systems must have the same display name \(case sensitive\). Otherwise, the job will fail, and no group members will be updated.
> 
> -   If a group exists in the target SAP Field Service Management system and you try to delete it, Identity Provisioning will only remove its group members. In this case, the relevant group members must exist in the target system.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Field Service Management* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter: *HTTP* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    Specify the URL to the API of your SAP Field Service Management system. It follows the pattern:

    <code>https://<i class="varname">&lt;cluster&gt;</i>.coresystems.net</code>
    
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
    
    Enter the OAuth Client Id, created for your SAP Field Service Management system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, created for your SAP Field Service Management system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL.

    For example: `https://<cluster>.coresuite.com/api/oauth2/v1/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `fsm.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Field Service Management groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `FSM_`

    You can use the example value or provide your own.

    -   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Field Service Management source system and will be provisioned to the target system with the following name pattern: <code>FSM_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Field Service Management groups in the target system will be distinguished from groups provisioned from other applications.

        If the property is not set, the SAP Field Service Management groups will be read and provisioned to the target system with their actual display names.

    -   When **set in the target system**, only groups containing the `FSM_` prefix in their display name will be provisioned to SAP Field Service Management. Groups without this prefix in the display name won't be provisioned.

        If the property is not set, all groups will be be provisioned to SAP Field Service Management.



    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Field Service Management* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Field Service Management system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    [Field Service Management - SCIM API](https://help.sap.com/viewer/fsm_scim_api/Cloud/en-US/scim-api.html)

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Field Service Management entity.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "($.emails EMPTY false) && ($.userName EMPTY false)",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "condition": "('%fsm.group.prefix%' === 'null') || ($.displayName =~ /%fsm.group.prefix%.*/)",
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
    >                         "condition": "('%fsm.group.prefix%' !== 'null') && (@ =~ /%fsm.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%fsm.group.prefix%",
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

6.  Add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio570b984678e74af1924386ba551e45c6__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

