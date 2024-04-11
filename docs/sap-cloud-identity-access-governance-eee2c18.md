<!-- loioeee2c1870eeb4209b46cd4976f7b8c40 -->

# SAP Cloud Identity Access Governance

Follow this procedure to set up SAP Cloud Identity Access Governance as a target system.



<a name="loioeee2c1870eeb4209b46cd4976f7b8c40__prereq_v1f_vr1_pzb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   You have created an instance and generated a service key for SAP Cloud Identity Access Governance. For more information, see [Initial Setup](https://help.sap.com/docs/SAP_CLOUD_IDENTITY_ACCESS_GOVERNANCE/e12d8683adfa4471ac4edd40809b9038/6809c3b49a1c474cb3ca00e35c21e6b8.html?version=CLOUDFOUNDRY) and [Creating Service Instances](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-service-instances?version=Cloud).

    The service key contains the API URL and the OAuth credentials \(`clientid` and `clientsecret`\) under the `uaa` property.

-   Provisioning HR events to SAP Cloud Identity Access Governance requires initial integration between SAP SuccessFactors and SAP Master Data Integration. For more information, see [Integrating SAP SuccessFactors Employee Central with SAP Master Data Integration](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL/634eabb3d94044d2b319aaf7a8f18fb9/00315e512acc4d07ad965de5c9d40547.html?version=latest)




<a name="loioeee2c1870eeb4209b46cd4976f7b8c40__context_y2y_nxx_rdb"/>

## Context

The SAP Cloud Identity Access Governance solution is built on the SAP Business Technology Platform \(SAP BTP\). It offers cloud services, such as Access Request Service, Access Analysis Service and Role Design Service which enable you to create access requests to business applications, analyze risks, and design roles. Last but not least, they help you implement HR-event driven identity lifecycle.

You can use Identity Provisioning to configure SAP Cloud Identity Access Governance as a target system for provisioning HR events. The HR events reflect the various stages of an employee’s lifecycle from hire to retire. For example: hire, termination, job change, position change. For more information, see [Events in Employee Central](https://help.sap.com/docs/SAP_SUCCESSFACTORS_EMPLOYEE_CENTRAL/b14dd15ca58f43e0856184a740a4b212/77bc104be8a64138aee4349f2241b286.html?version=latest). Based on the captured event, SAP Cloud Identity Access Governance decides whether to terminate user's permissions, give the user new permissions or change existing ones.

Currently, it is possible to read HR events only from SAP Master Data Integration. Configuring SAP Master Data Integration as a source system and linking it to SAP Cloud Identity Access Governance target system is only relevant for synchronizing HR events. Provisioning the user data for which the HR events apply is subject to customers’ implementation.

HR events are read with delta load marker so that SAP Cloud Identity Access Governance is aware of the previous and current instance of the event. The delta load marker is not deleted during system reset.



<a name="loioeee2c1870eeb4209b46cd4976f7b8c40__steps_w1f_vr1_pzb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Cloud Identity Access Governance* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL provided by the service key.
    
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
    
    Enter the user ID provided by the service key under *uaa* \> *clientid*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password provided by the service key under *uaa* \> *clientsecret*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL provided by the service key of your SAP Cloud Identity Access Governance instance. It follows the pattern: <code><i class="varname">&lt;uaa.url&gt;</i>/oauth/token</code>, where:

    -   *<uaa.url\>* is the URL provided by the service key under *uaa* \> *url*.

    -   `/oauth/token` is the suffix you need to add.



    
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

    Transformations are used to map the entity attributes \(in this case, HR events\) from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Cloud Identity Access Governance* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Cloud Identity Access Governance system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Cloud Identity Access Governance entity.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "event": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.instance.id",
    >         "optional": true,
    >         "targetVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "sourcePath": "$.instanceId",
    >         "optional": true,
    >         "targetVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "sourcePath": "$.previousInstance",
    >         "optional": true,
    >         "targetPath": "$.previousInstance",
    >         "hashing": false
    >       },
    >       {
    >         "sourcePath": "$.instance",
    >         "targetPath": "$.instance",
    >         "hashing": false
    >       },
    >       {
    >         "sourcePath": "$.versionId",
    >         "targetPath": "$.versionId"
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Add [SAP Master Data Integration](sap-master-data-integration-816385e.md) as a source system.




<a name="loioeee2c1870eeb4209b46cd4976f7b8c40__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Set Up Services](https://help.sap.com/docs/SAP_CLOUD_IDENTITY_ACCESS_GOVERNANCE/e12d8683adfa4471ac4edd40809b9038/1724d4e281d4455498b9c3b92ccf9033.html?version=CLOUDFOUNDRY)

