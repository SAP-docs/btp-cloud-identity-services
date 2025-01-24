<!-- loioeb95de0358124c8d944ec0ad190ba905 -->

# SAP Datasphere

Follow this procedure to set up SAP Datasphere as a target system.



<a name="loioeb95de0358124c8d944ec0ad190ba905__prereq_kqy_lfd_pcc"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   In SAP Datasphere, you have enabled a custom SAML Identity Provider, for which *User Attribute* is set to **Custom SAML User Mapping**. To learn how, see: [Enabling a Custom SAML Identity Provider](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/9b26536159354aea9024a99cbbe60b4e.html) 
-   In SAP Datasphere, you have added an OAuth client with authorization grant **Client Credentials**. To learn how, see: [Create OAuth2.0 Clients to Authenticate Against SAP Datasphere](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/3f92b46fe0314e8ba60720e409c219fc.html)



## Context

SAP Datasphere is a solution that harmonizes data management, analytics, and intelligent planning, including capabilities of SAP Data Intelligence Cloud and SAP Analytics Cloud. The solution enables SAP customers to consolidate their SAP data and analytics needs into a single SAP solution.

You can use Identity Provisioning to configure SAP Datasphere as a target system where you can provision users. The target system consumes SCIM 2.0 API provided by SAP Datasphere.

> ### Note:  
> SAP Datasphere does not support groups.



<a name="loioeb95de0358124c8d944ec0ad190ba905__steps_phw_gld_pcc"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Datasphere* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the URL to your SAP Datasphere system without adding the path information.
    
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
    
    Enter the client ID to retrieve the OAuth access token for SAP Datasphere.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the client secret to retrieve the OAuth access token for SAP Datasphere.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the URL of the access token provider service for your SAP Datasphere instance.

    This token URL is listed in the *Trusted Identity Providers* section of the *App Integration* page. For more information, see [Create OAuth2.0 Clients to Authenticate Against SAP Datasphere](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/3f92b46fe0314e8ba60720e409c219fc.html)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ds.api.csrf.protection`
    
    </td>
    <td valign="top">
    
    Specifies whether to fetch a CSRF token when sending requests to the system.

    This property is automatically added to the system, with default value: **enabled**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ds.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    This property appears by default when the system is created, and its value is set to *userName*.

    It defines by which unique attribute\(s\) an existing user to be resolved in the event of conflicting users.

    Other possible values:

    -   **emails\[0\].value**
    -   **userName,emails\[0\].value**
    -   **externalId**, or another SCIM attribute, or a conjunction of SCIM attributes

    > ### Note:  
    > If this property is missing, or you've deleted it, and the service does not find such a *userName*, it will try again to resolve the conflicting user – by *email*. If the second attempt for resolution is unsuccessful too, the creation of the conflicting user fails.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ds.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

    -   If set to *true*, `PATCH` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, only these changes will be provisioned and applied in the target system.

    -   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ds.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    Set this property to *true* if you want to enable SCIM bulk operations for provisioning users. That means, the Identity Provisioning service can write, update, and delete a potentially large collection of users in a single request. For more information, see: [SCIM Protocol: Bulk Operations](https://datatracker.ietf.org/doc/html/rfc7644#section-3.7) and [Bulk Operations](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/1ca8c4a9467f43df9ae6d4ed3734f05a.html?locale=en-US#bulk-operations)

    If not specified, the default value is *false*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ds.bulk.operations.max.count`
    
    </td>
    <td valign="top">
    
    If you have enabled the SCIM bulk operations, you can use this property to set the number of users to be provisioned per request.

    Default value: `30`

    > ### Note:  
    > The value must not exceed the number of entities defined by the SAP Datasphere system as a SCIM service provider. Otherwise, the provisioning job will fail with HTTP response code 413 \(*Payload Too Large*\).


    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Datasphere* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Datasphere system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Datasphere SCIM 2.0 API](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/1ca8c4a9467f43df9ae6d4ed3734f05a.html#loio1ca8c4a9467f43df9ae6d4ed3734f05a__section_esx_kxt_vbc)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "($.emails[0].value EMPTY false) && isValidEmail($.emails[0].value) && ($.userName EMPTY false)",
    >     "mappings": [
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:User",
    >           "urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters",
    >           "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "optional": true,
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "optional": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.preferredLanguage",
    >         "optional": true,
    >         "targetPath": "$.preferredLanguage"
    >       },
    >       {
    >         "sourcePath": "$.photos",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.photos",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.roles",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.roles"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value == []",
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.emails[0].value"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value != []",
    >         "sourcePath": "$.emails[?(@.primary == true)].value",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.emails[0].value",
    >         "functions": [
    >           {
    >             "function": "elementAt",
    >             "index": 0
    >           }
    >         ]
    >       },
    >       {
    >         "condition": "$.emails[0].length() > 0",
    >         "constant": true,
    >         "targetPath": "$.emails[0].primary"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']"
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']['idpUserId']"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value != []",
    >         "sourcePath": "$.emails[?(@.primary == true)].value",
    >         "preserveArrayWithSingleElement": false,
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']['idpUserId']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']['idpUserId']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:params:scim:schemas:extension:sac:2.0:user-custom-parameters']['idpUserId']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "functions": [
    >           {
    >             "type": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   }
    > }
    > ```

    > ### Note:  
    > Updating a user in SAP Datasphere depends on whether user attributes in SAP Datasphere are mapped to SAML attributes in your identity provider. If this is the case, the values of those attributes are populated by the identity provider and cannot be changed by the SAP Datasphere SCIM API or the UI. For more information, see [Map SAML Attributes to Users](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/a3498ed7979d4e16ba303b3e047aa6a3.html?locale=en-US) and [Create a User](https://help.sap.com/docs/SAP_DATASPHERE/9f804b8efa8043539289f42f372c4862/1ca8c4a9467f43df9ae6d4ed3734f05a.html?locale=en-US#create-a-user).

6.  Now, add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)

    > ### Caution:  
    > The **email** attribute is unique for *SAP Datasphere* but it might not be unique for other systems, such as *SAP SuccessFactors*. That's why, when you choose a source system, make sure that there are no users with duplicate e-mails. If there are such, then after the provisioning job all users with the same e-mail address will be created as a single user in *SAP Datasphere*.
    > 
    > To learn more, see *Guided Answers*: [Multiple Users from a Source System Are Created as One in the Target](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:34942)
    > 
    > To learn more about excluding users from SAP Datasphere target, see: [Exclude Users from Provisioning to Target Systems](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:55088)




<a name="loioeb95de0358124c8d944ec0ad190ba905__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

