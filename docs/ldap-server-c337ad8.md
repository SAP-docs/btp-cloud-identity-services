<!-- loioc337ad8cafa54de8a623f95e88c349ba -->

# LDAP Server

Follow this procedure to set up LDAP Server as a target system.



<a name="loioc337ad8cafa54de8a623f95e88c349ba__prereq_q3c_zb5_5fb"/>

## Prerequisites

> ### Restriction:  
> This system is available for standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on SAP Cloud Identity Services infrastructure and Neo environment can use it only through **SAP Identity Access Governance** bundle option.

> ### Note:  
> If you have purchased the Identity Provisioning service between **September 1, 2020** and **October 20, 2020**, and you want to make a connection to this on-premise system, follow the procedure in: [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-authentication/identity-authentication/connect-to-on-premise-systems-in-sap-cloud-identity-infrastructure?version=Cloud).

-   You have installed the Cloud Connector in your corporate environment and have done the initial configuration. For more information, see: [Cloud Connector \(Neo\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d751d065774e45e1b6bdbfdfd541da13.html) or [Cloud Connector \(Cloud Foundry\)](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector?locale=en-US&version=Cloud)
-   **For tenants running on the infrastructure of SAP Cloud Identity Services**: You have a multi-environment subaccount in the Cloud Foundry region that maps the region of your Identity Authentication tenant and it is subscribed to the *Cloud Identity Services* application. For more information, see [Connect to On-Premise Systems in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-provisioning/identity-provisioning/connecting-to-on-premise-systems-in-sap-cloud-identity-infrastructure?locale=en-US&version=Cloud).
-   You have the credentials of a technical user in the LDAP Server, which is used to call the LDAP Server API to write users and their attributes.



<a name="loioc337ad8cafa54de8a623f95e88c349ba__context_hyf_vkn_qgb"/>

## Context

You can use LDAP Server to write entities retrieved from a source system. This scenario supports writing **users** and **group assignments**.

There are two versions of the LDAP Server connector. Both consume the LDAP Server API to read and write users and groups. The versions are handled by the `ldap.api.version` property as follows:

-   When the value is set to *1* or the property is not defined \(typical for systems created before versioning was introduced on May 25, 2023\) LDAP Server API version 1 is used. This is the default value of `ldap.api.version`.

    When using this version of the connector, the entities \(users and groups\) are read with all attributes.

-   When the value is set to *2* – LDAP Server API version 2 is used.

    Тhis version of the connector comes with improved performance of the read operation for user and group attributes. You are now able to define which user and group attributes to be read. This is possible by adding values to the properties `ldap.user.attributes` or `ldap.group.attributes`.

    Via these properties, you are able to add also user and group operational attributes \(attributes which the directory organizes for internal use\). For more information, refer to the official LDAP server documentation. After the additional values of the properties are set, the default read or proxy read transformations should also be adjusted accordingly.

    For more information on how to update to LDAP Server connector version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).




<a name="loioc337ad8cafa54de8a623f95e88c349ba__steps_nys_2ns_gy"/>

## Procedure

1.  Add an access control system mapping for the **LDAP Server** in the Cloud Connector. This is needed to allow the Identity Provisioning service to access the LDAP server as a back-end system on the intranet. For more information, see [Configure Access Control \(LDAP\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/e4ba9b3aad764b38b9c253fdbcfde713.html).

2.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

4.  Add *LDAP Server* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

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
    
    > ### Remember:  
    > We strongly recommend that you enter different paths for LDAP users and groups. That means, the value of `ldap.user.path` should be different than the value of `ldap.group.path`.

    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    The LDAP Server target system is created by default with the properties listed below:

    **Default LDAP Properties**


    <table>
    <tr>
    <td valign="top">
    
    `ldap.user.attributes=` 

    `ldap.user.object.class=` **inetOrgPerson** 

    `ldap.group.object.class=` **groupOfNames** 

    `ldap.group.uniquename.attribute=` **cn** 

    `ldap.attribute.group.id`=**cn**

    `ldap.attribute.group.member`= **member**

    `ldap.attribute.group.object.class.required`=**cn**

    `ldap.attribute.user.object.class.required`=**cn**

    `ldap.attribute.user.id=` **uid** 

    `ldap.attribute.dn`=**distinguishedName**

    `ldap.page.size=` **100** 

    `ldap.attribute.user.mail=` **mail**

    `ldap.attribute.user.mobile`=**mobile**

    `ldap.attribute.user.givenName=` **givenName** 

    `ldap.attribute.user.surname=` **sn** 

    `ldap.attribute.user.groups`= **memberOf** 

    `ldap.attribute.user.telephoneNumber`= **telephoneNumber** 
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > The **ldap.attribute.\*** properties are used as parameterized properties in the default transformation. That is, if a property used in the transformation doesn't have a value, the provisioning job will fail when the transformation is loaded on runtime and the property value is substituted.
    > 
    > Also, you can change a property and use a new one \(with a new name\). In this case, you must replace the old property with the new one at all corresponding places in the transformation.

    > ### Note:  
    > The `ldap.attribute.dn` property is auttomatically assigned and cannot be configured. It is used in the target system configuration for conflict resolution during user or group provisioning by the service.

6.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *LDAP Server* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your LDAP server. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    Currently, the default write transformations of the two connector versions have no differences, so there is no need to update them.

    Before the write transformation \(in the intermediate JSON data\), the entity attributes are in SCIM format. After the transformation, the attributes in the LDAP Server are represented as arrays \(single-element arrays, or multi-value arrays separated by comma \(,\)\). For more information, see the official documentation for LDAP Server schema attributes in the **Related Information** section.

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
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
    >     "ignore": true,
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
    >             "condition": "@.type != 'Group'",
    >             "entityType": "user",
    >             "type": "resolveEntityIds"
    >           },
    >           {
    >             "condition": "@.type == 'Group'",
    >             "entityType": "group",
    >             "type": "resolveEntityIds"
    >           },
    >           {
    >             "condition": "@.type != 'Group'",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "value",
    >             "prefix": "%ldap.attribute.user.id%=",
    >             "suffix": ",%ldap.user.path%"
    >           },
    >           {
    >             "condition": "@.type == 'Group'",
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

    Below is illustrated an example of how the data from LDAP Server looks like before and after executing a certain mapping from the write transformation:


    <table>
    <tr>
    <th valign="top">

    Transformation Snippet

    \(from the group mapping\)
    
    </th>
    <th valign="top">

    Intermediate JSON Data

    \(before the transformation\)
    
    </th>
    <th valign="top">

    Target JSON Data

    \(written in the LDAP Server\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > 
    > "group": {
    > 	...
    >   {
    >     "sourcePath": "$.members[*]",
    >     "preserveArrayWithSingleElement": true,
    >     "optional": true,
    >     "targetVariable": "membersVariable",
    >     "functions": [
    > 	   {
    >           "condition": "@.type != 'Group'",
    >           "entityType": "user",
    >           "type": "resolveEntityIds"
    > 	   },
    > 	   {
    > 		"condition": "@.type == 'Group'",
    > 		"entityType": "group",
    > 		"type": "resolveEntityIds"
    > 	   },
    > 	   {
    > 		"condition": "@.type != 'Group'",
    > 		"function": "concatString",
    > 		"applyOnElements": true,
    > 		"applyOnAttribute": "value",
    > 		"prefix": "%ldap.attribute.user.id%=",
    > 
    > 		"suffix": ",%ldap.user.path%"
    > 
    >    	},
    > 	   {
    > 		"condition": "@.type == 'Group'",
    > 		"function": "concatString",
    > 		"applyOnElements": true,
    > 		"applyOnAttribute": "value",
    > 		"prefix": "%ldap.attribute.group.id%=",
    > 		"suffix": ",%ldap.group.path%"
    > 
    > 	   }
    > 	]
    >    },
    >    {
    > 	"sourceVariable": "membersVariable",
    > 	"preserveArrayWithSingleElement": true,
    > 	"optional": true,
    > 	"targetPath": "$.member",
    > 
    > 	"variablePath": "$[*].value"
    > 
    >    }
    >   ]
    >  }
    > }
    > 
    > ```


    
    </td>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > ...
    > "members":[
    >   {
    >     "value": "SALES_US"
    >   },
    >   {
    >     "value": "SALES_EU"
    >   },
    >   {
    >     "value": "SALES_JA"
    >   }
    > ]
    > …
    > ```


    
    </td>
    <td valign="top">
    
    > ### Sample Code:  
    > ```
    > ...
    > "member": [
    >    "SALES_US",
    >    "SALES_EU",
    >    "SALES_JA"
    > ]
    > …
    > ```


    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > By default, the **cn** attribute is used for writing the groups. An administrator can change this behavior by setting the following properties:
    > 
    > -   `ldap.group.uniquename.attribute` – the value can be either the CN or the whole DN \(**distinguishedName**\) of the group.
    > -   `ldap.attribute.group.id` – the value can be CN or another attribute to be used as a group ID instead \(for example, **displayName** or **description**\).
    > 
    > For more information about these properties, see: [List of Properties](list-of-properties-d6f3577.md)

7.  Now, add a source system to read users and groups from it. Choose from: [Source Systems](source-systems-58033be.md)


**Related Information**  


[Technical Documents](https://msdn.microsoft.com/en-us/library/jj712081.aspx)

[Setting Timeout for Ldap Operations](https://docs.oracle.com/javase/tutorial/jndi/newstuff/readtimeout.html)

[Connection Pooling Configuration](http://docs.oracle.com/javase/jndi/tutorial/ldap/connect/config.html)

