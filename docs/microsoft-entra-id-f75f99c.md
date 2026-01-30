<!-- loiof75f99c72ef94bedac5357febc8da612 -->

# Microsoft Entra ID

Follow this procedure to set up Microsoft Entra ID \(formerly known as Microsoft Azure Active Directory\) as a source system.



<a name="loiof75f99c72ef94bedac5357febc8da612__prereq_hcd_5cv_hz"/>

## Prerequisites

-   You've logged on to Microsoft Azure Portal, with credentials for a user with directory role **Global administrator**. For more information, see [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).
-   In *Azure Active Directory* \> *App registrations*, you've registered an application with a secret key and permissions for Microsoft Graph API. These permissions must be consented by an administrator. For more information, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).
-   \(Relevant to target systems\) Your registered application is assigned the **User Account Administrator** role. This role allows you to deprovision users. For more information, see [Add-MsolRoleMember](https://learn.microsoft.com/en-us/powershell/module/msonline/add-msolrolemember?view=azureadps-1.0).

    > ### Note:  
    > If this role isn't assigned, you can only disable users. To do that, set the `accountEnabled` property to **false**. For more information, see [MS Graph: user resource type](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/user)


**Permissions**

Assign the following permissions to your application, according to your scenario. Also, the permissions have to be of type *Application*.

-   Users – *User.Read.All*
-   Groups – *Group.Read.All*

For more information, see [MS Graph: Users](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/users) and [MS Graph: Groups](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/group)



<a name="loiof75f99c72ef94bedac5357febc8da612__context_opb_gly_rdb"/>

## Context

When using it as a source system, you can read both users and groups from Azure AD and provision them to any target system you've added in the Identity Provisioning user interface \(if it supports groups\).

If you've successfully finished with the initial setup \(described in the **Prerequisites** section\), continue with the procedure.



<a name="loiof75f99c72ef94bedac5357febc8da612__steps_wnk_3ly_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *Microsoft Entra ID* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the application ID registered in your Azure AD subscription \(see the **Prerequisites** section\).
    
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
    
    Enter one of the verified domain names from the corresponding Azure AD tenant. On this domain, you perform the provisioning operations. For more information, see [Managing custom domain names in your Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/domains-manage).
    
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
    
    \(Optional\) `aad.group.member.attributes`
    
    </td>
    <td valign="top">
    
    This property defines the attributes of a group member to be read by the Identity Provisioning. By default, it always reads the **type** and the **id** of a member.

    If you want the Identity Provisioning to read additional attributes, enter them as a single or a comma-separated value. For example:

    > ### Example:  
    > -   If you want to read the e-mails too, enter: `aad.group.member.attributes`=*mail*
    > 
    >     This reads a member's type, ID, and e-mail.
    > 
    > -   If you want to read multiple additional attributes, enter: `aad.group.member.attributes`=*mail,mobilePhone,displayName* 
    > 
    >     This reads a member's type, ID, e-mail, phone, and display name.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.user.attributes.membership.active`
    
    </td>
    <td valign="top">
    
    Use this property if you want to retrieve information about all the groups to which the users are assigned \(if any\).

    -   If the property is missing, or is set to *false* – group membership details for the users will not be extracted.
    -   If the property is set to *true* – group membership details for the users will be extracted.

    To learn more, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.user.filter`
    
    </td>
    <td valign="top">
    
    Use this property to filter users by specific criteria, according to the [Microsoft Graph REST API](https://docs.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#properties).

    > ### Note:  
    > This property replaces the deprecated `msgraph-filter` property. To learn more, see: [List of Properties](list-of-properties-d6f3577.md) 


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.group.filter`
    
    </td>
    <td valign="top">
    
    Use this property to filter groups by specific criteria, according to the [Microsoft Graph REST API](https://docs.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.user.filter.group.filter.combine`
    
    </td>
    <td valign="top">
    
    Use this property to filter users based on their group assignments.

    When set to **true**, this property combines user and group filters defined on the `aad.user.filter` and `aad.group.filter` properties to further narrow the search results. This way, only users that meet the following filtering criteria are returned:

    -   Users that match the user filter and at the same time are members of groups that match the group filter.

    -   Members of the filtered groups that match the user filter.


    When set to **false**, user and group filters are not combined.

    To learn more, see:

    [List of Properties](list-of-properties-d6f3577.md)

    [Identity Provisioning: How to Get Users Based on Group Assignments from MS Azure AD](https://blogs.sap.com/2021/09/28/identity-provisioning-how-to-get-users-based-on-group-assignments-from-ms-azure-ad/)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.user.attributes`
    
    </td>
    <td valign="top">
    
    Defines which user attributes are read from Microsoft Entra ID system.

    The property is set during system creation with the following default value: *id,mail,userPrincipalName,displayName,mailNickname,givenName,surname,mobilePhone,businessPhones*

    This means that by default, Identity Provisioning will read from Microsoft Entra ID the user attributes defined in the property value. Those attributes are used in the default read transformation.

    To check the complete set of user attributes \(properties\) supported by Microsoft Entra ID, see: [Microsoft Graph: User Properties](https://docs.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#properties)

    To learn more, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.group.attributes`
    
    </td>
    <td valign="top">
    
    Defines which group attributes are read from Microsoft Entra ID system.

    The property is set during system creation with the following default value: *id,displayName,mailNickname*

    This means that by default, Identity Provisioning will read from Microsoft Entra ID the group attributes defined in the property value and will also return the *members* attribute. Those attributes are used in the default read transformation.

    To check the complete set of group attributes \(properties\) supported by Microsoft Entra ID, see: [Microsoft Graph: Group Properties](https://docs.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties)

    To learn more, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `aad.entities.top`
    
    </td>
    <td valign="top">
    
    This property defines the number of entities to be read per page. Default value: *100* 
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Microsoft Entra ID* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules depending on your setup of entities in your Microsoft Entra ID. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [MS Graph: Users](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/users)

    [MS Graph: Groups](https://developer.microsoft.com/en-us/graph/docs/api-reference/v1.0/resources/group)

    **Default transformation:** 

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "$.userPrincipalName EMPTY false",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.mailNickname",
    >         "optional": true,
    >         "targetPath": "$.externalId",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.mail",
    >         "targetPath": "$.emails[0].value",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.userPrincipalName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "optional": true,
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.givenName",
    >         "optional": true,
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.surname",
    >         "optional": true,
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.mobilePhone",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[0].value"
    >       },
    >       {
    >         "condition": "$.mobilePhone EMPTY false",
    >         "constant": "mobile",
    >         "targetPath": "$.phoneNumbers[0].type"
    >       },
    >       {
    >         "sourcePath": "$.businessPhones[0]",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[1].value"
    >       },
    >       {
    >         "condition": "$.businessPhones.length() > 0",
    >         "constant": "work",
    >         "targetPath": "$.phoneNumbers[1].type"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups"
    >       },
    >       {
    >         "sourcePath": "$.manager.id",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.manager.displayName",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "ignore": true,
    >     "mappings": [
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.mailNickname",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members"
    >       },
    >       {
    >         "targetPath": "$.members[*].id",
    >         "constant": "value",
    >         "type": "rename",
    >         "optional": true
    >       },
    >       {
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       },
    >       {
    >         "constant": "userGroup",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >       },
    >       {
    >         "constant": "readWrite",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >       }
    >     ]
    >   }
    > }
    > ```

    **Custom Configurations**


    <table>
    <tr>
    <th valign="top">

    Goal
    
    </th>
    <th valign="top">

    Action
    
    </th>
    <th valign="top">

    Result
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    You want Identity Provisioning to read the additional user attributes specified in property `aad.user.attributes` and write them successfully in the target system.
    
    </td>
    <td valign="top">
    
    Extend the "*user*" mapping as follows:

    ```
    
    {
    	"user": {
    	   "condition": "$.userPrincipalName EMPTY false",
    	   "mappings": [
    		{
    		   "sourcePath": "$",
    		   "targetPath": "$"
    		},
    		{
    		   "sourcePath": "$.id",
    		   "targetVariable": "entityIdSourceSystem"
    		},
    ...
     
    ```


    
    </td>
    <td valign="top">
    
    For example, you specify the `aad.user.attributes` property and set its value to: *id,mail,userPrincipalName,city,department,companyName*

    As a result, every user in the target system will have the following attributes populated – ID, e-mail, user principle name, city, department, and company name.

    Returned information of an exemplary user:

    ```
    ...
    {
       "Resources":[
    	{
    	   "id":"555-aaaa-333-abcd-111222333",
    	   "mail":"john.smith@domain.com",
    	   "userPrincipalName":"abc@something.onmicrosoft.com",
    	   "city": "Sofia",
    	   "department":"029",
    	   "companyName":"SAP"
    	}
    ...
       ]
    }
    
    ```


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    You want Identity Provisioning to read the additional group attributes specified in property `aad.group.attributes` and write them successfully in the target system.
    
    </td>
    <td valign="top">
    
    Extend the "*group*" mapping as follows:

    ```
    
    {
    	"group": {
    	   "ignore": false,
    	   "mappings": [
    		{
    		   "sourcePath": "$",
    		   "targetPath": "$"
    		},
    		{
    		   "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    		   "targetPath": "$.schemas[0]"
    		},
    ...
     
    ```


    
    </td>
    <td valign="top">
    
    Example: Specify the `aad.group.attributes` property and set its value to: *id,displayName,recommendation,isSubscribedByMail*

    As a result, every group in the target system will have the following attributes populated – ID, display name, date and time of the last renewal, and information if it's subscribed by e-mail or not.

    Returned information of an exemplary group:

    ```
    ...
    {
       "Resources":[
    	{
    	   "id":"12345-ccc-000-xyz-777888999",
    	   "displayName":"ImportantGroup3",
    	   "renewedDateTime":"2018-01-01T00:00:00Z",
    	   "isSubscribedByMail":"true"
    	}
    ...
       ]
    }
    
    ```


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    You want the returned value of a group member to be not the ID but a different attribute.
    
    </td>
    <td valign="top">
    
    In the `"group"` mapping, replace **id** with the new attribute. For example:

    If you replace *id* with *mail*, the transformation will look like this:

    ```
    
    ...
    	{
    	   "sourcePath": "$.members",
    	   "preserveArrayWithSingleElement": true,
    	   "optional": true,
    	   "targetPath": "$.members"
    	},
    	{
    	   "targetPath": "$.members[*].mail",
    	   "constant": "value",
    	   "type": "rename",
    	   "optional": true
    	}
    ...
    ```

    > ### Caution:  
    > Make sure that you've added this attribute as a value of property *aad.group.member.attributes*.


    
    </td>
    <td valign="top">
    
    Returned information of an exemplary group member:

    ```
    ...
    {
       "members":[
    	{
    	   "id":"5555555-aaaa-333-abcd-1111122223333",
    	   "type":"user",
    	   "value":"johnsmith@mail.acme.com"
    	}
      ]
    }
    ...
    ```


    
    </td>
    </tr>
    </table>
    
6.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loiof75f99c72ef94bedac5357febc8da612__postreq_lvw_bqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

