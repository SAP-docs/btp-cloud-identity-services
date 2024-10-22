<!-- loio8d6586f20b814b5f83c85448f3b0b715 -->

# SAP Build Work Zone, standard edition

Follow this procedure to set up SAP Build Work Zone, standard edition as a target system.



## Prerequisites

You have created an instance and generated a service key for the standard service plan of SAP Build Work Zone, standard edition. For more information, see: [Initial Setup](https://help.sap.com/viewer/8c8e1958338140699bd4811b37b82ece/Cloud/en-US/fd79b232967545569d1ae4d8f691016b.html).

The service key contains the API URL and the OAuth credentials \(`clientid` and `clientsecret`\) under the `uaa` property.



<a name="loio8d6586f20b814b5f83c85448f3b0b715__context_y2y_nxx_rdb"/>

## Context

The SAP Build Work Zone, standard edition simplifies access to SAP, custom-built, and third party applications and extensions \(both on the cloud and on premise\) by establishing a central launchpad.

You can use the Identity Provisioning UI to configure SAP Build Work Zone, standard edition as a target system for provisioning users, groups and users’ group assignments from various source systems.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Build Work Zone, standard edition* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter the SAP Build Work Zone, standard edition API URL from the service key of your SAP Build Work Zone, standard edition instance under `endpoints [portal-service]`. It follows the pattern:

    `https://portal-service.cfapps.sap.hana.ondemand.com`
    
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
    
    Enter the OAuth Client Id, from the service key of your SAP Build Work Zone, standard edition instance under `uaa.clientid`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the OAuth Client Secret, from the service key of your SAP Build Work Zone, standard edition instance under `uaa.clientsecret`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 Token Service URL from the service key of your SAP Build Work Zone, standard edition instance. It follows the pattern: `<uaa.url>/oauth/token`.

    For example: `https://ips-cflp-woaealle.authentication.sap.hana.ondemand.com/oauth/token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cflp.providerId`
    
    </td>
    <td valign="top">
    
    Enter a valid providerID value.

    The provider ID is specified in the Channel Manager of the SAP Build Work Zone, standard edition when defining a new content provider. For more information about configuring the content provider to use the Identity Provisioning service, see: [Manage Content Providers \(Cloud\)](https://help.sap.com/docs/build-work-zone-standard-edition/sap-build-work-zone-standard-edition/manage-content-providers-cloud), [Manage Content Providers \(On Premise\)](https://help.sap.com/docs/build-work-zone-standard-edition/sap-build-work-zone-standard-edition/manage-content-providers-on-premise).

    > ### Note:  
    > All users and groups are provisioned to the target SAP Build Work Zone, standard edition system with the providerID defined for this target system. If you want to use different providerIDs, you need to create separate target systems for every providerID.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cflp.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a user that already exists in the target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

    SAP Build Work Zone, standard edition supports the following unique attributes which are automatically filled in when the target system is added in the service UI:

    `emails[0].value,['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId'],externalId`

    -   If the user has an `externalId`, the conflict is resolved by `externalId` and `providerId`.

    -   If the user doesn't have an `externalId`, the conflict is resolved by `email` and `providerId`.


    The general rule is that to resolve the conflict, there should be an existing user who matches both unique attributes.

    However, when resolving conflicts, Identity Provisioning decides whether to update an existing user or create a new one based on several criteria: whether the user was created by the Identity Provisioning service, if any of the provisioning systems \(source or target\) have been reset, and last but not least, the unique combination of user attributes. For more information, see **Step 4**.

    > ### Recommendation:  
    > We recommend that you do not modify the value of the `cflp.user.unique.attribute` property. Otherwise, user creation fails.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cflp.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a group that already exists in the target system \(a conflicting group\), this property defines the unique attributes by which the existing group will be searched and resolved.

    SAP Build Work Zone, standard edition supports a pair of unique attributes which is automatically filled in when the target system is added in the service UI:

    `externalId,['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']`

    For the conflict to be resolved, an existing group matching both unique attributes should be found. In this case, Identity Provisioning updates the group. This means, the conflicting group overwrites the existing one. If the group matches only one of the unique attributes, the conflict is not resolved, and the group creation fails.

    > ### Recommendation:  
    > We recommend that you do not modify the value of the `cflp.group.unique.attribute` property. Otherwise, the group creation fails.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cflp.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    This property enables bulk operations for users and groups.

    When the property is enabled \(set to *true*\), the following operations can be executed by Identity Provisioning service in a single request:

    -   Create or delete multiple users

    -   Create, update, or delete multiple groups


    When the property is disabled \(set to *false*\), the following operations can be executed by Identity Provisioning service for a single entity at a time:

    -   Create or delete a user

    -   Create, update, or delete a group


    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cflp.bulk.operations.max.count`
    
    </td>
    <td valign="top">
    
    If you have enabled the bulk operations, you can use this property to set the number of operations to be provisioned per request.

    **Possible values:**

    Default value: *20*

    Maximum value: *100* 

    If you enter a number larger than 100, the service will replace it with the default value \(20\).
    
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

5.  Configure the transformations.

    Transformations are used to map user and group attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Build Work Zone, standard edition* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    **Mapping logic** – The behavior of the default transformation logic is to map all attributes from the internal SCIM representation to the target SAP Build Work Zone, standard edition entity.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Build Work Zone, standard edition system. For more information, see: [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **User Update and Uniqueness**

    The write transformation of SAP Build Work Zone, standard edition supports three user unique attributes: *externalId*, *email* and *providerId*. Only providerId is mandatory in combination with at least one of the other attributes. Based on the combinations of these attributes, there can be distinguished three types of users:

    -   User 1 - with *email* and *providerId*, but no *externalId*

    -   User 2 - with *externalId* and *providerId*, but no *email*

    -   User 3 - with all three attributes: *externalId*, *email* and *providerId*


    The uniqueness of the user is ensured by the combination of two unique attributes: the *providerId* and *externalId* or the *providerId* and the *email*.

    Updating an existing user in the target system depends on how the user is identified there \(its combination of unique attributes\) and whether Identity Provisioning is aware of this user:

    -   The existing user was created by a provisioning job \(that is, the service is aware of this user\).

        If the following attributes are changed in the source system: the *email* of user 1, the *externalId* of user 2, or the *email* or *externalId* of user 3, after running a new job, Identity Provisioning will update the existing user.

    -   The existing user was not created by a provisioning job or was created by one but afterwards the source and the target systems have been reset \(that is, the service is not aware of this user\).

        If the following attributes are changed in the source system, expect the subsequent results after running a new job:

        -   Changing the *email* of user 1 will result in creating a new user in the target system, because the user won’t match the combination of two unique attributes: *email* and *providerId*.

        -   Changing the *externalId* of user 2 will result in creating a new user in the target, because the user won’t match the combination of two unique attributes: *externalId* and *providerId*.

        -   Changing the *email* or the *externalId* of user 3 will result in updating the user in the target system, because the user will still match a combination of two unique attributes. However, changing both, the *email* and the *externalId*, of user 3 will result in creating a new user in the target system, because the user will match only one unique attribute - the *providerId*.



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
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "constant": "%cflp.providerId%",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']"
    >             },
    >             {
    >                 "condition": "$.emails[?(@.primary == true)].value == []",
    >                 "sourcePath": "$.emails[0].value",
    >                 "optional": true,
    >                 "targetPath": "$.emails[0].value"
    >             },
    >             {
    >                 "condition": "$.emails[?(@.primary == true)].value != []",
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails[0].value",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "condition": "$.emails[0].length() > 0",
    >                 "constant": true,
    >                 "targetPath": "$.emails[0].primary"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.groups[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups[?(@.value)]",
    >                 "functions": [
    >                     {
    >                         "entityType": "group",
    >                         "function": "resolveEntityIds"
    >                     }
    >                 ]
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
    >                 "constant": "%cflp.providerId%",
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId']"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:mapping",
    >                 "optional": true,
    >                 "targetPath": "$.schemas[1]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId",
    >                 "functions": [
    >                     {
    >                         "function":"replaceAllString",
    >                         "regex":"(?i)(^pcd:)",
    >                         "replacement":""
    >                     },
    >                     {
    >                         "function": "replaceString",
    >                         "target": "/",
    >                         "replacement": ":"
    >                     },
    >                     {
    >                         "function": "replaceString",
    >                         "target": "(",
    >                         "replacement": "@"
    >                     },
    >                     {
    >                         "function": "replaceString",
    >                         "target": ")",
    >                         "replacement": "+"
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

6.  Add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio8d6586f20b814b5f83c85448f3b0b715__postreq_gpc_lrj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Configure Integration with the Identity Provisioning Service](https://help.sap.com/docs/build-work-zone-standard-edition/sap-build-work-zone-standard-edition/configure-integration-with-identity-provisioning-service)

