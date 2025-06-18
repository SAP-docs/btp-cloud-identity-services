<!-- loio04278923ec8b4b34ac912897062be317 -->

# SCIM System

Follow this procedure to set up a SCIM system as а target system.



<a name="loio04278923ec8b4b34ac912897062be317__prereq_wvj_nhz_fpb"/>

## Prerequisites

> ### Restriction:  
> This system is available for standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on SAP Cloud Identity Services infrastructure and Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   \(Optional\) You have installed the Cloud Connector in your corporate environment and have done the initial configuration. You need this only if the SCIM system is exposed in a private corporate network. For more information, see [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).
-   You have technical user credentials for a SCIM system, with read/write access permissions, depending on the scenario you want to implement. In case OAuth is used for authentication, client ID and secret are required when creating a destination for access token retrieval.



## Context

Create a general SCIM 2.0 based target system to write users and groups to it.



## Procedure

1.  \(Optional\) If the SCIM system is exposed in a private corporate network, add an access control system mapping in Cloud Connector. For more information, see [Configure Access Control \(HTTP\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e7d4927dbb571014af7ef6ebd6cc3511.html).

2.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

4.  Add *SCIM System* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

5.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Specify the service URL. For example:

    `http://<cloudfoundry_server>.com/api/uaa/`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Depending on your network exposure, enter one of the following:

    -   *Internet*
    -   *OnPremise*


    
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
    
    You can specify one of the following:

    -   Technical user ID
    -   Client ID for OAuth HTTP destinations. It's used for retrieving of the access token.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) You can enter one of the following:

    -   Technical user password
    -   Client secret for OAuth HTTP destinations. It's used for retrieving of the access token.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    If you need to make OAuth authentication to the system, enter the URL to the access token provider service for OAuth HTTP destinations.

    For example: `https://<token_provider>.com/api/oauth2/v2.0/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `scim.csrf.token.path`
    
    </td>
    <td valign="top">
    
    Path which is appended to the URL to retrieve the CSRF token.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `scim.api.csrf.protection`
    
    </td>
    <td valign="top">
    
    Specifies whether to fetch a CSRF token when sending requests to the system.

    **Possible values:**

    -   *enabled*
    -   *disabled*


    
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

6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SCIM* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SCIM system. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    -   **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target entity. If the entity has e-mail addresses, the first entry will be marked as primary.
    -   **User off-boarding** – Users can be deleted from the target system. Depending on the implementation, this could be done through a user interface \(if such exists\) or the SCIM REST API. Users could be deactivated, depending on the SCIM system implementation. The SCIM core schema defines an attribute “**active**”, whose definition depends on the service provider. For more information, see [SCIM: Singular Attributes](https://tools.ietf.org/html/rfc7643#section-4.1.1) 

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$",
    >                 "targetPath": "$"
    >             },
    >             {
    >                 "targetPath": "$.id",
    >                 "type": "remove"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "condition": "$.emails[0].length() > 0",
    >                 "targetPath": "$.emails[0].primary",
    >                 "constant": true
    >             },
    >             {
    >                 "type": "remove",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "ignore": true,
    >         "mappings": [
    >             {
    >                 "sourcePath": "$",
    >                 "targetPath": "$"
    >             },
    >             {
    >                 "targetPath": "$.id",
    >                 "type": "remove"
    >             },
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "targetPath": "$.members",
    >                 "type": "remove"
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
    > ```

7.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md) 




<a name="loio04278923ec8b4b34ac912897062be317__postreq_lvw_bqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

