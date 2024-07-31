<!-- loioe6a0606187b440199aeb1c56b11d9c9a -->

# SAP Ariba Category Management

Follow this procedure to set up SAP Ariba Category Management as а source system.



<a name="loioe6a0606187b440199aeb1c56b11d9c9a__prereq_gfl_gvx_rdb"/>

## Prerequisites

> ### Note:  
> Currently, SAP Ariba Category Management connector is only available for selected customers who are approached by SAP.

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

You have created an instance and generated a service key for the scim service plan of SAP Ariba Category Management. For more information, see [Creating a SAP Ariba Category Management SCIM Service Instance in Your Subaccount](https://help.sap.com/docs/categories/sap-ariba-category-management-configuration-guide/setting-up-user-replication?version=Latest).



## Context

SAP Ariba Category Management is a cloud-based solution that enables organizations to define and manage purchasing categories and provides actionable market intelligence, category insights, and various tools and templates for developing and operationalizing category strategies that drive business value and performance. This business solution is built on SAP Business Technology Platform \(BTP\). You can use Identity Provisioning to configure SAP Ariba Category Management as a source system where you can read users from and provision them to a target system.

> ### Note:  
> SAP Ariba Category Management does not support groups.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Ariba Category Management* as a source system. See: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL provided by the service key under the *scim-v1* field without adding the path information.
    
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
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `cm.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Ariba Category Management users matching the filter expression will be read. For example:

    -   *userName eq "SmithJ"*

    -   *emails.value eq "john.doe@example.com"*

    -   *emails.value eq "john.doe@example.com" or emails.value eq "john.d@example.com" or emails.value eq "j.doe@example.com"*



    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Ariba Category Management* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SCIM APIs for SAP Ariba Category Management](https://help.sap.com/docs/ariba/ariba-applications-wip/scim-apis-for-sap-ariba-category-management?state=DRAFT)

    **Mapping logic** – the behavior of the default transformation logic is to read all user attributes from the source SAP Ariba Category Management system, and then map them to the internal SCIM representation. It uses `entityIdSourceSystem` to store the unique ID of the identity.

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
    >             "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >             "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >             "optional": true
    >          },
    >          {
    >             "sourcePath":"$.name.givenName",
    >             "targetPath":"$.name.givenName",
    >             "optional":true
    >          },
    >          {
    >             "sourcePath":"$.name.familyName",
    >             "targetPath":"$.name.familyName",
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
    >             "sourcePath":"$.displayName",
    >             "targetPath":"$.displayName",
    >             "optional":true
    >          }
    >       ]
    >    }
    > }
    > ```

6.  Add a target system to provision users to it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loioe6a0606187b440199aeb1c56b11d9c9a__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[User Replication Setup](https://help.sap.com/docs/categories/sap-ariba-category-management-configuration-guide/sap-cloud-identity-services-setup?version=latest)

