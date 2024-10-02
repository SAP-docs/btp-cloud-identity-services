<!-- loioe74f131d7dc44d229baec9a2f7e0f87b -->

# SAP CPQ

Follow this procedure to set up SAP CPQ \(Configure, Price, and Quote\) as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   You have created a technical user with administrator permissions that will be used to call the API of SAP CPQ for creating and updating user and group information.

-   Make sure all users that need to be read from the source system have an organization unit name. This unit name must correspond to an existing company system ID in SAP CPQ. The *organization unit* and the *company system ID* must be exactly the same. Users with empty \(missing\) organization units will not be provisioned, as well as users whose organization units don't match any of the SAP CPQ company system IDs for the relevant tenant.

-   In order for a created user to be active in SAP CPQ, it should be assigned to an SAP CPQ target group, whose ID ends with suffix *–USERTYPE*. To learn more, see [SAP CPQ: SCIM API](https://help.sap.com/viewer/08a7929ad06d4680b4f18cb57bc1a1d3/latest/en-US/7cf5d969d59a4723bcfd01cc38322a00.html) → section **Mappings between SCIM API and SAP CPQ** → `groups`.




<a name="loioe74f131d7dc44d229baec9a2f7e0f87b__context_y2y_nxx_rdb"/>

## Context

SAP CPQ is a highly configurable system designated to help sales representatives to configure products, apply pricing and generate quotes. SAP CPQ is part of the SAP Sales Cloud portfolio.

Create an SAP CPQ target system to provision users and groups to it.

> ### Caution:  
> You can't create or delete groups on SAP CPQ. That means:
> 
> -   On the attempt to create a group on SAP CPQ, Identity Provisioning will only add new members or update existing ones. Also, if you read a group from a source system, there must be a group with the exact same display name \(case sensitive\) in the SAP CPQ target system. Otherwise, an error will be thrown and the group members will not be updated.
> -   On the attempt to delete a group on SAP CPQ, Identity Provisioning will only remove its members \(group assignments\). And this can happen only if the relevant group assignments have been provisioned/are present in the target system.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP CPQ* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP CPQ and configure the authentication method \(basic or OAuth certificate-based\).

    > ### Note:  
    > We recommend that you use OAuth certificate-based authentication.

    1.  In your newly added SAP CPQ target system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](Operation-Guide/generate-and-manage-certificates-for-outbound-connection-76867db.md).

        Skip this step if you use basic authentication. The next steps are relevant for OAuth certificate-based authentication only. For more information, see [Configure OAuth Certificate Authentication](Operation-Guide/configure-oauth-certificate-authentication-a40a3f3.md).

    2.  Convert your certificate file from `.crt` to `.cer`.

    3.  Login to SAP CPQ and navigate to *Security* \> *Certificate Management* \> *User Certificates* \> *New Certificate* and upload the certificate to the technical user of SAP CPQ.

        Make sure the *Enable User Certificates* option is turned on. Additionally, the technical user must be set to *Active*.


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

    Value
    
    </th>
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
    
    `ips.delete.existedbefore.entities`
    
    </td>
    <td valign="top">
    
    Enter: *true*

    SAP CPQ API does not allow creation and deletion of groups. Thus, if a previously read group is later deleted from the source system, this property will delete the relevant members from SAP CPQ \(not the group itself\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.delete.threshold.groups`
    
    </td>
    <td valign="top">
    
    \(Optional\) Use this property to control the number of group assignments to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of group assignments, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.delete.threshold.users`
    
    </td>
    <td valign="top">
    
    \(Optional\) Use this property to control the number of users to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of users, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Valid if *ClientCertificateAuthentication* is configured as authentication method.

    Enter the OAuth 2.0 Token Service URL.

    For example: `https://<cpq_url>/oauth2/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    \(Credential\) Specify the password for your technical user.
    
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
    
    Enter the URL to the API of your SAP CPQ system. It is the same as your SAP CPQ tenant URL. It must contain the domain name.

    For example: **https://sample1234.mycpqdomain.com**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    Enter the Username of your SAP CPQ technical user.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

6.  Configure the transformations.

    Identity Provisioning offers a default transformation for the *SAP CPQ* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP CPQ entity. You can change the default transformation mapping rules to reflect your current setup of entities in your SAP CPQ. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP CPQ: SCIM API](https://help.sap.com/viewer/08a7929ad06d4680b4f18cb57bc1a1d3/latest/en-US/7cf5d969d59a4723bcfd01cc38322a00.html)

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "condition": "($.emails EMPTY false) && isValidEmail($.emails[0].value)",
    >         "mappings": [
    >             {
    >                 "targetPath": "$.id",
    >                 "sourceVariable": "entityIdTargetSystem"
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
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.addresses",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.addresses"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.phoneNumbers"
    >             },
    >             {
    >                 "scope": "createEntity",
    >                 "constant": [],
    >                 "targetPath": "$.groups"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']"
    >             },
    >             {
    >                 "constant": true,
    >                 "targetPath": "$['urn:sap:cpq:scim:schemas:extension:custom:2.0:User']['IsSsoUser']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "condition": "('%cpq.group.prefix%' === 'null') || ($.displayName =~ /%cpq.group.prefix%.*/)",
    >         "mappings": [
    >             {
    >                 "targetPath": "$.id",
    >                 "sourceVariable": "entityIdTargetSystem"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "functions": [
    >                     {
    >                         "condition": "('%cpq.group.prefix%' !== 'null') && (@ =~ /%cpq.group.prefix%.*/)",
    >                         "function": "replaceFirstString",
    >                         "regex": "%cpq.group.prefix%",
    >                         "replacement": ""
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]",
    >                 "functions": [
    >                     {
    >                         "function": "resolveEntityIds"
    >                     }
    >                 ]
    >             }
    >         ]
    >     }
    > }
    > ```

7.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loioe74f131d7dc44d229baec9a2f7e0f87b__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

