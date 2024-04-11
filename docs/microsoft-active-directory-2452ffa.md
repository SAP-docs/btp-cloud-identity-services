<!-- loio2452ffa16f24492e912c54e264deaf82 -->

# Microsoft Active Directory

Follow this procedure to set up Microsoft Active Directory as a target system.



## Prerequisites

> ### Restriction:  
> This system is available for standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on SAP Cloud Identity Services infrastructure and Neo environment can use it only through **SAP Identity Access Governance** bundle option.

> ### Note:  
> If you have purchased the Identity Provisioning service between **September 1, 2020** and **October 20, 2020**, and you want to make a connection to this on-premise system, follow the procedure in: [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-authentication/identity-authentication/connect-to-on-premise-systems-in-sap-cloud-identity-infrastructure?version=Cloud).

-   You have installed the Cloud Connector in your corporate environment and have done the initial configuration. For more information, see: [Cloud Connector \(Neo\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d751d065774e45e1b6bdbfdfd541da13.html)
-   You have the credentials of a technical user in the Microsoft Active Directory, which is used to call the Microsoft Active Directory API to write users, groups and their attributes.



<a name="loio2452ffa16f24492e912c54e264deaf82__context_crj_3hm_sbb"/>

## Context

You can configure Microsoft Active Directory as a target system to provision identities. Currently, you can provision users, groups and group assignments.

There are two versions of the Microsoft AD connector. Both consume the LDAP Server API to read and write users and groups. The versions are handled by the `ldap.api.version` property as follows:

-   When the value is set to *1* or the property is not defined \(typical for systems created before versioning was introduced on June 19, 2023\) LDAP Server API version 1 is used. This is the default value of `ldap.api.version`.

    When using this version of the connector, the entities \(users and groups\) are read with all attributes.

    In this version, the `group members` attribute mapping in the proxy read transformation does not include `type` sub-attribute. In this case, all members are considered of type `User`, which is the sub-attribute fallback value. As a consequence, if the external system includes nested groups, they will not be handled properly.

-   When the value is set to *2* – LDAP Server API version 2 is used.

    Тhis version of the connector is with improved performance of the read operation for user and group attributes. You are now able to define which user and group attributes to be read. This is possible by adding values to the properties `ldap.user.attributes` or `ldap.group.attributes`.

    Via these properties, you are able to add also user and group operational attributes \(attributes which the directory organizes for internal use\). For more information, refer to the official LDAP server documentation. After the additional values of the properties are set, the default read or proxy read transformations should also be adjusted accordingly.

    In this version, the `group members` attribute mapping in the proxy read transformation is enhanced with `type` sub-attribute. The sub-attribute has two possible values – `User` and `Group`. This allows you to read and preserve nested groups.

    For more information on how to update to Microsoft Active Directory version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).




## Procedure

1.  Add an access control system mapping for the **Microsoft Active Directory** in the Cloud Connector. This is needed to allow the Identity Provisioning service to access Microsoft AD as a back-end system on the intranet. For more information, see [Configure Access Control \(LDAP\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/e4ba9b3aad764b38b9c253fdbcfde713.html).

2.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

4.  Add *Microsoft Active Directory* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Enter: *LDAP*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.url`
    
    </td>
    <td valign="top">
    
    Specify a destination URL. It must be in the following format:

    `ldap://<ext_host>:<ext_port>`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.proxyType`
    
    </td>
    <td valign="top">
    
    Enter: *OnPremise*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.authentication`
    
    </td>
    <td valign="top">
    
    Enter: *BasicAuthentication*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.user`
    
    </td>
    <td valign="top">
    
    Enter the *distinguishedName* or the *userPrincipalName* of the Microsoft AD technical user. This is the user you need to establish the connection and to perform all queries.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for the Microsoft AD technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.attribute.user.id`
    
    </td>
    <td valign="top">
    
    Default property, which denotes the ID of a user.

    By default, it's set to: *cn*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.attribute.group.id`
    
    </td>
    <td valign="top">
    
    Default property, which denotes the ID of a group.

    By default, it's set to: *cn*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.attribute.dn`
    
    </td>
    <td valign="top">
    
    Default property, which denotes the distinguished name of a user or a group.

    The distinguished name is auttomatically assigned and cannot be configured. It is used in the target system configuration for conflict resolution during user or group provisioning by the service.

    Only possible value: *distinguishedName*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.group.path`
    
    </td>
    <td valign="top">
    
    Enter the complete path to the node containing the groups in Microsoft Active Directory.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.user.path`
    
    </td>
    <td valign="top">
    
    Enter the complete path to the users in Microsoft Active Directory.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `CloudConnectorLocationId`
    
    </td>
    <td valign="top">
    
    Relevant when the proxy type is *OnPremise*. Use it only if your SAP Business Technology Platform account uses more than one Cloud Connector.
    
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
    
    Example for a destination or a set of properties:


    <table>
    <tr>
    <td valign="top">
    
    `Type=LDAP`

    `Name=MyADDestination`

    `ldap.user=john.smith@some.dummy.domain.com`

    `ldap.password=********`

    `ldap.attribute.user.id=cn`

    `ldap.attribute.group.id=cn`

    `ldap.attribute.dn=distinguishedName`

    `ldap.url=ldap://abcd:123`

    `ldap.proxyType=OnPremise`

    `ldap.authentication=BasicAuthentication`

    `ldap.group.path=OU=Groups,OU=IAS,DC=global,DC=corp,DC=mycompany`

    `ldap.user.path=OU=Users,OU=IAS,DC=global,DC=corp,DC=mycompany`
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Microsoft Active Directory* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    In the intermediate JSON data, the Microsoft Active Directory attributes are in SCIM format. After the write transformation, the attributes are represented as arrays – single-element arrays, or multi-value arrays separated by comma \(,\). For more information about Microsoft AD schema attributes, see the **Related Information** section.

    Currently, the default write transformations of the two connector versions have no differences, so there is no need to update them.

    You can change the default transformation mapping rules to reflect your current setup of entities in Microsoft AD. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    > ### Note:  
    > You can provision users with *unicodePwd* attribute to Microsoft Active Directory target systems although it is not included in the default write transformation. This attribute specifies the password of the user in Windows NT operating system one-way format \(OWF\).
    > 
    > To provision the user password in encrypted format, proceed as follows:
    > 
    > 1.  Add the unicodePwd attribute mapping in the write transformation. For example:
    > 
    >     > ### Code Syntax:  
    >     > ```
    >     > {
    >     > "sourcePath": "$.Source_System_Attribute",
    >     > "targetPath": "$.unicodePwd"
    >     > }
    >     > 
    >     > ```
    > 
    > 2.  Follow the requirements for provisioning users with *unicodePwd*, as described in [unicodePwd](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-adts/6e803168-f140-4d23-b2d3-c3a8ab5917d2)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "condition": "('%ldap.attribute.user.id%' != '%ldap.attribute.dn%')",
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.%ldap.attribute.user.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    > 
    > // If a user is not a direct member of the configured user base path, then its distinguishedName is configured to be equal to CN = <userName>,<nested_path>,<base_path>, 
    > // where <nested_path> is read from "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:User']['nestedPath']"
    >       {
    >         "condition": "('%ldap.attribute.user.id%' == '%ldap.attribute.dn%')",
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:User']['nestedPath']",
    >         "optional": true,
    >         "targetVariable": "nestedPathVariable",
    >         "defaultValue": "",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "condition": "('%ldap.attribute.user.id%' == '%ldap.attribute.dn%')",
    >         "sourcePath": "$.userName",
    >         "functions": [
    >           {
    >             "function": "concatString",
    >             "prefix": "CN="
    >           },
    >           {
    >             "condition": "('${nestedPathVariable}' != '')",
    >             "function": "concatString",
    >             "suffix": ","
    >           },
    >           {
    >             "condition": "('${nestedPathVariable}' != '')",
    >             "function": "concatString",
    >             "suffix": "${nestedPathVariable}"
    >           },
    >           {
    >             "function": "concatString",
    >             "suffix": ",%ldap.user.path%"
    >           }
    >         ],
    >         "targetPath": "$.%ldap.attribute.user.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.cn[0]",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.sAMAccountName[0]"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName[0]",
    >         "defaultValue": [],
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.mail[0]",
    >         "defaultValue": [],
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.givenName[0]",
    >         "defaultValue": [],
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.sn[0]",
    >         "defaultValue": [],
    >         "optional": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "ignore": true,
    >     "mappings": [
    >       {
    >         "condition": "('%ldap.attribute.group.id%' != '%ldap.attribute.dn%')",
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    > 
    > 
    > // If a group is not a direct member of the configured group base path, then its distinguishedName is configured to be equal to CN = <displayName>,<nested_path>,<base_path>, 
    > // where <nested_path> is read from "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:Group']['nestedPath']"
    >       {
    >         "condition": "('%ldap.attribute.group.id%' == '%ldap.attribute.dn%')",
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:Group']['nestedPath']",
    >         "optional": true,
    >         "targetVariable": "nestedPathVariable",
    >         "defaultValue": "",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "condition": "('%ldap.attribute.group.id%' == '%ldap.attribute.dn%')",
    >         "sourcePath": "$.displayName",
    >         "functions": [
    >           {
    >             "function": "concatString",
    >             "prefix": "CN="
    >           },
    >           {
    >             "condition": "('${nestedPathVariable}' != '')",
    >             "function": "concatString",
    >             "suffix": ","
    >           },
    >           {
    >             "condition": "('${nestedPathVariable}' != '')",
    >             "function": "concatString",
    >             "suffix": "${nestedPathVariable}"
    >           },
    >           {
    >             "function": "concatString",
    >             "suffix": ",%ldap.group.path%"
    >           }
    >         ],
    >         "targetPath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.cn[0]",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.sAMAccountName[0]"
    >       },
    >       {
    >         "sourcePath": "$.members[*]",
    >         "targetVariable": "membersVariable",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >           {
    >             "condition": "@.type != 'Group'",
    >             "entityType": "user",
    >             "applyOnElements": true,
    >             "type": "resolveEntityIds"
    >           },
    >           {
    >             "condition": "@.type == 'Group'",
    >             "entityType": "group",
    >             "applyOnElements": true,
    >             "type": "resolveEntityIds"
    >           },
    >           {
    >             "condition": "(@.type != 'Group') && ('%ldap.attribute.user.id%' != '%ldap.attribute.dn%')",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "value",
    >             "prefix": "%ldap.attribute.user.id%=",
    >             "suffix": ",%ldap.user.path%"
    >           },
    >           {
    >             "condition": "(@.type == 'Group') && ('%ldap.attribute.group.id%' != '%ldap.attribute.dn%')",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "value",
    >             "prefix": "%ldap.attribute.group.id%=",
    >             "suffix": ",%ldap.group.path%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourceVariable": "membersVariable",
    >         "variablePath": "$[*].value",
    >         "targetPath": "$.member",
    >         "defaultValue": [],
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       }
    >     ]
    >   }
    > }
    > ```

7.  Now, add a source system from which to read users and groups. Choose from: [Source Systems](source-systems-58033be.md)

    > ### Note:  
    > Identity Provisioning escapes the following special characters: comma \(,\), plus \(+\) and semicolon \(;\) in the CN component of the distinguished name \(DN\). This means that, if a user attribute in the source system contains a special character \(`John, Smith`\), and this attribute is mapped to the CN in Microsoft AD target system, the comma will be escaped in the DN.
    > 
    > The following special characters cannot be escaped and result in an error: equal sign \(=\), less than symbol \(<\), greater than symbol \(\>\), hash sign \(\#\) and backslash \(\\\).




<a name="loio2452ffa16f24492e912c54e264deaf82__postreq_fkt_zpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Microsoft AD: Technical Documents](https://msdn.microsoft.com/en-us/library/jj712081.aspx)

[Setting Timeout for Ldap Operations](https://docs.oracle.com/javase/tutorial/jndi/newstuff/readtimeout.html)

[Connection Pooling Configuration](http://docs.oracle.com/javase/jndi/tutorial/ldap/connect/config.html)

[Active Directory Domain Services Overview](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview?source=recommendations)

