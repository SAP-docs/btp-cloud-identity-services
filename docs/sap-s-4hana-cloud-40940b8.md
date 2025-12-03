<!-- loio40940b8223334b528e4899b92d42ce96 -->

# SAP S/4HANA Cloud

Follow this procedure to set up SAP S/4HANA Cloud as a target system.



<a name="loio40940b8223334b528e4899b92d42ce96__prereq_tcl_444_kfb"/>

## Prerequisites

To establish the connection between Identity Provisioning and SAP S/4HANA Cloud, you need to set up the communication \(user, system and arrangement\) on SAP S/4HANA Cloud. You can do it now \(as a prerequisite\) or in the process of configuring SAP S/4HANA Cloud as a target system, as described in step 3.



<a name="loio40940b8223334b528e4899b92d42ce96__context_tjq_xs3_kfb"/>

## Context

SAP S/4HANA Cloud is a complete enterprise resource planning \(ERP\) system with built-in intelligent technologies and advanced analytics.

You can use Identity Provisioning to configure SAP S/4HANA Cloud as a target system where you can provision users and group members from source systems of your choice.

SAP S/4HANA Cloud provides different APIs for integration with Identity Provisioning, resulting in different connector versions for each API. Each connector version supports specific attribute mappings within the transformations and requires particular property values. The value of the `s4hana.cloud.api.version` property controls which API you use. By default, the Identity Provisioning service uses API version *1*.

-   When the value is set to *1* or the property is not present \(typical for systems created before versioning was introduced on November 6, 2025\), the SOAP API provided by the communication scenario SAP\_COM\_0193 is used. In SAP S/4HANA Cloud connector version 1, groups correspond to business roles, thus group members are user assignments of a business role.

    > ### Note:  
    > Identity Provisioning cannot create and delete business roles in SAP S/4HANA Cloud target system. It can only create, update and delete user assignments of a role. Therefore, business roles must have been created in SAP S/4HANA Cloud system before you run a provisioning job.

    When SAP S/4HANA Cloud is configured as a target system, the integration with a human resource \(HR\) system is active by default. In this case, the synchronization of business partners is managed by the HR system and SAP S/4HANA Cloud. Identity Provisioning can only be used for managing business users \(login users and their login information, such as date/time preferences\) and role assignments.

    In SAP S/4HANA Cloud, business partners are the central master data objects that hold the complete person profile in the SAP S/4HANA Cloud. For example, business partners with role `Employee` and `Contingent Worker`. Business users are persons who can log on to SAP S/4HANA Cloud system to complete business tasks.

    For more information on how to update to version *3*, see [Update SAP S/4HANA Cloud](Operation-Guide/update-sap-s-4hana-cloud-6339b86.md).

-   When the value is set to *3*, the SCIM interface provided by the communication scenario SAP\_COM\_0465 is used. It supports provisioning of **business users** with their **assignments** to user groups and roles.

    This version allows you to create, update, and delete user groups, referred to as business user groups in SAP S/4HANA Cloud. However, similar to connector version 1, you cannot create or delete groups of type **authorization** \(business roles in SAP S/4HANA Cloud\). You can only update the role assignments. For more information, see [Groups](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/groups?locale=en-US&version=Cloud).

    > ### Note:  
    > For groups of the **userGroup** type, a user can have only one assignment at a time. If a user is assigned to a new group of the **userGroup** type, the previous assignment of the same type will be automatically removed, and the user will be exclusively assigned to the newly selected group.




<a name="loio40940b8223334b528e4899b92d42ce96__steps_ujq_xs3_kfb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP S/4HANA Cloud* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP S/4HANA Cloud and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP S/4HANA target system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/76867db8ce534becbfc08b050695df8e.html?version=Cloud).

        Skip step **a.** if you want to use basic authentication.

        The next steps are performed in SAP S/4HANA backend system and are relevant for both basic and certificate-based authentication.

    2.  [Create a communication user](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/Latest/en-US/0377adea0401467f939827242c1f4014.html) and provide the respective credentials.

        For basic authentication, provide *User Name* and *Password*.

        For certificate-based authentication, upload the certificate you have generated in the Identity Provisioning UI on the previous step.

    3.  [Create a communication system](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/Latest/en-US/1bfe32ae08074b7186e375ab425fb114.html) and assign the created user to the communication system.

        For your Identity Provisioning scenario, provide *System ID*, *System Name* and *Host Name*.

    4.  [Create a communication arrangement](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/Latest/en-US/a0771f6765f54e1c8193ad8582a32edb.html) with the created system.

        -   When `s4hana.cloud.api.version`=`1` is set in Identity Provisioning for the SAP S/4HANA Cloud target system, choose *Scenario ID* SAP\_COM\_0193 \(SAP Cloud Identity Provisioning Integration\).

            > ### Note:  
            > The communication scenario *SAP\_COM\_0193* is enhanced to support the User UUID attribute which is generated by Identity Authentication at user creation.
            > 
            > The User UUID is universally unique identifier. This attribute is immutable and unique across technology layers, such as user interface, APIs, and security tokens, as well as across products and lines of business contributing to a business process in the Intelligent Enterprise.

        -   When `s4hana.cloud.api.version`=`3` is set in Identity Provisioning for the SAP S/4HANA Cloud target system, choose *Scenario ID* SAP\_COM\_0465 \(System for Cross-domain Identity Management Integration\).

            > ### Note:  
            > The communication scenario *SAP\_COM\_0465* allows you to maintain data via SCIM \(System for Cross-domain Identity Management\). For more information, see [Integrate Cross-Domain Identity Management](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/aa4b03ced9dc481fafdf74c2f82976bc.html?version=2508.500).



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
    
    Enter the SAP S/4HANA Cloud API URL.

    You can find the correct URL in the *API-URL* field of the communication arrangement set up for the communication scenario used.

    For example: `https://my123456-api.s4hana.ondemand.com`
    
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
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    Enter the *User Name*

    > ### Restriction:  
    > Do not use special symbol '**,**' \(comma\) as it is not supported.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Valid if *BasicAuthentication* is configured as authentication method.

    Enter the *Password* for the user name from the communication arrangement.

    > ### Restriction:  
    > Do not use special symbol '**,**' \(comma\) as it is not supported.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.cloud.api.version`
    
    </td>
    <td valign="top">
    
    The version of the system API you use.

    By default, Identity Provisioning uses version *1*.

    Version *1* means your SAP S/4HANA Cloud system consumes SAP S/4HANA Cloud API: Business User.

    Version *3* means your SAP S/4HANA Cloud system consumes System for Cross-domain Identity Management \(SCIM\) API.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.cloud.hr.switch.active`
    
    </td>
    <td valign="top">
    
    Defines whether the human resources \(HR\) integration is active or not.

    The property is set to ***true*** by default. This means that the synchronization of business partners is managed by the HR system and SAP S/4HANA Cloud. When set to `false`, synchronization is handled by the identity management system instead.

    **Possible values:**

    -   true \(default\)

    -   false


    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.cloud.hr.switch.dependent.role.codes`
    
    </td>
    <td valign="top">
    
    A default property.

    As a comma-separated value, add the codes of the roles maintained by the HR integration. Make sure these role codes are part of your *read* and *write* transformations.

    By default, the following codes are added to your system: **BUP003 and BBP005**. That means, your HR integration will support *employees* and *contingent workers*.

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ips.date.variable.format`
    
    </td>
    <td valign="top">
    
    *yyyy-MM-dd*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.cloud.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a user that already exists in the SAP S/4HANA Cloud target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

    > ### Note:  
    > You can configure this property only when the integration between a human resource \(HR\) system and SAP S/4HANA Cloud target system is **OFF**.

    The possible values of this property depend on the API version which your SAP S/4HANA Cloud system consumes.

    Possible values:

    -   If your system consumes SAP S/4HANA Cloud API: Business User, the service searches for an existing user by *personExternalID* and *emails\[0\].value*.

        According to your use case, choose how to set up the property:

        -   Default behavior: This property does not appear in the UI during system creation. Its default value is *personExternalID*. That means, if the service finds an existing user by a *personExternalID*, it updates this user with the data of the conflicting one.

            If a user with such а *personExternalID* is not found, the creation of the conflicting user fails.

        -   Value = *emails\[0\].value*. If the service finds an existing user matching both unique attributes *email* and *personExternalID*, it updates this user with the data of the conflicting one. If the service finds an existing user matching only the *email*, the update of the existing user fails.

            If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


    -   If your system consumes System for Cross-domain Identity Management \(SCIM\) API, the service searches for an existing user by *userName*, *emails\[0\].value*, *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes.

        According to your use case, choose how to set up the property:

        -   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
        -   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
        -   Value = *externalId*. If the service finds an existing user with *externalId*, it updates this user with the data of the conflicting one. If a user with such *externalId* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


    For more information, see [List of Properties](list-of-properties-d6f3577.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.cloud.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP S/4HANA Cloud groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `S4HANACLOUD_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `S4HANACLOUD_` prefix in their display name will be provisioned to SAP S/4HANA Cloud. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be provisioned to SAP S/4HANA Cloud.

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

    **Relevant for connector version 3**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.cloud.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If the Identity Provisioning tries to create a group that already exists in the SAP S/4HANA Cloud target system, the creation will fail. In this case, the existing group only needs to be updated.

    In SAP S/4HANA Cloud the uniqueness of a group is defined by the combination of the following two attributes, which are automatically filled in when the target system is created: *externalId,\['urn:ietf:params:scim:schemas:extension:sap:2.0:Group'\]\['type'\]*. To resolve the conflict, an existing group must match both of these attributes. If the group matches only one of the attributes, the conflict is not resolved, and group creation will fail.

    > ### Note:  
    > Although you can define your own unique combination of attributes \(for example, *externalId,displayName*\), we recommend that you do not modify the automatically filled value of the `s4hana.cloud.group.unique.attribute` property.

    If the property is not specified, the search is done by the default attribute *displayName*.

    **Relevant for connector version 3**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.cloud.patch.group.members.above.threshold`
    
    </td>
    <td valign="top">
    
    Defines the threshold number of group members above which they are provisioned on batches with `PATCH` requests, and below which they are provisioned with `PUT` request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

    The expected value is a positive integer without any separators, such as a space, comma, or period.

    **Possible values**: integer

    Default value: *20000*

    Minimum value: *1*

    Maximum value: *20000*

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

    > ### Note:  
    > Regardless of the threshold number you define, when removing group members in SAP S/4HANA Cloud, the maximum number of members which can be removed per one `PATCH` request is 50.

    **Relevant for connector version 3**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.cloud.user.roles.overwrite`
    
    </td>
    <td valign="top">
    
    This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP S/4HANA Cloud target system.

    -   **true** – the current user roles will be deleted in the target system, and the user will be updated only with the roles provisioned by the service.
    -   **false** – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the target system.

    See also: [Extended Explanation of the \*.user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.cloud.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request. For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

    If not specified, the default value is *false*.

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.cloud.bulk.operations.max.count`
    
    </td>
    <td valign="top">
    
    If you have enabled the bulk operations, you can use this property to set the number of users to be provisioned per request.

    The default value, if not specified, is *20*.

    The maximum value is **100**. If you enter a number larger than 100, the service will replace it with the default value \(20\).

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.roles`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of user assignments of a role to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of user assignments of a role, for example by adding a filter or condition.

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

    Exemplary destination:


    <table>
    <tr>
    <td valign="top">
    
    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `ProxyType`=*Internet*

    `URL`=*https://my1234567-api.s4hana.ondemand.com*

    `User`=*MyS4HANAuser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `s4hana.cloud.api.version`=*1*

    `ips.date.variable.format`=*yyyy-MM-dd*

    `s4hana.cloud.hr.switch.active`=*true*

    `s4hana.cloud.hr.switch.dependent.role.codes`=*BUP003,BBP005*

    `s4hana.cloud.user.roles.overwrite` = *false*

    `s4hana.cloud.support.bulk.operation` = *true*

    `s4hana.cloud.bulk.operations.max.count` = *50*
    
    </td>
    </tr>
    </table>
    
6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. Identity Provisioning offers a default transformation for the *SAP S/4HANA Cloud* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules depending on your setup of entities in SAP S/4HANA Cloud. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP S/4HANA Cloud API: Business User](https://help.sap.com/viewer/f1531d40f450474dbf95f0404cb62007/latest/en-US/640fb5fa26664a7486de073b1882405c.html)

    [System for Cross-domain Identity Management \(SCIM\)](https://api.sap.com/api/CE_APS_IAM_API_SCIM/overview)

    [Integrate Cross-Domain Identity Management](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/aa4b03ced9dc481fafdf74c2f82976bc.html?version=2508.500)

    **Default transformation for connector version 1:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "('%s4hana.cloud.roles.prefix%' === 'null') || ($.groups[?(@.display =~ /%s4hana.cloud.roles.prefix%.*/)] empty false)",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.personExternalID"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.personExternalID",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true,
    >         "targetPath": "$.personExternalID"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$.user.globalUserID"
    >       },
    >       {
    >         "targetPath": "$.personID",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "targetPath": "$.markedForArchivingIndicator",
    >         "constant": "false"
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "optional": true,
    >         "targetPath": "$.user.timeZoneCode",
    >         "functions": [
    >           {
    >             "type": "convertTimezoneCode",
    >             "outputFormat": "sap"
    >           }
    >         ],
    >         "defaultValue": "CET"
    >       },
    >       {
    >         "type": "valueMapping",
    >         "sourcePaths": [
    >           "$.userType"
    >         ],
    >         "targetPath": "$.businessPartnerRoleCode",
    >         "defaultValue": "BUP003",
    >         "valueMappings": [
    >           {
    >             "key": [
    >               "Employee"
    >             ],
    >             "mappedValue": "BUP003"
    >           },
    >           {
    >             "key": [
    >               "Contingent Worker"
    >             ],
    >             "mappedValue": "BBP005"
    >           }
    >         ]
    >       },
    >       {
    >         "scope": "createEntity",
    >         "sourceVariable": "currentDate",
    >         "targetPath": "$.user.validityPeriod.startDate"
    >       },
    >       {
    >         "scope": "createEntity",
    >         "constant": "9999-12-31",
    >         "targetPath": "$.user.validityPeriod.endDate"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.personalInformation.firstName",
    >         "optional": true
    >       },
    >       {
    >         "condition": "%s4hana.cloud.hr.switch.active% != null && %s4hana.cloud.hr.switch.active% == true",
    >         "optional": true,
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.personalInformation.lastName"
    >       },
    >       {
    >         "condition": "%s4hana.cloud.hr.switch.active% == null || %s4hana.cloud.hr.switch.active% == false",
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.personalInformation.lastName"
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "targetPath": "$.personalInformation.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.formatted",
    >         "targetPath": "$.personalInformation.personFullName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.user.userName"
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "targetPath": "$.user.logonLanguageCode",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.workplaceInformation.emailAddress",
    >         "optional": true
    >       },
    >       {
    >         "targetPath": "$.user.lockedIndicator",
    >         "constant": "false"
    >       },
    >       {
    >         "condition": "$.active == false",
    >         "targetPath": "$.user.lockedIndicator",
    >         "constant": "true"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, s4hana.cloud.roles.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], s4hana.cloud.roles.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, s4hana.cloud.roles.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%s4hana.cloud.roles.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, s4hana.cloud.roles.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%s4hana.cloud.roles.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "function": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   }
    > }
    > ```

    See also: [nullExtended Explanation of the \*user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

    **Default transformation for connector version 3:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "(('%s4hana.cloud.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%s4hana.cloud.group.prefix%.*/)] empty false))",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "constant": ["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:sap:2.0:User"],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "functions": [
    >           {
    >             "function": "toUpperCaseString",
    >             "locale": "en_EN"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.externalId",
    >         "functions": [
    >           {
    >             "function": "toUpperCaseString",
    >             "locale": "en_EN"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "targetPath": "$.externalId",
    >         "optional": true,
    >         "functions": [
    >           {
    >             "function": "toUpperCaseString",
    >             "locale": "en_EN"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true,
    >         "functions": [
    >           {
    >             "function": "toUpperCaseString",
    >             "locale": "en_EN"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.name.formatted",
    >         "optional": true,
    >         "targetPath": "$.name.formatted"
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
    >         "sourcePath": "$.displayName",
    >         "optional": true,
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails",
    >         "functions": [
    >           {
    >             "function": "putIfAbsent",
    >             "key": "type",
    >             "defaultValue": "work"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.addresses",
    >         "targetPath": "$.addresses",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "optional": true,
    >         "targetPath": "$.userType"
    >       },
    >       {
    >         "sourcePath": "$.preferredLanguage",
    >         "optional": true,
    >         "targetPath": "$.preferredLanguage"
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "optional": true,
    >         "targetPath": "$.locale"
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "optional": true,
    >         "targetPath": "$.timezone"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "optional": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['decimalFormatCode']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['decimalFormatCode']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['dateFormatCode']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['dateFormatCode']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['timeFormatCode']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['timeFormatCode']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuidHistory']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuidHistory']",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.groups[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups[?(@.value)]",
    >         "functions": [
    >           {
    >             "entityType": "group",
    >             "type": "resolveEntityIds"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, s4hana.cloud.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], s4hana.cloud.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings": [
    >       {
    >         "targetPath": "$.id",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "constant": ["urn:ietf:params:scim:schemas:core:2.0:Group","urn:ietf:params:scim:schemas:extension:sap:2.0:Group"],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, s4hana.cloud.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%s4hana.cloud.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.externalId",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, s4hana.cloud.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%s4hana.cloud.group.prefix%",
    >             "replacement": ""
    >           },
    >           {
    >             "function": "toUpperCaseString",
    >             "locale": "en_EN"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true,
    >         "functions": [
    >           {
    >             "function": "toUpperCaseString",
    >             "locale": "en_EN"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "entityType": "user",
    >             "type": "resolveEntityIds"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']",
    >         "optional": true,
    >         "targetPath": "$.externalId",
    >         "functions": [
    >           {
    >             "function": "toUpperCaseString",
    >             "locale": "en_EN"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "optional": true,
    >         "defaultValue": "userGroup"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "optional": true
    >       }
    >     ]
    >   }
    > }
    > ```

    **Group Uniqueness and Provisioning**

    In the most common scenario, Identity Authentication connector version 2 or Local Identity Directory is used as the source system for groups and SAP S/4HANA Cloud connector version 3 is the target system.

    In SAP S/4HANA Cloud version 3, the uniqueness of a group is defined by the combination of `externalId` and `type` attributes. The system supports two group types: `userGroup` and `authorization` \(role\). As a result, two different groups can share the same `externalId` while belonging to different types, potentially causing conflicts when provisioned to the target system.

    To avoid conflicts, ensure the following:

    -   Your SAP S/4HANA Cloud target system must be updated to version 3, as described in [Update SAP S/4HANA Cloud](Operation-Guide/update-sap-s-4hana-cloud-6339b86.md) and it must have the group uniqueness property: `s4hana.cloud.group.unique.attribute`, set with the following combination of values: `externalId,['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']`. For more information, see [List of Properties](list-of-properties-d6f3577.md).

    -   The groups in your Identity Authentication connector version 2 or Local Identity Directory source systems must have a value for the `externalName` attribute, which is mapped to the `externalId` attribute.


7.  Now, add a source system from which to read users and roles. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio40940b8223334b528e4899b92d42ce96__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP S/4HANA Cloud Documentation](https://help.sap.com/viewer/9d794cbd48c648bc8a176e422772de7e/latest/en-US/7af7b8541486ed05e10000000a4450e5.html)

