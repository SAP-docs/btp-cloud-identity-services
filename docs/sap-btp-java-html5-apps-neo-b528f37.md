<!-- loiob528f37af1ca4869a4941f141a51d3e5 -->

# SAP BTP Java/HTML5 apps \(Neo\)

Follow this procedure to set up SAP Business Technology Platform as a source system, from which you can read user-to-groups assignments for Java/HTML5 applications that run on SAP BTP, Neo environment.



<a name="loiob528f37af1ca4869a4941f141a51d3e5__prereq_n1b_khq_h2b"/>

## Prerequisites

You have created a new Platform API OAuth client, with *Authorization Management* scopes. Save the *Client ID* and *Client Secret* as you'll need them when you configure your source system. Make sure you save the client secret as you cannot retrieve it later.

For more information, see [Create a Platform API Client](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/392af9d162694d6595499f1549978aa6.html).



<a name="loiob528f37af1ca4869a4941f141a51d3e5__context_wmw_khq_h2b"/>

## Context

The Identity Provisioning service helps companies to automatically manage the user-to-groups assignments for Java/HTML5 applications running on SAP BTP, Neo environment. For this scenario, SAP BTP is the source system. The target system can be a solution supported by the Identity Provisioning service with write access for user and group artifacts.

This provisioning scenario is based on the Authorization Management REST API of the SAP Business Technology Platform. For more information, see [Using the Authorization Management REST API](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dbea343ebe184c26b6067daaabaa9ac6.html).



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP BTP Java/HTML5 apps \(Neo\)* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter: `https://api.<SAP_BTP_host>/authorization/v1/accounts/<SAP_BTP_account>` 

    Examples:

    -   \(Europe – Rot\) *https://api.hana.ondemand.com/authorization/v1/accounts/abc123xyz*
    -   \(Japan – Tokyo\) *https://api.jp1.hana.ondemand.com/authorization/v1/accounts/abc123xyz*


    
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
    
    Enter the Client ID of the new Platform API OAuth client created for the Authorization Management API \(see the prerequisites\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the Client Secret of the new Platform API OAuth client created for the Authorization Management API \(see the prerequisites\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter: `https://api.<SAP_BTP_host>/oauth2/apitoken/v1`

    Examples:

    -   \(Europe – Rot\) *https://api.hana.ondemand.com/oauth2/apitoken/v1*
    -   \(US East – Sterling\) *https://api.us3.hana.ondemand.com/oauth2/apitoken/v1*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `hcp.application.names` 
    
    </td>
    <td valign="top">
    
    Enter a comma-separated list of application names. That could be applications deployed on your account, or applications for which your account has subscribed. The property returns the roles assigned to these applications.

    Use the following format \(no spaces\):

    *<app\_name1\>,<app\_name2\>,<provider\_subaccount\>:<provider\_app\>* 

    > ### Caution:  
    > You must not leave this property with an empty value.


    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP Java/HTML5 apps \(Neo\)* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    Using the default transformation, all groups and their members \(with roles\) available in the SAP Business Technology Platform source system will be created as groups and respective members \(with roles\) in the chosen target system.

    You can change the default transformation mapping rules to reflect the data to be written in the target system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP BTP: Authorization Management API](https://api.hana.ondemand.com/authorization/v1/documentation)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > // To read the roles assigned to your applications, add property hcp.application.names to your system configuration. 
    > {
    >   "role": {
    >     "mappings": [
    >       {
    >         "targetPath": "$",
    >         "sourcePath": "$"
    >       },
    >       {
    >         "targetVariable": "entityIdSourceSystem",
    >         "constant": "-",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "prefix": "$.applicationName",
    >             "suffix": "$.name"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "targetPath": "$.id",
    >         "sourcePath": "$.name"
    >       },
    >       {
    >         "targetVariable": "entityIdSourceSystem",
    >         "sourcePath": "$.name"
    >       },
    >       {
    >         "targetPath": "$.displayName",
    >            "sourcePath": "$.name",
    >         "functions": [
    >           {
    >             "condition": "'%hcp.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%hcp.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "targetPath": "$.schemas[0]",
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group"
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "optional": true
    >       },
    >       {
    >         "constant": "User",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[*].type",
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "targetPath": "$.displayName",
    >         "sourcePath": "$.name"
    >       },
    >       {
    >         "targetPath": "$.userName",
    >         "sourcePath": "$.name",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "targetPath": "$.schemas[0]",
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.groups[?(@.value)]",
    >         "optional": true
    >       },
    >       {
    >         "constant": "direct",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.groups[*].type",
    >         "optional": true
    >       }
    >     ]
    >   }
    > }
    > 
    > 
    > ```

6.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loiob528f37af1ca4869a4941f141a51d3e5__postreq_lpw_sqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[What is SAP BTP](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/73beb06e127f4e47b849aa95344aabe1.html)

