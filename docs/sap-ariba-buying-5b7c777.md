<!-- loio5b7c777fe14a44e19d1563e79fa4cbec -->

# SAP Ariba Buying

Follow this procedure to set up SAP Ariba Buying as a target system.



<a name="loio5b7c777fe14a44e19d1563e79fa4cbec__prereq_mcb_1kn_q1c"/>

## Prerequisites



## Context

SAP Ariba Buying offers users a personalized, guided process for finding and ordering things they need for work. SAP Ariba Buying allows buyers and suppliers to integrate procurement solutions with their procurement process seamlessly.

After fulfilling the prerequisites, you can create an SAP Ariba Buying target system to provision *users*.

These target systems consume SCIM 2.0 API provided by SAP Ariba Buying.

> ### Note:  
> SAP Ariba Buying does not support groups.



<a name="loio5b7c777fe14a44e19d1563e79fa4cbec__steps_xqv_dkn_q1c"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Ariba Buying* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the OAuth Client ID.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Secret.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.buying.include.if.match.wildcard.header`
    
    </td>
    <td valign="top">
    
    Makes the SAP Ariba Buying connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Ariba Buying system for entity versioning.

    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ariba.buying.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    When Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

    This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find such a user, the creation will fail.

    The property is automatically added during system creation. If the service finds an existing user by at least one of the uniqueness criteria, which are *email*, *userName*, or *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the update of the conflicting user fails. If more than one users with these unique attributes are found, the update fails.

    For more information, see [List of Properties](list-of-properties-d6f3577.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ariba.buying.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified users in the source system are updated in the target system.

    -   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

        For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

    -   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


    Users can be updated in the target system in various cases, such as:

    -   In the source system, some user attributes are modified, or new attributes are added.

    -   In the source system, a condition or a filter is set for users not to be read anymore.

    -   A user is deleted from the source system.


    In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false*
    
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

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Ariba Buying* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Ariba Applications. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    API LINK

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > ```

6.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio5b7c777fe14a44e19d1563e79fa4cbec__postreq_emv_vdb_kdb"/>

## Next Steps

1.  Before starting a provisioning job, you can first subscribe to the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during your jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
2.  Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

[The SAP Ariba developer portal](https://help.sap.com/viewer/b61dd8c7e22c4fe489f191f66b4c48d6/cloud/en-US/1d55722e669e4c6aaa4eda5a011519ac.html)

[Video: Create application and API approval process](https://www.youtube.com/watch?v=CQQlADnbM6w)

