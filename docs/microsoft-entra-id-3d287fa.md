<!-- loio3d287fa432904f71a8f83d2d88082c3b -->

# Microsoft Entra ID

Follow this procedure to set up Microsoft Entra ID \(formerly known as Microsoft Azure Active Directory\) as a target system.



<a name="loio3d287fa432904f71a8f83d2d88082c3b__prereq_hcd_5cv_hz"/>

## Prerequisites

> ### Restriction:  
> This system is available for standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on SAP Cloud Identity Services infrastructure and Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   You've logged on to Microsoft Azure Portal, with credentials for a user with directory role **Global administrator**. For more information, see [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).
-   In *Azure Active Directory* \> *App registrations*, you've registered an application with a secret key and permissions for Microsoft Graph API. These permissions must be consented by an administrator. For more information, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).
-   \(Relevant to target systems\) Your registered application is assigned the **User Account Administrator** role. This role allows you to deprovision users. For more information, see [Add-MsolRoleMember](https://learn.microsoft.com/en-us/powershell/module/msonline/add-msolrolemember?view=azureadps-1.0).

    > ### Note:  
    > If this role isn't assigned, you can only disable users. To do that, set the `accountEnabled` property to **false**. For more information, see [MS Graph: user resource type](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/user)


**Permissions**

Assign the following permissions to your application, according to your scenario. Also, the permissions have to be of type *Application*.

-   Users – *User.ReadWrite.All*, *Directory.AccessAsUser.All*
-   Groups – *Group.ReadWrite.All*

For more information, see [MS Graph: Users](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/users) and [MS Graph: Groups](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/group)



## Context

When using it as a target system, you can write both users and groups, read from any source system you've added in the Identity Provisioning user interface. The Microsoft Entra ID target systems use Microsoft Graph API. For more information, see [Microsoft Graph](https://developer.microsoft.com/en-us/graph/docs/overview/overview).

If you've successfully finished with the initial setup \(described in the **Prerequisites** section\), continue with the procedure.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *Microsoft Entra ID* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter: **https://graph.microsoft.com**
    
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
    
    Enter the application ID registered in your Microsoft Entra ID subscription \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the secret key associated to your app registration.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `aad.domain.name`
    
    </td>
    <td valign="top">
    
    Enter one of the verified domain names from the corresponding Microsoft Entra ID tenant. On this domain, you perform the provisioning operations. For more information, see [Managing custom domain names in your Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/domains-manage).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter: **https://login.microsoftonline.com/<your\_domain\>/oauth2/token**, where `<your_domain>` is the domain name you have set in the `aad.domain.name` property.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.oauth2.resource.name`
    
    </td>
    <td valign="top">
    
    Specifies the OAuth2 resource name for Microsoft Graph API.

    Enter: **https://graph.microsoft.com**

    You can change the Microsoft Graph endpoint to match your organization's cloud environment. For more information, see [Microsoft Graph national cloud deployments](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Flearn.microsoft.com%2Fen-us%2Fgraph%2Fdeployments).
    
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
    <tr>
    <td valign="top">
    
    \(Deprecated\) `oauth.resource.name`
    
    </td>
    <td valign="top">
    
    Enter: **https://graph.microsoft.com**

    > ### Note:  
    > The **oauth.resource.name** property has been deprecated, as it is no longer needed by the MS Entra ID connector. Use the **aad.oauth2.resource.name** property instead.


    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Microsoft Entra ID* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in Microsoft Entra ID. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [MS Graph: Users](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/users)

    [MS Graph: Groups](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/group)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.onPremisesImmutableId",
    >                 "optional": true,
    >                 "targetPath": "$.onPremisesImmutableId"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "optional": true,
    >                 "targetPath": "$.accountEnabled"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true,
    >                 "targetPath": "$.mailNickname"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true,
    >                 "targetPath": "$.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional": true,
    >                 "targetPath": "$.surname"
    >             },
    >             {
    >                 "sourcePath": "$.addresses[0].locality",
    >                 "optional": true,
    >                 "targetPath": "$.city"
    >             },
    >             {
    >                 "sourcePath": "$.addresses[0].country",
    >                 "optional": true,
    >                 "targetPath": "$.country"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userPrincipalName",
    >                 "scope": "createEntity",
    >                 "functions": [
    >                     {
    >                         "type": "concatString",
    >                         "suffix": "@%aad.domain.name%"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.accountEnabled",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "targetPath": "$.mailNickname",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "targetPath": "$.passwordProfile.password",
    >                 "scope": "createEntity",
    >                 "functions": [
    >                     {
    >                         "type": "randomPassword",
    >                         "passwordLength": 16,
    >                         "minimumNumberOfLowercaseLetters": 1,
    >                         "minimumNumberOfUppercaseLetters": 1,
    >                         "minimumNumberOfDigits": 1,
    >                         "minimumNumberOfSpecialSymbols": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "constant": false,
    >                 "targetPath": "$.passwordProfile.forceChangePasswordNextSignIn",
    >                 "scope": "createEntity"
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
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.description",
    >                 "optional": true,
    >                 "targetPath": "$.description"
    >             },
    >             {
    >                 "sourcePath": "$.allowExternalSenders",
    >                 "optional": true,
    >                 "targetPath": "$.allowExternalSenders"
    >             },
    >             {
    >                 "sourcePath": "$.autoSubscribeNewMembers",
    >                 "optional": true,
    >                 "targetPath": "$.autoSubscribeNewMembers"
    >             },
    >             {
    >                 "sourcePath": "$.isSubscribedByMail",
    >                 "optional": true,
    >                 "targetPath": "$.isSubscribedByMail"
    >             },
    >             {
    >                 "sourcePath": "$.visibility",
    >                 "optional": true,
    >                 "targetPath": "$.visibility"
    >             },
    >             {
    >                 "sourcePath": "$.securityEnabled",
    >                 "optional": true,
    >                 "targetPath": "$.securityEnabled"
    >             },
    >             {
    >                 "sourcePath": "$.mailEnabled",
    >                 "optional": true,
    >                 "targetPath": "$.mailEnabled"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.mailNickname",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "constant": true,
    >                 "targetPath": "$.mailEnabled",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "constant": false,
    >                 "targetPath": "$.securityEnabled",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "constant": "Unified",
    >                 "targetPath": "$.groupTypes[0]",
    >                 "scope": "createEntity"
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio3d287fa432904f71a8f83d2d88082c3b__postreq_lvw_bqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

