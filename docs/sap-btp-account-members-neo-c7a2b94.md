<!-- loioc7a2b94364fe48d5b7c6713284ebc5d8 -->

# SAP BTP Account Members \(Neo\)

Follow this procedure to set up your SAP Business Technology Platform as a target system, to which you can provision and write members in your Neo account.



<a name="loioc7a2b94364fe48d5b7c6713284ebc5d8__prereq_n1b_khq_h2b"/>

## Prerequisites

You have created a new Platform API OAuth client, with API *Account Member Management* and scopes *Manage Account Members* and *Read Account Members*.

Save the *Client ID* and *Client Secret* as you'll need them when you configure your target system. Make sure you save the client secret as you cannot retrieve it later.

For more information, see [Create a Platform API Client](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/392af9d162694d6595499f1549978aa6.html).



## Context

The Identity Provisioning service helps companies to automatically manage the user-to-platform roles assignments for SAP Business Technology Platform subaccounts. For this aim, the service reuses data from an active company user store. For this scenario, as a target system are used SAP Business Technology Platform subaccounts. A source system can be a solution supported by the Identity Provisioning service with read access for user artifacts.

This provisioning scenario is based on the Platform Authorization Management API of SAP BTP. For more information, see [Platform Authorization Management API](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/eb01a9f3ecad4a41a6033855ca61a9a8.html).



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP BTP Account Members \(Neo\)* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter: `https://api.<SAP_BTP_host>/authorization/v1/platform/accounts/<SAP_BTP_account>` 

    Examples:

    -   \(Europe – Rot\) *https://api.hana.ondemand.com/authorization/v1/platform/accounts/abc123xyz*
    -   \(Japan – Tokyo\) *https://api.jp1.hana.ondemand.com/authorization/v1/platform/accounts/abc123xyz*


    
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
    
    Enter the Client ID of the new Platform API OAuth client created for the **Account Member Management** API \(see the prerequisites\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the Client Secret of the new Platform API OAuth client created for the **Account Member Management** API \(see the prerequisites\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter: `https://api.<SAP_CP_host>/oauth2/apitoken/v1`

    Examples:

    -   \(Europe – Rot\) *https://api.hana.ondemand.com/oauth2/apitoken/v1*
    -   \(US East – Sterling\) *https://api.us3.hana.ondemand.com/oauth2/apitoken/v1*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `scp.user.userbase`
    
    </td>
    <td valign="top">
    
    This property specifies the host to the identity provider to be used with this proxy system. All provisioned users can be authenticated only by this identity provider. Default value: *account.sap.com*

    If you use another IdP, enter its value as configured in the SAP BTP cockpit. For example: `<account_ID>.accounts.ondemand.com`
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP Account Members* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    Using the default transformation, all groups that are available in the source system and their respective members \(as identifiers\) are assigned as platform roles to the users. These users are added to the SAP Business Technology Platform subaccount via the target system.

    You can change the default transformation mapping rules to reflect your current setup of entities in your target system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP BTP: Authorization Management API](https://api.hana.ondemand.com/authorization/v1/documentation)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    > 
    > // The roles in the conditions below are placeholder names mapped to the SAP BTP roles. You can replace these names with the actual role names used in your source system. 
    > // You can delete some of these roles (if redundant), or add new mappings for additional roles.
    >       {
    >         "condition": " (('%scp.group.prefix%' === 'null') && ($.groups[*].value contains 'AccountAdministrator')) || (('%scp.group.prefix%' !== 'null') && ($.groups[*].value contains '%scp.group.prefix%AccountAdministrator'))",
    >         "constant": "AccountAdministrator",
    >         "targetPath": "$.roles[0].value"
    >       },
    >       {
    >         "condition": " (('%scp.group.prefix%' === 'null') && ($.groups[*].value contains 'Developer')) || (('%scp.group.prefix%' !== 'null') && ($.groups[*].value contains '%scp.group.prefix%Developer'))",
    >         "constant": "Developer",
    >         "targetPath": "$.roles[1].value"
    >       },
    >       {
    >         "condition": " (('%scp.group.prefix%' === 'null') && ($.groups[*].value contains 'CloudConnectorAdministrator')) || (('%scp.group.prefix%' !== 'null') && ($.groups[*].value contains '%scp.group.prefix%CloudConnectorAdministrator'))",
    >         "constant": "CloudConnectorAdministrator",
    >         "targetPath": "$.roles[2].value"
    >       },
    >       {
    >         "condition": " (('%scp.group.prefix%' === 'null') && ($.groups[*].value contains 'ApplicationUserAdministrator')) || (('%scp.group.prefix%' !== 'null') && ($.groups[*].value contains '%scp.group.prefix%ApplicationUserAdministrator'))",
    >         "constant": "ApplicationUserAdministrator",
    >         "targetPath": "$.roles[3].value"
    >       },
    >       {
    >         "condition": " (('%scp.group.prefix%' === 'null') && ($.groups[*].value contains 'ReadOnly')) || (('%scp.group.prefix%' !== 'null') && ($.groups[*].value contains '%scp.group.prefix%ReadOnly'))",
    >         "constant": "ReadOnly",
    >         "targetPath": "$.roles[4].value"
    >       },
    >       {
    >         "constant": "%scp.user.userbase%",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:UserExt']['userbase']"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "constant": "urn:sap:cloud:scim:schemas:extension:custom:2.0:UserExt",
    >         "targetPath": "$.schemas[1]"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "('%scp.group.prefix%' === 'null') || ($.displayName =~ /%scp.group.prefix%.*/)",
    >     "skipOperations": [
    >       "delete"
    >     ],
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "('%scp.group.prefix%' !== 'null') && (@ =~ /%scp.group.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%scp.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true,
    >         "sourcePath": "$.members[*].value",
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "type": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Now, add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loioc7a2b94364fe48d5b7c6713284ebc5d8__postreq_lpw_sqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[What is SAP BTP](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/73beb06e127f4e47b849aa95344aabe1.html)

