<!-- loioecddce6d325e41b49089d4f3a2ce9a18 -->

# SAP BTP XS Advanced UAA \(Cloud Foundry\)

Follow this procedure to set up the SAP BTP XS Advanced UAA \(running on SAP BTP, Cloud Foundry environment\) as а target system.



<a name="loioecddce6d325e41b49089d4f3a2ce9a18__prereq_rjs_2yp_wy"/>

## Prerequisites

You have created credentials to call the REST APIs of the SAP Authorization and Trust Management service on global account, subaccount, or directory level. For more information, see: [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis) and [btp create security/api-credential](https://help.sap.com/docs/btp/btp-cli-command-reference/btp-create-security-api-credential).



<a name="loioecddce6d325e41b49089d4f3a2ce9a18__context_jgv_gc1_123"/>

## Context

The SAP BTP XS Advanced UAA connector enables you to provision platform users, business users, groups and group assignments to the local user stores of global accounts, directories, and multi-environment subaccounts on SAP BTP. These users and groups \(considered role collections in SAP BTP\), are typically read from source systems, such as identity providers like SAP Cloud Identity Services.

Create a separate target system for each global account, subaccount and directory, and configure the respective credentials and connectivity properties. Depending on where you want to provision your entities, you need to:

-   Create a target system for the global account to provision **platform users** and groups.

-   Create a target system for the directory to provision **platform users** and groups.

-   Create a target system for the subaccount to provision **platform users**, **business users** and groups.


> ### Note:  
> Provisioning of platform users as **org members** and **space members** requires the usage of a different connector: SAP BTP Platform Members \(Cloud Foundry\). For more information, see [SAP BTP Platform Members \(Cloud Foundry\)](sap-btp-platform-members-cloud-foundry-f5cefa9.md).

Creating, updating, and deleting groups follow the standard processes. If groups exist in the source but do not exist in the target, Identity Provisioning will create them. If groups have been changed or deleted in the source, Identity Provisioning will update or delete them accordingly. Deleting involves deassigning the group members and deleting the group itself.

Follow the steps below to create SAP BTP XS Advanced UAA as a target system to provision SAP BTP users and groups to global accounts, directories, and multi-environment subaccounts on SAP BTP.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP BTP Advanced UAA \(Cloud Foundry\)* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Choose the *Properties* tab to configure the connection settings for your system.

    > ### Note:  
    > If your Identity Provisioning tenant is running on SAP BTP, Neo environment, you can create a [connectivity destination](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/72696d6d06c0490394ac3069da600278.html) in your subaccount in the SAP BTP cockpit, and then select it from the *Destination Name* combo box in your Identity Provisioning User Interface.
    > 
    > If one and the same property exists both in the cockpit and in the *Properties* tab, the value set in the *Properties* tab is considered with higher priority.
    > 
    > We recommend that you use the *Properties* tab. Use a connectivity destination only if you need to reuse one and the same configuration for multiple provisioning systems.

    **Properties**


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
    
    Enter the API URL in the following format:

    <code>https://api.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com</code> or

    <code>https://api.authentication.<i class="varname">&lt;region&gt;</i>.accounts.cloud.sap</code>

    For more information, see [Call an API](https://help.sap.com/docs/btp/sap-business-technology-platform/call-api?version=Cloud).

    > ### Restriction:  
    > The `accounts.cloud.sap` domain is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.


    
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
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL to the OAuth2 token service in the following format:

    -   <code>https://<i class="varname">&lt;global_account_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code> or

        <code>https://<i class="varname">&lt;global_account_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.accounts.cloud.sap/oauth/token</code>

    -   <code>https://<i class="varname">&lt;subaccount_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code> or

        <code>https://<i class="varname">&lt;subaccount_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.accounts.cloud.sap/oauth/token</code>

    -   <code>https://<i class="varname">&lt;directory_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code> or

        <code>https://<i class="varname">&lt;directory_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.accounts.cloud.sap/oauth/token</code>


    For more information, see [Call an API](https://help.sap.com/docs/btp/sap-business-technology-platform/call-api?version=Cloud).

    > ### Restriction:  
    > The `accounts.cloud.sap` domain is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the respective OAuth client ID that was generated when you created credentials for each global account, subaccount and directory.

    For more information, see [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the respective OAuth client secret that was generated when you created credentials for each global account, subaccount and directory.

    For more information, see [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `xsuaa.origin`
    
    </td>
    <td valign="top">
    
    Enter the Origin Key of your identity provider.

    -   Identity provider for platform users:

        In the SAP BTP cockpit, go to your global account \(see [Navigate in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-in-cockpit?version=Cloud)\), choose *Security* \> *Trust Configuration* and copy the *Origin Key* value used for platform users. This origin key always ends with `-platform`.

    -   Identity provider for business users:

        In the SAP BTP cockpit, go to your subaccount \(see [Navigate in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-in-cockpit?version=Cloud)\), choose *Security* \> *Trust Configuration* and copy the *Origin Key* value used for business \(application\) users. For example: sap.custom


    > ### Note:  
    > If multiple origins are configured, the user will be created multiple times, once per origin. For more information, see [Configure Single and Multiple Origins](configure-single-and-multiple-origins-aeaab63.md)


    
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

    Exemplary destination:


    <table>
    <tr>
    <td valign="top">
    
    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `ProxyType`=*Internet*

    `URL`=*https://api.authentication.eu10.hana.ondemand.com*

    `OAuth2TokenServiceURL`=*https://myaccount.authentication.eu10.hana.ondemand.com/oauth/token*

    `User`=*sb-full-access!a76125*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `xsuaa.origin`=*sap.custom*
    
    </td>
    </tr>
    </table>
    
5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP Advanced UAA* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    -   **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the intermediate Identity Provisioning representation to the SAP BTP XS Advanced UAA target attributes.
    -   **User offboarding** – If a user has been deleted from the source system, this change is recognized and the user is deleted in the SAP BTP XS Advanced UAA target system too.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP BTP XS Advanced UAA system. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md) and the API documentation.

    -   [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/resource/SCIM_groups_role_collections)- SCIM groups - role collections

    -   [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/resource/SCIM_users_shadow_users) - SCIM users - shadow users


    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "isValidEmail($.emails[0].value) && (('%xsuaa.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%xsuaa.group.prefix%.*/)] empty false))",
    >     "mappings": [
    >       {
    >         "constant": "xsuaa-dummy-value",
    >         "targetPath": "$.id",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "defaultValue": true,
    >         "optional": true
    >       },
    >       {
    >         "scope": "createEntity",
    >         "constant": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.verified",
    >         "targetPath": "$.verified",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
    >         "targetPath": "$.verified",
    >         "optional": true
    >       },
    >       {
    >         "scope": "createEntity",
    >         "constant": true,
    >         "targetPath": "$.verified"
    >       },
    >       {
    >         "constant": "%xsuaa.origin%",
    >         "targetPath": "$.origin"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "targetPath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value == []",
    >         "targetPath": "$.emails[0].primary",
    >         "constant": true
    >       },
    >       {
    >         "constant": "urn:scim:schemas:core:1.0",
    >         "targetPath": "$.schemas[0]"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, xsuaa.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], xsuaa.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "targetVariable": "entityIdTargetSystem",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, xsuaa.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%xsuaa.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.description",
    >         "targetPath": "$.description",
    >         "optional": true
    >       },
    >       {
    >         "constant": "urn:scim:schemas:core:1.0",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members",
    >         "functions": [
    >           {
    >             "function": "resolveEntityIds"
    >           }
    >         ]
    >       },
    >       {
    >         "constant": "USER",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[*].type",
    >         "optional": true
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loioecddce6d325e41b49089d4f3a2ce9a18__postreq_krz_xpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Authorization and Trust Management Service](https://help.sap.com/docs/authorization-and-trust-management-service?locale=en-US&version=Cloud)

[btp CLI Command Reference](https://help.sap.com/docs/btp/btp-cli-command-reference/btp-cli-command-reference)

[SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario?version=Cloud)

