<!-- loio5aa97c79e648430fb8c0df6d6d7f649d -->

# SAP Market Communication for Utilities

Follow this procedure to set up SAP Market Communication for Utilities as a target system.



<a name="loio5aa97c79e648430fb8c0df6d6d7f649d__prereq_tcl_4r3_kfb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

To establish the connection between Identity Provisioning and SAP Market Communication for Utilities, you need to set up the communication user in SAP BTP ABAP environment. You can do it now \(as a prerequisite\) or in the process of configuring SAP Market Communication for Utilities as a target system, as described in step 3.



<a name="loio5aa97c79e648430fb8c0df6d6d7f649d__context_tjq_xs3_kfb"/>

## Context

The SAP Market Communication for Utilities application is based on SAP BTP ABAP environment. You can use Identity Provisioning to configure SAP Market Communication for Utilities as a target system to provision entities from a given source system.

This scenario supports writing **users** and **assignments**. In SAP Market Communication for Utilities, groups correspond to roles, thus group members are user assignments of a role.

> ### Note:  
> Identity Provisioning cannot create and delete roles in SAP Market Communication for Utilities target system. It can only create, update and delete user assignments of a role. Therefore, roles must have been created in SAP Market Communication for Utilities target system before you run a provisioning job.
> 
> For example, if you try to create or delete a role in SAP Market Communication for Utilities, Identity Provisioning will only add or remove the user assignments of that role, respectively.

The Identity Provisioning service manages the complete set of **business partners** and their relevant **business users** \(Employee\).



<a name="loio5aa97c79e648430fb8c0df6d6d7f649d__steps_ujq_xs3_kfb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Market Communication for Utilities* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP Market Communication for Utilities and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP Market Communication for Utilities target system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](Operation-Guide/generate-and-manage-certificates-for-outbound-connection-76867db.md).

        Skip step **a.** if you want to use basic authentication.

        The next steps are performed in SAP BTP ABAP environment backend system and are relevant for both basic and certificate-based authentication.

    2.  [Create a communication user](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/0377adea0401467f939827242c1f4014.html?version=Cloud) and provide the respective credentials.

        For basic authentication, provide *User Name* and *Password*.

        For certificate-based authentication, upload the certificate you have generated in the Identity Provisioning UI on the previous step.

    3.  [Create a communication system](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/c2234acd55774ebcbedb66744199273e.html?version=Cloud) and assign the created user to the communication system.

        For your Identity Provisioning scenario, provide *System ID*, *System Name* and *Host Name*.

    4.  [Create a communication arrangement](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/a0771f6765f54e1c8193ad8582a32edb.html?version=Cloud) with the created system.

        For your Identity Provisioning scenario, choose *Scenario ID* SAP\_COM\_0193 \(SAP Cloud Identity Provisioning Integration\).

        For more information, see [Maintain a Communication Arrangement for Inbound Communication](https://developers.sap.com/tutorials/abap-environment-communication-arrangement.html)

        > ### Note:  
        > The communication scenario *SAP\_COM\_0193* is enhanced to support the User UUID attribute which is generated by Identity Authentication at user creation.
        > 
        > The User UUID is universally unique identifier. This attribute is immutable and unique across technology layers, such as user interface, APIs, and security tokens, as well as across products and lines of business contributing to a business process in the Intelligent Enterprise.


5.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Specify the API URL to your SAP Market Communication for Utilities system.
    
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
    
    `ips.date.variable.format`
    
    </td>
    <td valign="top">
    
    *yyyy-MM-dd*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `maco.user.unique.attribute`
    
    </td>
    <td valign="top">
    
    If Identity Provisioning tries to provision a user that already exists in the SAP Market Communication for Utilities target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

    According to your use case, choose how to set up this property:

    -   Default behavior: This property does not appear in the UI during system creation. Its default value is *personExternalID*. That means, if the service finds an existing user by a *personExternalID*, it updates this user with the data of the conflicting one.

        If a user with such а *personExternalID* is not found, the creation of the conflicting user fails.

    -   Value = *emails\[0\].value*. If the service finds an existing user matching both unique attributes *email* and *personExternalID*, it updates this user with the data of the conflicting one. If the service finds an existing user matching only the *email*, the update of the existing user fails.

        If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


    Possible values:

    -   *personExternalID*
    -   *emails\[0\].value*

    Default value: *personExternalID*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `maco.user.roles.overwrite`
    
    </td>
    <td valign="top">
    
    This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP Market Communication for Utilities target system.

    -   **true** – the current user roles will be deleted in the target system, and the user will be updated only with the roles provisioned by the service.
    -   **false** – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the target system.

    Default value \(if the property is missing during system creation\): *true* 

    Default value \(if the property appears during system creation\): *false*

    See also: [Extended Explanation of the \*.user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `maco.roles.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Market Communication for Utilities roles by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `SMC_`

    You can use the example value or provide your own.

    When **set in the target system**, only roles containing the `SMC_` prefix in their role name will be provisioned to SAP Market Communication for Utilities. Roles without this prefix in the role name won't be provisioned.

    If the property is not set, all roles will be be provisioned to SAP Market Communication for Utilities.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `maco.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request. For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

    If not specified, the default value is *false*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `maco.bulk.operations.max.count`
    
    </td>
    <td valign="top">
    
    If you have enabled the bulk operations, you can use this property to set the number of users to be provisioned per request.

    The default value, if not specified, is *20*.

    The maximum value is **100**. If you enter a number larger than 100, the service will replace it with the default value \(20\).
    
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

    `URL`=*https://12345-aaaaa-3333.abap.hana.ondemand.com*

    `User`=*MyMaCoUser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `ips.date.variable.format`=*yyyy-MM-dd*

    `maco.user.roles.overwrite`=*false*

    `maco.support.bulk.operation` = *true*

    `maco.bulk.operations.max.count` = *50*
    
    </td>
    </tr>
    </table>
    
6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Market Communication for Utilities* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in SAP Market Communication for Utilities. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP S/4HANA Cloud API: Business User](https://help.sap.com/viewer/f1531d40f450474dbf95f0404cb62007/latest/en-US/640fb5fa26664a7486de073b1882405c.html)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "condition": "($.emails EMPTY false) && isValidEmail($.emails[0].value)",
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
    >         "targetPath": "$.personID",
    >         "sourceVariable": "entityIdTargetSystem"
    >       },
    >       {
    >         "targetPath": "$.markedForArchivingIndicator",
    >         "constant": "false"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$.user.globalUserID"
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
    >         "condition": "$.active == false",
    >         "targetPath": "$.user.lockedIndicator",
    >         "constant": "true"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "('%maco.roles.prefix%' === 'null') || ($.displayName =~ /%maco.roles.prefix%.*/)",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "('%maco.roles.prefix%' !== 'null') && (@ =~ /%maco.roles.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%maco.roles.prefix%",
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
    >             "condition": "('%maco.roles.prefix%' !== 'null') && (@ =~ /%maco.roles.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%maco.roles.prefix%",
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

7.  Now, add a source system from which to read users and roles. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio5aa97c79e648430fb8c0df6d6d7f649d__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP S/4HANA Cloud Documentation](https://help.sap.com/viewer/9d794cbd48c648bc8a176e422772de7e/latest/en-US/7af7b8541486ed05e10000000a4450e5.html)

