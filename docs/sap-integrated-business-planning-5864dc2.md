<!-- loio5864dc217f31443dab6d32fd2eeefda9 -->

# SAP Integrated Business Planning

Follow this procedure to set up SAP Integrated Business Planning \(in short, SAP IBP\) as a target system.



<a name="loio5864dc217f31443dab6d32fd2eeefda9__prereq_tcl_4r3_kfb"/>

## Prerequisites

To establish the connection between Identity Provisioning and SAP Integrated Business Planning, you need to set up the communication \(user, system and arrangement\) on SAP Integrated Business Planning. You can do it now \(as a prerequisite\) or in the process of configuring SAP Integrated Business Planning as a target system, as described in step 3.



<a name="loio5864dc217f31443dab6d32fd2eeefda9__context_tjq_xs3_kfb"/>

## Context

SAP Integrated Business Planning is a cloud-based solution that combines sales and operations planning \(S&OP\), forecasting and demand, response and supply, demand-driven replenishment, and inventory planning.

You can use Identity Provisioning to configure SAP IBP as a target system where you can provision entities from a particular source system. This scenario supports provisioning **users** and **role assignments**. In SAP Integrated Business Planning, groups correspond to roles, thus group members are user assignments of a role.

> ### Note:  
> Identity Provisioning cannot create and delete roles in SAP Integrated Business Planning target system. It can only create, update and delete user assignments of a role. Therefore, roles must have been created in SAP Integrated Business Planning system before you run a provisioning job.
> 
> For example, if you try to create or delete a role in SAP Integrated Business Planning, Identity Provisioning will only add or remove the user assignments of that role, respectively.

The Identity Provisioning service manages the complete set of **business partners** and their relevant **business users** \(employee\).

SAP Integrated Business Planning provides different APIs for integration with Identity Provisioning, resulting in different connector versions for each API. Each connector version supports specific attribute mappings within the transformations and requires particular property values. By default, the Identity Provisioning service uses version *1*. The value of the `ibp.api.version` property controls which API you use.

-   When the value is set to *1*, or the property is not defined \(typical for systems created before versioning was introduced on June 3, 2025\), SAP Integrated Business Planning API: Business User is used. This API version is SOAP based. It supports provisioning **users** and **role assignments**. In SAP Integrated Business Planning version 1, groups correspond to roles, thus group members are user assignments of a role.

    > ### Note:  
    > Identity Provisioning cannot create and delete roles in SAP Integrated Business Planning target system. It can only create, update and delete user assignments of a role. Therefore, roles must have been created in SAP Integrated Business Planning system before you run a provisioning job.
    > 
    > For example, if you try to create or delete a role in SAP Integrated Business Planning, Identity Provisioning will only add or remove the user assignments of that role, respectively.

    For more information on how to update to version *2*, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).

-   When the value is set to *2*, SCIM Interface for IAM is used. It supports provisioning of **business users** with their **assignments** to groups of type **userGroup** and **authorization**. For more information, see [Groups](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/groups?locale=en-US&version=Cloud).




<a name="loio5864dc217f31443dab6d32fd2eeefda9__steps_ujq_xs3_kfb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Integrated Business Planning* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP Integrated Business Planning and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP Integrated Business Planning target system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/76867db8ce534becbfc08b050695df8e.html?version=Cloud).

        Skip step **a.** if you want to use basic authentication.

        The next steps are performed in SAP Integrated Business Planning backend system and are relevant for both basic and certificate-based authentication.

    2.  [Create a communication user](https://help.sap.com/viewer/feae3cea3cc549aaa9d9de7d363a83e6/Latest/en-US/4bff8d203d4c4b1c8dd25564d1913302.html) and provide the respective credentials.

        For basic authentication, provide *User Name* and *Password*.

        For certificate-based authentication, upload the certificate you have generated in the Identity Provisioning UI on the previous step.

    3.  [Create a communication system](https://help.sap.com/viewer/feae3cea3cc549aaa9d9de7d363a83e6/Latest/en-US/084a6cce1a7e4c3c9c2f2bca8384b243.html) and assign the created user to the communication system.

        For your Identity Provisioning scenario, provide *System ID*, *System Name* and *Host Name*.

    4.  [Create a communication arrangement](https://help.sap.com/viewer/feae3cea3cc549aaa9d9de7d363a83e6/Latest/en-US/065d578693334cbeb86b8f31f0edfc93.html) with the created system.

        For your Identity Provisioning scenario, choose *Scenario ID* SAP\_COM\_0193 \(SAP Cloud Identity Provisioning Integration\).

        > ### Note:  
        > The communication scenario *SAP\_COM\_0193* is enhanced to support the User UUID attribute which is generated by Identity Authentication at user creation.
        > 
        > The User UUID is universally unique identifier. This attribute is immutable and unique across technology layers, such as user interface, APIs, and security tokens, as well as across products and lines of business contributing to a business process in the Intelligent Enterprise.

        -   When SAP Integrated Business Planning version *1* is used:

            For your Identity Provisioning scenario, choose *Scenario ID* SAP\_COM\_0193 \(SAP Cloud Identity Provisioning Integration\).

            > ### Note:  
            > The communication scenario *SAP\_COM\_0193* is enhanced to support the User UUID attribute which is generated by Identity Authentication at user creation.
            > 
            > The User UUID is universally unique identifier. This attribute is immutable and unique across technology layers, such as user interface, APIs, and security tokens, as well as across products and lines of business contributing to a business process in the Intelligent Enterprise.

        -   When SAP Integrated Business Planning version *2* is used:

            For your Identity Provisioning scenario, choose *Scenario ID* SAP\_COM\_0465 \(System for Cross-domain Identity Management Integration\).

            > ### Note:  
            > The communication scenario *SAP\_COM\_0465* allows you to maintain data via SCIM \(System for Cross-domain Identity Management\). For more information, see [Integrate Cross-Domain Identity Management](https://help.sap.com/docs/SAP_INTEGRATED_BUSINESS_PLANNING/feae3cea3cc549aaa9d9de7d363a83e6/09a1bebaf6eb4954af2df326b025d0ec.html?locale=en-US&version=2505).



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
    
    Specify the URL to your SAP IBP system.
    
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

    Enter the *User Name* from the communication arrangement.

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
    
    `ibp.api.version`
    
    </td>
    <td valign="top">
    
    The API version which is consumed by the SAP Integrated Business Planning system.

    By default, Identity Provisioning uses version *1*.
    
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
    
    `ibp.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a user that already exists in the SAP Integrated Business Planning target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

    -   Default behavior: This property does not appear in the UI during system creation. Its default value is *personExternalID*. That means, if the service finds an existing user by a *personExternalID*, it updates this user with the data of the conflicting one.

        If a user with such а *personExternalID* is not found, the creation of the conflicting user fails.

    -   Value = *emails\[0\].value*. If the service finds an existing user matching both unique attributes *email* and *personExternalID*, it updates this user with the data of the conflicting one. If the service finds an existing user matching only the *email*, the update of the existing user fails.

        If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


    Possible values:

    -   *personExternalID*
    -   *emails\[0\].value*

    Default value: *personExternalID*

    The possible values of this property depend on the API version which your SAP Integrated Business Planning system consumes.

    Possible values:

    -   If your system consumes SAP Integrated Business Planning API: Business User, the service searches for an existing user by *personExternalID* and *emails\[0\].value*.

        According to your use case, choose how to set up the property:

        -   Default behavior: This property does not appear in the UI during system creation. Its default value is *personExternalID*. That means, if the service finds an existing user by a *personExternalID*, it updates this user with the data of the conflicting one.

            If a user with such а *personExternalID* is not found, the creation of the conflicting user fails.

        -   Value = *emails\[0\].value*. If the service finds an existing user matching both unique attributes *email* and *personExternalID*, it updates this user with the data of the conflicting one. If the service finds an existing user matching only the *email*, the update of the existing user fails.

            If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


    -   If your system consumes SCIM Interface for IAM, the service searches for an existing user by *userName*, *emails\[0\].value*, *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes.

        According to your use case, choose how to set up the property:

        -   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
        -   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
        -   Value = *externalId*. If the service finds an existing user with *externalId*, it updates this user with the data of the conflicting one. If a user with such *externalId* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


    For more information, see [List of Properties](list-of-properties-d6f3577.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ibp.user.roles.overwrite`
    
    </td>
    <td valign="top">
    
    This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP IBP target system.

    -   **true** – the current user roles will be deleted in the target system, and the user will be updated only with the roles provisioned by the service.
    -   **false** – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the target system.

    See also: [Extended Explanation of the \*.user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ibp.roles.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Integrated Business Planning roles by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `IBP_`

    You can use the example value or provide your own.

    When **set in the target system**, only roles containing the `IBP_` prefix in their role name will be provisioned to SAP Integrated Business Planning. Roles without this prefix in the role name won't be provisioned.

    If the property is not set, all roles will be provisioned to SAP Integrated Business Planning.

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ibp.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Integrated Business Planning groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `IBP_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `IBP_` prefix in their display name will be provisioned to SAP Integrated Business Planning. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be provisioned to SAP Integrated Business Planning.

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

    **Relevant for connector version 2**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ibp.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If the Identity Provisioning tries to create a group that already exists in the SAP Integrated Business Planning target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

    Default value \(when not specified\): *externalId* and *\['urn:ietf:params:scim:schemas:extension:sap:2.0:Group'\]\['type'\]*

    If the property is not specified, the search is done by the default attributes.

    **Relevant for connector version 2**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ibp.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request. For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

    If not specified, the default value is *false*.

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ibp.bulk.operations.max.count`
    
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
    
    `ibp.patch.group.members.above.threshold`
    
    </td>
    <td valign="top">
    
    Defines the threshold number of group members above which they are provisioned on batches with `PATCH` requests, and below which they are provisioned with `PUT` request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

    The expected value is a positive integer without any separators, such as a space, comma, or period.

    > ### Note:  
    > You can use this property when SAP Integrated Business Planning is based on SCIM Interface for IAM \(in short, SCIM API\).

    **Possible values**: integer

    Default value: *20000*

    Minimum value: *1*

    Maximum value: *20000*

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

    **Relevant for connector version 2**
    
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

    `URL`=*https://my1234567-api.scmibp.ondemand.com*

    `User`=*MyIBPCloudUser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `ips.date.variable.format`=*yyyy-MM-dd*

    `ibp.user.roles.overwrite` = *false*

    `ibp.support.bulk.operation` = *true*

    `ibp.bulk.operations.max.count` = *50*
    
    </td>
    </tr>
    </table>
    
6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP IBP* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules depending on your setup of entities in your SAP IBP. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Integrated Business Planning API: Business User](https://help.sap.com/doc/7de2c58e5f4b4b9cb9aed9be86c0b069/Cloud/en-US/Business_User_IBP.pdf)

    [SAP Business Accelerator Hub: SAP IBP](https://api.sap.com/package/IBPAPIIdentityManagementService?section=Artifacts)

    [Integrate Cross-Domain Identity Management](https://help.sap.com/docs/SAP_INTEGRATED_BUSINESS_PLANNING/feae3cea3cc549aaa9d9de7d363a83e6/09a1bebaf6eb4954af2df326b025d0ec.html?locale=en-US&version=2505)

    [SCIM Interface for IAM](https://help.sap.com/docs/SAP_INTEGRATED_BUSINESS_PLANNING/da797ae2bf6246d58abd417f24915d55/0826103882b14d9780537f4492b81727.html?locale=en-US&version=2505)

    **Default transformationfor connector version 1:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "isValidEmail($.emails[0].value) && (('%ibp.roles.prefix%' === 'null') || ($.groups[?(@.display =~ /%ibp.roles.prefix%.*/)] empty false))",
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
    >         "targetPath": "$.personExternalID",
    >         "optional": true
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
    >           }
    >         ]
    >       },
    >       {
    >         "scope": "createEntity",
    >         "targetPath": "$.validityPeriod.startDate",
    >         "sourceVariable": "currentDate"
    >       },
    >       {
    >         "scope": "createEntity",
    >         "targetPath": "$.validityPeriod.endDate",
    >         "constant": "9999-12-31"
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
    >         "targetPath": "$.workplaceInformation.emailAddress"
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
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, ibp.roles.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], ibp.roles.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, ibp.roles.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%ibp.roles.prefix%",
    >             "replacement": ""
    >           }
    >         ],
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, ibp.roles.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%ibp.roles.prefix%",
    >             "replacement": ""
    >           }
    >         ],
    >         "targetPath": "$.displayName"
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
    > 
    > ```

    See also: [Extended Explanation of the \*user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

    **Default transformation for connector version 2:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "(('%ibp.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%ibp.group.prefix%.*/)] empty false))",
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
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId",
    >         "optional": true
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
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['language']['logonLanguage']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['language']['logonLanguage']",
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
    >     "condition": "isAttributeWithOptionalPrefix($.displayName, ibp.group.prefix) && isAttributeWithOptionalPrefix($['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name'], ibp.group.prefix) && (isRegularGroup() || isApplicationSpecificGroup())",
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
    >             "condition": "isAttributeWithMandatoryPrefix(@, ibp.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%ibp.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.externalId",
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, ibp.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%ibp.group.prefix%",
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
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "targetPath": "$.externalId",
    >         "optional": true,
    >         "functions": [
    >           {
    >             "condition": "isAttributeWithMandatoryPrefix(@, ibp.group.prefix)",
    >             "function": "replaceFirstString",
    >             "regex": "%ibp.group.prefix%",
    >             "replacement": ""
    >           },
    >           {
    >             "function": "replaceString",
    >             "target": ":authorization",
    >             "replacement": ""
    >           },
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

    The most common scenario includes SAP Integrated Business Planning version 2 as source system and Identity Authentication version 2 or Local Identity Directory as target system, that supports the custom name attribute.

    The uniqueness of the group in SAP Integrated Business Planning version 2 is ensured by the combination of two unique attributes: `externalId` and `type`. Since we distinguish two group types, `userGroup` and `authorization`, there is a possibility that two groups of different `type` share the same `externalId`. As the `externalId` attribute is mapped to the `custom name` of the group in Identity Authentication version 2 and Local Identity Directory, potential conflicts may occure.

    When a group of type `authorization` is provisioned from SAP Integrated Business Planning version 2 source, the suffix *:authorization* is appended to its `custom name` in the target system. This ensures the successful provisioning of two groups with identical `externalIds` to Identity Authentication version 2 or Local Identity Directory, as they are provisioned with unique custom names to the target.

    When these groups are provisioning from Identity Authentication version 2 or Local Identity Directory as source system back to SAP Integrated Business Planning version 2 as target, each group `custom name` is checked for the suffix *:authorization*. If such is detected, it is removed so that the initial value of the `externalId` of the group in SAP Integrated Business Planning version 2 system is restored.

7.  Now, add a source system from which to read users and roles. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio5864dc217f31443dab6d32fd2eeefda9__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Integrated Business Planning](https://help.sap.com/viewer/product/SAP_INTEGRATED_BUSINESS_PLANNING/latest/en-US)

