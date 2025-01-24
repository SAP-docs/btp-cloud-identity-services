<!-- loio8f3edc371dff4c749714702974cd1e48 -->

# SAP Sales Cloud and SAP Service Cloud

Follow this procedure to set up SAP Sales Cloud and SAP Service Cloud, formerly known as *SAP Cloud for Customer* \(in short, C4C\), as a source system.



<a name="loio8f3edc371dff4c749714702974cd1e48__prereq_kfb_sdl_5cb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

To integrate SAP Sales Cloud and SAP Service Cloud with Identity Provisioning, you need to use SAP Cloud Integration \(SAP CI\). This service provides a package with integration flows \(iFlows\) for enabling the creation of users and assignment of users to groups via SCIM API in SAP Sales Cloud and SAP Service Cloud.

-   To configure SAP Cloud Integration and SAP Sales Cloud and SAP Service Cloud, see: [Identity Provisioning in SAP Cloud for Customer using System for Cross-Domain Identity Management \(SCIM\)](https://help.sap.com/viewer/b5196c50731249cdb877bd3b44d9f48d/CLOUD/en-US/30727bdccd6a4646aa7087bebd783ecd.html)

-   To set up and use the *SAP Cloud for Customer Integration with Identity Provisioning via System for Cross-domain Identity Management* package, see: [SAP Business Accelerator Hub: SAP Cloud for Customer Integration with Identity Provisioning via System for Cross-domain Identity Management](https://api.sap.com/package/IdentityProvisioninginSAPCloudforCustomerviaSCIM/overview)




## Context

SAP Sales Cloud and SAP Service Cloud is a cloud-based solution that helps customers manage day-to-day sales and service interactions by sending and receiving signals between front- and back-office solutions and providing a single view of the customer.

You can use Identity Provisioning to configure SAP Sales Cloud and SAP Service Cloud as a source system where you can read *business users*, *employee users*, and *groups* from and provision them to a target system.

This scenario is relevant for existing SAP Sales Cloud and SAP Service Cloud customers \(brown-field approach\). This means that business users, employees, and groups have already been created in SAP Sales Cloud and SAP Service Cloud and can be provisioned to the Identity Authentication target system. After the users and groups are created in Identity Authentication, reflecting the business users and group assignments in SAP Sales Cloud and SAP Service Cloud, Identity Authentication can become the leading system in user provisioning.



<a name="loio8f3edc371dff4c749714702974cd1e48__steps_r2s_fdl_5cb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Sales Cloud and SAP Service Cloud* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter SAP Cloud Integration runtime URL.

    See: [How to Get SAP Cloud Integration Runtime URL](https://help.sap.com/docs/sap-digital-manufacturing/integration-guide/how-to-get-sap-cloud-integration-runtime-url)
    
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

    *BasicAuthentication*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter SAP Cloud Integration user ID to connect to SAP Cloud Integration. See:

    -   [Setting Up Inbound HTTP Connections \(with Basic Authentication\), Neo Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/391c45cfcd0f4435952ab085283b7f7d.html)

    -   [Basic Authentication of IdP User for Integration Flow Processing \(Cloud Foundry environment\)](https://help.sap.com/docs/CLOUD_INTEGRATION/368c481cd6954bdfa5d0435479fd4eaf/5d46e56550a048e99995f23e1e20083a.html)



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter SAP Cloud Integration password to connect to SAP Cloud Integration. See:

    -   [Setting Up Inbound HTTP Connections \(with Basic Authentication\), Neo Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/391c45cfcd0f4435952ab085283b7f7d.html)

    -   [Basic Authentication of IdP User for Integration Flow Processing \(Cloud Foundry environment\)](https://help.sap.com/docs/CLOUD_INTEGRATION/368c481cd6954bdfa5d0435479fd4eaf/5d46e56550a048e99995f23e1e20083a.html)



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `c4c.api.version`
    
    </td>
    <td valign="top">
    
    The version of the SAP Sales Cloud and SAP Service Cloud API you use. By default, the Identity Provisioning service uses version **3** - the SCIM 2.0 based API.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `c4c.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those C4C users matching the filter expression will be read.

    For example:

    -   userName eq "Smith"

    -   email eq "test@abc.com"

    -   employeeNumber eq "56789"

    -   addresses.country eq "USA"



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `c4c.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those C4C groups matching the filter expression will be read.

    Example: **displayName eq "ProjectTeam1"**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`c4c.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Sales Cloud and SAP Service Cloud groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `C4C_`

    You can use the example value or provide your own.

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Sales Cloud and SAP Service Cloud source system and will be provisioned to the target system with the following name pattern: <code>C4C_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Sales Cloud and SAP Service Cloud groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Sales Cloud and SAP Service Cloud groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    The Identity Provisioning offers a default transformation for the *SAP Sales Cloud and SAP Service Clouds* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in C4C. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary == true)].value",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "optional": true,
    >         "targetPath": "$.userType"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "optional": true,
    >         "targetPath": "$.name.middleName"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "optional": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']"
    >      },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >           {
    >             "condition": "'%c4c.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "display",
    >             "prefix": "%c4c.group.prefix%"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "'%c4c.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%c4c.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Now, add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio8f3edc371dff4c749714702974cd1e48__postreq_zqx_nqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

