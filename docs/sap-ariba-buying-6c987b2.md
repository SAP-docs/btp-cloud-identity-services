<!-- loio6c987b23294245ff800c2d040016ce23 -->

# SAP Ariba Buying

Follow this procedure to set up SAP Ariba Buying as a source system.



<a name="loio6c987b23294245ff800c2d040016ce23__prereq_bb4_jgn_q1c"/>

## Prerequisites



## Context

SAP Ariba Buying offers users a personalized, guided process for finding and ordering things they need for work. SAP Ariba Buying allows buyers and suppliers to integrate procurement solutions with their procurement process seamlessly.

You can read *users* from SAP Ariba Buying source system and provision them to a target system of your choice.

These source systems consume SCIM 2.0 API provided by SAP Ariba Buying.

> ### Note:  
> SAP Ariba Buying does not support groups.



<a name="loio6c987b23294245ff800c2d040016ce23__steps_hr4_myx_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Ariba Buying* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the SCIM API URL for your SAP Ariba Buying application.
    
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
    
    Enter the OAuth Client ID \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Secret \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL` 
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL \(see the **Prerequisites** section\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ariba.buying.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Ariba Buying users matching the filter expression will be read. You can set a single attribute or multiple ones as search criteria.

    Supported filtering by the following attributes:

    -   *id*

    -   *userName*

    -   *emails.value*

    -   *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*

    -   *active*


    For more information, see [List of Properties](list-of-properties-d6f3577.md).
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Ariba Buying* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your *SAP Ariba Buying* source system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    API LINK

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > ```

6.  Now, add a target system to provision users into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio6c987b23294245ff800c2d040016ce23__postreq_wss_rpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

