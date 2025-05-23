<!-- loiof34f0be140f448639a1e543110ee0cd5 -->

# SAP SuccessFactors Learning

Follow this procedure to set up SAP SuccessFactors Learning as а source system.



<a name="loiof34f0be140f448639a1e543110ee0cd5__prereq_gfl_gvx_rdb"/>

## Prerequisites

You have created a technical user with administrator permissions that will be used to call the API of SAP SuccessFactors Learning for reading user information.



## Context

SAP SuccessFactors Learning is a learning solution which helps organizations to improve employee skills and talent management, align learning outcomes with performance goals, boost compliance, and train external audiences.

You can use Identity Provisioning to configure SAP SuccessFactors Learning as a source system where you can read **users** from and provision them to a target system.

When users from SAP SuccessFactors Learning source system, are provisioned to Identity Authentication target system, all newly created users get the *userUUID* attribute generated by Identity Authentication. The Identity Provisioning in its turn sends the *userUUID* back to SAP SuccessFactors Learning to update the users.

> ### Restriction:  
> Reading *groups* is not supported.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP SuccessFactors Learning* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    \(Optional\) `lms.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those users matching the filter expression will be read.

    **Possible values:**

    -   *userName eq "testName"*

    -   *externalID eq "testID"*

    -   *active eq "true"*

    -   *sourceSystem eq "Learning"* - indicates that the user is created directly in SAP SuccessFactors Learning with no involvement of Identity Provisioning.

    -   *sourceSystem eq "Identity Provisioning"* - indicates that the user is created in SAP SuccessFactors Learning by Identity Provisioning.



    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    The Identity Provisioning offers a default transformation for the *SAP SuccessFactors Learning* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    The behavior of the default transformation logic is to read all user attributes from the source SAP SuccessFactors Learning system, and then map them to the internal SCIM representation. It uses `entityIdSourceSystem` to store the unique ID of the identity.

    You can change the default transformation mapping rules depending on your setup of entities in your SAP SuccessFactors Learning. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Business Accelerator Hub: SAP SuccessFactors Learning](https://api.sap.com/package/SuccessFactorsLMSCurriculawithSAPHCMQualification?section=Overview)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
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
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "optional": true,
    >         "targetPath": "$.locale"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['siteID']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['siteID']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['sourceSystem']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['sourceSystem']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['applicationID']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['applicationID']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['110']",
    >         "optional": true,
    >         "targetPath": "$.custom-column-path-1"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['120']",
    >         "optional": true,
    >         "targetPath":  "$.custom-column-path-2"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
    > 						
    >       }
    >     ]
    >   }
    > }
    > ```

    > ### Tip:  
    > Your main scenario with this source connector might be provisioning SAP SuccessFactors Learning users to SAP Cloud Identity Service – Identity Authentication. In this case, you can add the following **condition** at the beginning of the "user" resource since *emails* and *name.familyName* are mandatory attributes for Identity Authentication users.
    > 
    > ```
    > 
    > {
    >   "user": {
    > 
    > "condition": "($.emails[0].value EMPTY false) && ($.name.familyName EMPTY false)",
    >     "mappings": [
    >       ...
    > ```

    > ### Note:  
    > When SAP SuccessFactors Learning users are provisioned to Identity Authentication, the service generates a user UUID for every newly created user. Within the same provisioning job, Identity Provisioning returns the user UUID back to SAP SuccessFactors Learning and updates the *userUUID* attribute.
    > 
    > Identity Provisioning updates *userUUID* when its value is *null* or when its value already exists. The latter is valid in cases where, for example, a user is deleted in the Identity Authentication target system and after running a Resync Job, the deleted user is created again. A new user UUID is generated which updates the old value in SAP SuccessFactors Learning.
    > 
    > Returning the user UUID back to SAP SuccessFactors Learning and updating the *userUUID* attribute is supported for standard and real-time provisioning scenarios. It is also supported in bulk scenarios, when bulk operations are enabled on the Identity Authentication target system.

6.  Now, add a target system to provision users to it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loiof34f0be140f448639a1e543110ee0cd5__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP SuccessFactors Learning](https://www.sap.com/products/corporate-lms/technical-information.html)

