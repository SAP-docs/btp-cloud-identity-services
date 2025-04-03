<!-- loio816385e4afd242e388ca8c8bcf04dfbe -->

# SAP Master Data Integration

Follow this procedure to set up SAP Master Data Integration \(in short, MDI\) as a source system.



<a name="loio816385e4afd242e388ca8c8bcf04dfbe__prereq_c1j_nxx_rdb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created a tenant in a subaccount on SAP BTP, Cloud Foundry environment. You can create your own tenant \(free of charge\), or integrate with an existing one.
-   You have created a service instance for MDI in the subaccount in order to connect a new system to your tenant and read user account information from it. To learn how, see: [Creating Service Instances](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8221b7434d8e484fab5ec5d219b7bf64.html) 
-   You have created a service key in this instance, which contains the necessary credentials to connect to the MDI service. Creating multiple service keys in the same service instance is not supported. To learn how, see: [Creating service Instances](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8221b7434d8e484fab5ec5d219b7bf64.html)

    > ### Tip:  
    > The *serviceKey* payload provides you with the following properties that you will later need for your system configuration:
    > 
    > -   **uri** =`URL`
    > -   **uaa.url** = `OAuth2TokenServiceURL`
    > -   **uaa.clientid** = `User`
    > -   **clientsecret** = `Password`




<a name="loio816385e4afd242e388ca8c8bcf04dfbe__context_y2y_nxx_rdb"/>

## Context

As part of SAP’s data model and integration unification strategy, SAP BTP Integration Suite has *Master Data Integration* to enable a harmonized integration and distribution of different master data objects and data between SAP solutions. This includes master data for business partners, cost centers, and workforce data. Workforce data is provided for integration scenarios that need data from SAP SuccessFactors Employee Central or other HR systems.

To learn more, see: [Integrating SAP SuccessFactors Employee Central with SAP Master Data Integration](https://help.sap.com/viewer/634eabb3d94044d2b319aaf7a8f18fb9/latest/en-US/00315e512acc4d07ad965de5c9d40547.html)

You can use Identity Provisioning to configure SAP Master Data Integration as a source system for provisioning of users and HR events to a target system of your choice. The HR events reflect the various stages of an employee’s lifecycle from hire to retire. For example: hire, termination, job change, position change. For more information, see [Events in Employee Central](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL/b14dd15ca58f43e0856184a740a4b212/77bc104be8a64138aee4349f2241b286.html?version=latest).

HR events are read with delta load marker so that the target system is aware of the previous and current instance of the event. The delta load marker is deleted during system reset.



<a name="loio816385e4afd242e388ca8c8bcf04dfbe__steps_hr4_myx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Master Data Integration* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL to the relevant integration application running in the relevant region of SAP Business Technology Platform.

    See the **Prerequisites** section → *serviceKey* tip.
    
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
    
    Enter the technical user that has access to the API of your MDI service.

    See the **Prerequisites** section → *serviceKey* tip.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for this technical user.

    See the **Prerequisites** section → *serviceKey* tip.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL` 
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL.

    See the **Prerequisites** section → *serviceKey* tip.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Master Data Integration* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your MDI source system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [Field Mapping Between Employee Central and SAP Master Data Integration](https://help.sap.com/viewer/634eabb3d94044d2b319aaf7a8f18fb9/latest/en-US/8d71b5bac47649f5a7481d079e39f0f9.html)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:sfsf:2.0:User']['personGUID']",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.profileDetail[0].content.scriptedProfileDetails[0].firstName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.profileDetail[0].content.scriptedProfileDetails[0].lastName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.profileDetail[0].content.scriptedProfileDetails[0].middleName",
    >         "targetPath": "$.name.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.userAccount.userName",
    >         "targetPath": "$.userName",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "constant": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.isDefault == true)].address",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "targetPath": "$.emails[*].usage",
    >         "type": "remove"
    >       },
    >       {
    >         "targetPath": "$.emails[*].address",
    >         "type": "rename",
    >         "constant": "value"
    >       },
    >       {
    >         "targetPath": "$.emails[*].isDefault",
    >         "type": "rename",
    >         "constant": "primary"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:User",
    >           "urn:sap:cloud:scim:schemas:extension:sfsf:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       }
    >     ]
    >   },
    >   "event": {
    >     "ignore": true,
    >     "condition": "($.instance.id EMPTY false) || ($.instanceId EMPTY false)",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.instance.id",
    >         "optional": true,
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.instanceId",
    >         "optional": true,
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$",
    >         "targetPath": "$"
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Now, add a target system to provision users into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio816385e4afd242e388ca8c8bcf04dfbe__postreq_wss_rpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

[SAP Community: The New Master Data Integration Service for SAP SuccessFactors](https://blogs.sap.com/2020/05/26/the-new-master-data-integration-service-for-sap-successfactors/)

