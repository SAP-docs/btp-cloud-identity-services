<!-- loiocee1e14c80e44c0eab41a23f67cf940f -->

# SAP Enable Now

Follow this procedure to set up SAP Enable Now as a source system.



<a name="loiocee1e14c80e44c0eab41a23f67cf940f__prereq_kqy_lfd_pcc"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created a technical user in SAP Enable Now with the necessary permissions for establishing a connection with Identity Provisioning.




## Context

The SAP Enable Now solution is SAP’s digital adoption platform. It can help you improve the adoption, productivity, and efficiency of your software by providing in-application help and e-learning content to users.

You can use Identity Provisioning to configure SAP Enable Now as a source system where you can read users and provision them to target systems of your choice. The source system consumes SCIM 2.0 API provided by SAP Enable Now.



<a name="loiocee1e14c80e44c0eab41a23f67cf940f__steps_pl4_rlx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Enable Now* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL to your SAP Enable Now system. It follows the pattern:

    -   <code>https://<i class="varname">&lt;company-name&gt;</i>.enable-now.cloud.sap/scim/v2</code>

    -   <code>https://<i class="varname">&lt;company-name&gt;</i>.sap-enable-now.cn/scim/v2</code> \(relevant for China\)



    
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
    
    Enter the username of the SAP Enable Now technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password of the SAP Enable Now technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `en.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Enable Now users matching the filter expression will be read

    For example: *userName eq "SmithJ"*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`en.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Enable Now groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `EN_`

    You can use the example value or provide your own.

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Enable Now source system and will be provisioned to the target system with the following name pattern: <code>EN_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Enable Now groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Enable Now groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Enable Now* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Enable Now system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
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
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true,
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.middleName",
    >                 "optional": true,
    >                 "targetPath": "$.name.middleName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional": true,
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "optional": true,
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true,
    >                 "functions": [
    >                     {
    >                         "condition": "'%en.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "applyOnElements": true,
    >                         "applyOnAttribute": "display",
    >                         "prefix": "%en.group.prefix%"
    >                     }
    >                 ]
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
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "'%en.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "prefix": "%en.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "optional": true
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

6.  Now, add a target system to provision users into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loiocee1e14c80e44c0eab41a23f67cf940f__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Enable Now](https://help.sap.com/docs/SAP_ENABLE_NOW?version=Latest)

