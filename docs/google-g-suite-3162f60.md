<!-- loio3162f601739f496cb3b818e0e13ecac3 -->

# Google G Suite

Follow this procedure to set up Google G Suite as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on SAP Cloud Identity Services infrastructure and Neo environment can use it only through **SAP Identity Access Governance** bundle option.

1.  Sign in to the Google API console \([https://console.developers.google.com](https://console.developers.google.com)\) and create a project.
2.  Enable the Admin SDK. To do this, go to *Dashboard* \> *ENABLE API* \> *Admin SDK* \> *ENABLE*.
3.  Create a service account for your project. We recommend that you select *Enable G Suite Domain-wide Delegation* during the creation. If you skip this option, you can set it later. For more information, see [Creating a service account](https://developers.google.com/identity/protocols/OAuth2ServiceAccount?hl=en_US#creatinganaccount).
4.  Then, in the Google admin console \([https://admin.google.com](https://admin.google.com)\), a user with **Super Admin** role can delegate domain-wide authority to your service account. This way, it will have access to the Google Admin SDK on behalf of your user. For more information, see [Delegating domain-wide authority](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#delegatingauthority).

    > ### Note:  
    > When specifying the scopes, the administrator has to enter the following:
    > 
    > `https://www.googleapis.com/auth/admin.directory.user, https://www.googleapis.com/auth/admin.directory.group`




## Context

A Google service account with delegated domain-wide authority is required for authentication and authorization of the Identity Provisioning service to G Suite domain. The authentication is based on OAuth 2.0 protocol with JSON Web Token \(JWT\). The private key for the signature is distributed by Google via one-time downloadable JSON data, which is accessible by the domain administrator. The private key is encoded in PKCS8 format and is in the *private\_key* field of the JSON data. For more information, see [JSON Web Token \(JWT\)](https://tools.ietf.org/html/rfc7519).

-   When using it as a source system, you can read both users and groups from Google G Suite and provision them to any target system you have added in the Identity Provisioning user interface.
-   When using it as a target system, you can write both users and groups, read from any source system you have added in the Identity Provisioning user interface. Google G Suite can automatically create accounts for your users in the Google Cloud Datastore.

The Identity Provisioning service supports user and group operations based on the following Google Directory API. See the table below.


<table>
<tr>
<th valign="top">

User Operations

</th>
<th valign="top">

Group Operations

</th>
</tr>
<tr>
<td valign="top">

[Create a user](https://developers.google.com/admin-sdk/directory/v1/reference/users/insert) 

</td>
<td valign="top">

[Create a group](https://developers.google.com/admin-sdk/directory/v1/reference/groups/insert) 

</td>
</tr>
<tr>
<td valign="top">

[Retrieve a user](https://developers.google.com/admin-sdk/directory/v1/reference/users/get) 

</td>
<td valign="top">

[Retrieve a group's properties](https://developers.google.com/admin-sdk/directory/v1/reference/groups/get) 

</td>
</tr>
<tr>
<td valign="top">

[Update a user](https://developers.google.com/admin-sdk/directory/v1/reference/users/update) 

</td>
<td valign="top">

[Update a group's properties](https://developers.google.com/admin-sdk/directory/v1/reference/groups/update) 

</td>
</tr>
<tr>
<td valign="top">

[Delete a user](https://developers.google.com/admin-sdk/directory/v1/reference/users/delete) 

</td>
<td valign="top">

[Delete a group](https://developers.google.com/admin-sdk/directory/v1/reference/groups/delete) 

</td>
</tr>
</table>

> ### Caution:  
> You can only provision users whose e-mails are from verified domains.

If you have successfully finished with the initial setup \(described in the **Prerequisites** section\), continue with the procedure below.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *Google G Suite* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify the service URL:

    `https://www.googleapis.com/admin/directory`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Enter: `Internet`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    Enter: *BasicAuthentication*

    The authentication type in use is actually **OAuth** with JWT. But for any provisioning system based on OAuth, **BasicAuthentication** is used along with the `OAuth2TokenServiceURL` additional property.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter the service account’s ID. You can take it from the *"client\_email"* field in the JSON data, downloaded during the setup of Google service account.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the service account’s private key, which represents a long string in PKCS8 format. You can take it from the *"private key"* field in the JSON data, downloaded during the setup of Google service account.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    To make OAuth authentication to the Google G Suite system, enter the URL to the access token provider service. For more information, see Using [OAuth 2.0 to Access Google APIs](https://developers.google.com/identity/protocols/OAuth2).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `jwt.subject`
    
    </td>
    <td valign="top">
    
    Enter the Google G Suite user on behalf of which the Google Directory API is called. This user has been assigned the role **User Management Admin**.

    This property corresponds to “sub” claim in JWT being generated during access token request: [JWT: "sub" \(Subject\) Claim](https://tools.ietf.org/html/rfc7519#section-4.1.2)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `jwt.scope`
    
    </td>
    <td valign="top">
    
    Enter space-separated Google Directory API authorization scopes. For example:

    `https://www.googleapis.com/auth/admin.directory.user`
    
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

    **Exemplary Configuration:**


    <table>
    <tr>
    <td valign="top">
    
    `ProxyType`=*Internet*

    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `URL`=*https://www.googleapis.com/admin/directory*

    `User`=*1234567890-compute@developer.gserviceaccount.com*

    `Password`=*\-----BEGIN PRIVATE KEY-----\\n123ABCDEFG123456789...*

    *… /123456789ABCDEFG123=\\n-----END PRIVATE KEY-----\\n*

    `OAuth2TokenServiceURL`=*https://www.googleapis.com/oauth2/v4/token*

    `jwt.subject`=*john.smith@me123.accounts.ondemand.com*

    `jwt.scope`=*https://www.googleapis.com/auth/admin.directory.user*
    
    </td>
    </tr>
    </table>
    
5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Google G Suite* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    Transformation principles for the target system integration:

    -   **Mapping logic** – The provisioning framework reads all attributes from the intermediate JSON data and tries to create consistent records in the Google G Suite target system, using all the available attributes accepted by the Google Directory API. When a required attribute is missing, the default transformation is designed with a condition that will exclude the inconsistent records. Bear in mind the following:

        -   Make sure that the JSON data sent by the source system is consistent with the configuration template of the target. For example, if the source system contains mandatory fields and the target one does not support such kind of data, then the target system skips these fields. This may cause crucial data loss.
        -   There is a special user status type called **suspended** \(temporarily blocks a user without deleting any account data\) for the Google directory accounts. When the status of the user account is changed to **suspended**, the Google Directory API will not accept any changes on the user attributes. Once the suspended user is restored by the administrator, all attribute changes pending for the account will be successfully provisioned with the next provisioning job.

        > ### Caution:  
        > An initial password setup is mandatory for all newly provisioned users. This is required by the Google G Suite API and must be provided when new accounts are created. The constant value that you see as configuration for the password attribute in the default transformation is generated by SAP. You have to change the constant value with another one, known only by the representatives of your company, before starting to use the Identity Provisioning service for creating users in your corporate Google G Suite system automatically.

    -   **User off-boarding** – Identity Provisioning service is handling the deletion status of the users. When a user is deleted from the source system, this deletion will be enforced into the Google G Suite system as well.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Google G Suite. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [Google Directory API: Users](https://developers.google.com/admin-sdk/directory/v1/reference/users)

    [Google Directory API: Groups](https://developers.google.com/admin-sdk/directory/v1/reference/groups)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "condition": "($.emails.length() > 0) && ($.name.familyName EMPTY false)",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name"
    >             },
    >             {
    >                 "sourcePath": "$.emails[0].value",
    >                 "targetPath": "$.primaryEmail"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "optional": true,
    >                 "targetPath": "$.phones"
    >             },
    >             {
    >                 "targetPath": "$.password",
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
    >                 "constant": "false",
    >                 "targetPath": "$.suspended"
    >             },
    >             {
    >                 "condition": "$.active == false",
    >                 "constant": true,
    >                 "targetPath": "$.suspended"
    >             },
    >             {
    >                 "constant": "true",
    >                 "targetPath": "$.changePasswordAtNextLogin"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "ignore": true,
    >         "mappings": [
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.name"
    >             },
    > // Google G Suite requires a group e-mail. By default, the email attribute is mapped to displayName. If group's Display Name does not contain an e-mail, 
    > // you can either map email to another attribute, or concatenate displayName with your domain. To learn how, see the detailed explanation and example below.  
    >   
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.email",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "sourcePath": "$.members[?(@.type == 'User')].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.id)]",
    >                 "functions": [
    >                     {
    >                         "entityType": "user",
    >                         "type": "resolveEntityIds"
    >                     }
    >                 ]
    >             }
    >         ]
    >     }
    > }
    >        
    > ```

    If the **displayName** attribute in the source system transformation does not provide group e-mails, you can modify the transformation the following ways:

    -   Map **email** to another attribute that contains a unique group e-mail.
    -   Concatenate the **displayName** attribute with your domain. For example:

        > ### Sample Code:  
        > ```
        > 
        >        {
        >            "sourcePath": "$.displayName",
        >            "targetPath": "$.email",
        >            "scope": "createEntity",
        >            "functions": [
        >                {
        >                    "type": "concatString",
        >                    "suffix": "@test.myaccount.ondemand.com"
        >                }
        >            ]
        >        }
        > 
        > 
        > ```


6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio3162f601739f496cb3b818e0e13ecac3__postreq_wss_rpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

