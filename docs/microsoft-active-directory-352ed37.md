<!-- loio352ed37dfa2b40d5ae538a65b9590ed9 -->

# Microsoft Active Directory

Follow this procedure to set up Microsoft Active Directory as a proxy system.



<a name="loio352ed37dfa2b40d5ae538a65b9590ed9__prereq_zvl_bnv_jgb"/>

## Prerequisites

> ### Note:  
> If you have purchased the Identity Provisioning service between **September 1, 2020** and **October 20, 2020**, and you want to make a connection to this on-premise system, follow the procedure in: [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-authentication/identity-authentication/connect-to-on-premise-systems-in-sap-cloud-identity-infrastructure?version=Cloud).

-   You have installed the Cloud Connector in your corporate environment and have done the initial configuration. For more information, see: [Cloud Connector \(Neo\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d751d065774e45e1b6bdbfdfd541da13.html)
-   You have the credentials of a technical user in the Microsoft Active Directory, which is used to call the Microsoft Active Directory API to read and write users, groups and their attributes.

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



## Context

You can use Microsoft Active Directory as a proxy connector to execute *hybrid* scenarios. That means, it can provision its entities to another \(external\) back-end system by request, and then can continue executing CRUD operations back to Microsoft Active Directory, whenever the external back-end requests such.

This scenario supports provisioning **users**, **groups** and **group assignments**.

There are two versions of the Microsoft AD connector. Both consume the LDAP Server API to read and write users and groups. The versions are handled by the `ldap.api.version` property as follows:

-   When the value is set to *1* or the property is not defined \(typical for systems created before versioning was introduced on June 19, 2023\) LDAP Server API version 1 is used. This is the default value of `ldap.api.version`.

    When using this version of the connector, the entities \(users and groups\) are read with all attributes.

    In this version, the `group members` attribute mapping in the proxy read transformation does not include `type` sub-attribute. In this case, all members are considered of type `User`, which is the sub-attribute fallback value. As a consequence, if the external system includes nested groups, they will not be handled properly.

-   When the value is set to *2* – LDAP Server API version 2 is used.

    Тhis version of the connector is with improved performance of the read operation for user and group attributes. You are now able to define which user and group attributes to be read. This is possible by adding values to the properties `ldap.user.attributes` or `ldap.group.attributes`.

    Via these properties, you are able to add also user and group operational attributes \(attributes which the directory organizes for internal use\). For more information, refer to the official LDAP server documentation. After the additional values of the properties are set, the default read or proxy read transformations should also be adjusted accordingly.

    In this version, the `group members` attribute mapping in the proxy read transformation is enhanced with `type` sub-attribute. The sub-attribute has two possible values – `User` and `Group`. This allows you to read and preserve nested groups.

    For more information on how to update to Microsoft Active Directory version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).


> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



## Procedure

1.  Open Cloud Connector to add an access control system mapping for **Microsoft Active Directory**. This is needed to allow the Identity Provisioning service to access Microsoft Active Directory as a back-end system on the intranet. To learn how, see: [Configure Access Control \(LDAP\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/e4ba9b3aad764b38b9c253fdbcfde713.html)

2.  Open your subaccount in SAP BTP cockpit \(valid for OAuth authentication to the Identity Provisioning proxy system\).

    > ### Note:  
    > If you have a bundle tenant, then in the cockpit → *Neo* → *Overview*, you can see the Global account, which SAP provides for your bundle in the corresponding Identity Provisioning region. Then, in the global account, you can see your subaccount, where the Identity Provisioning is enabled as a service for the bundle. The display name of the subaccount starts with **SAP\_BUNDLE**.

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Users & Authorizations* \> *Administrators*.

4.  Create a technical user with the necessary authorizations. It will later be used by the external consumer to connect to Identity Provisioning.

    -   For **Certificate-based authentication**, follow the procedure in [Manage Certificates for Inbound Connection](Operation-Guide/manage-certificates-for-inbound-connection-952e7c7.md) → *SAP BTP, Neo Environment*

    -   For **OAuth authentication**, proceed as follows:

        1.  Go to *Security* \> *OAuth* \> *Clients* and choose *Register New Client*.

        2.  From the *Subscription* combo box, select **<provider\_subaccount\>/ipsproxy**.

        3.  From the *Authorization Grant* combo box, select **Client Credentials**.

        4.  In the *Secret* field, enter a password \(client secret\) and remember it. You will need it later, for the repository configuration in the external system.

        5.  Copy/paste and save \(in a notepad\) the generated *Client ID*. You will need it later, too.

        6.  From the left-side navigation, choose *Subscriptions* \> *Java Applications* \> *ipsproxy* .

        7.  From the left-side navigation, choose *Roles* \> *IPS\_PROXY\_USER*.

        8.  Choose *Assign* and enter **oauth\_client\_<client\_ID\>**.

            For *<client\_ID\>*, enter the one you have saved in the previous main step.


    -   For **Certificate-based authentication**, upload the certificate for the technical user of type *System*, as described in [Add System as Administrator](https://help.sap.com/docs/identity-authentication/identity-authentication/add-administrators?version=Cloud#add-system-as-administrator) and enable the *Access Proxy System API* permission.

    -   For **Basic authentication**, proceed as follows:

        1.  Add an administrator user of type **System** and configure the basic authentication method for this user.

            If you already have a technical user, skip this step.

        2.  Save your changes.

        3.  Select your administrator user of type **System** and enable the *Access Proxy System API* permission.

        4.  Save your changes.



5.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

6.  Add *Microsoft Active Directory* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

7.  Choose the *Properties* tab to configure the connection settings for your system.

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

    Only possible value: *distinguishedName*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.respond.with.resource.after.create`
    
    </td>
    <td valign="top">
    
    Default property, whose value is *true*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.respond.with.resource.after.update`
    
    </td>
    <td valign="top">
    
    Default property, whose value is *true*.
    
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
    
    \(Optional\)`ldap.api.version`
    
    </td>
    <td valign="top">
    
    Handles the version of the LDAP Server connector.

    **Possible values:**

    -   *1*- Indicates that Microsoft AD API version 1 is used.

    -   *2* - Indicates that Microsoft AD API version 2 is used.


    Default value: *1*
    
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

8.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *Microsoft Active Directory* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your Microsoft AD. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    Default read and write transformations:

    > ### Tip:  
    > The proxy *Read Transformation* is used when the external client application \(for example, SAP Identity Management\) makes initial load. That is, executing GET requests to the resource endpoints \(**/Users** or **/Groups**\) to retrieve the corresponding entities of the particular type. The external client application can also execute GET requests to a single resource endpoint \(querying a single resource is supported\). In this case, the proxy system acts as a *source* one.
    > 
    > The proxy *Write Transformation* is used when the external application manages the entities in the proxy system – creates new entities, updates existing ones, or deletes existing ones. In this case, the proxy system acts as a *target* one.
    > 
    > However, after a *Create* or *Update* operation is performed on the proxy system, the *Read Transformation* is applied to the result, so that the created or updated entity is sent back to the external application. This behavior demonstrates that the proxy *Read Transformation* is used for *write* cases, as well.

    > ### Note:  
    > You can provision users with *unicodePwd* attribute to Microsoft Active Directory proxy systems although it is not included in the default proxy write transformation. This attribute specifies the password of the user in Windows NT operating system one-way format \(OWF\).
    > 
    > To provision the user password in encrypted format, proceed as follows:
    > 
    > 1.  Add the unicodePwd attribute mapping in the proxy write transformation. For example:
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

    **Default read and write transformations for Microsoft AD connector version 1:**


    <table>
    <tr>
    <th valign="top">

    Read Transformation
    
    </th>
    <th valign="top">

    Write Transformation
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.id%[0]",
    >         "targetVariable": "entityIdSourceSystem",
    >         "targetPath": "$.id",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "targetPath": "$.meta.location",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
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
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdSourceSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "targetPath": "$.meta.location",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
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


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
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
    >  
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
    >         "optional": true,
    >         "targetPath": "$.displayName[0]"
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "optional": true,
    >         "targetPath": "$.mail[0]"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.givenName[0]"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.sn[0]"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "condition": "('%ldap.attribute.group.id%' != '%ldap.attribute.dn%')",
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    > 	  
    > // If a group is not a direct member of the configured group base path, then its distinguishedName is configured to be equal to CN = <displayName>,<nested_path>,<base_path>, 
    > // where <nested_path> is read from "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:Group']['nestedPath']"
    >  
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
    >         "constant": [],
    >         "targetPath": "$.member"
    >       },
    >       {
    >         "sourcePath": "$.members[*]",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetVariable": "membersVariable",
    >         "functions": [
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
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.member",
    >         "variablePath": "$[*].value"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
    **Default read transformation for Microsoft AD connector version 2:**


    <table>
    <tr>
    <th valign="top">

    Read Transformation
    
    </th>
    <th valign="top">

    Write Transformation
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.id%[0]",
    >         "targetVariable": "entityIdSourceSystem",
    >         "targetPath": "$.id",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "targetPath": "$.meta.location",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
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
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdSourceSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "targetPath": "$.meta.location",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
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
    >         "targetPath": "$.members",
    >         "optional": true
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
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
    >  
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
    >         "optional": true,
    >         "targetPath": "$.displayName[0]"
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "optional": true,
    >         "targetPath": "$.mail[0]"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.givenName[0]"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.sn[0]"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "condition": "('%ldap.attribute.group.id%' != '%ldap.attribute.dn%')",
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    > 	  
    > // If a group is not a direct member of the configured group base path, then its distinguishedName is configured to be equal to CN = <displayName>,<nested_path>,<base_path>, 
    > // where <nested_path> is read from "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:Group']['nestedPath']"
    >  
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
    >         "constant": [],
    >         "targetPath": "$.member"
    >       },
    >       {
    >         "sourcePath": "$.members[*]",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetVariable": "membersVariable",
    >         "functions": [
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
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.member",
    >         "variablePath": "$[*].value"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
9.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.




<a name="loio352ed37dfa2b40d5ae538a65b9590ed9__postreq_cf4_lgj_kfb"/>

## Next Steps

When a proxy system is connected to an external backend system \(in the case of SAP Identity Management this means the exported CSV file is imported into the Identity Management Admin UI and a repository is configured\), you can start managing the users and groups into this external system. Usually, the first operation is the initial load of the existing entities into your external system. When this load has finished, changes in the external system, such as creating new users or updating existing ones, can trigger CRUD requests back to the proxy system.

To see an example with SAP Identity Management, see [Hybrid Scenario: SAP Identity Management](https://help.sap.com/docs/identity-provisioning/identity-provisioning/hybrid-scenario-sap-identity-management?version=Cloud) → sections **Next Steps** and **Future Identity Lifecycle**.

> ### Caution:  
> Effective **September 2020**, Shanghai \(China\) tenants that reside on SAP BTP, Neo environment can be only accessed on the following domain: `dispatcher.cn1.platform.sapcloud.cn`
> 
> So make sure you use the correct domain when you construct your REST API requests.
> 
> For example: **GET** *https://ipsproxyabcd12345-xyz789.dispatcher.cn1.platform.sapcloud.cn/ipsproxy/api/v1/scim/bbb111aa-1234-aaaa-7777-1234567abcde/Users/s123456789*
> 
> To learn more, see: [Proxy Systems](proxy-systems-b10d68a.md)

**Related Information**  


[Microsoft AD: Technical Documents](https://msdn.microsoft.com/en-us/library/jj712081.aspx)

[Setting Timeout for Ldap Operations](https://docs.oracle.com/javase/tutorial/jndi/newstuff/readtimeout.html)

[Connection Pooling Configuration](http://docs.oracle.com/javase/jndi/tutorial/ldap/connect/config.html)

[Active Directory Domain Services Overview](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview?source=recommendations)

