<!-- loioacd73077e45e47b59bd4bfcc929dbae6 -->

# SAP Data Custodian

Follow this procedure to set up SAP Data Custodian as a source system.



<a name="loioacd73077e45e47b59bd4bfcc929dbae6__prereq_rdf_ntd_r3b"/>

## Prerequisites

> ### Restriction:  
> This system is available for all standalone tenants and bundle tenants running on SAP Cloud Identity Services infrastructure. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created an SAP Data Custodian tenant.

-   You have created a user within your tenant with the required roles for your scenario.

-   You have added your user to SAP Identity Service Management \(SAP ISM\).

-   You have completed the Transparency and Control Service Onboarding Process or the Key Management Service Onboarding Process, depending on the scenario you want to implement. For more information, see [Transparency and Control Service Onboarding Process](https://help.sap.com/docs/SAP_DATA_CUSTODIAN/538dde61cf134c89bda1c31100a6c0e1/22a3ec71c2314004b87d8a4d1df01492.html?locale=en-US&version=2210) and [Key Management Service Onboarding Process](https://help.sap.com/docs/SAP_DATA_CUSTODIAN/538dde61cf134c89bda1c31100a6c0e1/21ec63132e22411c9308894d397e3901.html?locale=en-US&version=2210).




<a name="loioacd73077e45e47b59bd4bfcc929dbae6__context_fk3_xgh_dwb"/>

## Context

> ### Note:  
> Currently, SAP Data Custodian connector is only available for selected customers who are approached by SAP. For more information, see [3319946](https://me.sap.com/notes/3319946).

SAP Data Custodian is a robust Software as a Service \(SaaS\) solution that protects sensitive data stored in public, private, hybrid, and multicloud environments. This solution integrates with partnered public hyperscalers, SAP applications, and SAP managed clouds.

After fulfilling the prerequisites, follow the procedure below to add a source system for SAP Data Custodian to read users and user assignments to groups. This source system consumes SCIM 2.0 API provided by SAP Data Custodian.



<a name="loioacd73077e45e47b59bd4bfcc929dbae6__steps_gk3_xgh_dwb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Data Custodian* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    `dc.group.filter`
    
    </td>
    <td valign="top">
    
    This property filters groups by display name or externalId.

    When specified, only those groups matching the filter expression will be read.

    **Possible values:**

    -   *SAP\_Data\_Custodian\_Auditor*

    -   *SAP\_Data\_Custodian\_Service\_Admin*

    -   *SAP\_Data\_Custodian\_Key\_Admin*

    -   *SAP\_Data\_Custodian\_Key\_User*


    For example: *displayName eq "SAP\_Data\_Custodian\_Auditor"*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dc.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Data Custodian users matching the filter expression will be read. You can filter users by *userName*, *displayName* or *externalId*.

    **Possible values:**

    For example: *****userName eq "Smith.J"*
    
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

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Data Custodian source system and will be provisioned to the target system with the following name pattern: <code>DC_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Data Custodian groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Data Custodian groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Data Custodian* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    > ### Note:  
    > During user creation, the expected format for `userName` is email. Hence, the primary email of the user is set for `userName`.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SCIM system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Data Custodian SCIM 2.0 API](https://api-kms-devel.datacustodian.cloud.sap/kms/scim/v1/ui/)

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
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "functions": [
    >                     {
    >                         "condition": "'%dc.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "applyOnElements": true,
    >                         "applyOnAttribute": "display",
    >                         "prefix": "%dc.group.prefix%"
    >                     }
    >                 ]
    >             }
    >         ]
    >     },
    >     "group": {
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
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "'%dc.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "prefix": "%dc.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId",
    >                 "optional": true
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a target system to provision users and their group assignments to it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loioacd73077e45e47b59bd4bfcc929dbae6__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Data Custodian](https://help.sap.com/docs/SAP_DATA_CUSTODIAN?version=2210&locale=en-US)

