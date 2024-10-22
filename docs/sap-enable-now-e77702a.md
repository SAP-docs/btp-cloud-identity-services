<!-- loioe77702a9f53d4a1d93d94e585eb0252d -->

# SAP Enable Now

Follow this procedure to set up SAP Enable Now as a target system.



<a name="loioe77702a9f53d4a1d93d94e585eb0252d__prereq_kqy_lfd_pcc"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created a technical user in SAP Enable Now with the necessary permissions for establishing a connection with Identity Provisioning.




## Context

The SAP Enable Now solution is SAP’s digital adoption platform. It can help you improve the adoption, productivity, and efficiency of your software by providing in-application help and e-learning content to users.

You can use Identity Provisioning to configure SAP Enable Now as a target system where you can provision users and groups. The target system consumes SCIM 2.0 API provided by SAP Enable Now.



<a name="loioe77702a9f53d4a1d93d94e585eb0252d__steps_phw_gld_pcc"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Enable Now* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    `en.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a user that already exists in the target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

    Default value: *userName*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `en.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

    -   If set to *true*, `PATCH` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, only these changes will be provisioned and applied in the target system.

    -   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


    Default value: *false* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `en.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Enable Now groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `EN_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `EN_` prefix in their display name will be provisioned to SAP Enable Now. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Enable Now.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.users`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of users to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of users, for example by adding a filter or condition.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Enable Now* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Enable Now system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)",
    >         "mappings": [
    >             {
    >                 "targetPath": "$.id",
    >                 "sourceVariable": "entityIdTargetSystem"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true
    >             }
    >         ]
    >     },
    >     "group": {
    >         "condition": "('%en.group.prefix%' === 'null') || ($.displayName =~ /%en.group.prefix%.*/)",
    >         "mappings": [
    >             {
    >                 "targetPath": "$.id",
    >                 "sourceVariable": "entityIdTargetSystem"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "('%en.group.prefix%' !== 'null') && (@ =~ /%en.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%en.group.prefix%",
    >                         "replacement": ""
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >                 "optional": true
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
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)

    > ### Caution:  
    > The **email** attribute is unique for *SAP Enable Now* but it might not be unique for other systems, such as *SAP SuccessFactors*. That's why, when you choose a source system, make sure that there are no users with duplicate e-mails. If there are such, then after the provisioning job all users with the same e-mail address will be created as a single user in *SAP Enable Now*.
    > 
    > To learn more, see *Guided Answers*: [Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)
    > 
    > To learn more about excluding users from SAP Enable Now target, see: [Exclude Users from Provisioning to Target Systems](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:55088)




<a name="loioe77702a9f53d4a1d93d94e585eb0252d__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Enable Now](https://help.sap.com/docs/SAP_ENABLE_NOW?version=Latest)

