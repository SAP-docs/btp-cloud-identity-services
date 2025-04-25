<!-- loio2c0c2775a5224fbbbf6909277579b433 -->

# SAP SuccessFactors Learning

Follow this procedure to set up SAP SuccessFactors Learning as a target system.



<a name="loio2c0c2775a5224fbbbf6909277579b433__prereq_gc2_vs2_jrb"/>

## Prerequisites

You have created a technical user with administrator permissions that will be used to call the SAP SuccessFactors Learning API for provisioning user information.



<a name="loio2c0c2775a5224fbbbf6909277579b433__context_y2y_nxx_rdb"/>

## Context

SAP SuccessFactors Learning is a learning solution which helps organizations to improve employee skills and talent management, align learning outcomes with performance goals, boost compliance, and train external audiences.

You can use the Identity Provisioning user interface \(UI\) to configure SAP SuccessFactors Learning as a target system where you can provision users from source systems.

> ### Restriction:  
> Provisioning **groups** is not supported.



<a name="loio2c0c2775a5224fbbbf6909277579b433__steps_hc2_vs2_jrb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP SuccessFactors Learning* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify the URL to the API of your SAP SuccessFactors Learning system. It follows the pattern: <code>https://<i class="varname">&lt;root URL&gt;</i>/learning/public-api/rest/admin/Integration.svc/ias</code> 
    
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
    
    Enter the technical user ID for SAP SuccessFactors Learning.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for the SAP SuccessFactors Learning technical user. For more information, see [Learning Technical User](https://help.sap.com/docs/SAP_SUCCESSFACTORS_LEARNING/82cf7c83c7db42a8aa1d3bbdbc39e93d/8009aa4bef254d3da888aa864528c695.html).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `lms.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    This property appears by default when the system is created, and its value is set to *userName*.

    It defines by which unique attribute\(s\) an existing user to be resolved in the event of conflicting users.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `lms.support.patch.operation`
    
    </td>
    <td valign="top">
    
    Controls how modified users in the source system are updated in the target system.

    -   If set to *true*, PATCH operations are used to update users in the target system.

    -   If set to *false*, PUT operations are used to update users in the target system.



    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP SuccessFactors Learning* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP SuccessFactors Learning system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Business Accelerator Hub: SAP SuccessFactors Learning](https://api.sap.com/package/SuccessFactorsLMSCurriculawithSAPHCMQualification?section=Overview)

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP SuccessFactors Learning entity.

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": ["urn:ietf:params:scim:schemas:core:2.0:User","urn:sap:cloud:scim:schemas:extension:custom:2.0:User","urn:ietf:params:scim:schemas:extension:sap:2.0:User"],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.locale",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['siteID']",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['siteID']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.custom-column-path-1",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['110']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.custom-column-path-2",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['120']",
    >         "optional": true
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary== true)] empty false",
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails[?(@.value)]"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary== true)] empty true",
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.emails[0].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "targetPath": "$.name.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "condition": "$.phoneNumbers[?(@.primary== true)] empty false",
    >         "sourcePath": "$.phoneNumbers[?(@.primary== true)].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[?(@.value)]"
    >       },
    >       {
    >         "condition": "$.phoneNumbers[?(@.primary== true)] empty true",
    >         "sourcePath": "$.phoneNumbers[0].value",
    >         "targetPath": "$.phoneNumbers[0].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
    >       }
    >     ]
    >   }
    > }
    > ```

6.  Add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio2c0c2775a5224fbbbf6909277579b433__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

