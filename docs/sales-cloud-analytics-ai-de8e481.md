<!-- loiode8e481f1ad34ea7910c4f2591d592b8 -->

# Sales Cloud – Analytics & AI

Follow this procedure to set up Sales Cloud – Analytics & AI as a source system.



<a name="loiode8e481f1ad34ea7910c4f2591d592b8__prereq_rdf_ntd_r3b"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

You have technical user credentials for an Sales Cloud – Analytics & AI \(in short, *SCAAI*\) system with read and write access permissions.



## Context

After fulfilling the prerequisites, follow the procedure to add a source system for Sales Cloud – Analytics & AI to read users and user assignments to groups. This source system consumes SCIM 2.0 API provided by SCAAI.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *Sales Cloud – Analytics & AI* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify the URL to the SCIM API portal of your SCAAI system.
    
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
    
    Enter the user for your SCAAI system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for your SCAAI user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL to the OAuth2 token service.

    If not sure about the exact URL, ask your SCAAI administrator.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`sales.cloud.analytics_ai.group.filter`
    
    </td>
    <td valign="top">
    
    Enter a group filter criteria, according to the API syntax of SCAAI.

    For example: **displayName eq "first\_group"**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`sales.cloud.analytics_ai.user.filter`
    
    </td>
    <td valign="top">
    
    Enter a user filter criteria, according to the API syntax of SCAAI.

    For example: **externalId eq "John123"**
    
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

    `URL`=*http://myscaai:8080/scim\_services*

    `User`=*MySCAAIUser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `OAuth2TokenServiceURL`=*http://myscaai:8080/gateway\_services/api/auth/ips/token* 
    
    </td>
    </tr>
    </table>
    
5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Sales Cloud – Analytics & AI* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SCAAI system. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    The behavior of the default transformation logic is to read all user attributes from the source SCAAI system, and then map them to the internal SCIM representation. It uses `entityIdSourceSystem` to store the unique ID of the identity.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional" : true
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$.groups[*].display"
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$.groups[*].ref"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true,
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members"
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$.members[*].$ref"
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$.members[*].display"
    >             }
    >         ]
    >     }
    > }
    > 
    > ```

6.  Now, add a target system to provision users and their group assignments to it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loiode8e481f1ad34ea7910c4f2591d592b8__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

