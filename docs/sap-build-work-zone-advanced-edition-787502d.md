<!-- loio787502df6ce14225b0e7cf7821e785eb -->

# SAP Build Work Zone, advanced edition

Follow this procedure to set up SAP Build Work Zone, advanced edition as a target system.



## Prerequisites

You have OAuth credentials for SAP Build Work Zone, advanced edition. To learn how, see [SAP Build Work Zone, advanced edition: Add an OAuth Client](https://help.sap.com/viewer/b03c84105ff74f809631e494bd612e83/Cloud/en-US/b3c804e1f999448b8011a475fea1da6c.html)



<a name="loio787502df6ce14225b0e7cf7821e785eb__context_zhf_2vx_ybb"/>

## Context

After fulfilling the prerequisites, follow the procedure below to create a target SAP Build Work Zone, advanced edition system to provision users and groups.

These target systems consume SCIM 2.0 API provided by SAP Build Work Zone, advanced edition.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Build Work Zone, advanced edition* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP Build Work Zone, advanced edition and configure the authentication method \(basic or OAuth certificate-based\).

    > ### Note:  
    > We recommend that you use OAuth certificate-based authentication in the regions where it is supported by SAP Build Work Zone, advanced edition. This authentication method is supported for subaccounts created on the recommended data centers for new customers according to the [SAP Build Work Zone, advanced edition documentation](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/prerequisites#create-a-subaccount).

    1.  In your newly added SAP Build Work Zone, advanced edition target system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](Operation-Guide/generate-and-manage-certificates-for-outbound-connection-76867db.md).

        Skip step **a.** if you want to use basic authentication.

        The next steps are performed in the SAP Build Work Zone, advanced edition Admin Console and are relevant for certificate-based authentication only.

    2.  Login to the SAP Build Work Zone, advanced edition Admin Console and execute substep *2. f. iii. Use X.509 Certificate-Based Authentication* from *Step 3: Configure the Identity Authentication service and the Identity Provisioning service* in [Option 1: Create a new tenant](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/run-configurator?locale=en-US#option-1%3A-create-a-new-tenant).


5.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Enter the URL related to your SAP Build Work Zone, advanced edition system, in format: `https://<account><sap_wz_domain>.workzone.ondemand.com`

    For example: *https://mytenant.mydomain123.workzone.ondemand.com*
    
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
    
    Enter your authentication method:

    -   *BasicAuthentication*

    -   *ClientCertificateAuthentication*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    Enter the OAuth client key, created for your SAP Build Work Zone, advanced edition tenant \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    \(Credential\) Enter the OAuth client secret, created for your SAP Build Work Zone, advanced edition tenant \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Build Work Zone, advanced edition instance, based on the configured authentication method:

    -   *BasicAuthentication* - `https://<account><sap_wz_domain>.workzone.ondemand.com/api/v1/auth/token` 

        For example: *https://myaccountmydomain123.workzone.ondemand.com/api/v1/auth/token*



    -   *ClientCertificateAuthentication* - `https://<company_uuid>.api-<region_host>.dws.workzone.ondemand.com/api/v2/auth/token` 

        > ### Note:  
        > The `api-` prefix before `<region_host>` is necessary for using *ClientCertificateAuthentication* authentication.

        For example: *https://mycompanyuuid123.api-eu-20.dws.workzone.ondemand.com/api/v2/auth/token*





    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `client_id`
    
    </td>
    <td valign="top">
    
    Valid if *ClientCertificateAuthentication* is configured as authentication method.

    Enter the OAuth Client id used for access token retrieval.
    
    </td>
    </tr>
    <tr>
    <td valign="top" align="center" colspan="2">
    
    **Optional Properties**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `workzone.content.type`
    
    </td>
    <td valign="top">
    
    This property makes the SAP Build Work Zone, advanced edition target system to send the specified value for the *Content-Type* HTTP header.

    Example: **application/json**

    Default value \(when not specified\): *application/scim+json*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `workzone.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This is a default property – it appears during system creation.

    Its default value is *true*. That means, when the Identity Provisioning identifies a changed entity in the source system, it will execute the updates as PATCH requests instead of PUT. That means, only the changes will be written in SAP Build Work Zone, advanced edition, instead of provisioning the whole entity data.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `workzone.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the SAP Build Work Zone, advanced edition target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

    Default value \(when not specified\): *userName*

    To learn more, see: [List of Properties](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/d6f3577f30ec4af98e734b0126a60e37.html)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `workzone.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If the Identity Provisioning tries to create a group that already exists on the SAP Build Work Zone, advanced edition target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

    Default value \(when not specified\): *displayName*

    To learn more, see: [List of Properties](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/d6f3577f30ec4af98e734b0126a60e37.html)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `workzone.include.if.match.wildcard.header`
    
    </td>
    <td valign="top">
    
    This property makes the SAP Build Work Zone, advanced edition target system to send the *If-Match* HTTP header with a value of “**\***” for every request to SAP Build Work Zone, advanced edition. This header could be used for entity versioning.

    Default value \(when not specified\): *false*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.failed.request.retry.attempts`
    
    </td>
    <td valign="top">
    
    Predefined value: *2*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.failed.request.retry.attempts.interval`
    
    </td>
    <td valign="top">
    
    Predefined value: *30*
    
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

6.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Build Work Zone, advanced edition* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Build Work Zone, advanced edition. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Build Work Zone SCIM API](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/user-and-user-list-provisioning-using-scim-api)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id",
    >                 "scope": "deleteEntity"
    >             },
    > 
    > // When a user is supposed to be deleted from SAP Work Zone, it actually has its status set to inactive instead of being deleted.
    >             {
    >                 "constant": false,
    >                 "targetPath": "$.active",
    >                 "scope": "deleteEntity"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >                 "targetPath": "$.schemas[1]"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:extension:sap:2.0:User",
    >                 "targetPath": "$.schemas[2]"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas",
    >                 "optional": true
    >             },
    >             {
    >                  "sourcePath": "$.userType",
    >                  "optional":true,
    >                  "targetPath": "$.userType"
    >             },
    >             {
    >                 "condition": "$.groups[?(@.value == 'Workzone_User_Type_public')] EMPTY false",
    >                 "constant": "public",
    >                 "targetPath": "$.userType"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "targetPath": "$.userName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "condition": "$.emails[0].length() > 0",
    >                 "constant": true,
    >                 "targetPath": "$.emails[0].primary"
    >             },
    >             {
    >                 "condition": "($.locale EMPTY false) && ($.addresses[?(@.type == 'work')].country EMPTY false)",
    >                 "sourcePath": "$.locale",
    >                 "targetPath": "$.locale",
    >                 "functions": [
    >                     {
    >                         "function": "toLowerCaseString"
    >                     },
    >                     {
    >                         "function": "concatString",
    >                         "suffix": "_"
    >                     },
    >                     {
    >                         "function": "concatString",
    >                         "suffix": "$.addresses[?(@.type == 'work')].country"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.title",
    >                 "targetPath": "$.title",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "optional": true,
    >                 "targetPath": "$.timezone"
    >             },
    >             {
    >                 "sourcePath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.addresses"
    >             },
    >             {
    >                 "condition": "$.addresses[?(@.type == 'work')].country EMPTY false",
    >                 "constant": true,
    >                 "targetPath": "$.addresses[1].primary"
    >             },
    >             {
    >                 "condition": "$.groups[?(@.value == 'Workzone_Admin')] EMPTY false",
    >                 "constant": "Administrator",
    >                 "targetPath": "$.roles[0].value"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >                 "optional": true,
    >                 "functions": [
    >                     {
    >                         "function": "resolveEntityIds"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['attributes']",
    >                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:JamCustomUser']['attributes']",
    >                 "optional": true
    >             }
    >         ]
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]",
    >                 "functions": [
    >                     {
    >                         "type": "resolveEntityIds"
    >                     }
    >                 ]
    >             }
    >         ]
    >     }
    > }
    >  
    > ```

7.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio787502df6ce14225b0e7cf7821e785eb__postreq_emv_vdb_kdb"/>

## Next Steps

1.  Before starting a provisioning job, you can first subscribe to the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during your jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
2.  Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

