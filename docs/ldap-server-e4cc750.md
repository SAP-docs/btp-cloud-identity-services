<!-- loioe4cc75008246420b902ef38b13d94fdf -->

# LDAP Server

Follow this procedure to set up LDAP Server as a proxy system.



<a name="loioe4cc75008246420b902ef38b13d94fdf__prereq_xjc_5ln_qgb"/>

## Prerequisites

> ### Note:  
> This system is available for all standalone tenants. Bundle tenants running on SAP Cloud Identity Services infrastructure and Neo environment can use it as a proxy system for reading entities only.

> ### Note:  
> If you have purchased the Identity Provisioning service between **September 1, 2020** and **October 20, 2020**, and you want to make a connection to this on-premise system, follow the procedure in: [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-authentication/identity-authentication/connect-to-on-premise-systems-in-sap-cloud-identity-infrastructure?version=Cloud).

-   You have installed the Cloud Connector in your corporate environment and have done the initial configuration. For more information, see: [Cloud Connector \(Neo\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d751d065774e45e1b6bdbfdfd541da13.html) or [Cloud Connector \(Cloud Foundry\)](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector?locale=en-US&version=Cloud)
-   **For tenants running on the infrastructure of SAP Cloud Identity Services**: You have a multi-environment subaccount in the Cloud Foundry region that maps the region of your Identity Authentication tenant and it is subscribed to the *Cloud Identity Services* application. For more information, see [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-provisioning/identity-provisioning/connecting-to-on-premise-systems-in-sap-cloud-identity-infrastructure?locale=en-US&version=Cloud).
-   You have the credentials of a technical user in the LDAP Server, which is used to call the LDAP Server API to read and write users and their attributes.

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loioe4cc75008246420b902ef38b13d94fdf__context_hyf_vkn_qgb"/>

## Context

You can use LDAP Server as a proxy connector to execute *hybrid* scenarios. That means, it can provision its entities to another \(external\) back-end system by request, and then can continue executing CRUD operations back to the LDAP Server, whenever the external back-end requests such.

This scenario supports provisioning **users**, **groups** and **group assignments**.

There are two versions of the LDAP Server connector. Both consume the LDAP Server API to read and write users and groups. The versions are handled by the `ldap.api.version` property as follows:

-   When the value is set to *1* or the property is not defined \(typical for systems created before versioning was introduced on May 25, 2023\) LDAP Server API version 1 is used. This is the default value of `ldap.api.version`.

    When using this version of the connector, the entities \(users and groups\) are read with all attributes.

    In this version, the `group members` attribute mapping in the proxy read transformation does not include `type` sub-attribute. In this case, all members are considered of type `User`, which is the sub-attribute fallback value. As a consequence, if the external system includes nested groups, they will not be handled properly.

-   When the value is set to *2* – LDAP Server API version 2 is used.

    Тhis version of the connector comes with improved performance of the read operation for user and group attributes. You are now able to define which user and group attributes to be read. This is possible by adding values to the properties `ldap.user.attributes` or `ldap.group.attributes`.

    Via these properties, you are able to add also user and group operational attributes \(attributes which the directory organizes for internal use\). For more information, refer to the official LDAP server documentation. After the additional values of the properties are set, the default read or proxy read transformations should also be adjusted accordingly.

    In this version, the `group members` attribute mapping in the proxy read transformation is enhanced with `type` sub-attribute. The sub-attribute has two possible values – `User` and `Group`. This allows you to read and preserve nested groups.

    For more information on how to update to LDAP Server connector version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).


> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



<a name="loioe4cc75008246420b902ef38b13d94fdf__steps_cm3_zln_qgb"/>

## Procedure

1.  Open Cloud Connector to add an access control system mapping for **LDAP Server**. This is needed to allow the Identity Provisioning service to access LDAP Server as a back-end system on the intranet. To learn how, see: [Configure Access Control \(LDAP\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/e4ba9b3aad764b38b9c253fdbcfde713.html)

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

6.  Add *LDAP Server* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    Specify the destination URL. It must be in the following format:

    `ldap://<external_host>:<external_port>`
    
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
    
    Enter the *distinguishedName* of the technical LDAP user. This is the user you need to establish the connection and to perform all queries.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for the LDAP technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.group.path`
    
    </td>
    <td valign="top">
    
    Enter the complete path to the node containing the groups in the LDAP tree.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ldap.user.path`
    
    </td>
    <td valign="top">
    
    Enter the complete path to the users in the LDAP tree.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`ldap.api.version`
    
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
    
    \(Optional\) `ldap.group.filter`
    
    </td>
    <td valign="top">
    
    You can optimize the search to return only particular groups.

    To enter correct group filters, stick to the standard LDAP specification. See: [LDAP Representation of Filters – Examples](https://tools.ietf.org/html/rfc4515#section-4).

    For example:

    Value *\(cn=mar\*\)* will return only groups whose CN starts with "mar" \(such as *marked*, *March*, or *Marketing*\).

    By default, this filter is empty. That is, if the property is not specified, the filter will search for every group.
    
    </td>
    </tr>
    </table>
    
    > ### Remember:  
    > We strongly recommend that you enter different paths for LDAP users and groups. That means, the value of `ldap.user.path` should be different than the value of `ldap.group.path`.

    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    The LDAP Server proxy system is created by default with the properties listed below:

    **Default LDAP Properties**


    <table>
    <tr>
    <td valign="top">
    
    `ldap.user.object.class=` **inetOrgPerson** 

    `ldap.group.object.class=` **groupOfNames** 

    `ldap.group.uniquename.attribute=` **cn** 

    `ldap.attribute.group.object.class.required`=**cn**

    `ldap.attribute.user.object.class.required`=**cn**

    `ldap.attribute.group.id`=**cn**

    `ldap.attribute.group.member`= **member**

    `ldap.attribute.user.id=` **uid** 

    `ldap.attribute.dn`=**distinguishedName**

    `ldap.attribute.user.mail=` **mail**

    `ldap.attribute.user.mobile`=**mobile**

    `ldap.attribute.user.givenName=` **givenName** 

    `ldap.attribute.user.surname=` **sn** 

    `ldap.attribute.user.groups`= **memberOf** 

    `ldap.attribute.user.telephoneNumber`= **telephoneNumber**

    `ldap.respond.with.resource.after.create`=**true**

    `ldap.respond.with.resource.after.update`=**true** 
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > The **ldap.attribute.\*** properties are used as parameterized properties in the default transformation. That is, if a property used in the transformation doesn't have a value, the provisioning job will fail when the transformation is loaded on runtime and the property value is substituted.
    > 
    > Also, you can change a property and use a new one \(with a new name\). In this case, you must replace the old property with the new one at all corresponding places in the transformation.

8.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *LDAP Server* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your LDAP Server. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    Default read and write transformations:

    > ### Tip:  
    > The proxy *Read Transformation* is used when the external client application \(for example, SAP Identity Management\) makes initial load. That is, executing GET requests to the resource endpoints \(**/Users** or **/Groups**\) to retrieve the corresponding entities of the particular type. The external client application can also execute GET requests to a single resource endpoint \(querying a single resource is supported\). In this case, the proxy system acts as a *source* one.
    > 
    > The proxy *Write Transformation* is used when the external application manages the entities in the proxy system – creates new entities, updates existing ones, or deletes existing ones. In this case, the proxy system acts as a *target* one.
    > 
    > However, after a *Create* or *Update* operation is performed on the proxy system, the *Read Transformation* is applied to the result, so that the created or updated entity is sent back to the external application. This behavior demonstrates that the proxy *Read Transformation* is used for *write* cases, as well.

    **Default read and write transformations for LDAP Server connector version 1:**


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
    >         "sourcePath": "$.%ldap.attribute.user.id%[0]",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.mail%[0]",
    >         "targetPath": "$.emails[0].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.givenName%[0]",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.surname%[0]",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.groups%",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups[?(@.value)]"
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.mobile%[0]",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[0].value"
    >       },
    >       {
    >         "condition": "$.%ldap.attribute.user.mobile%.length() > 0",
    >         "constant": "mobile",
    >         "targetPath": "$.phoneNumbers[0].type"
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.telephoneNumber%[0]",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[1].value"
    >       },
    >       {
    >         "condition": "$.%ldap.attribute.user.telephoneNumber%.length() > 0",
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
    >         "sourcePath": "$.%ldap.attribute.group.id%[0]",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.group.member%",
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
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.%ldap.attribute.user.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.%ldap.attribute.user.object.class.required%[0]"
    >       },
    >       {
    >         "sourcePath": "$.emails[*].value",
    >         "optional": true,
    >         "targetPath": "$.%ldap.attribute.user.mail%"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.%ldap.attribute.user.givenName%[0]"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.%ldap.attribute.user.surname%[0]"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers[*].value",
    >         "optional": true,
    >         "targetPath": "$.%ldap.attribute.user.mobile%"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.%ldap.attribute.group.object.class.required%[0]"
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
    >         "variablePath": "$[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.member"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
    **Default read transformation for LDAP Server connector version 2:**


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
    >         "sourcePath": "$.%ldap.attribute.user.id%[0]",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.mail%[0]",
    >         "targetPath": "$.emails[0].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.givenName%[0]",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.surname%[0]",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.groups%",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.groups[?(@.value)]"
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.mobile%[0]",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[0].value"
    >       },
    >       {
    >         "condition": "$.%ldap.attribute.user.mobile%.length() > 0",
    >         "constant": "mobile",
    >         "targetPath": "$.phoneNumbers[0].type"
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.user.telephoneNumber%[0]",
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[1].value"
    >       },
    >       {
    >         "condition": "$.%ldap.attribute.user.telephoneNumber%.length() > 0",
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
    >         "sourcePath": "$.%ldap.attribute.group.id%[0]",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.%ldap.attribute.group.member%",
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
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.%ldap.attribute.user.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.%ldap.attribute.user.object.class.required%[0]"
    >       },
    >       {
    >         "sourcePath": "$.emails[*].value",
    >         "optional": true,
    >         "targetPath": "$.%ldap.attribute.user.mail%"
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.%ldap.attribute.user.givenName%[0]"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.%ldap.attribute.user.surname%[0]"
    >       },
    >       {
    >         "sourcePath": "$.phoneNumbers[*].value",
    >         "optional": true,
    >         "targetPath": "$.%ldap.attribute.user.mobile%"
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.%ldap.attribute.group.id%[0]",
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.%ldap.attribute.group.object.class.required%[0]"
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
    >         "variablePath": "$[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.member"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > By default, the **cn** attribute is used for every read or written group. An administrator can change this behavior by setting the following properties:
    > 
    > -   `ldap.group.uniquename.attribute` – the value can be either the CN or the whole DN \(**distinguishedName**\) of the group.
    > -   `ldap.attribute.group.id` – the value can be CN or another attribute to be used as a group ID instead \(for example, **displayName** or **description**\).
    > 
    > For more information about these properties, see: [List of Properties](list-of-properties-d6f3577.md)

9.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.


**Related Information**  


[Technical Documents](https://msdn.microsoft.com/en-us/library/jj712081.aspx)

[Setting Timeout for Ldap Operations](https://docs.oracle.com/javase/tutorial/jndi/newstuff/readtimeout.html)

[Connection Pooling Configuration](http://docs.oracle.com/javase/jndi/tutorial/ldap/connect/config.html)

