<!-- loioc135a52ce7b24d0dbd7b27fdc4a3d620 -->

# SAP BTP XS Advanced UAA \(Cloud Foundry\)

Follow this procedure to set up the SAP BTP XS Advanced UAA \(running on SAP BTP, Cloud Foundry environment\) as а source system.



<a name="loioc135a52ce7b24d0dbd7b27fdc4a3d620__prereq_rjs_2yp_wy"/>

## Prerequisites

You have created credentials to call the REST APIs of the SAP Authorization and Trust Management service on global account, subaccount, or directory level. For more information, see: [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis) and [btp create security/api-credential](https://help.sap.com/docs/btp/btp-cli-command-reference/btp-create-security-api-credential).



<a name="loioc135a52ce7b24d0dbd7b27fdc4a3d620__context_jgv_gc1_123"/>

## Context

The SAP BTP XS Advanced UAA connector enables you to read platform users, business users, groups and group assignments from the local user stores of global accounts, directories, and multi-environment subaccounts on SAP BTP. These users and groups \(considered role collections in SAP BTP\), can then be provisioned to target systems of your choice.

Create a separate source system for each global account, subaccount and directory, and configure the respective credentials and connectivity properties. Depending from where you want to read your entities, you need to:

-   Create a source system for the global account to provision **platform users** and groups.

-   Create a source system for the directory to provision **platform users** and groups.

-   Create a source system for the subaccount to provision **platform users**, **business users** and groups.


> ### Note:  
> Reading of platform users as **org members** and **space members** requires the usage of a different connector: SAP BTP Platform Members \(Cloud Foundry\). For more information, see [SAP BTP Platform Members \(Cloud Foundry\)](sap-btp-platform-members-cloud-foundry-f5cefa9.md).

Follow the steps below to create SAP BTP XS Advanced UAA as a source system to read SAP BTP users and groups from global accounts, directories, and multi-environment subaccounts on SAP BTP.



<a name="loioc135a52ce7b24d0dbd7b27fdc4a3d620__steps_cyl_j21_qfb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP BTP XS Advanced UAA \(Cloud Foundry\)* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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

    For more information, see [Call an API](https://help.sap.com/docs/btp/sap-business-technology-platform/call-api?version=Cloud).
    
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

    -   <code>https://<i class="varname">&lt;subaccount_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code> or

    -   <code>https://<i class="varname">&lt;directory_subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code> or


    For more information, see [Call an API](https://help.sap.com/docs/btp/sap-business-technology-platform/call-api?version=Cloud).
    
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
    
    `xsuaa.origin.filter.enabled`
    
    </td>
    <td valign="top">
    
    This flag property depends on `xsuaa.origin`. Possible values: **true** or **false**

    -   If set to *true*, the Identity Provisioning service will read only users whose identity provider is set as a value of `xsuaa.origin`.
    -   If set to *false*, the Identity Provisioning service will read all users, regardless of their origin.
    -   If set to *true* but the `xsuaa.origin` property is missing, the provisioning job will fail.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `xsuaa.origin`
    
    </td>
    <td valign="top">
    
    Enter the Origin Key of your identity provider. This is needed only when the `xsuaa.origin.filter.enabled` property is set to *true*.

    -   Identity provider for platform users:

        In the SAP BTP cockpit, go to your global account \(see [Navigate in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-in-cockpit?version=Cloud)\), choose *Security* \> *Trust Configuration* and copy the *Origin Key* value used for platform users. This origin key always ends with `-platform`.

    -   Identity provider for business users:

        In the SAP BTP cockpit, go to your subaccount \(see [Navigate in the Cockpit](https://help.sap.com/docs/btp/sap-business-technology-platform/navigate-in-cockpit?version=Cloud)\), choose *Security* \> *Trust Configuration* and copy the *Origin Key* value used for business \(application\) users. For example: sap.custom


    > ### Note:  
    > If multiple origins are configured, a user will be read multiple times - once per origin - but only one user will be created in the target. For more information, see [Configure Single and Multiple Origins](configure-single-and-multiple-origins-eb966c3.md)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `xsuaa.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP BTP XS Advanced UAA \(Cloud Foundry\) groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `XSUAA_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `XSUAA_` prefix in their display name will be provisioned to SAP BTP XS Advanced UAA \(Cloud Foundry\). Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP BTP XS Advanced UAA \(Cloud Foundry\).
    
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

    `xsuaa.origin.filter.enabled`=*true*
    
    </td>
    </tr>
    </table>
    
5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP Advanced UAA* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    -   **Mapping logic** – The behavior of the default transformation logic is to map all attributes from an SAP BTP XS Advanced UAA entity to the intermediate Identity Provisioning representation.
    -   **User offboarding** – If a user or group has been deleted from the SAP BTP XS Advanced UAA, this change is recognized and the user/group is deleted in the target system too.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP BTP XS Advanced UAA system. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md) and the API documentation.

    -   [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/resource/SCIM_groups_role_collections)- SCIM groups - role collections

    -   [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/resource/SCIM_users_shadow_users) - SCIM users - shadow users


    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
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
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >           {
    >             "condition": "'%xsuaa.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "display",
    >             "prefix": "%xsuaa.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "targetPath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
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
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
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
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "'%xsuaa.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%xsuaa.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    >       },
    >       {
    >         "sourcePath": "$.description",
    >         "targetPath": "$.description",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.zoneId",
    >         "targetPath": "$.zoneId",
    >         "optional": true
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
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >       }
    >     ]
    >   }
    > }
    > 
    > ```

6.  Add a target system to which to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loioc135a52ce7b24d0dbd7b27fdc4a3d620__postreq_krz_xpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Authorization and Trust Management Service](https://help.sap.com/docs/authorization-and-trust-management-service?locale=en-US&version=Cloud)

[btp CLI Command Reference](https://help.sap.com/docs/btp/btp-cli-command-reference/btp-cli-command-reference)

[SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario?version=Cloud)

