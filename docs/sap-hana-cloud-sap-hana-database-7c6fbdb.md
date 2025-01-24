<!-- loio7c6fbdb3373f44a395c523508e9a70c7 -->

# SAP HANA Cloud, SAP HANA Database

Follow this procedure to set up SAP HANA Cloud, SAP HANA Database as a source system.



<a name="loio7c6fbdb3373f44a395c523508e9a70c7__prereq_tcl_444_kfb"/>

## Prerequisites

You have created a technical user for Identity Provisioning in the SAP HANA database with the OPERATOR and ROLE ADMIN system privileges. For more information, see [SAP Identity Provisioning Service](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/sap-identity-provisioning-service) → *Prerequisites*.



## Context

SAP HANA Cloud allows you to consume the SAP HANA database from cloud applications running on SAP Business Technology Platform, as well as from applications running elsewhere using the standard SAP HANA clients. Every instance of SAP HANA Cloud has its own single SAP HANA Database.

You can use Identity Provisioning to configure SAP HANA Cloud, SAP HANA Database as a source system where you can read users, roles and user role assignments from and provision them to target systems of your choice.

> ### Note:  
> In SAP HANA Cloud, SAP HANA Database, groups correspond to roles.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP HANA Cloud, SAP HANA Database* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    Enter: *BasicAuthentication* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.instance.type`
    
    </td>
    <td valign="top">
    
    Refers to the type of instance being configured or used within the SAP HANA Cloud.

    The value is set to *hdb* at system creation.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.instance.id`
    
    </td>
    <td valign="top">
    
    Refers to a unique identifier associated with a specific database instance within the SAP HANA Cloud.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.user.filter`
    
    </td>
    <td valign="top">
    
    \(Optional\) When specified, only those SAP HANA Cloud, SAP HANA Database users matching the filter expression will be read.

    Example: **name.familyName eq "Smith"**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hana.cloud.db.group.filter`
    
    </td>
    <td valign="top">
    
    \(Optional\) When specified, only those SAP HANA Cloud, SAP HANA Database roles matching the filter expression will be read.

    Example: **displayName eq "ProjectTeam1" or "Employees2020"**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL.

    For example: `https://demo-hc-3-test.authentication.sap.hana.ondemand.com/oauth/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, created for your SAP HANA Database system.
    
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
    
    Enter the SAP HANA Cloud, SAP HANA Database API URL.

    For example: `https://api.gateway.orchestration.<cluster>-<datacenter>.hanacloud.ondemand.com`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the OAuth Client Id, created for your SAP HANA Database system.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP HANA Cloud, SAP HANA Database* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    > ### Note:  
    > Given that the SAP HANA Database username attribute is immutable and the email is not supported, refer to [Handling Specific Attributes](handling-specific-attributes-e957782.md) for your provisioning scenarios, particularly with Identity Authentication.

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
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userId']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User']['authenticationDetails']['providerName']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User']['authenticationDetails']['providerName']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User']['userCategory']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User']['userCategory']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User']['authenticationDetails']['authenticationType']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap.hana.db:2.0:User']['authenticationDetails']['authenticationType']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true,
    >         "functions": [
    >           {
    >             "condition": "'%hana.cloud.db.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "display",
    >             "prefix": "%hana.cloud.db.group.prefix%"
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
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "'%hana.cloud.db.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%hana.cloud.db.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true
    >       }
    >     ]
    >   }
    > }
    > ```

    By default, Identity Provisioning reads group IDs and members. If you want the service to also read group descriptions, you can add an extra mapping to the *"group"* resource. To learn how, see [Guided Answers: Business Role Description](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:39660:40191).

6.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio7c6fbdb3373f44a395c523508e9a70c7__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[User Provisioning](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-administration-guide/user-provisioning)

