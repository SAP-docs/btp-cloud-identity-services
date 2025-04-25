<!-- loio26b1c1e786984bfbb1e242efd293b6af -->

# SAP Enterprise Portal

Follow this procedure to set up SAP Enterprise Portal as а source system.



<a name="loio26b1c1e786984bfbb1e242efd293b6af__prereq_gfl_gvx_rdb"/>

## Prerequisites

-   You are using SAP NetWeaver 7.5 Patch Level 22 and higher.

-   You have prepared AS Java to use the SCIM application for REST API calls, as described in [Initial Setup](https://help.sap.com/viewer/44a42f8a693e4498be42434d28ff3457/7.5.22/en-US/c790be0c2fb84579b8f189fafad6d43f.html).

    This means, you have activated the SCIM application and created and set user authorization.




## Context

SAP Enterprise Portal uses and builds on the user management of SAP NetWeaver AS for Java. Using SAP Enterprise Portal, organizations can give their employees, customers, partners, and suppliers a single point of access to the company applications, services, and information needed for conducting daily work. The portal offers business users the capability to easily create and manage portal pages and to generate their own portal content.

You can use Identity Provisioning to configure SAP Enterprise Portal as a source system where you can read users, groups and group assignments and provision them to target systems of your choice. In SAP Enterprise Portal, those entities correspond to users, Portal roles and user assignments to Portal roles, respectively.

> ### Note:  
> When reading groups from SAP Enterprise Portal source system, only the exposed Portal roles are returned. When reading users, only user members of the exposed roles are returned.

In a typical scenario, SAP Enterprise Portal is configured as a source system and [SAP Build Work Zone, standard edition](sap-build-work-zone-standard-edition-8d6586f.md) is configured as a target system. The SCIM Portal application for AS Java is developed to satisfy the SAP Enterprise Portal and SAP Build Work Zone, standard edition requirements for synchronization of exposed Portal roles and the user assignments to Portal roles.

For more information, see [SCIM Portal Application for AS Java](https://help.sap.com/viewer/44a42f8a693e4498be42434d28ff3457/7.5.22/en-US/ccf9fe02648c40299e39775eb54011cf.html)



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Enterprise Portal* as a source system. See: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Choose the *Properties* tab to configure the connection settings for your system.

    > ### Note:  
    > If your Identity Provisioning tenant is running on SAP BTP, Neo environment, you can create a [connectivity destination](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/72696d6d06c0490394ac3069da600278.html) in your subaccount in the SAP BTP cockpit, and then select it from the *Destination Name* combo box in your Identity Provisioning User Interface.
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
    
    Specify the URL to the SCIM API of your SAP Enterprise Portal system. It follows the pattern:

    `http://<host>:<port>` of SAP NetWeaver where the SAP Enterprise Portal runs on.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Enter: *OnPremise* 
    
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
    
    Enter the user name of the technical user you have created following the *Create and Set User Authorization* step in the *Prerequisites* section.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password of the technical user you have created following the *Create and Set User Authorization* step in the *Prerequisites* section.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ep.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Enterprise Portal users matching the filter expression will be read. For more information, see [Filtering](https://help.sap.com/docs/SAP_NETWEAVER_750/44a42f8a693e4498be42434d28ff3457/ccf9fe02648c40299e39775eb54011cf.html?version=7.5.22#filtering).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ep.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Enterprise Portal groups matching the filter expression will be read. For more information, see [Filtering](https://help.sap.com/docs/SAP_NETWEAVER_750/44a42f8a693e4498be42434d28ff3457/ccf9fe02648c40299e39775eb54011cf.html?version=7.5.22#filtering).
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map user and group attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Enterprise Portal* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SCIM Implementation for AS Java](https://help.sap.com/viewer/44a42f8a693e4498be42434d28ff3457/7.5.22/en-US/dc03f76e1cf349fc8bfc5776e8b6d5f8.html)

    **Mapping logic** – the behavior of the default transformation logic is to read all user attributes from the source SAP Enterprise Portal system, and then map them to the internal SCIM representation. It uses `entityIdSourceSystem` to store the unique ID of the identity.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
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
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails",
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
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Add a target system to provision users and groups to it. For example: [SAP Build Work Zone, standard edition](sap-build-work-zone-standard-edition-8d6586f.md).




<a name="loio26b1c1e786984bfbb1e242efd293b6af__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Enterprise Portal](https://help.sap.com/viewer/40fb2965584a448a996f1e1aa3e3c08d/7.5.22/en-US/75321c70b9df46ffbd06023ffe67361d.html)

