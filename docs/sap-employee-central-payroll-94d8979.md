<!-- loio94d89796b08448f7af07fb850e67773d -->

# SAP Employee Central Payroll

Follow this procedure to set up SAP Employee Central Payroll as а source system.



<a name="loio94d89796b08448f7af07fb850e67773d__prereq_gfl_gvx_rdb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.



## Context

SAP Employee Central Payroll is a cloud product for payroll processing. It's a service offering where SAP SuccessFactors Employee Central is used for maintenance of core HR master data and SAP HCM Payroll system hosted in an SAP or Hyperscaler data center is used for payroll.

You can use Identity Provisioning to configure SAP Employee Central Payroll as a source system where you read users and groups from and then provision them to a target system.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Employee Central Payroll* as a source system. See: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    \(Optional\) `ecp.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Employee Central Payroll users matching the filter expression will be read.

    Supported operators: eq \(equal\) and sw \(starts with\).

    For example:

    -   Value = *userName eq "JohnSmith"*

    -   Value = *userName sw "J"*

    -   Value = *emails.value eq "john.smith@example.com"*

    -   Value = *userUuid eq "1ab6c132-5de5-4530-8g14-1234h26373ab"*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ecp.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Employee Central Payroll groups matching the filter expression will be read.

    Supported operators: eq \(equal\) and sw \(starts with\).

    For example:

    -   Value = *displayName eq "ProjectTeam1"*

    -   Value = *displayName sw "P"*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ecp.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Employee Central Payroll groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `ECP_`

    You can use the example value or provide your own.

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Employee Central Payroll source system and will be provisioned to the target system with the following name pattern: <code>ECP_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Employee Central Payroll groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Employee Central Payroll groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Employee Central Payroll* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **Mapping logic** – the behavior of the default transformation logic is to read all user attributes from the source SAP Employee Central Payroll system, and then map them to the internal SCIM representation. It uses `entityIdSourceSystem` to store the unique ID of the identity.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.nickName",
    >                 "targetPath": "$.nickName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.title",
    >                 "targetPath": "$.title",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.userUuid",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "targetPath": "$.phoneNumbers",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary== true)].value",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true,
    >                 "functions": [
    >                     {
    >                         "function": "concatString",
    >                         "condition": "'%ecp.group.prefix%' !== 'null'",
    >                         "applyOnElements": true,
    >                         "applyOnAttribute": "display",
    >                         "prefix": "%ecp.group.prefix%"
    >                     }
    >                 ]
    >             }
    >         ]
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "'%ecp.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "prefix": "%ecp.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Add a target system to provision users to it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio94d89796b08448f7af07fb850e67773d__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP SuccessFactors Employee Central Payroll](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL_PAYROLL?version=latest)

