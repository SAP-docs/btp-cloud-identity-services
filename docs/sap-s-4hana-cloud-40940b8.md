<!-- loio40940b8223334b528e4899b92d42ce96 -->

# SAP S/4HANA Cloud

Follow this procedure to set up SAP S/4HANA Cloud as a target system.



<a name="loio40940b8223334b528e4899b92d42ce96__prereq_tcl_444_kfb"/>

## Prerequisites

To establish the connection between Identity Provisioning and SAP S/4HANA Cloud, you need to set up the communication \(user, system and arrangement\) on SAP S/4HANA Cloud. You can do it now \(as a prerequisite\) or in the process of configuring SAP S/4HANA Cloud as a target system, as described in step 3.



<a name="loio40940b8223334b528e4899b92d42ce96__context_tjq_xs3_kfb"/>

## Context

SAP S/4HANA Cloud is a complete enterprise resource planning \(ERP\) system with built-in intelligent technologies and advanced analytics.

You can use Identity Provisioning to configure SAP S/4HANA Cloud as a target system where you can provision users and group members from source systems of your choice. In SAP S/4HANA Cloud, groups correspond to business roles, thus group members are user assignments of a business role.

> ### Note:  
> Identity Provisioning cannot create and delete business roles in SAP S/4HANA Cloud target system. It can only create, update and delete user assignments of a role. Therefore, business roles must have been created in SAP S/4HANA Cloud system before you run a provisioning job.
> 
> For example, if you try to create or delete a business role in SAP S/4HANA Cloud, Identity Provisioning will only add or remove the user assignments of that role, respectively.

In scenarios where SAP S/4HANA Cloud is configured as a target system, the integration with a human resource \(HR\) system is active and cannot be switched off. In this case, the synchronization of business partners is managed by the HR system and SAP S/4HANA Cloud. Identity Provisioning can only be used for managing business users \(login users and their login information, such as date/time preferences\) and role assignments.

In SAP S/4HANA Cloud, business partners are the central master data objects that hold the complete person profile in the SAP S/4HANA Cloud. For example, business partners with role `Employee` and `Contingent Worker`. Business users are persons who can log on to SAP S/4HANA Cloud system to complete business tasks.



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

        For your Identity Provisioning scenario, choose *Scenario ID* SAP\_COM\_0193 \(SAP Cloud Identity Provisioning Integration\).

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
    
    Enter the SAP S/4HANA Cloud API URL.

    You can find the correct URL in the *API-URL* field of the communication arrangement set up for communication scenario SAP\_COM\_0193.

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

    Version *1* means your SAP S/4HANA Cloud system uses *SAP\_COM\_0193* communication arrangement.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `s4hana.cloud.hr.switch.active`
    
    </td>
    <td valign="top">
    
    A default property, whose only possible value is **true**. That means, HR integration is enabled for your system.

    > ### Caution:  
    > Do not change this value! Otherwise, your provisioning job will fail.


    
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
    > You can configure this property only when the integration between a human resource \(HR\) system and SAP S/4HANA Cloud target system is **OFF**. Since the HR integration is active and cannot be switched off for SAP S/4HANA Cloud target systems, configuring the `s4hana.cloud.user.unique.attribute` property is currently irrelevant.

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
    
    `s4hana.cloud.user.roles.overwrite`
    
    </td>
    <td valign="top">
    
    This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP S/4HANA Cloud target system.

    -   **true** – the current user roles will be deleted in the target system, and the user will be updated only with the roles provisioned by the service.
    -   **false** – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the target system.

    See also: [Extended Explanation of the \*.user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.cloud.support.bulk.operation`
    
    </td>
    <td valign="top">
    
    Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request. For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

    If not specified, the default value is *false*.
    
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
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.roles`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of roles to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of roles, for example by adding a filter or condition.

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

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
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
    >         "condition": "$.active == false",
    >         "targetPath": "$.user.lockedIndicator",
    >         "constant": "true"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "condition": "('%s4hana.cloud.roles.prefix%' === 'null') || ($.displayName =~ /%s4hana.cloud.roles.prefix%.*/)",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity",
    >         "functions": [
    >           {
    >             "condition": "('%s4hana.cloud.roles.prefix%' !== 'null') && (@ =~ /%s4hana.cloud.roles.prefix%.*/)",
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
    >             "condition": "('%s4hana.cloud.roles.prefix%' !== 'null') && (@ =~ /%s4hana.cloud.roles.prefix%.*/)",
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

7.  Now, add a source system from which to read users and roles. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio40940b8223334b528e4899b92d42ce96__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP S/4HANA Cloud Documentation](https://help.sap.com/viewer/9d794cbd48c648bc8a176e422772de7e/latest/en-US/7af7b8541486ed05e10000000a4450e5.html)

