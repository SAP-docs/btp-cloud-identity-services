<!-- loio6544f38b8d8943c594552744ac2cf293 -->

# SAP SuccessFactors

Follow this procedure to set up SAP SuccessFactors as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

-   You are using **SAP SuccessFactors HCM Suite OData API**

    You have created a technical user with permissions to **call** the SAP SuccessFactors HCM Suite OData API to **import** employee data into an SAP SuccessFactors system. For more information, see [Permissions](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/3d71f690709243db99102127557a3d73.html?version=Latest), [Setting Up an API User for Sync Jobs in SAP SuccessFactors](https://help.sap.com/viewer/568fdf1f14f14fd089a3cd15194d19cc/latest/en-US/0a6e6705d89e42649e3aa8732f2b0724.html) and [URI Conventions \(OData Version 2.0\)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).

-   You are using **SAP SuccessFactors Workforce SCIM API**

    Consumers of the SAP SuccessFactors Workforce SCIM API can either create a technical user and assign the necessary permissions, or use the predefined technical user with built-in permissions for communication between SAP SuccessFactors and Identity Provisioning using certificate authentication. For more information, see [Upgrade to X.509 Certificate-Based Authentication for Incoming Calls](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/2b8f220f51ce455da3f349ef851d264c.html?version=Latest) and [Permissions](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html?version=Latest#permissions).




## Context

SAP SuccessFactors provides two APIs for its integration with Identity Provisioning: SAP SuccessFactors HCM Suite OData API and SAP SuccessFactors Workforce SCIM API. The value of `sf.api.version` property controls which API you use.

-   When the value is set to `1`, or the property is not defined - SAP SuccessFactors HCM Suite OData API \(in short, OData API\) is used. This is the default value. SAP SuccessFactors source systems created before the introduction of `sf.api.version` property, use OData API.

    This version allows you to create and update **users**, as well as update **dynamic groups** and **group members**. To update a group from the source system, a group with the same name should already exist in SAP SuccessFactors.

    > ### Restriction:  
    > Note the following restrictions when using SAP SuccessFactors HCM Suite OData API:
    > 
    > -   You cannot *create* or *delete* groups as these operations are currently not supported.
    > 
    > -   Managing SAP SuccessFactors **static groups** is not supported.

-   When the value is set to `2` - SAP SuccessFactors Workforce SCIM API \(in short, SCIM API\) is used.

    This version allows you to provision static permission groups and user's group assignments. Provisioning of user's group assignments from a given source system to SAP SuccessFactors target system is possible if the user is an active employee with a work assignment and has a value of the `perPersonUuid` attribute. Alternatively, `personIdExternal` could be used as a fallback attribute.

    This requires that SAP SuccessFactors users are first provisioned with the attribute to the given system, for example Identity Authentication, where the `perPersonUuid` must be mapped to a custom attribute. Afterwards, assigning users to groups in Identity Authentication and running a provisioning job would result in correct user assignments in SAP SuccessFactors target.

    To update a group from the source system, a group with the same name should already exist in SAP SuccessFactors.

    > ### Restriction:  
    > Note the following restrictions when using SAP SuccessFactors Workforce SCIM API:
    > 
    > -   You cannot *create* or *delete* groups using the `Groups` APIs.
    > 
    > -   The `Groups` patch API only supports updating membership of static permission groups.
    > 
    > 
    > For more information, see [Overview of SAP SuccessFactors Workforce System for Cross-Domain Identity Management API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html?version=2311).


For more information about the difference between static and dynamic groups in SAP SuccessFactors, see [Permission Groups](https://help.sap.com/docs/SAP_SUCCESSFACTORS_ONBOARDING/12be6a11886846cba1de18bf9027a0b6/edcaffe1b2e64e2683347de16325750c.html?version=2305).

For more information on how to update to version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).

You can configure *SAP SuccessFactors* as a target system to provision entities from a given source system. With regards to user termination, it is a standard HR process that is triggered from the SAP SuccessFactors system.



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP SuccessFactors* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP SuccessFactors and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP SuccessFactors target system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/76867db8ce534becbfc08b050695df8e.html?version=Cloud).

        Skip this step if you use basic authentication. The next steps are performed in SAP SuccessFactors Admin Center and are relevant for certificate-based authentication only.

    2.  Login to SAP SuccessFactors and go to *Admin Center*. Follow the procedure described in [Upgrade to X.509 Certificate-Based Authentication for Incoming Calls](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/2b8f220f51ce455da3f349ef851d264c.html).

        Make sure you select *Identity Provisioning Service* in the *Integration Name* field.


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
    
    Specify the URL to your SAP SuccessFactors API.

    For example:

    -   For version 1:

        -   When *BasicAuthentication* is configured as authentication method:

            `https://apitest.successfactors.com/odata/v2`

        -   When *ClientCertificateAuthentication* is configured as authentication method:

            `https://apitest.cert.successfactors.com/odata/v2`


    -   For version 2:

        -   When *BasicAuthentication* is configured as authentication method:

            `https://apitest.successfactors.com`

        -   When *ClientCertificateAuthentication* is configured as authentication method:

            `https://apitest.cert.successfactors.com`



    To see the list of all SAP SuccessFactors data centers, see: [SAP SuccessFactors API Reference Guide \(OData V2\): List of SAP SuccessFactors API Servers](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/af2b8d5437494b12be88fe374eba75b6.html?locale=en-US&version=2411) and [System for Cross-domain Identity Management for Workforce in SuccessFactors](https://api.sap.com/api/PLTScim/resource) 
    
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
    
    Enter your authentication method:

    -   *BasicAuthentication*

    -   *ClientCertificateAuthentication*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.api.version`
    
    </td>
    <td valign="top">
    
    Handles the version of the API which is consumed by the SAP SuccessFactors system.

    **Possible values:**

    -   *1* - Indicates that SAP SuccessFactors HCM Suite OData API \(in short, OData API\) is used.

    -   *2* - Indicates that SAP SuccessFactors Workforce SCIM API \(in short, SCIM API\) is used.


    Default value: *1*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    Enter the *userID* of your SAP SuccessFactors technical user in the following format: **<user\_ID\>@<company\_ID\>**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Valid if *BasicAuthentication* is configured as authentication method.

    Enter the password for your SAP SuccessFactors technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sf.company.id`
    
    </td>
    <td valign="top">
    
    Valid if *ClientCertificateAuthentication* is configured as authentication method.

    Enter the Company ID of your SAP SuccessFactors system.

    The Company ID is a short string of characters that identifies each SAP SuccessFactors system. It is like a username for your organization. All users of the same system share the same Company ID.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sf.user.attributes`
    
    </td>
    <td valign="top">
    
    Default property. It's a string representing a comma-separated list of user attributes by which the Identity Provisioning service retrieves the users that have to be updated in SAP SuccessFactors during the writing process. You can leave the default property value \(all listed attributes\), or leave only some of them.

    > ### Remember:  
    > Always make sure that attribute `lastModifiedDateTime` is in the list. If you don't specify it, the provisioning to SAP SuccessFactors will fail.

    **Connector version**: SAP SuccessFactors version 1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sf.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

    This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). **If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one.** If the service does not find such a user, the creation will fail.

    According to your use case and system type, choose how to set up this property:

    -   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
    -   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
    -   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

    **Possible values:**

    -   *userName*
    -   *emails\[0\].value*
    -   *userName,emails\[0\].value*
    -   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes

    Default value: *userName*

    **Connector version**: SAP SuccessFactors version 2
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.user.attributes.expand`
    
    </td>
    <td valign="top">
    
    This property writes additional user data related to *complex attributes*, which are specified in `sf.user.attributes`.

    Default value: *personKeyNav*

    **Connector version**: SAP SuccessFactors version 1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sf.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If the service tries to create a group that already exists in the target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\).

    To make the search filter by a specific attribute, specify this attribute as a value for the `sf.group.unique.attribute` property.

    If the property is not specified, the search is done by the default attribute: *displayName*

    **Connector version**: SAP SuccessFactors version 2
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP SuccessFactors groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `SF_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `SF_` prefix in their display name will be provisioned to SAP SuccessFactors. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, the SAP SuccessFactors groups will be read and provisioned to the target system with their actual display names.

    **Connector version**: SAP SuccessFactors version 2
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified users in the source system are updated in the target system.

    -   If set to *true*, `PATCH` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, only this change will be provisioned and applied in the target system.

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

    **Connector version**: SAP SuccessFactors version 2
    
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

    Exemplary destination \(configuration\):


    <table>
    <tr>
    <td valign="top">
    
    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `ProxyType`=*Internet*

    `URL`=*https://apitest.successfactors.com/odata/v2*

    `User`=*sfsf\_admin@mycompany.com*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `sf.user.attributes`=*userId,username,addressLine1,jobTitle,lastName,country,email,location,firstName,lastModifiedDateTime,personKeyNav,manager/username*

    `sf.user.attributes.expand`=*personKeyNav,manager*
    
    </td>
    </tr>
    </table>
    
6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP SuccessFactors* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    When you configure SAP SuccessFactors as a target system, the Identity Provisioning service will read all user attributes from the selected source system and write them as user records in SAP SuccessFactors. Groups can be only updated if such already exist in SAP SuccessFactors.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP SuccessFactors. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP SuccessFactors HCM Suite OData API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?locale=en-US&version=latest)

    [SAP SuccessFactors Workforce SCIM API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html)

    To make group assignments via the user resource, you need to change the default transformation of the target system as described in [Enabling Group Assignment](Operation-Guide/enabling-group-assignment-0d80033.md).

    **Default transformation for SAP SuccessFactors HCM Suite OData API version 1:** 

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "skipOperations": [
    >             "delete"
    >         ],
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.userId"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userId",
    >                 "scope": "createEntity"
    >             },
    >             {
    >                 "constant": "t",
    >                 "targetPath": "$.status"
    >             },
    >             {
    >                 "condition": "$.active == false",
    >                 "constant": "f",
    >                 "targetPath": "$.status"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "optional": true,
    >                 "targetPath": "$.username"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional": true,
    >                 "targetPath": "$.lastName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true,
    >                 "targetPath": "$.firstName"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificPrefix",
    >                 "optional": true,
    >                 "targetPath": "$.salutation"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificSuffix",
    >                 "optional": true,
    >                 "targetPath": "$.suffix"
    >             },
    >             {
    >                 "sourcePath": "$.emails[0].value",
    >                 "optional": true,
    >                 "targetPath": "$.email"
    >             },
    >             {
    >                 "condition": "$.emails[?(@.primary == true)].value != []",
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.email",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "optional": true,
    >                 "targetPath": "$.timeZone"
    >             },
    >             {
    >                 "sourcePath": "$.nickName",
    >                 "optional": true,
    >                 "targetPath": "$.nickname"
    >             },
    >             {
    >                 "sourcePath": "$.addresses[0].country",
    >                 "optional": true,
    >                 "targetPath": "$.country"
    >             },
    >             {
    >                 "condition": "$.addresses[?(@.primary == true)].country != []",
    >                 "sourcePath": "$.addresses[?(@.primary == true)].country",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.country",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.addresses[0].locality",
    >                 "optional": true,
    >                 "targetPath": "$.city"
    >             },
    >             {
    >                 "condition": "$.addresses[?(@.primary == true)].locality != []",
    >                 "sourcePath": "$.addresses[?(@.primary == true)].locality",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.city",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.addresses[0].formatted",
    >                 "optional": true,
    >                 "targetPath": "$.addressLine1"
    >             },
    >             {
    >                 "sourcePath": "$.addresses[1].formatted",
    >                 "optional": true,
    >                 "targetPath": "$.addressLine2"
    >             },
    >             {
    >                 "sourcePath": "$.addresses[2].formatted",
    >                 "optional": true,
    >                 "targetPath": "$.addressLine3"
    >             },
    >             {
    >                 "condition": "$.phoneNumbers[?(@.type == 'work')].value != []",
    >                 "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.businessPhone",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "condition": "$.phoneNumbers[?(@.type == 'fax')].value != []",
    >                 "sourcePath": "$.phoneNumbers[?(@.type == 'fax')].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.fax",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "condition": "$.phoneNumbers[?(@.type == 'mobile')].value != []",
    >                 "sourcePath": "$.phoneNumbers[?(@.type == 'mobile')].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.cellPhone",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "condition": "$.phoneNumbers[?(@.type == 'home')].value != []",
    >                 "sourcePath": "$.phoneNumbers[?(@.type == 'home')].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.homePhone",
    >                 "functions": [
    >                     {
    >                         "function": "elementAt",
    >                         "index": 0
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >                 "optional": true,
    >                 "targetPath": "$.empId"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "optional": true,
    >                 "targetPath": "$.division"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "optional": true,
    >                 "targetPath": "$.department"
    >             }
    >         ]
    >     },
    > 
    > // By default, the group mapping is inactive (ignored) but groups are supported. 
    > // To start provisioning groups, either delete the statement "ignore": true, or set its value to false.
    >     "group": {
    >         "ignore": true,
    >         "skipOperations": [
    >             "delete"
    >         ],
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.groupID"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.groupName"
    >             },
    >             {
    >                 "constant": "DynamicGroup",
    >                 "targetPath": "$.__metadata.uri"
    >             },
    >             {
    >                 "constant": "permission",
    >                 "targetPath": "$.groupType"
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

    **Default transformation for SCIM API version 2**:

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:extension:successfactors:2.0:User",
    >           "urn:ietf:params:scim:schemas:core:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:sap:2.0:User",
    >           "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "targetPath": "$.userType"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.locale",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "condition": "$.emails.length() > 0",
    >         "targetPath": "$.emails[*].type",
    >         "constant": "work"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "optional": true,
    >         "targetPath": "$.name.middleName"
    >       },
    >       {
    >         "sourcePath": "$.name.honorificPrefix",
    >         "optional": true,
    >         "targetPath": "$.name.honorificPrefix"
    >       },
    >       {
    >         "sourcePath": "$.name.honorificSuffix",
    >         "optional": true,
    >         "targetPath": "$.name.honorificSuffix"
    >       },
    >       {
    >         "sourcePath": "$.name.formatted",
    >         "optional": true,
    >         "targetPath": "$.name.formatted"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['perPersonUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['perPersonUuid']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['loginMethod']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['loginMethod']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['personIdExternal']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['personIdExternal']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['customFields']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['customFields']"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.groups[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups[?(@.value)]",
    >         "functions": [
    >           {
    >             "entityType": "group",
    >             "function": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "('%sf.group.prefix%' === 'null') || ($.displayName =~ /%sf.group.prefix%.*/)",
    >     "skipOperations": [
    >       "delete"
    >     ],
    >     "mappings": [
    >       {
    >         "targetPath": "$.id",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "scope": "createEntity",
    >         "functions": [
    >           {
    >             "condition": "('%sf.group.prefix%' !== 'null') && (@ =~ /%sf.group.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%sf.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "targetPath": "$.members",
    >         "type": "remove"
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "targetPath": "$.members[?(@.value)]",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true,
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

7.  Now, add a source system to read users from it. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio6544f38b8d8943c594552744ac2cf293__postreq_vng_gqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

[URI Conventions \(OData Version 2.0\)](http://www.odata.org/documentation/odata-version-2-0/uri-conventions)

[SAP SuccessFactors HCM Suite OData API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?version=latest)

[SAP SuccessFactors Workforce SCIM API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html)

