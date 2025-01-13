<!-- loioc135a52ce7b24d0dbd7b27fdc4a3d620 -->

# SAP BTP XS Advanced UAA \(Cloud Foundry\)

Follow this procedure to set up the SAP BTP XS Advanced UAA \(running on SAP BTP, Cloud Foundry environment\) as а source system.



<a name="loioc135a52ce7b24d0dbd7b27fdc4a3d620__prereq_rjs_2yp_wy"/>

## Prerequisites

-   You have created the API credentials which enable you to access the APIs of SAP Authorization and Trust Management service. For more information, see [Accessing Administration Using APIs of the SAP Authorization and Trust Management Service](https://help.sap.com/docs/btp/sap-business-technology-platform/accessing-administration-using-apis-of-sap-authorization-and-trust-management-service?version=Cloud).

-   You have a global account in SAP BTP cockpit with a multi-environment subaccount and Cloud Foundry applications for which you have been subscribed.




<a name="loioc135a52ce7b24d0dbd7b27fdc4a3d620__context_jgv_gc1_123"/>

## Context

In simple terms, XS Advanced is basically the Cloud Foundry open-source PaaS with a number of tweaks and extensions provided by SAP. These SAP enhancements include integration with the SAP HANA database, OData support, compatibility with XS classic model, and some additional features designed to improve application security. XS Advanced also provides support for business applications that are composed of multiple micro-services, also known as multi-target applications.

SAP BTP XS Advanced UAA is responsible for the connection of identity providers with business users \(for applications\). SAP BTP XS Advanced UAA provides authorizations on application level:*role collections*, *roles*, *attributes*, and *role templates*. To learn more, see: [What Is the SAP Authorization and Trust Management Service?](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/649961f8d4ad463daca33b3a20deba4c.html)

Follow the steps below to create SAP BTP XS Advanced UAA as a source system to read SAP BTP users and groups from your Cloud Foundry applications, which can then be provisioned to a certain target system.

These source systems consume SCIM 1.1 API provided by SAP BTP XS Advanced UAA.



<a name="loioc135a52ce7b24d0dbd7b27fdc4a3d620__steps_cyl_j21_qfb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP BTP XS Advanced UAA \(Cloud Foundry\)* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the API URL in the following format:

    <code>https://api.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com</code>

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

    <code>https://<i class="varname">&lt;my-subdomain&gt;</i>.authentication.<i class="varname">&lt;region&gt;</i>.hana.ondemand.com/oauth/token</code>

    For more information, see [Call an API](https://help.sap.com/docs/btp/sap-business-technology-platform/call-api?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the OAuth client ID you have created as a prerequisite.

    For more information, see [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth client secret you have created as a prerequisite.

    For more information, see [Get Access to the APIs](https://help.sap.com/docs/btp/sap-business-technology-platform/get-access-to-apis?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `xsuaa.origin`
    
    </td>
    <td valign="top">
    
    Enter the location of your identity provider. To do this:

    1.  Open your SAP BTP cockpit.
    2.  Go to your Cloud Foundry global account and choose your subaccount.
    3.  From the left-side navigation, choose *Trust Configuration*.
    4.  Copy/paste the *Origin Key* value.

    This value will be used as the *origin* attribute in the system transformation.

    For more information, see [Configure Single and Multiple Origins](configure-single-and-multiple-origins-eb966c3.md).
    
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

    `User`=*MyXSUAAuser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `xsuaa.origin`=*myaccount-xsuaa.accounts.ondemand.com*

    `xsuaa.origin.filter.enabled`=*true*
    
    </td>
    </tr>
    </table>
    
5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP Advanced UAA* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    -   **Mapping logic** – The behavior of the default transformation logic is to map all attributes from an SAP BTP XS Advanced UAA entity to the intermediate Identity Provisioning representation.
    -   **User offboarding** – If a user or group has been deleted from the SAP BTP XS Advanced UAA, this change is recognized and the user/group is deleted in the target system too.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP BTP XS Advanced UAA system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/resource/SCIM_groups_role_collections)- SCIM groups - role collections

    [User Management \(System for Cross-domain Identity Management \(SCIM\)\)](https://api.sap.com/api/PlatformAPI/resource/SCIM_users_shadow_users) - SCIM users - shadow users

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
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
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
    >         "sourcePath": "$.meta",
    >         "targetPath": "$.meta",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >             "function": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       }
    >     ]
    >   }
    > }
    > 
    > ```

6.  Now, add a target system to which to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loioc135a52ce7b24d0dbd7b27fdc4a3d620__postreq_krz_xpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[XS CLI: User Administration](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/latest/en-US/4b38012ac63141bfa15bc1cb6418cc6a.html)

