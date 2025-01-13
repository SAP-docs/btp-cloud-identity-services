<!-- loioab474a823bad4b919e9903a4e254f531 -->

# Microsoft Active Directory

Follow this procedure to set up Microsoft Active Directory as a source system.



## Prerequisites

> ### Note:  
> If you have purchased the Identity Provisioning service between **September 1, 2020** and **October 20, 2020**, and you want to make a connection to this on-premise system, follow the procedure in: [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-authentication/identity-authentication/connect-to-on-premise-systems-in-sap-cloud-identity-infrastructure?version=Cloud).

-   You have installed the Cloud Connector in your corporate environment and have done the initial configuration. For more information, see: [Cloud Connector \(Neo\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d751d065774e45e1b6bdbfdfd541da13.html)
-   You have the credentials of a technical user in the Microsoft Active Directory, which is used to call the Microsoft Active Directory API to read the users and their attributes.



<a name="loioab474a823bad4b919e9903a4e254f531__context_crj_3hm_sbb"/>

## Context

You can configure Microsoft Active Directory \(Microsoft AD\) as a source system to read users, groups and permission assignments.

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

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

4.  Add *Microsoft Active Directory* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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

    Only possible value: *distinguishedName*
    
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
    
    `ldap.group.path`
    
    </td>
    <td valign="top">
    
    Enter the complete path to the node containing the groups in Microsoft AD.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.user.path`
    
    </td>
    <td valign="top">
    
    Enter the complete path to the users in Microsoft AD.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.api.version`
    
    </td>
    <td valign="top">
    
    Defines the version of LDAP Server API.

    **Possible values:** 

    -   `1` - Indicates that LDAP Server API version 1 is used.
    -   `2` - Indicates that LDAP Server API version 2 is used.

    If the property is not defined - LDAP Server API version 1 is used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.user.attributes`
    
    </td>
    <td valign="top">
    
    Shows which user attributes from the source system to be included in the Microsoft AD read result \(and respectively, in the intermediate JSON data\). Separate the attributes by comma \(,\).

    **Possible values:**

    -   Microsoft AD version 1 - Even though you specified the attributes to be included in the Microsoft AD read result, Identity Provisioning will return all attributes from the Microsoft AD.

    -   Microsoft AD version 2 - Only the specified attributes will be included in the Microsoft AD read result. *sAMAccountName* is always included as mandatory user attribute for Microsoft AD version 2.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.group.attributes`
    
    </td>
    <td valign="top">
    
    Shows which group attributes from the source system to be included in the Microsoft AD read result \(and respectively, in the intermediate JSON data\). Separate the attributes by comma \(,\).

    **Possible values:**

    -   Microsoft AD version 1 - Even though you specified the attributes to be included in the Microsoft AD read result, Identity Provisioning will return all attributes from the Microsoft AD.

    -   Microsoft AD version 2 - Only the specified attributes will be included in the or Microsoft AD.


    If nothing is set, all attributes are included.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ad.group.flatten`
    
    </td>
    <td valign="top">
    
    There are target systems that do not support nested groups \(group structures\). Therefore, if your Microsoft AD system contains such groups, they will not be resolved properly during the provisioning job. Such target systems are:

    -   *SAP Jam Collaboration*
    -   *Identity Authentication*

    To enable reading of group structures, you can use the `ad.group.flatten` property and set it to *true*. It will read the group structure recursively and will "flatten" it so that all users from all groups and subgroups will be resolved and written in the target system as members of the main parent group.

    > ### Note:  
    > Performance might be affected when `ad.group.flatten` is set to true and group structure is very complex \(contains a lot of nested groups\).

    For best results, we recommend you also set the system property `ldap.group.filter` whose value is one or multiple Microsoft AD parent groups. For example, if a parent group is named **Canteen**, the property should be set as: `ldap.group.filter`= *\(cn=Canteen\)*

    See the example below with multiple parent groups.
    
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

    `ldap.group.filter=(|(cn=Canteen)(cn=Finance)(cn=Support_Team))`

    `ad.group.flatten=true`
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Microsoft Active Directory* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    Before the read transformation, the Microsoft Active Directory attributes are represented as arrays – single-element arrays, or multi-value arrays separated by comma \(,\). After the read transformation \(in the intermediate JSON data\), the attributes are in SCIM format. For more information about Microsoft AD schema attributes, see the **Related Information** section.

    Currently, the default read transformations of the two connector versions have no differences, so there is no need to update them.

    You can change the default transformation mapping rules to reflect your current setup of entities in Microsoft Active Directory. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.id%[0]",
    >         "targetVariable": "entityIdSourceSystem",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "condition": "('%ldap.attribute.user.id%' == '%ldap.attribute.dn%')",
    >         "constant": "",
    >         "functions": [
    >           {
    >             "function": "concatString",
    >             "prefix": "(?i)cn=.*?,(.*?)",
    >             "suffix": ",%ldap.user.path%"
    >           }
    >         ],
    >         "targetVariable": "nestedPathRegex"
    >       },
    > 
    > // If a user is not a direct member of the configured user base path, then function getMatchedRegexGroup extracts the nested path from the distinguishedName of this user, 
    > // and maps the nested path to attribute ['urn:sap:cloud:scim:schemas:extension:ad:2.0:User']['nestedPath']
    >       {
    >         "condition": "('%ldap.attribute.user.id%' == '%ldap.attribute.dn%')",
    >         "sourcePath": "$.%ldap.attribute.user.id%[0]",
    >         "functions": [
    >           {
    >             "function": "getMatchedRegexGroup",
    >             "regex": "${nestedPathRegex}",
    >             "groupIndex": 1
    >           }
    >         ],
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:User']['nestedPath']",
    >         "defaultValue": ""
    >       },
    >       {
    >         "sourcePath": "$.sAMAccountName[0]",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.displayName[0]",
    >         "targetPath": "$.displayName",
    >         "optional": true
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.mail[0]",
    >         "targetPath": "$.emails[0].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.givenName[0]",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.sn[0]",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.memberOf",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups[?(@.value)]"
    >       },
    >       {
    >         "sourcePath": "$.mobile[0]",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[0].value"
    >       },
    >       {
    >         "condition": "$.mobile.length() > 0",
    >         "constant": "mobile",
    >         "targetPath": "$.phoneNumbers[0].type"
    >       },
    >       {
    >         "sourcePath": "$.telephoneNumber[0]",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[1].value"
    >       },
    >       {
    >         "condition": "$.telephoneNumber.length() > 0",
    >         "constant": "work",
    >         "targetPath": "$.phoneNumbers[1].type"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "ignore": true,
    >     "mappings": [
    >       {
    >         "sourcePath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "condition": "('%ldap.attribute.group.id%' == '%ldap.attribute.dn%')",
    >         "constant": "",
    >         "functions": [
    >           {
    >             "function": "concatString",
    >             "prefix": "(?i)cn=.*?,(.*?)",
    >             "suffix": ",%ldap.group.path%"
    >           }
    >         ],
    >         "targetVariable": "nestedPathRegex"
    >       },
    > 
    > // If a group is not a direct member of the configured group base path, then function getMatchedRegexGroup extracts the nested path from the distinguishedName of this group, 
    > // and maps the nested path to attribute ['urn:sap:cloud:scim:schemas:extension:ad:2.0:Group']['nestedPath']
    >       {
    >         "condition": "('%ldap.attribute.group.id%' == '%ldap.attribute.dn%')",
    >         "sourcePath": "$.%ldap.attribute.group.id%[0]",
    >         "functions": [
    >           {
    >             "function": "getMatchedRegexGroup",
    >             "regex": "${nestedPathRegex}",
    >             "groupIndex": 1
    >           }
    >         ],
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:Group']['nestedPath']",
    >         "defaultValue": ""
    >       },
    >       {
    >         "sourcePath": "$.sAMAccountName[0]",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.member",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "optional": true
    >       }
    >     ]
    >   }
    > }
    > ```

    As result of this mapping, that is how the data from Microsoft Active Directory looks like before and after the read transformation:


    <table>
    <tr>
    <th valign="top">

    Source JSON Data

    \(as read from Microsoft Active Directory\)
    
    </th>
    <th valign="top">

    Intermediate JSON Data

    \(as a result from the transformation\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > ...
    > "memberOf": [
    > "SALES_US",
    > "SALES_EU"
    > ]
    > …
    > ```


    
    </td>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > ...
    > "groups":[
    >   {
    >     "value": "SALES_US"
    >   },
    >   {
    >     "value": "SALES_EU"
    >   },
    > ]
    > …
    > ```


    
    </td>
    </tr>
    </table>
    
7.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loioab474a823bad4b919e9903a4e254f531__postreq_fkt_zpj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Now, start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Technical Documents](https://msdn.microsoft.com/en-us/library/jj712081.aspx)

[Setting Timeout for Ldap Operations](https://docs.oracle.com/javase/tutorial/jndi/newstuff/readtimeout.html)

[Connection Pooling Configuration](http://docs.oracle.com/javase/jndi/tutorial/ldap/connect/config.html)

[Active Directory Domain Services Overview](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview?source=recommendations)

