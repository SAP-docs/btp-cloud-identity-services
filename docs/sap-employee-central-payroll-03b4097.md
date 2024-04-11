<!-- loio03b4097a408f4010b0396c56c2660bb1 -->

# SAP Employee Central Payroll

Follow this procedure to set up SAP Employee Central Payroll as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.



<a name="loio03b4097a408f4010b0396c56c2660bb1__context_y2y_nxx_rdb"/>

## Context

SAP Employee Central Payroll is a cloud product for payroll processing. It's a service offering where SAP SuccessFactors Employee Central is used for maintenance of core HR master data and an SAP HCM Payroll system hosted in an SAP or Hyperscaler data center is used for payroll.

You can use Identity Provisioning to configure SAP Employee Central Payroll as a target system where you provision users and groups from source systems.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Employee Central Payroll* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL to your SAP Employee Central Payroll system.

    For more information, see [Prerequisite: Finding the Access URL](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL_PAYROLL/185f14fbe60d4bbb8d7d5e4f8d89b24b/354c96a533104bb283f13133fae39c5d.html?q=url&version=latest) → step 8.
    
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
    
    Enter your authentication method:

    -   *BasicAuthentication*

    -   *ClientCertificateAuthentication*

        For more information, see [Prerequisite: Finding the Access URL](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL_PAYROLL/185f14fbe60d4bbb8d7d5e4f8d89b24b/354c96a533104bb283f13133fae39c5d.html?q=url&version=latest) → step 5 → **X.509 Client Certificate**.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    For more information, see [Prerequisite: Finding the Access URL](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL_PAYROLL/185f14fbe60d4bbb8d7d5e4f8d89b24b/354c96a533104bb283f13133fae39c5d.html?q=url&version=latest) → step 5.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Valid if *BasicAuthentication* is configured as authentication method.

    For more information, see [Prerequisite: Finding the Access URL](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL_PAYROLL/185f14fbe60d4bbb8d7d5e4f8d89b24b/354c96a533104bb283f13133fae39c5d.html?q=url&version=latest) → step 5.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ecp.sap-client`
    
    </td>
    <td valign="top">
    
    URL parameter

    Enter three character abbreviation for client.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ecp.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a user that already exists in the target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

    Possible values:

    -   *userName* \(default value\)

    -   *userUuid*

    -   *emails\[0\].value*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ecp.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If the Identity Provisioning tries to create a group that already exists in the target system \(a conflicting group\), this property defines the unique attributes by which the existing group will be searched and resolved.

    **Possible values:** *displayName* \(default value if not specified\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)

    `ecp.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Employee Central Payroll groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `ECP_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `ECP_` prefix in their display name will be provisioned to SAP Employee Central Payroll. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Employee Central Payroll.
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Employee Central Payroll* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Employee Central Payroll system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Employee Central Payroll entity.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >                 ],
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "optional": true,
    >                 "targetPath": "$.name"
    >             },
    >             {
    >                 "sourcePath": "$.nickName",
    >                 "optional": true,
    >                 "targetPath": "$.nickName"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$.userUuid"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.phoneNumbers"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary== true)].value",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "condition": "('%ecp.group.prefix%' === 'null') || ($.displayName =~ /%ecp.group.prefix%.*/)",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:Group"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "('%ecp.group.prefix%' !== 'null') && (@ =~ /%ecp.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%ecp.group.prefix%",
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
    >             },
    >             {
    >                 "constant": "User",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[*].type",
    >                 "scope": "createEntity"
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio03b4097a408f4010b0396c56c2660bb1__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP SuccessFactors Employee Central Payroll](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL_PAYROLL?version=latest)

