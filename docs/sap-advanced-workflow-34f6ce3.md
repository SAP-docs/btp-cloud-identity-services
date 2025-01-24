<!-- loio34f6ce31dfbc471e96a115e9f8baf7f1 -->

# SAP Advanced Workflow

Follow this procedure to set up a target connector for SAP Advanced Workflow.



<a name="loio34f6ce31dfbc471e96a115e9f8baf7f1__prereq_yqm_k54_wxb"/>

## Prerequisites

-   You have technical credentials for SAP Advanced Workflow. Note that SAP Advanced Workflow is available to SAP SuccessFactors Incentive Management customers as an optional add-on. You create an Admin user in SAP SuccessFactors Incentive Management, which is synchronized with SAP Advanced Workflow. For more information, see: [Adding an Admin User](https://help.sap.com/docs/SAP_Commissions/4ec7f498159b4d04892ecb0a4726f89d/7273e2517c231014a804993ce4041860.html?version=2306&locale=en-US) and [Commissions User Synchronization](https://help.sap.com/docs/Advanced_Workflow/b7cb13f8b6a04157a722ad9ddfde4a28/72a134767c231014a804993ce4041860.html?locale=en-US&version=2306).

-   You have set up SSO between Identity Authentication and SAP Advanced Workflow. For more information, see [Integration with SAP IdP](https://help.sap.com/docs/Advanced_Workflow/b7cb13f8b6a04157a722ad9ddfde4a28/677264fa7fd3492f8d7ac5e8fcc62f79.html?version=2306&locale=en-US).




## Context

SAP Advanced Workflow enables you to analyse, organize, and execute business processes to connect people, data, and daily activities. Workflow provides you the tools you need to configure and customize your business processes based on your specific business needs.

After fulfilling the prerequisites, follow the procedure below to add a target system for SAP Advanced Workflow where you can provision **users** from source systems. This target system consumes Workflow SCIM API.

> ### Note:  
> SAP Advanced Workflow does not support groups.



<a name="loio34f6ce31dfbc471e96a115e9f8baf7f1__steps_wd3_2v4_wxb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Advanced Workflow* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify the URL to the API of your SAP Advanced Workflow system.
    
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
    
    Enter the user for your SAP Advanced Workflow system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for your SAP Advanced Workflow user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `awf.domain`
    
    </td>
    <td valign="top">
    
    The domain name is the name of your SAP Advanced Workflow tenant.

    If you don't know your tenant name, contact your supervisor or administrator, or refer to the email notification you received when your account was created.
    
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

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Advanced Workflow* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Advanced Workflow. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target entity. If the entity has more than one e-mail addresses, only one of them is used. It is either the e-mail set as primary in the source system, or if no primary e-mail is set, the one that comes first is used.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "condition": "($.emails EMPTY true) || isValidEmail($.emails[0].value)",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": ["urn:ietf:params:scim:schemas:core:2.0:User", "urn:ietf:params:scim:schemas:extension:sap.spm.workflow:2.0:User"],
    >                 "targetPath": "$.schemas"
    >             },
    >                         {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.name.givenName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.middleName",
    >                 "targetPath": "$.name.middleName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "targetPath": "$.name.familyName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "targetPath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "targetPath": "$.timezone",
    >                 "optional": true
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio34f6ce31dfbc471e96a115e9f8baf7f1__postreq_lvw_bqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

