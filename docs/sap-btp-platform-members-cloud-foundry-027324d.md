<!-- loio027324df5c2d471cb09514491565646b -->

# SAP BTP Platform Members \(Cloud Foundry\)

Follow this procedure to set up the SAP BTP Platform Members \(Cloud Foundry\) as а source system.



<a name="loio027324df5c2d471cb09514491565646b__prereq_l4f_cnz_scc"/>

## Prerequisites

-   You have a global account in SAP BTP with at least one multi-environment subaccount with enabled Cloud Foundry environment.

-   You have established trust between your SAP Cloud Identity Services tenant as custom identity provider for platform users and your global account\(s\) containing these subaccounts. For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users](https://help.sap.com/docs/btp/sap-business-technology-platform/establish-trust-and-federation-of-custom-identity-providers-for-platform-users?locale=en-US&version=Cloud).

-   You have created a CF provisioning user \(which is a regular user of type *Employee* in the local identity directory of your SAP Cloud Identity Services tenant\) that will be used for provisioning. Give this user an email address with the following pattern `cf-user-provisioning-<origin_key>@sap.invalid`, where `<origin_key>` is the origin key of the trust configuration for BTP platform users which points to your SAP Cloud Identity Services tenant. You have set an initial password for the user and marked its email adress as *verified*. For more information, see [Create a New User](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/create-new-user?locale=en-US&version=Cloud) and [List and Edit User Details](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/list-and-edit-user-details?locale=en-US&version=Cloud).

    > ### Note:  
    > The password lifetime for the CF provisioning user depends on the password policy set for the *SAP Business Technology Platform* application in the administration console of SAP Cloud Identity Services. For more information, see [Set a Password Policy for an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/set-password-policy-for-application?version=Cloud).

-   You have activated the account of the CF provisioning user by opening the *Profile Page* of SAP Cloud Identity Services, in a separate browser session, and changing its initial password. The URL has the following pattern: `https://<tenant ID>.accounts.ondemand.com` or `https://<tenant ID>.accounts.cloud.sap`
-   You have created the group *cf-user-provisioning* in your SAP Cloud Identity Services tenant and added the CF provisioning user to it. For more information, see [Create a New Group](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/create-new-user-group?locale=en-US&version=Cloud) and [Add Users to a Group](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/add-users-to-group?locale=en-US&version=Cloud).

-   You have added the CF provisioning user as org member with role **Org Manager** to each Cloud Foundry organization where you want to provision users, in the SAP BTP cockpit. For more information, see [Add Org Members](https://help.sap.com/docs/btp/sap-business-technology-platform/add-org-members-using-cockpit?locale=en-US&version=Cloud) and [About Roles in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/about-roles-in-cloud-foundry-environment?version=Cloud).




## Context

The Cloud Foundry environment enables you to create polyglot cloud applications in Cloud Foundry. It contains the SAP BTP, Cloud Foundry runtime service, which is based on the open-source application platform managed by the Cloud Foundry Foundation. For more information, see [Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/cloud-foundry-environment?version=Cloud).

When you enable the Cloud Foundry environment in your subaccount, the system automatically creates a Cloud Foundry organization for you. You can add platform users as org members and space members and assign roles to grant these users platform access.

In this scenario, your SAP Cloud Identity Services tenant acts as your identity provider and SAP BTP acts as your service provider. Identity Provisioning in between provides the SAP BTP Platform Members \(Cloud Foundry\) connector to replicate the org and space members with their role assignments from the identity provider to the local user storage of SAP BTP. For more information, see [SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario?version=Cloud).

SAP BTP Platform Members \(Cloud Foundry\) connector manages org and space members, as well as their role assignments, in the Cloud Foundry environment of a multi-environment subaccount, where a **single** SAP Cloud Identity Services tenant acts as custom identity provider. We recommend that you use the Identity Provisioning service enabled in this SAP Cloud Identity Services tenant.

> ### Note:  
> Identity Provisioning bundle tenants delivered before March 15, 2022, and Identity Provisioning standalone tenants delivered before September 1, 2020, run on SAP BTP, Neo environment. Customers with tenants on Neo environment are encouraged to migrate them to the SAP Cloud Identity Services infrastructure.
> 
> For more information, see [Migrate Identity Provisioning Bundle Tenant](https://help.sap.com/docs/identity-provisioning/identity-provisioning/migrate-identity-provisioning-bundle-tenant).

Follow the steps below to create SAP BTP Platform Members \(Cloud Foundry\) as a source system to read users \(org members and space members\), roles \(organization and space\), and role assignments from your Cloud Foundry environment, which can then be provisioned to target systems of your choice. In SAP BTP Platform Members \(Cloud Foundry\), groups correspond to roles in particular Cloud Foundry orgs or spaces, thus group members are user assignments of a role in a specific Cloud Foundry org or space.

> ### Note:  
> In case you have Cloud Foundry environment enabled in multiple Cloud Foundry landscapes or more than one SAP Cloud Identity Services tenants, you must configure a separate SAP BTP Platform Members \(Cloud Foundry\) connector for each of them.

The source system consumes User Account and Authentication API and Cloud Foundry V3 API provided by Cloud Foundry.



## Procedure

1.  To enable provisioning of platform users and user role assignments to and from Cloud Foundry environment, create a Support Ticket on component BC-CP-CF-SEC-IAM.

    Specify your SAP Cloud Identity Services tenant ID and the origin key of the trust configuration for BTP platform users which points to your SAP Cloud Identity Services tenant. You can find the origin key value in the SAP BTP cockpit. Go to your SAP BTP subaccount, choose *Trust Configuration* and see the value under *Origin Key* for the relevant *Custom Identity Provider for Platform Users*.

2.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

4.  Add *SAP BTP Platform Members \(Cloud Foundry\)* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

5.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Enter the `email` of the CF provisioning user \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for the CF provisioning user \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `btp.cf.pm.origin`
    
    </td>
    <td valign="top">
    
    Enter the origin key of your SAP Cloud Identity Services tenant \(see **Step 1**\).

    The value of this property is a string, which always ends with the suffix *\-platform*.

    It will be used as the *origin* attribute in the system transformation.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `btp.cf.pm.landscape`
    
    </td>
    <td valign="top">
    
    Enter the technical key of the landscape in which your multi-environment subaccount with enabled Cloud Foundry environment is located. For more information, see [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-and-api-endpoints-available-for-cloud-foundry-environment?version=Cloud).

    For example: `cf-eu10-002`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `btp.cf.pm.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP BTP Platform Members \(Cloud Foundry\) users matching the filter expression will be read.

    For example: *userName eq "SmithJ"*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `btp.cf.pm.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP BTP Platform Members \(Cloud Foundry\) groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `BTP_CF_PM_`

    When set in the source system, the prefix will be prepended to the name of the groups that are read from the SAP BTP Platform Members \(Cloud Foundry\) source system and will be provisioned to the target system with the following name pattern: <code>BTP_CF_PM_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP BTP Platform Members \(Cloud Foundry\) groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP BTP Platform Members \(Cloud Foundry\) groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.trace.failed.entity.content`
    
    </td>
    <td valign="top">
    
    If a provisioning job repeatedly fails and you need problem investigation, you can enable logging and tracing for the personal and sensitive data of your provisioned entities. To do this, set this property to *true*. For more information, see [List of Properties](list-of-properties-d6f3577.md).
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP Platform Members \(Cloud Foundry\)* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    -   **Mapping logic** – The behavior of the default transformation logic is to map all attributes from a SAP BTP Platform Members \(Cloud Foundry\) entity to the intermediate Identity Provisioning representation.
    -   **User offboarding** – If a user or a user assignment of a role has been deleted from the SAP BTP Platform Members \(Cloud Foundry\), this change is recognized, and the user/user assignment of a role is deleted from the target system too.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP BTP Platform Members \(Cloud Foundry\) system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [Cloud Foundry V3 API](https://v3-apidocs.cloudfoundry.org/version/3.178.0/index.html)

    > ### Caution:  
    > Keep in mind that when you add or delete users and user role assignments in SAP BTP Platform Members \(Cloud Foundry\), the operations order must adhere to the Cloud Foundry Environment hierarchy. In this case, you can expect the following behavior:
    > 
    > -   When adding a user as space member, it must already be present as member of the relevant organization with assigned role **Org User**. When deleting an org member, it should be first removed from the spaces of the relevant organization. In case you end up with erroneous entity structure, you can manually add or delete users via the administration console for SAP Cloud Identity Services.
    > 
    > -   When adding user role assignments, you should first add the org roles and afterwards proceed with the space roles. Also, when deleting user role assignments, you should first delete the space roles and then proceed with the org roles. If this condition is not fullfiled the job will finish with error. In that case, you can rerun the job until it finishes successfully.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.verified",
    >         "targetPath": "$.verified",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.origin",
    >         "targetPath": "$.origin",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.zoneId",
    >         "targetPath": "$.zoneId",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
    > 	   //The attribute group extension name is used to map the read users and user assignments of a role 
    > 	   //to the relevant Cloud Foundry organization or space.
    > 	   //the organization group extension name follows the pattern: <org_ID> <org_role>
    > 	   //the space group extension name follows the pattern: <org_ID> <space_ID> <space_role>
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:Group"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    > 	   //the organization group display name follows the pattern: <btp.cf.pm.group.prefix>_<btp.cf.pm.landscape>:<org_name>:<org_role>
    > 	  //the space group display name follows the pattern: <btp.cf.pm.group.prefix>_<btp.cf.pm.landscape>:<org_name>:<space_name>:<space_role>
    >         "functions": [
    >           {
    >             "condition": "'%btp.cf.pm.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%btp.cf.pm.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       },
    >       {
    >         "constant": "authorization",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >       },
    >       {
    >         "constant": "userOnlyMembership",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >       }
    >     ]
    >   }
    > }
    > ```

7.  Now, add a target system to which to provision users and user assignment of a role. For example: [Identity Authentication](identity-authentication-f217bd3.md)[Local Identity Directory](local-identity-directory-59557ae.md)

8.  \(Optional\) Run a *Simulate* and/or a *Validate* job before you run the actual provisioning job to verify that Identity Provisioning configurations produce the desired result in the target systems. For more information, see [Simulate Provisioning Jobs](Operation-Guide/simulate-provisioning-jobs-9d96db2.md) and [Validate Provisioning Jobs](Operation-Guide/validate-provisioning-jobs-fcaec67.md).




<a name="loio027324df5c2d471cb09514491565646b__postreq_krz_xpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario)

