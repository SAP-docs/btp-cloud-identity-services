<!-- loiof540d52ec1ac43aab6ec9f74577328cb -->

# SAP Ariba Central Invoice Management

Follow this procedure to set up SAP Ariba Central Invoice Management as а source system.



<a name="loiof540d52ec1ac43aab6ec9f74577328cb__prereq_gfl_gvx_rdb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

You have created an instance and generated a service key for the scim service plan of SAP Ariba Central Invoice Management. For more information, see [Setting Up Invoice Processing with SAP Ariba Central Invoice Management \(4N6\)](https://support.sap.com/content/dam/SAAP/Sol_Pack/S4C/Library/Setup/4N6_Set-Up_EN_XX.pdf) –\> *7.4 Configure User Replication*.



## Context

SAP Ariba Central Invoice Management is an SAP BTP SaaS application running on SAP BTP, Cloud Foundry environment. This application enables central management of supplier invoices from multiple connected systems, such as SAP S/4HANA Cloud systems. You can use Identity Provisioning to configure SAP Ariba Central Invoice Management as a source system where you can read users and groups from and provision them to a target system.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Ariba Central Invoice Management* as a source system. See: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL provided by the service key under the *ips-connector* field without adding the path information.

    For example: `https://eu10.cim.cloud.sap`
    
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
    
    Enter the value from the *clientid* field of the service key.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the value from the *clientsecret* field of the service key.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL. This is the value from the *url* field of the service key plus `/oauth/token`

    For example: <code>https://<i class="varname">&lt;my tenant&gt;</i>.authentication.eu10.hana.ondemand.com/oauth/token</code>
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cim.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Ariba Central Invoice Management users matching the filter expression will be read.

    Example: *name.familyName eq "Smith"* and *addresses.country eq "US"*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cim.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Ariba Central Invoice Management groups matching the filter expression will be read.

    Example: *displayName eq "ProjectTeam1" or "Students2018"*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cim.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Ariba Central Invoice Management groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `CIM_`

    You can use the example value or provide your own.

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Ariba Central Invoice Management source system and will be provisioned to the target system with the following name pattern: <code>CIM_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Ariba Central Invoice Management groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Ariba Central Invoice Management groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Ariba Central Invoice Management* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **Mapping logic** – the behavior of the default transformation logic is to read all user attributes from the source SAP Ariba Central Invoice Management system, and then map them to the internal SCIM representation. It uses `entityIdSourceSystem` to store the unique ID of the identity.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >    "user":{
    >       "mappings":[
    >          {
    >             "sourcePath":"$.id",
    >             "targetVariable":"entityIdSourceSystem"
    >          },
    >          {
    >             "sourcePath":"$.schemas",
    >             "targetPath":"$.schemas",
    >             "preserveArrayWithSingleElement":true
    >          },
    >          {
    >             "sourcePath":"$.userName",
    >             "targetPath":"$.userName",
    >             "correlationAttribute":true
    >          },
    >          {
    >             "sourcePath":"$.externalId",
    >             "targetPath":"$.externalId",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.name.givenName",
    >             "targetPath":"$.name.givenName",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.name.middleName",
    >             "targetPath":"$.name.middleName",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.name.familyName",
    >             "targetPath":"$.name.familyName",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.name.formatted",
    >             "targetPath":"$.name.formatted",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.name.honorificPrefix",
    >             "targetPath":"$.name.honorificPrefix",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.name.honorificSuffix",
    >             "targetPath":"$.name.honorificSuffix",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.emails[*].value",
    >             "targetPath":"$.emails[?(@.value)]",
    >             "optional":true,
    >             "preserveArrayWithSingleElement":true
    >          },
    >          {
    >             "sourcePath":"$.emails[?(@.primary== true)].value",
    >             "optional":true,
    >             "correlationAttribute":true
    >          },
    >          {
    >             "sourcePath":"$.active",
    >             "targetPath":"$.active"
    >          },
    >          {
    >             "sourcePath":"$.userType",
    >             "targetPath":"$.userType",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.locale",
    >             "targetPath":"$.locale",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.timezone",
    >             "targetPath":"$.timezone",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.displayName",
    >             "targetPath":"$.displayName",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.groups",
    >             "targetPath":"$.groups",
    >             "optional":true,
    >             "preserveArrayWithSingleElement":true,
    >             "functions":[
    >                {
    >                   "condition":"'%cim.group.prefix%' !== 'null'",
    >                   "function":"concatString",
    >                   "applyOnElements":true,
    >                   "applyOnAttribute":"display",
    >                   "prefix":"%cim.group.prefix%"
    >                }
    >             ]
    >          }
    >       ]
    >    },
    >    "group":{
    >       "mappings":[
    >          {
    >             "sourcePath":"$.id",
    >             "targetVariable":"entityIdSourceSystem"
    >          },
    >          {
    >             "sourcePath":"$.externalId",
    >             "targetPath":"$.externalId"
    >          },
    >          {
    >             "sourcePath":"$.schemas",
    >             "targetPath":"$.schemas",
    >             "preserveArrayWithSingleElement":true
    >          },
    >          {
    >             "sourcePath":"$.displayName",
    >             "targetPath":"$.displayName",
    >             "functions":[
    >                {
    >                   "condition":"'%cim.group.prefix%' !== 'null'",
    >                   "function":"concatString",
    >                   "prefix":"%cim.group.prefix%"
    >                }
    >             ]
    >          },
    >          {
    >             "sourcePath":"$.members",
    >             "targetPath":"$.members",
    >             "optional":true,
    >             "preserveArrayWithSingleElement":true
    >          }
    >       ]
    >    }
    > }
    > ```

6.  Add a target system to provision users to it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loiof540d52ec1ac43aab6ec9f74577328cb__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Ariba Central Invoice Management](https://help.sap.com/docs/CENTRAL_INVOICE_MANAGEMENT)

