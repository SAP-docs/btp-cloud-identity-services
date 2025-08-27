<!-- loiod3f93a7870c341c0993cd733ed9e9b3a -->

# SAP S/4HANA Cloud

Follow this procedure to set up SAP S/4HANA Cloud as a source system.



<a name="loiod3f93a7870c341c0993cd733ed9e9b3a__prereq_tcl_444_kfb"/>

## Prerequisites

To establish the connection between Identity Provisioning and SAP S/4HANA Cloud, you need to set up the communication \(user, system and arrangement\) on SAP S/4HANA Cloud. You have the option to do it either now, as a prerequisite, or while configuring SAP S/4HANA Cloud as a source system, as described in step 3.



## Context

SAP S/4HANA Cloud is a complete enterprise resource planning \(ERP\) system with built-in intelligent technologies and advanced analytics.

You can use Identity Provisioning to configure SAP S/4HANA Cloud as a source system where you can read entities from and provision them to target systems of your choice. This scenario supports reading **business users** \(Employee, Contingent Worker\), **user assignments**, and **business roles** \(which are considered as *groups*\).

SAP S/4HANA Cloud provides different APIs for integration with Identity Provisioning, resulting in different connector versions for each API. Each connector version supports specific attribute mappings within the transformations and requires particular property values. The value of the `s4hana.cloud.api.version` property controls which API you use. By default, the Identity Provisioning service uses version *1*.

-   When the value is set to *1*, or the property is not defined \(typical for systems created before versioning was introduced on **August XX, 2025**\), SAP S/4HANA Cloud API: Business User is used. It supports reading **business users** \(Employee, Contingent Worker\), **user assignments**, and **business roles** \(which are considered as *groups*\). For more information on how to update to version *3*, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).

-   When the value is set to *3*, System for Cross-domain Identity Management \(SCIM\) API is used. It supports provisioning of **business users** with their **assignments** to groups of type **userGroup** and **authorization**. For more information, see [Groups](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/groups?locale=en-US&version=Cloud).




## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SAP S/4HANA Cloud* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Set up the communication between Identity Provisioning and SAP S/4HANA Cloud and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP S/4HANA source system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/76867db8ce534becbfc08b050695df8e.html?version=Cloud).

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

        -   When SAP S/4HANA Cloud version *1* is used:

            For your Identity Provisioning scenario, choose *Scenario ID* SAP\_COM\_0193 \(SAP Cloud Identity Provisioning Integration\).

            > ### Note:  
            > The communication scenario *SAP\_COM\_0193* is enhanced to support the User UUID attribute which is generated by Identity Authentication at user creation.
            > 
            > The User UUID is universally unique identifier. This attribute is immutable and unique across technology layers, such as user interface, APIs, and security tokens, as well as across products and lines of business contributing to a business process in the Intelligent Enterprise.

        -   When SAP S/4HANA Cloud version *3* is used:

            For your Identity Provisioning scenario, choose *Scenario ID* SAP\_COM\_0465 \(System for Cross-domain Identity Management Integration\).

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
    
    `s4hana.cloud.skip.read.archived`
    
    </td>
    <td valign="top">
    
    In the event of archived \(disabled\) entities in a source SAP S/4HANA Cloud system, choose whether the provisioning jobs to continue reading such entities or to skip them.

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
    
    \(Optional\) `s4hana.cloud.roles.filter`
    
    </td>
    <td valign="top">
    
    Enter OData filtering for reading roles in the S/4HANA system.

    To learn what criteria you can use, see: [OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → **4.5 Filter System Query Option**

    **Relevant for connector version 1**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.cloud.group.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP S/4HANA Cloud groups matching the filter expression will be read.

    Supported operators: eq \(equal\), co \(contains\), and sw \(starts with\).

    **Possible values:**:

    -   `displayName`
    -   `externalId`
    -   `urn:ietf:params:scim:schemas:extension:sap:2.0:Group:type`

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

    **Relevant for connector version 3**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.cloud.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP S/4HANA Cloud users matching the filter expression will be read. You can filter users by **list of attributes** according to the API syntax of SAP S/4HANA Cloud.

    You can set a single attribute or multiple ones as filter criteria. If you enter multiple attributes \(using OR operator\), the filter will search for any of them.

    Supported operators: eq \(equal\), ne \(not equal\), sw \(starts with\), ew \(ends with\) and co \(contains\)

    **Possible values:**

    -   `userName`
    -   `externalId`
    -   `emails[0].value`

    For example:

    -   *userName eq "johnbrown" and externalId eq "P000252"*
    -   *userName sw "J" or externalId eq "P000252"*
    -   *userName eq "johnbrown" and emails\[0\].value eq "johnbrown@email.com"*
    -   *userName eq "johnbrown" and emails\[0\].value ne "johnbrown@email.com" or externalId eq "P000252"*

        > ### Note:  
        > These combinations are valid for both 'or' and 'and' operators.


    **Relevant for connector version 3**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `s4hana.cloud.roles.page.size`
    
    </td>
    <td valign="top">
    
    Indicate how many business roles \(considered as *groups*\) per page to be read from your SAP S/4HANA Cloud system.

    The value must be an integer number.

    **Relevant for connector version 1**
    
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

    When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP S/4HANA Cloud source system and will be provisioned to the target system with the following name pattern: <code>S4HANACLOUD_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP S/4HANA Cloud groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP S/4HANA Cloud groups will be read and provisioned to the target system with their actual display names.

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

    **Relevant for connector version 3**
    
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

    `s4hana.cloud.skip.read.archived`=*true*

    `s4hana.cloud.roles.filter`=*startswith\(ID, 'EMPLOYEE\_LEVEL\_3'\) eq true*

    `s4hana.cloud.roles.page.size`=*30*
    
    </td>
    </tr>
    </table>
    
6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP S/4HANA Cloud* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules depending on your setup of entities in your SAP S/4HANA Cloud. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP S/4HANA Cloud API: Business User](https://help.sap.com/viewer/f1531d40f450474dbf95f0404cb62007/latest/en-US/640fb5fa26664a7486de073b1882405c.html)

    [System for Cross-domain Identity Management \(SCIM\)](https://api.sap.com/api/CE_APS_IAM_API_SCIM/overview)

    [Integrate Cross-Domain Identity Management](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/aa4b03ced9dc481fafdf74c2f82976bc.html?version=2508.500)

    **Default transformation for connector version 1::**

    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "condition": "($.user.validityPeriod.startDate <= '${currentDate}') && ($.user.validityPeriod.endDate > '${currentDate}')",
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
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "functions": [
    >           {
    >             "condition": "'%s4hana.cloud.roles.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "prefix": "%s4hana.cloud.roles.prefix%",
    >             "applyOnAttribute": "roleName",
    >             "assignToAttribute": "display"
    >           },
    >           {
    >             "condition": "'%s4hana.cloud.roles.prefix%' === 'null'",
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
    >           },
    >           {
    >             "key": [
    >               "BBP005"
    >             ],
    >             "mappedValue": "Contingent Worker"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.ID",
    >         "targetPath": "$.displayName",
    >         "targetVariable": "entityIdSourceSystem",
    >         "functions": [
    >           {
    >             "condition": "'%s4hana.cloud.roles.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%s4hana.cloud.roles.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "constant": "authorization",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >       },
    >       {
    >         "constant": "readWrite",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >       },
    >       {  "condition": "'%ips.application.id%' !== 'null'",
    >          "constant": "%ips.application.id%",
    >          "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']"
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

    **Default transformation for connector version 3:**

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
    >         "optional": true,
    >         "targetPath": "$.emails"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.phoneNumbers",
    >         "optional": true
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
    >         "targetPath": "$.timezone",
    >         "functions": [
    >           {
    >             "type": "convertTimezoneCode",
    >             "outputFormat": "iana"
    >           }
    >         ]
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
    >         "sourcePath": "$.groups",
    >         "targetPath": "$.groups",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >             {
    >                 "function": "concatString",
    >                 "condition": "'%s4hana.cloud.group.prefix%' !== 'null'",
    >                 "applyOnElements": true,
    >                 "applyOnAttribute": "display",
    >                 "prefix": "%s4hana.cloud.group.prefix%"
    >             }
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
    >             {
    >                 "condition": "'%s4hana.cloud.group.prefix%' !== 'null'",
    >                 "function": "concatString",
    >                 "prefix": "%s4hana.cloud.group.prefix%"
    >             }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']",
    >         "optional": true
    >       },
    >       {
    >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type'] == 'userGroup'",
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >           {
    >             "condition": "'%s4hana.cloud.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%s4hana.cloud.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "condition": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type'] == 'authorization'",
    >         "sourcePath": "$.externalId",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    >         "functions": [
    >           {
    >             "function": "compositeId",
    >             "separator": ":",
    >             "subId": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >           },
    >           {
    >             "condition": "'%s4hana.cloud.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%s4hana.cloud.group.prefix%"
    >           }
    >         ]
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

    **Group Uniqueness and Provisioning**

    The most common scenario includes SAP S/4HANA Cloud version 3 as source system and Identity Authentication version 2 or Local Identity Directory as target system, that supports the custom name attribute.

    The uniqueness of the group in SAP S/4HANA Cloud version 3 is ensured by the combination of two unique attributes: `externalId` and `type`. Since we distinguish two group types, `userGroup` and `authorization`, there is a possibility that two groups of different `type` share the same `externalId`. As the `externalId` attribute is mapped to the `custom name` of the group in Identity Authentication version 2 and Local Identity Directory, potential conflicts may occure.

    When a group of type `authorization` is provisioned from SAP S/4HANA Cloud version 3 source, the suffix *:authorization* is appended to its `custom name` in the target system. This ensures the successful provisioning of two groups with identical `externalIds` to Identity Authentication version 2 or Local Identity Directory, as they are provisioned with unique custom names to the target.

    When these groups are provisioning from Identity Authentication version 2 or Local Identity Directory as source system back to SAP S/4HANA Cloud version 3 as target, each group `custom name` is checked for the suffix *:authorization*. If such is detected, it is removed so that the initial value of the `externalId` of the group in SAP S/4HANA Cloud version 3 system is restored.

7.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loiod3f93a7870c341c0993cd733ed9e9b3a__postreq_vgg_5qj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[SAP S/4HANA Cloud Documentation](https://help.sap.com/viewer/9d794cbd48c648bc8a176e422772de7e/latest/en-US/7af7b8541486ed05e10000000a4450e5.html)

