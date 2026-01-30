<!-- loio65a847ebea7d44c7a9b4a7530f07736a -->

# SAP Integrated Business Planning

Follow this procedure to set up SAP Integrated Business Planning \(in short, SAP IBP\) as a source system.



<a name="loio65a847ebea7d44c7a9b4a7530f07736a__prereq_tcl_4r3_kfb"/>

## Prerequisites

To establish the connection between Identity Provisioning and SAP Integrated Business Planning, you need to set up the communication \(user, system and arrangement\) on SAP Integrated Business Planning. You can do it now \(as a prerequisite\) or in the process of configuring SAP Integrated Business Planning as a source system, as described in step 3.



## Context

SAP Integrated Business Planning is a cloud-based solution that combines sales and operations planning \(S&OP\), forecasting and demand, response and supply, demand-driven replenishment, and inventory planning.

You can use Identity Provisioning to configure SAP IBP as a source system where you can read entities from and provision them to a target system.

SAP Integrated Business Planning provides different APIs for integration with Identity Provisioning, resulting in different connector versions for each API. Each connector version supports specific attribute mappings within the transformations and requires particular property values. By default, the Identity Provisioning service uses API version *1*. The value of the `ibp.api.version` property controls which API you use.

-   When the value is set to *1* or the property is not present \(typical for systems created before versioning was introduced on November 6, 2025\), the SOAP API provided by the communication scenario SAP\_COM\_0193 is used. It supports reading **business users** \(employees\), **user assignments to business roles**, and **business roles** \(considered as *groups*\).

    For more information on how to update to version *2*, see [Update SAP Integrated Business Planning](Operation-Guide/update-sap-integrated-business-planning-18d1280.md).

-   When the value is set to *2*, the SCIM interface provided by the communication scenario SAP\_COM\_0465 is used. It supports provisioning of **business users**, including their **assignments** to groups of type **userGroup** and **authorization** \(roles\). For more information, see [Groups](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/groups?locale=en-US&version=Cloud).




## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP Integrated Business Planning* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP Integrated Business Planning and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP Integrated Business Planning source system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/76867db8ce534becbfc08b050695df8e.html?version=Cloud).

        Skip step **a.** if you want to use basic authentication.

        The next steps are performed in SAP Integrated Business Planning backend system and are relevant for both basic and certificate-based authentication.

    2.  [Create a communication user](https://help.sap.com/viewer/feae3cea3cc549aaa9d9de7d363a83e6/Latest/en-US/4bff8d203d4c4b1c8dd25564d1913302.html) and provide the respective credentials.

        For basic authentication, provide *User Name* and *Password*.

        For certificate-based authentication, upload the certificate you have generated in the Identity Provisioning UI on the previous step.

    3.  [Create a communication system](https://help.sap.com/viewer/feae3cea3cc549aaa9d9de7d363a83e6/Latest/en-US/084a6cce1a7e4c3c9c2f2bca8384b243.html) and assign the created user to the communication system.

        For your Identity Provisioning scenario, provide *System ID*, *System Name* and *Host Name*.

    4.  [Create a communication arrangement](https://help.sap.com/viewer/feae3cea3cc549aaa9d9de7d363a83e6/Latest/en-US/065d578693334cbeb86b8f31f0edfc93.html) with the created system.

        -   When `ibp.api.version`=`1` is set in Identity Provisioning for the SAP IBP source system, choose *Scenario ID* SAP\_COM\_0193 \(SAP Cloud Identity Provisioning Integration\).

            > ### Note:  
            > The communication scenario *SAP\_COM\_0193* is enhanced to support the User UUID attribute which is generated by Identity Authentication at user creation.
            > 
            > The User UUID is universally unique identifier. This attribute is immutable and unique across technology layers, such as user interface, APIs, and security tokens, as well as across products and lines of business contributing to a business process in the Intelligent Enterprise.

        -   When `ibp.api.version`=`2` is set in Identity Provisioning for the SAP IBP source system, choose *Scenario ID* SAP\_COM\_0465 \(System for Cross-domain Identity Management Integration\).

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

    Description & Value SAP Integrated Business Planning 
    
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
    
    `ibp.skip.read.archived`
    
    </td>
    <td valign="top">
    
    In the event of archived \(disabled\) entities in a source SAP IBP system, choose whether the provisioning jobs to continue reading such entities or to skip them.

    This property is enabled by default. If you want to always read disabled entities, set the property to **false**, or delete it.

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
    
    \(Optional\) `ibp.roles.filter`
    
    </td>
    <td valign="top">
    
    Enter OData filtering for reading roles in the SAP IBP system.

    To learn what criteria you can use, see: [OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → **4.5 Filter System Query Option**

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ibp.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Integrated Business Planning groups matching the filter expression will be read.

    Supported operators: eq \(equal\), co \(contains\), and sw \(starts with\).

    **Possible values:**:

    -   `displayName`
    -   `externalId`
    -   `urn:ietf:params:scim:schemas:extension:sap:2.0:Group:type`

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

    **Relevant for connector version 2**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ibp.roles.page.size`
    
    </td>
    <td valign="top">
    
    Indicate how many business roles \(considered as *groups*\) per page to be read from your SAP IBP system.

    The value must be an integer number.

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

    When **set in the source system**, the prefix will be prepended to the name of the roles that are read from the SAP Integrated Business Planning source system and will be provisioned to the target system with the following name pattern: <code>IBP_<i class="varname">&lt;role_name&gt;</i></code>. This way SAP Integrated Business Planning roles in the target system will be distinguished from roles provisioned from other applications.

    If the property is not set, the SAP Integrated Business Planning roles will be read and provisioned to the target system with their actual role names.

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

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Integrated Business Planning source system and will be provisioned to the target system with the following name pattern: <code>IBP_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Integrated Business Planning groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Integrated Business Planning groups will be read and provisioned to the target system with their actual display names.

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

    **Relevant for connector version 2**
    
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

    `User`=*MyIBPuser*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `ips.date.variable.format`=*yyyy-MM-dd*

    `ibp.skip.read.archived`=*true*

    `ibp.roles.filter`=*startswith\(ID, 'EMPLOYEE\_LEVEL\_3'\) eq true*

    `ibp.roles.page.size`=*30*
    
    </td>
    </tr>
    </table>
    
6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP IBP* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules depending on your setup of entities in your SAP IBP. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Integrated Business Planning API: Business User](https://help.sap.com/doc/7de2c58e5f4b4b9cb9aed9be86c0b069/Cloud/en-US/Business_User_IBP.pdf)

    [SAP Business Accelerator Hub: SAP IBP](https://api.sap.com/package/IBPAPIIdentityManagementService?section=Artifacts)

    [Integrate Cross-Domain Identity Management](https://help.sap.com/docs/SAP_INTEGRATED_BUSINESS_PLANNING/feae3cea3cc549aaa9d9de7d363a83e6/09a1bebaf6eb4954af2df326b025d0ec.html?locale=en-US&version=2505)

    [SCIM Interface for IAM](https://help.sap.com/docs/SAP_INTEGRATED_BUSINESS_PLANNING/da797ae2bf6246d58abd417f24915d55/0826103882b14d9780537f4492b81727.html?locale=en-US&version=2505)

    **Default transformation for connector version 1:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "($.validityPeriod.startDate <= '${currentDate}') && ($.validityPeriod.endDate > '${currentDate}')",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.personID",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.personalInformation.firstName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.personalInformation.lastName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.personalInformation.middleName",
    >         "targetPath": "$.name.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.personalInformation.personFullName",
    >         "targetPath": "$.name.formatted",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.user.userName",
    >         "targetPath": "$.userName",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "constant": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "condition": "$.user.lockedIndicator == 'true'",
    >         "constant": false,
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "condition": "($.user.validityPeriod.startDate > '${currentDate}') || ('${currentDate}' > $.user.validityPeriod.endDate)",
    >         "constant": false,
    >         "optional": true,
    >         "targetPath": "$.active"
    >       },
    >       {
    >         "sourcePath": "$.workplaceInformation.emailAddress",
    >         "targetPath": "$.emails[0].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.user.logonLanguageCode",
    >         "optional": true,
    >         "targetPath": "$.locale"
    >       },
    >       {
    >         "sourcePath": "$.PersonExternalID",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.user.globalUserID",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$.user.role",
    >         "optional": true,
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "functions": [
    >           {
    >             "condition": "'%ibp.roles.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "prefix": "%ibp.roles.prefix%",
    >             "applyOnAttribute": "roleName",
    >             "assignToAttribute": "display"
    >           },
    >           {
    >             "condition": "'%ibp.roles.prefix%' === 'null'",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "prefix": "",
    >             "applyOnAttribute": "roleName",
    >             "assignToAttribute": "display"
    >           },
    >           {
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "prefix": "",
    >             "applyOnAttribute": "roleName",
    >             "assignToAttribute": "value"
    >           }
    >         ]
    >       },
    >       {
    >         "type": "remove",
    >         "targetPath": "$.groups[*].roleName"
    >       },
    >       {
    >         "sourcePath": "$.user.timeZoneCode",
    >         "optional": true,
    >         "targetPath": "$.timezone",
    >         "functions": [
    >           {
    >             "type": "convertTimezoneCode",
    >             "outputFormat": "iana"
    >           }
    >         ],
    >         "defaultValue": "Europe/Berlin"
    >       },
    >       {
    >         "type": "valueMapping",
    >         "sourcePaths": [
    >           "$.businessPartnerRoleCode"
    >         ],
    >         "targetPath": "$.userType",
    >         "defaultValue": "Employee",
    >         "valueMappings": [
    >           {
    >             "key": [
    >               "BUP003"
    >             ],
    >             "mappedValue": "Employee"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.ID",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.ID",
    >         "functions": [
    >           {
    >             "condition": "'%ibp.roles.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%ibp.roles.prefix%"
    >           }
    >         ],
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "sourcePath": "$.ID",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       },
    >       {
    >         "constant": "authorization",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.to_BusinessUserAssignment.results",
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members"
    >       },
    >       {
    >         "type": "remove",
    >         "targetPath": "$.members[*].__metadata"
    >       },
    >       {
    >         "type": "remove",
    >         "targetPath": "$.members[*].UserName"
    >       },
    >       {
    >         "type": "rename",
    >         "constant": "value",
    >         "targetPath": "$.members[*].PersonID"
    >       },
    >       {
    >         "constant": "User",
    >         "targetPath": "$.members[*].type"
    >       }
    >     ]
    >   }
    > }
    > ```

    By default, Identity Provisioning reads group IDs and members. If you want the service to also read group descriptions, you can add an extra mapping to the *"group"* resource. To learn how, see [Guided Answers: Business Role Description](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:39660:40191).

    **Default transformation for connector version 2:**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
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
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers"
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "optional": true,
    >         "targetPath": "$.userType"
    >       },
    >       {
    >         "condition": "$.preferredLanguage !== 'not_unique'",
    >         "sourcePath": "$.preferredLanguage",
    >         "optional": true,
    >         "targetPath": "$.preferredLanguage"
    >       },
    >       {
    >         "condition": "$.locale !== 'not_unique'",
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
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['language']['logonLanguage']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['language']['logonLanguage']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['decimalFormatCode']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['decimalFormatCode']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['dateFormatCode']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['dateFormatCode']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['timeFormatCode']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['regionalSettings']['timeFormatCode']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuidHistory']",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuidHistory']"
    >       },
    >       {
    >         "sourcePath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups",
    >         "functions": [
    >           {
    >             "function": "concatString",
    >             "condition": "'%ibp.group.prefix%' !== 'null'",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "display",
    >             "prefix": "%ibp.group.prefix%"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "'%ibp.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%ibp.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >       },
    >       {
    >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type'] == 'userGroup'",
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >           {
    >             "function": "compositeId",
    >             "separator": ":",
    >             "subId": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >           },
    >           {
    >             "condition": "'%ibp.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%ibp.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type'] == 'authorization'",
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >           {
    >             "condition": "'%ibp.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%ibp.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    >       },
    >       {
    >         "condition": "'%ips.application.id%' !== 'null'",
    >         "constant": "%ips.application.id%",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
    >       }
    >     ]
    >   }
    > }
    > ```

    > ### Note:  
    > If you are using SAP Integrated Business Planning version 2511, note that the `timeZone` value is not provided in the `IANA` format required by SCIM. To fix this, you need to manually add the `convertTimezoneCode` function within the `timeZone` mapping, as shown below:
    > 
    > ```
    > {
    >    "sourcePath":"$.timeZone",
    >    "optional":true,
    >    "targetPath":"$.timezone",
    >    "functions":[
    >       {
    >          "type":"convertTimezoneCode",
    >          "outputFormat":"iana"
    >       }
    >    ],
    >    "defaultValue":"Europe/Berlin"
    > },
    > ```

    **Group Uniqueness and Provisioning**

    In the most common scenario, SAP Integrated Business Planning connector version 2 is used as the source system for groups and Identity Authentication connector version 2 or Local Identity Directory is the target system.

    In SAP Integrated Business Planning version 2, the uniqueness of a group is defined by the combination of `externalId` and `type` attributes. The system supports two group types: `userGroup` and `authorization` \(role\). As a result, two different groups can share the same `externalId` while belonging to different types, potentially causing conflicts when provisioned to the target system.

    To avoid conflicts, ensure the following:

    -   Your SAP Integrated Business Planning system is updated to version 2, as described in [Update SAP Integrated Business Planning](Operation-Guide/update-sap-integrated-business-planning-18d1280.md).

    -   Your target system \(Identity Authentication version 2 or Local Identity Directory\) has the respective group uniqueness property: `ias.group.unique.attribute` or `idds.group.unique.attribute`, set with the following combination of values: `['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type'],['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName'],['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']`. For more information, see [List of Properties](list-of-properties-d6f3577.md).

        Because the `externalId` attribute in SAP Integrated Business Planning version 2 connector is mapped to the `name` attribute in the target, when a group of type `userGroup` is provisioned from the source to the target, the suffix `:userGroup` is automatically appended to its `name`. This ensures that even if two groups share the same `externalId`, their names remain unique in the target system.


7.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio65a847ebea7d44c7a9b4a7530f07736a__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP Integrated Business Planning](https://help.sap.com/viewer/product/SAP_INTEGRATED_BUSINESS_PLANNING/latest/en-US)

