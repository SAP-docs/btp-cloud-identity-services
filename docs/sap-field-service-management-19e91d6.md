<!-- loio19e91d648f1f4f58b0b2913f45699d08 -->

# SAP Field Service Management

Follow this procedure to set up SAP Field Service Management as а source system.



<a name="loio19e91d648f1f4f58b0b2913f45699d08__prereq_gfl_gvx_rdb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

You have OAuth credentials for SAP Field Service Management. For more information, see: [Generating Client ID & Secret](https://help.sap.com/viewer/fsm_admin/Cloud/en-US/generating-client-id.html)



## Context

SAP Field Service Management is a cloud-based solution that is used to resolve customers issues with end-to-end field service management. For example, it helps customers overcome resource limitations, such as having enough skilled technicians in all locations.

You can use the Identity Provisioning user interface \(UI\) to configure SAP Field Service Management as a source system where you can read users, groups, and group members.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Field Service Management* as a source system. See: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    \(Optional\) `fsm.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Field Service Management users matching the filter expression will be read.

    Example: **name.familyName eq "Smith" and addresses.country eq "US"**

    > ### Note:  
    > Using this property makes sense only if you have set the *"ignore": true* statement to **false**.


    
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
    
    \(Optional\) `fsm.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Field Service Management groups matching the filter expression will be read.

    Example: **displayName eq "ProjectTeam1" or "Employees2020"**
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Field Service Management* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Field Service Management - SCIM API](https://help.sap.com/viewer/fsm_scim_api/Cloud/en-US/scim-api.html)

    **Mapping logic** – the behavior of the default transformation logic is to read all user attributes from the source SAP Field Service Management system, and then map them to the internal SCIM representation. It uses `entityIdSourceSystem` to store the unique ID of the identity.

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
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true,
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional": true,
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups",
    >                 "functions": [
    >                     {
    >                         "condition": "'%fsm.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "applyOnElements": true,
    >                         "applyOnAttribute": "display",
    >                         "prefix": "%fsm.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
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
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "'%fsm.group.prefix%' !== 'null'",
    >                         "function": "concatString",
    >                         "prefix": "%fsm.group.prefix%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members"
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Add a target system to provision users and groups to it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio19e91d648f1f4f58b0b2913f45699d08__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Field Service Management – Collection](https://blogs.sap.com/2020/11/06/sap-central-business-configuration-collection/)

