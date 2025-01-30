<!-- loiod6f3577f30ec4af98e734b0126a60e37 -->

# List of Properties

On this page you can find all the available properties to use in the Identity Provisioning service. You can filter them by system type name, "All Systems", by a word or only part of it.



****


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Description

</th>
<th valign="top">

System Type

</th>
</tr>
<tr>
<td valign="top">

`Type` 

</td>
<td valign="top">

Protocol type for making a connection

**Possible values:**

-   *HTTP*
-   *LDAP*
-   *RFC*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`URL` 

</td>
<td valign="top">

URL needed to make an HTTP\(S\) connection to an on-premise system or a cloud service

**Possible value:**

-   When the proxy type of the HTTP connection is `Internet`:

    `http(s)://<host>:<port>`

-   When the proxy type of the HTTP connection is `OnPremise`:

    `http://<virtualhost>:<virtualport>`


**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All HTTP systems

</td>
</tr>
<tr>
<td valign="top">

`ProxyType` 

</td>
<td valign="top">

Proxy type required for HTTP connection

**Possible values:**

-   *Internet*
-   *OnPremise*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All HTTP systems

</td>
</tr>
<tr>
<td valign="top">

`Authentication` 

</td>
<td valign="top">

Authentication type required for HTTP connection

**Possible values:**

-   *NoAuthentication*

-   *BasicAuthentication*

-   *ClientCertificateAuthentication*


**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All HTTP systems

> ### Note:  
> Identity Provisioning supports certificate-based authentication for secure communication with the provisioning systems \(connectors\) provided by the service. Refer to the documentation of the respective systems to find out how to upload Identity Provisioning certificates on their end. For example, see [How to Create Communication Users](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/0377adea0401467f939827242c1f4014.html) in SAP BTP ABAP Environment.



</td>
</tr>
<tr>
<td valign="top">

`User` 

</td>
<td valign="top">

It represents:

-   User name – used in standard destinations
-   Client ID – used for access token retrieval in OAuth HTTP destinations

**Possible values:** Text/numeric string

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All HTTP systems

</td>
</tr>
<tr>
<td valign="top">

`client_id` 

</td>
<td valign="top">

The OAuth Client id used for access token retrieval in case of OAuth certificate authentication.

Possible values: Text/numeric string

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All HTTP systems

</td>
</tr>
<tr>
<td valign="top">

`Password` 

</td>
<td valign="top">

\(Credential\)

It represents:

-   Password – used in standard destinations
-   Client secret key – used for access token retrieval in OAuth HTTP destinations

**Possible values:** Encrypted string

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All HTTP systems

</td>
</tr>
<tr>
<td valign="top">

`abap.user.filter` 

</td>
<td valign="top">

Filters users by a regular expression on their username. The regex can define any kind of search pattern.

> ### Caution:  
> This property is rather obsolete. For newly created systems, please use `abap.user.name.filter`.

**Possible values:**

For example: `abap.user.filter` = *^A.\**

This filter returns all user names that start with capital *A*.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`abap.role.filter` 

</td>
<td valign="top">

> ### Caution:  
> This property is rather obsolete. For newly created systems, please use `abap.role.name.filter`.

**Possible values:**

For example: `abap.role.filter` = *^order.\**

This filter provisions all roles that start with *order*.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`abap.user.name.filter` 

</td>
<td valign="top">

Filters user roles by a regular expression. The regex can defineFilters users by a regular expression on their username. The regex can define any kind of search pattern.

This property has a higher priority over `abap.user.filter`. That means, if you set both properties in a system, the value of `abap.user.name.filter` will be used. However, if the value of `abap.user.name.filter` is empty, then `abap.user.filter`’s value will be used instead.

> ### Note:  
> As `abap.user.filter` is obsolete, we recommend that you use `abap.user.name.filter`.

**Possible values:**

For example: `abap.user.name.filter` = *^MAR.\**

This regex reads all user names that start with *MAR*, such as *MARK*, *MARTINA*, and so on.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`abap.role.name.filter` 

</td>
<td valign="top">

Filters roles by a regular expression. The regex can define any kind of search pattern.

This property has a higher priority over `abap.role.filter`. That means, if you set both properties in a system, the value of `abap.role.name.filter` will be used. However, if the value of `abap.role.name.filter` is empty, then `abap.role.filter`’s value will be used instead.

> ### Note:  
> As `abap.role.filter` is obsolete, we recommend that you use `abap.role.name.filter`.

**Possible values:**

For example: `abap.role.name.filter` = *^inter.\**

This regex reads all roles that start with *inter*, such as *internal*, *internship*, and so on.

For more information about specific search patterns, refer to SAP Note [3546855](https://me.sap.com/notes/3546855).

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`abap.role.prefix`

</td>
<td valign="top">

This property distinguishes SAP Application Server ABAP \(AS ABAP\) roles by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `ABAP_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the roles that are read from the AS ABAP source system and will be provisioned to the target system with the following name pattern: <code>ABAP_<i class="varname">&lt;role_name&gt;</i></code>. This way AS ABAP roles in the target system will be easily distinguished from roles provisioned from other applications.

    If the property is not set, the AS ABAP roles will be read and provisioned to the target system with their actual role names.

-   When **set in the target system**, only roles containing the `ABAP_` prefix in their role name will be provisioned to AS ABAP. Roles without this prefix in their names won't be provisioned.

    If the property is not set, all roles will be be provisioned to AS ABAP.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`abap.user.membership.filter` 

</td>
<td valign="top">

Filters users by a regular expression, based on their *Role* memberships in AS ABAP. The regex can define any kind of search pattern.

**Possible values:**

For example: `abap.user.membership.filter` = *\(?i\)^new.\**

This reads all users who have an assigned role which starts with *new*. This regex is case insensitive, which means the result can be roles starting with *new*, or *New*, or *NEW*, and so on.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.api.key`

</td>
<td valign="top">

\(Credential\)

This property corresponds to the *Application key* for your SAP Ariba application. You obtain it during the creation of your application in the SAP Ariba developer portal.

See: [How to find your application's application key and OAuth client ID](https://help.sap.com/viewer/b61dd8c7e22c4fe489f191f66b4c48d6/cloud/en-US/eb84c80e00324dbe972cd3078bab0e32.html)

**Possible values:** Text/numeric string

For example: This property corresponds to the SAP Ariba realm that your application has access to. To learn how to get it, see: *123abc123XYZ000abc123ABC012345*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.realm.id`

</td>
<td valign="top">

[This property corresponds to the SAP Ariba realm that yourHow to find your SAP Ariba realm name?](https://blogs.sap.com/2021/01/12/how-to-find-your-sap-ariba-realm-name/)

**Possible values:** Text/numeric string

For example: *123abc123XYZ000abc123ABC012345*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.group.flatten`

</td>
<td valign="top">

This property allows or forbids reading "nested groups" \(group structures\) from SAP Ariba Applications. If enabled \(*true*\), group members of type *group* will be ignored during read in order not to be provisioned to target systems that do not support nested groups.

**Possible values:**

Default value:

-   *Source systems:**true*

-   *Proxy systems:* *false*


Predefined value \(during system creation\):

-   *Source systems:* *true*

    Set it to *false* only if you are sure that the target system supports nested groups.

-   *Proxy systems:* *false*

    Leave the default/predefined value only if you are sure that the consuming external application \(identity management system\) supports nested groups.

    > ### Note:  
    > If you set this property to *true* in your proxy system, the execution of requests with parameter `membersType=group` will not be supported.


**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP Ariba Applications groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `ARIBA_APPLICATIONS_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Ariba Applications source system and will be provisioned to the target system with the following name pattern: <code>ARIBA_APPLICATIONS_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Ariba Applications groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Ariba Applications groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `ARIBA_APPLICATIONS_` prefix in their display name will be provisioned to SAP Ariba Applications. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Ariba Applications.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.support.patch.operation`

</td>
<td valign="top">

The default value of this property is *false*. But for SAP Ariba Applications proxy systems, this property appears during creation and its predefined value is *true*. That means, when the Identity Provisioning identifies a changed entity in the back-end system, it will execute the updates as PATCH requests instead of PUT. That is, only changes will be written in SAP Ariba Applications, instead of provisioning the whole entity data.

Note that only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated. For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

> ### Note:  
> Removing empty groups returns 400 Bad Request instead of 200 OK.

**Possible values:**

Default value: *false*

Predefined value \(during system creation\): *true*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.user.filter`

</td>
<td valign="top">

When specified, only those SAP Ariba Applications users matching the filter expression will be read.

**Possible values:**

For example: *userName eq "SmithJ"* 

**System Role:** Source

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.group.filter`

</td>
<td valign="top">

When specified, only those SAP Ariba Applications groups matching the filter expression will be read.

**Possible values:**

For example: *displayName eq "ProjectTeam1"*

**System Role:** Source

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.content.type`

</td>
<td valign="top">

This property makes a SAP Ariba Applications connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP Ariba Applications could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Ariba Applications. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*

Default value: *userName* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists on the SAP Ariba Applications target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

**Possible values:**

Default value \(when not specified\): *displayName*

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP Ariba Applications connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Ariba Applications system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.group.members.page.size`

</td>
<td valign="top">

The number of group members that SAP Ariba Applicationsreturns per request when reading a group.

When the Identity Provisioning reads a group, it compares the number of group members with the value configured for `ariba.applications.group.members.page.size`. Depending on the number of group members, you can expect the following results:

-   If the number of group members is equal or exceeds the configured value, and the `ariba.applications.group.members.paging.enabled` property is set to *true*, Identity Provisioning will read all group members in separate requests.

    For example, if a group has 6 group members and the value of the page size is set to *2*, Identity Provisioning will send 3 requests to read the group members.

-   If the number of group members is less than the configured value for `ariba.applications.group.members.page.size` or the property `ariba.applications.group.members.paging.enabled` is disabled, the Identity Provisioning will read all group members via one request.

    For example, if a group has 2 group members and the value of the page size is set to *6*, Identity Provisioning will read all group members via one request.


Setting the property `ariba.applications.group.members.paging.enabled` allows you to read groups with a large number of group members. For more information, see `ariba.applications.group.members.paging.enabled`.

Default value: *50*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.group.members.paging.enabled`

</td>
<td valign="top">

This property enables paging of group members.

When it is set to *true*, all groups with members count exceeding the value defined in `ariba.applications.group.members.page.size` will be read by the Identity Provisioning via subsequent requests.

**Possible values:**

-   *true* - Paging is enabled.
-   *false* - Paging is disabled.

Default value: *true*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.user.groups.page.size`

</td>
<td valign="top">

The number of user groups that SAP Ariba Application returns per request when reading a user.

When the Identity Provisioning reads a user, it compares the number groups assigned with the value configured for `ariba.applications.user.groups.page.size`. Depending on the number of groups assigned to the user, you can expect the following results:

-   If the number of assigned groups is equal or exceeds the configured value, and the `ariba.applications.user.groups.paging.enabled` property is set to *true*, Identity Provisioning will read all user groups in separate requests.

    For example, if a user has 6 groups assigned and the value of the page size is set to *2*, Identity Provisioning will send 3 requests to read the user groups.

-   If the number of assigned groups is less than the configured value for `ariba.applications.user.groups.page.size` or the property `ariba.applications.user.groups.paging.enabled` is disabled, the Identity Provisioning will read all user groups via one request.

    For example, if a user has 2 groups assigned and the value of the page size is set to *6*, Identity Provisioning will read all user groups via one request.


Setting the property `ariba.applications.user.groups.paging.enabled` allows you to read users with a large number of groups assigned. For more information, see `ariba.applications.user.groups.paging.enabled`.

Default value: *50*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.user.groups.paging.enabled`

</td>
<td valign="top">

This property enables paging of user’s groups.

This maximum value is specified by the property `ariba.applications.group.members.page.size`.

To read a user with *'groups'* attribute over the configured value, set `ariba.applications.user.groups.paging.enabled` to *true*.

**Possible values:**

-   *true* - Paging is enabled.

-   *false* - Paging is disabled.


Default value: *true*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.buying.user.filter`

</td>
<td valign="top">

When specified, only those SAP Ariba Buying users matching the filter expression will be read. You can set a single attribute or multiple ones as search criteria.

Supported filtering by the following attributes:

-   *id*

-   *userName*

-   *emails.value*

-   *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*

-   *active*


**Possible values:**

For example:

-   Single attribute: *userName eq "Julie Armstrong"*
-   Multiple attributes \(with `AND`\): *userName eq "Julie Armstrong" and emails.value eq julie.armstrong@example.com*
-   Multiple attributes \(with `OR`\): *userName eq "Julie Armstrong" or active eq false*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Buying

</td>
</tr>
<tr>
<td valign="top">

`ariba.buying.support.patch.operation`

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md)**deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Buying

</td>
</tr>
<tr>
<td valign="top">

`ariba.buying.user.unique.attribute`

</td>
<td valign="top">

When Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find such a user, the creation will fail.

If the service finds an existing user by at least one of the uniqueness criteria, which are *email*, *userName*, or *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the update of the conflicting user fails. If more than one users with these unique attributes are found, the update fails.

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails.value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*. If the service finds an existing user with such *userUuid*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails.value*
-   *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userUuid*
-   a conjunction of the above-mentioned attributes


Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Buying

</td>
</tr>
<tr>
<td valign="top">

`ariba.buying.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP Ariba Buying connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Ariba Buying system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy



</td>
<td valign="top">

SAP Ariba Buying

</td>
</tr>
<tr>
<td valign="top">

`c4c.api.version` 

</td>
<td valign="top">

This property defines the API version that the API of your SAP Sales Cloud and SAP Service Cloud system uses.

**Possible values:**

-   *1*
-   *2*
-   *3*

By default, Identity Provisioning uses version *3*, which means - SCIM 2.0 based API.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`btp.cf.pm.origin` 

</td>
<td valign="top">

The value of this property is the origin key of your SAP Cloud Identity Services tenant.

You can find it in the SAP BTP cockpit. Go to your SAP BTP subaccount, choose *Trust Configuration* and see the value under *Origin Key* for the relevant *Custom Identity Provider for Platform Users*.

The value of this property is a string, which always ends with the suffix *\-platform*.

It will be used as the *origin* attribute in the system transformation.

**Possible values:** Text/numeric string

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP BTP Platform Members \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`btp.cf.pm.landscape` 

</td>
<td valign="top">

Enter the technical key of the landscape in which your multi-environment subaccount with enabled Cloud Foundry environment is located. For more information, see [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-and-api-endpoints-available-for-cloud-foundry-environment?version=Cloud).

For example: `cf-eu10-002`

**Possible values:** Text/numeric string

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP BTP Platform Members \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`btp.cf.pm.group.prefix` 

</td>
<td valign="top">

This property distinguishes SAP BTP Platform Members \(Cloud Foundry\) groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `BTP_CF_PM_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP BTP Platform Members \(Cloud Foundry\) source system and will be provisioned to the target system with the following name pattern: <code>BTP_CF_PM_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP BTP Platform Members \(Cloud Foundry\) groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP BTP Platform Members \(Cloud Foundry\) groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `BTP_CF_PM_` prefix in their display name will be provisioned to SAP BTP Platform Members \(Cloud Foundry\). Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP BTP Platform Members \(Cloud Foundry\).


**System Role:** Source and Target

</td>
<td valign="top">

SAP BTP Platform Members \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`btp.cf.pm.user.filter` 

</td>
<td valign="top">

When specified, only those SAP BTP Platform Members \(Cloud Foundry\) users matching the filter expression will be read.

**Possible values:**

For example: *userName eq "SmithJ"*

**System Role:**Source, Proxy

</td>
<td valign="top">

SAP BTP Platform Members \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`c4c.custom.namespace.<prefix>` 

</td>
<td valign="top">

> ### Note:  
> Only relevant to API **v.2**.

The Identity Provisioning service uses a single predefined namespace for all attributes. However, you can provision entities by defining your own \(custom\) namespaces for some attributes. For this purpose, you have to:

1.  Specify a namespace using this property.
2.  Set the custom namespace in the JSON transformation.

For more information, see: [SAP Sales Cloud and SAP Service Cloud](sap-sales-cloud-and-sap-service-cloud-1a974bc.md)

**Possible values:**

The value of this property is the namespace URI. For **<prefix\>**, enter the prefix of the custom XML namespace \(for example, *a123*\).

Example for setting up the whole property:

*c4c.custom.namespace.a123=http://sap.com/xi/AP/CustomerExtension/ABC/A123XX*

**System Role:** Target

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`cbc.user.filter` 

</td>
<td valign="top">

When specified, only those SAP Central Business Configuration users matching the filter expression will be read.

> ### Note:  
> For source systems only:
> 
> Using this property makes sense only if you have set the *"ignore": true* statement to *false*.

**Possible values:**

For example: *name.familyName eq "Smith" and addresses.country eq "US"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Central Business Configuration

</td>
</tr>
<tr>
<td valign="top">

`cbc.group.filter` 

</td>
<td valign="top">

When specified, only those SAP Central Business Configuration groups matching the filter expression will be read.

**Possible values:**

For example: *displayName eq "ProjectTeam1" or "Employees2020"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Central Business Configuration

</td>
</tr>
<tr>
<td valign="top">

`cbc.group.prefix` 

</td>
<td valign="top">

This property distinguishes SAP Central Business Configuration groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `CBC_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Central Business Configuration source system and will be provisioned to the target system with the following name pattern: <code>CBC_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Central Business Configuration groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Central Business Configuration groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `CBC_` prefix in their display name will be provisioned to SAP Central Business Configuration. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Central Business Configuration.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Central Business Configuration

</td>
</tr>
<tr>
<td valign="top">

`dc.group.filter` 

</td>
<td valign="top">

This property filters groups by display name or externalId.

When specified, only those groups matching the filter expression will be read.

**Possible values:**

-   *SAP\_Data\_Custodian\_Auditor*

-   *SAP\_Data\_Custodian\_Service\_Admin*

-   *SAP\_Data\_Custodian\_Key\_Admin*

-   *SAP\_Data\_Custodian\_Key\_User*


For example: *displayName eq "SAP\_Data\_Custodian\_Auditor"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Data Custodian

</td>
</tr>
<tr>
<td valign="top">

`dc.group.unique.attribute` 

</td>
<td valign="top">

If the service tries to create a group that already exists in the target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\).

To make the search filter by a specific attribute, specify this attribute as a value for the `dc.group.unique.attribute` property.

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Data Custodian

</td>
</tr>
<tr>
<td valign="top">

`dc.user.filter` 

</td>
<td valign="top">

When specified, only those SAP Data Custodian users matching the filter expression will be read. You can filter users by *userName*, *displayName* or *externalId*.

**Possible values:**

For example: *userName eq "Smith.J"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Data Custodian

</td>
</tr>
<tr>
<td valign="top">

`dc.user.unique.attribute` 

</td>
<td valign="top">

When Identity Provisioning attempts to provision a user for the first time, it may detect that this user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user will be searched and resolved. If the service finds a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find a user on the target system via this filter, the creation will fail.

**Default behavior**: This property is missing during system creation. Its default value is *userName*. This means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such *userName* is not found, the creation of the conflicting user fails.

**Possible values:**

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Data Custodian

</td>
</tr>
<tr>
<td valign="top">

`dc.content.type` 

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Data Custodian

</td>
</tr>
<tr>
<td valign="top">

`dc.include.if.match.wildcard.header` 

</td>
<td valign="top">

Makes the SAP Data Custodian connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Data Custodian system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Data Custodian

</td>
</tr>
<tr>
<td valign="top">

`dc.support.patch.operation` 

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Data Custodian

</td>
</tr>
<tr>
<td valign="top">

`dc.group.prefix` 

</td>
<td valign="top">

This property distinguishes SAP Data Custodian groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `DC_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Data Custodian source system and will be provisioned to the target system with the following name pattern: <code>DC_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Data Custodian groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Data Custodian groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `DC_` prefix in their display name will be provisioned to SAP Data Custodian. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Data Custodian.


**System Role:** Source, Target

</td>
<td valign="top">

SAP Data Custodian

</td>
</tr>
<tr>
<td valign="top">

`ds.user.filter` 

</td>
<td valign="top">

When specified, only those SAP Datasphere users matching the filter expression will be read.

**Possible values:**

For example: *userName eq "SmithJ"*

**System Role:**Source, Proxy

</td>
<td valign="top">

SAP Datasphere

</td>
</tr>
<tr>
<td valign="top">

`ds.user.unique.attribute` 

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Datasphere. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Datasphere

</td>
</tr>
<tr>
<td valign="top">

`ds.include.if.match.wildcard.header` 

</td>
<td valign="top">

This property makes the SAP Datasphere connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. The header could be used by an SAP Datasphere system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Datasphere

</td>
</tr>
<tr>
<td valign="top">

`ds.support.patch.operation` 

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

-   If set to *true*, `PATCH` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, only these changes will be provisioned and applied in the target system.

-   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Datasphere

</td>
</tr>
<tr>
<td valign="top">

`ds.support.bulk.operation` 

</td>
<td valign="top">

This property enables bulk operations for users.

When bulk operations are enabled \(set to *true*\), Identity Provisioning service creates, updates, and deletes multiple users in one request.

When bulk operations are not enabled \(set to *false*\), Identity Provisioning service creates, updates, and deletes one user at a time.

For more information, see: [SCIM Protocol: Bulk Operations](https://datatracker.ietf.org/doc/html/rfc7644#section-3.7)

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target

</td>
<td valign="top">

SAP Datasphere

</td>
</tr>
<tr>
<td valign="top">

`ds.bulk.operations.max.count` 

</td>
<td valign="top">

If you have enabled the SCIM bulk operations, you can use this property to set the number of users to be provisioned per request.

**Possible values:**

Default value: *30* 

> ### Note:  
> The value must not exceed the number of entities defined by the SAP Datasphere system as a SCIM service provider. Otherwise, the provisioning job will fail with HTTP response code 413 \(*Payload Too Large*\).

**System Role:** Target

</td>
<td valign="top">

SAP Datasphere

</td>
</tr>
<tr>
<td valign="top">

`ds.api.csrf.protection` 

</td>
<td valign="top">

Specifies whether to fetch a CSRF token when sending requests to the system. The property is automatically added in the system, with default value: *enabled*.

**Possible values:**

-   *enabled*
-   *disabled*

Default value: *enabled*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Datasphere

</td>
</tr>
<tr>
<td valign="top">

`hcp.application.names` 

</td>
<td valign="top">

Enter a comma-separated list of application names. That could be applications deployed on your account, or applications for which your account has subscribed. The property returns the roles assigned to these applications.

**Possible values:**

Use the following format \(no spaces\):

*<app\_name1\>,<app\_name2\>,<provider\_subaccount\>:<provider\_app\>*

For example:

*myapp1,myapp2,provider1:app123,provider2:cloud789,mynewapp*

> ### Caution:  
> You must not leave this property with an empty value.

**System Role:** Source

</td>
<td valign="top">

SAP BTP Java/HTML5 apps \(Neo\)

</td>
</tr>
<tr>
<td valign="top">

`hcp.read.group.roles` 

</td>
<td valign="top">

If you set this property to *true*, the Identity Provisioning will read the following additional attributes for a SAP Business Technology Platform group:

-   Application roles
-   Group mappings, defined by your identity provider

> ### Restriction:  
> This property is applicable only if SAP Business Technology Platform and the external SCIM-based system belong to one and the same region.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Proxy

</td>
<td valign="top">

SAP BTP Java/HTML5 apps \(Neo\)

</td>
</tr>
<tr>
<td valign="top">

`hcp.group.prefix`

</td>
<td valign="top">

This property distinguishes groups from Java/HTML5 applications running on SAP BTP, Neo environment by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `HCP_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Business Technology Platform source system and will be provisioned to the target system with the following name pattern: <code>HCP_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way groups from Java/HTML5 applications running on SAP BTP, Neo environment in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the groups from Java/HTML5 applications running on SAP BTP, Neo environment will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `HCP_` prefix in their display name will be provisioned to SAP Business Technology Platform. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be provisioned to SAP Business Technology Platform.


**System Role:** Source and Target

</td>
<td valign="top">

SAP BTP Java/HTML5 apps \(Neo\)

</td>
</tr>
<tr>
<td valign="top">

`hcp.patch.response.with.resource` 

</td>
<td valign="top">

Use this property when you execute hybrid scenarios with SAP Business Technology Platform \(Neo\) as a SCIM proxy system, and you update an entity \(mostly relevant to groups, like when you change the members of a group\) via a PATCH request.

If you set this property to *true*, the successful `PATCH` request will return a response code 200 \(*OK*\) back to the consumer client application with a payload body containing the updated attributes of the relevant group.

If you don't specify the property \(or it's set to *false*\), the successful `PATCH` request will return a response code 204 \(*No Content*\) indicating successful group update but with no payload body.

For more information, see: [SCIM 2.0: Modifying with PATCH](https://tools.ietf.org/html/rfc7644#section-3.5.2).

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Proxy

</td>
<td valign="top">

SAP BTP Java/HTML5 apps \(Neo\)

</td>
</tr>
<tr>
<td valign="top">

`ia.group.filter` 

</td>
<td valign="top">

When specified, only those SAP Intelligent Agriculture groups matching the filter expression will be read.

**Possible values:**

-   *intagri\_Data\_Scientist*

-   *intagri\_Farm\_Manager*

-   *intagri\_Operator*

-   *intagri\_Operations\_Planner*

-   *intagri\_Master\_Data\_Manager*

-   *intagri\_Administrator*


For example: *displayName eq "intagri\_Master\_Data\_Manager"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Intelligent Agriculture

</td>
</tr>
<tr>
<td valign="top">

`ia.user.filter` 

</td>
<td valign="top">

When specified, only those SAP Intelligent Agriculture users matching the filter expression will be read.

Supported operators: `eq` \(equal\), `ne` \(not equal\), `sw` \(starts with\), `ew` \(ends with\) and `co` \(contains\)

**Possible values:**

For example: *userName eq "Smith.J"*

*emails eq "julie.armstrong@example.com"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Intelligent Agriculture

</td>
</tr>
<tr>
<td valign="top">

`ia.group.unique.attribute` 

</td>
<td valign="top">

If the service tries to create a group that already exists in the target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\).

This property defines by which unique attribute\(s\) the existing group will be searched and resolved. The default value is *displayName*. Currently, it is the only unique attribute that is supported. When set, you can expect the following behavior:

-   If a group with the given *displayName* is found in the target system, the group that you try to provision will overwrite the existing one.

-   If a group with the given *displayName* is not found in the target system, the group that you try to provision will not be created in the target system.


**Possible values:**

If the property is not specified, the search is done by the default attribute: `displayName`

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Intelligent Agriculture

</td>
</tr>
<tr>
<td valign="top">

`ia.user.unique.attribute` 

</td>
<td valign="top">

When Identity Provisioning attempts to provision a user for the first time, it may detect that this user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user will be searched and resolved. If the service finds a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find a user on the target system via this filter, the creation will fail.

**Default behavior**: This property is missing during system creation. Its default value is *userName*. This means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such *userName* is not found, the creation of the conflicting user fails.

**Possible values:**

-   *userUuid*
-   *emails*
-   *userName*
-   *externalId*

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Intelligent Agriculture

</td>
</tr>
<tr>
<td valign="top">

`ia.support.patch.operation` 

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

-   If set to *true*, `PATCH` operations are used to update users and groups in the target system. This means, for example, that if a group member is removed from a group, only these changes will be provisioned and applied in the target system.

-   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Intelligent Agriculture

</td>
</tr>
<tr>
<td valign="top">

`ia.group.prefix` 

</td>
<td valign="top">

This property distinguishes SAP Intelligent Agriculture groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `IA_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Intelligent Agriculture source system and will be provisioned to the target system with the following name pattern: <code>IA_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Intelligent Agriculture groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Intelligent Agriculture groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `IA_` prefix in their display name will be provisioned to SAP Intelligent Agriculture. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Intelligent Agriculture.


**System Role:** Source, Target

</td>
<td valign="top">

SAP Intelligent Agriculture

</td>
</tr>
<tr>
<td valign="top">

`ia.include.if.match.wildcard.header` 

</td>
<td valign="top">

Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Intelligent Agriculture system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Intelligent Agriculture

</td>
</tr>
<tr>
<td valign="top">

`idds.group.filter` 

</td>
<td valign="top">

This property filters groups by display name. You can set a single display name or multiple ones as filter criteria. If you enter multiple display names \(using `OR` operator\), the filter will search for any of them.

Value pattern \(single\): *displayName eq "<group\_name\>"*

Value pattern \(multiple\): *displayName eq "<group\_name1\>" or displayName eq "<group\_name2\>"*

**Possible values:**

For example:

-   Single: *displayName eq "FellowshipTeam1"* 
-   Multiple: *displayName eq "FellowshipTeam1" or displayName eq "JuniorTest3"*

**System Role:** Source, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.user.filter` 

</td>
<td valign="top">

This property filters users by particular attributes. You can set a single attribute or multiple ones as search criteria.

Value pattern \(single\): *<user\_attribute\> eq "<value\>"*

Value pattern \(multiple\): *<user\_attribute1\> eq "<value1\>" and/or <user\_attribute2\> eq "<value2\>"*

**Possible values:**

For example:

-   Single: *userName eq "Sebastian"* 
-   Multiple \(with `OR`\): *userName eq "Sebastian" or addresses.country eq "France"*
-   Multiple \(with `AND`\): *userName eq "Sebastian" and addresses.country eq "France"*
-   Multiple \(with brackets\): *userName eq "Sebastian" or \(addresses.country eq "France" and emails.value eq "sebastian123@mail.com"\)* 
-   Multiple \(enterprise attributes\): *urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department eq "Dev" and urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization eq "Technology"*

**System Role:** Source, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.group.members.paging.enabled` 

</td>
<td valign="top">

This property enables paging of group members.

The maximum number of group members returned per request is 20 000. To read more than 20 000 group members, paging must be enabled.

**Possible values:**

-   *true* - Paging is enabled.
-   *false* - Paging is disabled.

Default value: *false*

**System Role:** Source, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.user.groups.paging.enabled` 

</td>
<td valign="top">

This property enables paging of user’s groups.

The maximum number of user’s groups returned per request is 1000. To read more than 1000 user’s groups, paging must be enabled.

**Possible values:**

-   *true* - Paging is enabled.
-   *false* - Paging is disabled.

Default value: *false*

**System Role:** Source, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.content.type` 

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.group.unique.attribute` 

</td>
<td valign="top">

If you try to provision a group that already exists in a target system, the group creation will fail. In this case, the existing group only needs to be updated.

This property defines by which unique attribute\(s\) the existing group will be searched and resolved. The default value is *displayName*. Currently, it is the only unique attribute that is supported. When set, you can expect the following behavior:

-   If a group with the given *displayName* is found in the target system, the group that you try to provision will overwrite the existing one.

-   If a group with the given *displayName* is not found in the target system, the group that you try to provision will not be created in the target system.


**Possible values:**

If the property is not specified, the search is done by the default attribute: `displayName`

**System Role:** Target, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.include.if.match.wildcard.header` 

</td>
<td valign="top">

Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by a SCIM system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.support.patch.operation` 

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with "scope": "createEntity", such as:

    ```
    {
       "constant":true,
       "targetPath":"$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
       "scope":"createEntity"
    }
    ```

-   If set to *false*, Identity Provisioning sends a `PUT` request to the user or group resource in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


Users and groups can be updated in the target system in various cases, such as:

-   In the source system, some user or group attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users or groups not to be read anymore.

-   A user or a group is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.user.automatic.conflict.resolution` 

</td>
<td valign="top">

Controls whether automatic conflict resolution is switched on or off in Local Identity Directory \(target system\) when provisioning is triggered from source systems containing different users with the same user identifiers \(IDs\).

For example, when SAP SuccessFactors and SAP SuccessFactors Learning are configured as source systems for provisioning users to Local Identity Directory, it could happen that different SAP SuccessFactors and SAP SuccessFactors Learning users have the same user IDs. In this case, when the first user is created in Local Identity Directory, after triggering a provisioning job, the second \(conflicting\) user will either overwrite the already existing one \(automatic conflict resolution is switched on\) or will fail and won't be created \(automatic conflict resolution is switched off\).

To control this behavior, you can use the `idds.user.automatic.conflict.resolution` property in the target Local Identity Directory system. This property is not added by default.

**Possible values:**

-   *true* - If the property is set to true, or is not set at all, the automatic conflict resolution is switched on. This means that Identity Provisioning takes into account the unique attribute\(s\) defined on the `idds.user.unique.attribute` property and tries to find an already existing user in Local Identity Directory matching these attributes.

    -   If a user is found, the provisioning of a new \(conflicting\) user is resolved as follows: the conflicting user overwrites the existing one.

    -   If a user is not found, the provisioning of a conflicting user fails, and it is not created in Local Identity Directory.


-   *false* - If the property is set to false, the automatic conflict resolution is switched off. This means that Identity Provisioning does not take into account the unique attribute\(s\) defined on the `idds.user.unique.attribute` property and fails the provisioning of a conflicting user. This user is not created in Local Identity Directory and does not overwrite the existing one.

    In the Job Log, an error code ***409, uniqueness*** will be displayed.


Default value: *true*

**System Role:** Target

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.user.unique.attribute` 

</td>
<td valign="top">

When Identity Provisioning attempts to provision a user for the first time, it may detect that this user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user will be searched and resolved. **If the service finds a user on the target system via this filter, then the conflicting user will overwrite the existing one.** If the service does not find a user on the target system via this filter, the creation will fail.

According to your use case and system type, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *phoneNumbers\[0\].value*. If the service finds an existing user with such *phoneNumber*, it updates this user with the data of the conflicting one. If a user with such *phoneNumber* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *This property allows you to update user attributes withuserName, phoneNumbers\[0\].value*. If the service finds an existing user with both these *userName* and *phoneNumber*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

-   Value = *userName, emails\[0\].value, phoneNumbers\[0\].value*. If the service finds an existing user with these *userName*, *email* and *phoneNumber*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


**Possible values:**

-   *userName*

-   *emails\[0\].value*

-   *userName,emails\[0\].value*

-   *phoneNumbers\[0\].value*

-   *userName, phoneNumbers\[0\].value*

-   *userName, emails\[0\].value, phoneNumbers\[0\].value*

-   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes


Default value: *userName* 

**System Role:** Target, Proxy

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.user.update.instead.delete` 

</td>
<td valign="top">

`PATCH` request in Local Identity Directory target system and to preserve the user record instead of deleting it. This behavior is supported only when the scope of the attribute is set to **deleteEntity**.

In addition to configuring this property, you also need to adapt the write transformation. For example, if you want to disable a user account in Local Identity Directory, you need to do the following:

1.  Set `idds.user.update.instead.delete`=*true*

2.  Adapt the write transformation as follows:

    ```
    {
       "user":{
          "mappings":[
             {
                "constant":"urn:ietf:params:scim:api:messages:2.0:PatchOp",
                "targetPath":"$.schemas[0]",
                "scope":"deleteEntity"
             },
             {
                "constant":"replace",
                "targetPath":"$.Operations[0].op",
                "scope":"deleteEntity"
             },
             {
                "constant":"active",
                "targetPath":"$.Operations[0].path",
                "scope":"deleteEntity"
             },
             {
                "constant":false,
                "targetPath":"$.Operations[0].value",
                "scope":"deleteEntity"
             },
    ...
    
    ```


In this case, the `PATCH` operation will replace *true* with *false* as the value of the `active` user attribute. As a result, when the `PATCH` operation is executed, the user record in the target system will no longer be managed by Identity Provisioning as it is considered deleted.

For more information, see: [Transformation Expressions](transformation-expressions-bb8537b.md) → *Scope* → *deleteEntity*

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

When the property is set to *true*, adapt the write transformation with the attribute name and the attribute value you want to update:

```
{
   "user":{
      "mappings":[
         {
            "constant":"urn:ietf:params:scim:api:messages:2.0:PatchOp",
            "targetPath":"$.schemas[0]",
            "scope":"deleteEntity"
         },
         {
            "constant":"replace",
            "targetPath":"$.Operations[0].op",
            "scope":"deleteEntity"
         },
         {
            "constant":"<attribute_name>",
            "targetPath":"$.Operations[0].path",
            "scope":"deleteEntity"
         },
         {
            "constant":<attribute_value>,
            "targetPath":"$.Operations[0].value",
            "scope":"deleteEntity"
         },
...

```

**System Role:** Target

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`ips.date.variable.format` 

</td>
<td valign="top">

This is a default property that the Identity Provisioning UI automatically adds to the configuration of every newly created system. The property allows you to change the default date format to another, more suitable for your scenario.

See also: [Transformation Variables](transformation-variables-8376adb.md).

**Possible values:**

Default value:

*yyyy-MM-dd HH:mm:ss.SSS*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.delete.existedbefore.entities` 

</td>
<td valign="top">

**Use case:** An entity exists on the target system, and then a provisioning job reads the same entity from a source system and updates it on the target. If later on you delete this entity from the source system, the next provisioning job will recognize it as a "previously existed one" and will **not delete** it from the target.

If you want such *recognized* entities to be deleted from the target as well, open the relevant target system and set this property to **true**.

For more information, see [Manage Deleted Entities](Operation-Guide/manage-deleted-entities-3d6bdf1.md).

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.overwrite.existedbefore.assignments` 

</td>
<td valign="top">

This property defines whether or not the Identity Provisioning service to overwrite user/group assignments that have existed in the target system before you start provisioning entities to that system.

**Example:** Let's say there is a group in the target system that contains some assignments \(users and subgroups\). In the source system there is a matching group, which contains different assignments.

-   If you start a provisioning job without setting this property \(by default, it's *true*\), all assignments from the source group will overwrite the ones from the target group.
-   If you set the property to *false*, all existing assignments will be kept in the target system group, and the new ones will just be added.

**Possible values:**

-   *true*
-   *false*

Default value: *true*

**System Role:** Target

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`ips.failed.request.retry.attempts` 

</td>
<td valign="top">

If an entity operation fails due to an occurred exception \(rate limit, bad gateway, missing authorization, or timeout\), you can specify a number of retries for this operation. Use this property to set the number of retries.

> ### Note:  
> Rate limit is the controlled rate of requests sent to a system. Some systems implement rate limit to avoid overloading and performance issues.

**Possible values:**

Default value: *2*

Maximum value: *3*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All systems

> ### Note:  
> For more information about the cases in which the retry is supported, see [Handle Failed Operations](Operation-Guide/handle-failed-operations-0382a0c.md).



</td>
</tr>
<tr>
<td valign="top">

`ips.failed.request.retry.attempts.interval` 

</td>
<td valign="top">

Specify a time interval \(in seconds\) between the retries, in case an operation fails due to an occurred exception.

This property is related to `ips.failed.request.retry.attempts`.

**Possible values:**

Default value: *30*

Maximum value: *60*

> ### Note:  
> Following an HTTP 502 Bad Gateway server error, the time interval for SAP BTP XS Advanced UAA \(Cloud Foundry\) and SAP Sales Cloud and SAP Service Cloud must not exceed 50 \(seconds\).

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All systems

> ### Note:  
> For more information about the cases in which the retry is supported, see [Handle Failed Operations](Operation-Guide/handle-failed-operations-0382a0c.md).



</td>
</tr>
<tr>
<td valign="top">

`ips.job.notification.repeat.on.failure` 

</td>
<td valign="top">

If you have activated notifications for a source system and a provisioning job fails, you'll receive notification e-mails with subject *Provisioning Finished with Error*. You can also receive an e-mail if you manually stop a running job.

With property `ips.job.notification.repeat.on.failure`, you can control the frequency of the received notifications.

-   If you set the property to *true*, you will receive notification e-mails every time a job fails.
-   If you want to stop or control the notification frequency, set the property to *false* \(default value\).

This property has a higher priority than `ips.job.notification.ignored.consecutive.failures`.

See also: [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).

**Possible values:**

-   *true*
-   *false*

Default value: *false*. That means, when a job fails, only one notification e-mail will be sent.

**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.job.notification.ignored.consecutive.failures` 

</td>
<td valign="top">

If you have activated notifications for a source system and a provisioning job fails, you'll receive notification e-mails with subject *Provisioning Finished with Error*. You can also receive an e-mail if you manually stop a running job.

With property `ips.job.notification.ignored.consecutive.failures`, you can control the number of the received consecutive notifications.

> ### Note:  
> Property `ips.job.notification.repeat.on.failure` must be set to *false* or not specified at all.

**Example:** If you set `ips.job.notification.ignored.consecutive.failures` = *3* and the job is constantly failing, the first three times you'll not receive a notification. On the fourth job fail, you will receive one notification e-mail. No subsequent e-mails will be sent by the service until the first successful run of the job.

See also: [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).

**Possible values:**

Default value: *0*.

That means, a notification e-mail will be sent after the first job fail.

**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.job.notification.skip.intermediate.notifications` 

</td>
<td valign="top">

If you have activated notifications for a source system, and an entity fails during the provisioning job, you'll receive one notification e-mail with subject *Provisioning Running with Error*.

Property `ips.job.notification.skip.intermediate.notifications` controls whether you will receive a notification or not.

-   If the property is set to *true*, no notifications will be sent.

-   If the property is not specified or is set to *false* \(default\), you'll receive one notification e-mail. No subsequent e-mails will be sent by the service until the first successful run of the job.


See also: [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).

**Possible values:**

-   *true*
-   *false*

Default value: *false*. That means, after the first failed entity, a notification e-mail will be sent.

**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.trace.failed.entity.content` 

</td>
<td valign="top">

If a provisioning job repeatedly fails and you need problem investigation, you can enable logging and tracing for the personal and sensitive data of your provisioned entities. To do this, set this property to *true*.

If the property is not set, in the logs you see: `content = <hidden content>`

To learn more about personal and sensitive data, see:

-   [Glossary for Data Protection and Privacy](https://help.sap.com/docs/identity-provisioning/identity-provisioning/glossary-for-data-protection-and-privacy)
-   [Customer Data](https://help.sap.com/docs/identity-provisioning/identity-provisioning/customer-data) → **Data Storage Security**

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.trace.skipped.entity.content` 

</td>
<td valign="top">

If a provisioning job results in skipping entities from source or target systems, you can view the details for each skipped user and group.

To do this, you need to enable logging and tracing for the personal and sensitive data of your provisioned entities by setting the property to *true*.

If the property is not set, in the logs you see: `content = <hidden content>`

To learn more about personal and sensitive data, see:

-   [Glossary for Data Protection and Privacy](https://help.sap.com/docs/identity-provisioning/identity-provisioning/glossary-for-data-protection-and-privacy)
-   [Customer Data](https://help.sap.com/docs/identity-provisioning/identity-provisioning/customer-data) → **Data Storage Security**

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.trace.created.entity.content` 

</td>
<td valign="top">

If a provisioning job results in created entities in target or proxy systems, you can view the details for each created user and group.

To do this, you need to enable logging and tracing for the personal and sensitive data of your provisioned entities by setting the property to *true*.

If the property is not set, in the logs you see: `content = <hidden content>`

To learn more about personal and sensitive data, see:

-   [Glossary for Data Protection and Privacy](https://help.sap.com/docs/identity-provisioning/identity-provisioning/glossary-for-data-protection-and-privacy)
-   [Customer Data](https://help.sap.com/docs/identity-provisioning/identity-provisioning/customer-data) → **Data Storage Security**

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.trace.skipped.entity` 

</td>
<td valign="top">

This property allows you to download and view the details of all skipped entities for a given job in a `zip` archive. For more information, see [Manage Provisioning Job Logs](Monitoring-and-Reporting/manage-provisioning-job-logs-041b5ff.md)

**Possible values:**

-   *true* - The downloaded `zip` file contains all skipped entities for the given job, the systems they are skipped from, the reason behind this, as well as the content of the entities \(if `ips.trace.skipped.entity.content` is set to `true`\).

-   *false* - The downloaded `zip` file is empty.


Default value: *false*

**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.trace.created.entity` 

</td>
<td valign="top">

This property allows you to download and view the details of all created entities for a given job in a `zip` archive. For more information, see [Manage Provisioning Job Logs](Monitoring-and-Reporting/manage-provisioning-job-logs-041b5ff.md)

**Possible values:**

-   *true* - The downloaded `zip` file contains all created entities for the given job, the systems in which they are created, as well as the content of the entities \(if `ips.trace.created.entity.content` is set to `true`\).

-   *false* - The downloaded `zip` file is empty.


Default value: *false*

**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.http.header.<header_name>` 

</td>
<td valign="top">

Use this property to pass additional information with the HTTP requests.

The provisioning system may override your custom HTTP headers, if specific header settings are implemented in the system.

**Possible values:**

Example for an authorization header:

`ips.http.header.authorization` = *Basic VDAwdfhjgHGSzmfnNA==*

> ### Note:  
> If you provide credentials for the provisioning system, this property will not take effect. Its value \(token\) will be overridden by the token generated by the system implementation.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All HTTP systems

</td>
</tr>
<tr>
<td valign="top">

`ips.delta.read` 

</td>
<td valign="top">

If this property is enabled, every time a provisioning job is started, it does not retrieve the entire amount of source system data but only the last changed entities.

For more information, see [Manage Full and Delta Read](Operation-Guide/manage-full-and-delta-read-b7f817c.md).

**Possible values:**

-   *enabled*
-   *disabled*

**System Role:** Source

</td>
<td valign="top">

-   Identity Authentication

-   Intelligent Opportunity Analyzer

-   Local Identity Directory

-   Microsoft Active Directory

-   SAP Advanced Financial Closing

-   SAP Advanced Workflow

-   SAP Central Business Configuration

-   SAP CPQ

-   SAP Data Custodian

-   SAP Intelligent Agriculture

-   SAP SuccessFactors

-   SAP SuccessFactors Learning

-   SCIM System




</td>
</tr>
<tr>
<td valign="top">

`ips.full.read.force.count` 

</td>
<td valign="top">

If your system \(connector\) works in *delta read* mode, it's recommended to enforce full reads from time to time. To achieve this, set this property to an integer number.

**Possible values:**

For example: *10*

This value results in alternating full reads after every 10 delta reads are performed.

In case the property is not set, only delta read jobs will be executed. For more information, see [Manage Full and Delta Read](Operation-Guide/manage-full-and-delta-read-b7f817c.md).

**System Role:** Source

</td>
<td valign="top">

-   Identity Authentication

-   Local Identity Directory

-   SAP Advanced Financial Closing

-   SAP Advanced Workflow

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP BTP ABAP environment

-   SAP BTP Account Members \(Neo\)

-   SAP BTP Java/HTML5 apps \(Neo\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Build Work Zone, advanced edition

-   SAP Business Network

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP SuccessFactors Incentive Management

-   SAP Concur

-   SAP CPQ

-   SAP Data Custodian

-   SAP Enetrprise Portal

-   SAP Fieldglass

-   SAP Field Service Management

-   SAP Integrated Business Planning for Supply Chain

-   SAP Jam Collaboration

-   SAP Market Communication for Utilities

-   SAP Marketing Cloud

-   SAP Master Data Integration

-   SAP S/4HANA Cloud

-   SAP S/4HANA for procurement planning

-   SAP S/4HANA On-Premise

-   SAP Sales Cloud and SAP Service Cloud

-   SAP SuccessFactors

-   SAP SuccessFactors Learning

-   Sales Cloud – Analytics & AI

-   Cloud Foundry UAA server

-   Google G Suite

-   LDAP Server

-   Microsoft Active Directory

-   Microsoft Entra ID

-   SCIM System




</td>
</tr>
<tr>
<td valign="top">

`ips.application.id` 

</td>
<td valign="top">

This property holds the value of the *Application ID* of the application, created in the SAP Cloud Identity Services tenant. Its main purpose is to show that a group is associated with a particular application. This is an optional property set by the customer.

The *application ID* is the identifier of an application configured in SAP Cloud Identity Services - Identity Authentication that corresponds to a particular source system configured in the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services. It is used to distinguish groups provisioned from various source systems to the Identity Directory of SAP Cloud Identity Services.

When the property is set, the groups are provisioned with their *applicationId* attribute which is internally mapped to the name of the corresponding application. As a result, the name of the associated application with the group is displayed in the *Application Name* field under *Users&Authorizations* \> *Groups*.

**System Role:** Source, Target

</td>
<td valign="top">

-   SAP Advanced Financial Closing

-   SAP BTP Platform Members \(Cloud Foundry\)

-   SAP Analytics Cloud

-   SAP Ariba Applications




</td>
</tr>
<tr>
<td valign="top">

`OAuth2TokenServiceURL` 

</td>
<td valign="top">

If you need to make OAuth authentication to the system, enter the URL to the access token provider service.

**Possible values:** Access token URL

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   Cloud Foundry UAA Server

-   Google G Suite

-   Intelligent Opportunity Analyzer

-   Microsoft Entra ID

-   Sales Cloud – Analytics & AI

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP Ariba Category Management

-   SAP Ariba Central Invoice Management

-   SAP BTP Account Members \(Neo\)

-   SAP BTP Java/HTML5 apps \(Neo\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Build Work Zone, advanced edition

-   SAP Build Work Zone, standard edition

-   SAP Business Network

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP CPQ

-   SAP Data Custodian

-   SAP Datasphere

-   SAP Fieldglass

-   SAP Field Service Management

-   SAP HANA Cloud, SAP HANA Database

-   SAP Intelligent Agriculture

-   SAP Jam Collaboration

-   SAP Master Data Integration

-   SAP Advanced Financial Closing

-   Procurement Data Warehouse

-   SAP S/4HANA for procurement planning

-   SCIM System




</td>
</tr>
<tr>
<td valign="top">

`OAuth2TokenScope` 

</td>
<td valign="top">

If your backend system is OAuth protected and requires an access token with scope, use this property to specify the scope. It defines the token's level of access to protected resources.

This is an optional property. Providing a value only makes sense if the backend system and its trusted OAuth server requires it. For more information, see [OAuth Scopes](https://oauth.net/2/scope/).

Example value of Google G Suite OAuth scope: `https://www.googleapis.com/auth/admin.directory.user`

Although Google G Suite OAuth scopes look like URLs, they are not web pages. They are access token permissions.

**Possible values:** Scopes are system specific.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   Cloud Foundry UAA Server

-   Google G Suite

-   Microsoft Entra ID

-   Sales Cloud – Analytics & AI

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP BTP Account Members \(Neo\)

-   SAP BTP Java/HTML5 apps \(Neo\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Build Work Zone, advanced edition

-   SAP Build Work Zone, standard edition

-   SAP Business Network

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP Data Custodian

-   SAP Fieldglass

-   SAP Jam Collaboration

-   SAP Master Data Integration

-   SAP Advanced Financial Closing

-   SAP S/4HANA for procurement planning

-   SCIM System




</td>
</tr>
<tr>
<td valign="top">

`jco.client.user` 

</td>
<td valign="top">

Enter the user for AS ABAP.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.client.passwd` 

</td>
<td valign="top">

\(Credential\)

Enter the password for the AS ABAP user.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.client.ashost` 

</td>
<td valign="top">

Enter the virtual host entry that you have configured in the Cloud connector → *Access Control* configuration.

**Possible values:**

For example: *abapserver.hana.cloud*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.client.client` 

</td>
<td valign="top">

Enter the client to be used in the ABAP system. Valid format is a three-digit number.

**Possible values:**

For example: *001*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.client.r3name` 

</td>
<td valign="top">

Enter the three-character system ID of the ABAP system to be addressed.

**Possible values:**

For example: *WPE*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.client.sysnr` 

</td>
<td valign="top">

Enter the "system number" of the ABAP system.

**Possible values:**

For example: *42*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.destination.proxy_type` 

</td>
<td valign="top">

Defines the proxy type of the connection you need to provide for your ABAP system.

The proxy type *OnPremise* requires the Cloud Connector to access resources within your on-premise network.

**Possible values:*OnPremise***

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.destination.peak_limit` 

</td>
<td valign="top">

Represents the maximum number of active connections that can simultaneously be created for a destination.

**Possible values:**

For example: *10*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.destination.pool_capacity` 

</td>
<td valign="top">

Represents the maximum number of idle connections kept open by the destination.

**Possible values:**

For example: *5*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`jco.client.mshost` 

</td>
<td valign="top">

Represents the message server host to be used.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`X-ConsumerKey` 

</td>
<td valign="top">

\(Credential\)

Enter the Concur access token needed for the connection.

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Concur

</td>
</tr>
<tr>
<td valign="top">

`jwt.subject` 

</td>
<td valign="top">

Enter the Google G Suite user on behalf of which the Google Directory API is called.

**System Role:** Target, Proxy

</td>
<td valign="top">

Google G Suite

</td>
</tr>
<tr>
<td valign="top">

`jwt.scope` 

</td>
<td valign="top">

Enter space-separated Google Directory API authorization scopes.

**System Role:** Target, Proxy

</td>
<td valign="top">

Google G Suite

</td>
</tr>
<tr>
<td valign="top">

`ldap.url` 

</td>
<td valign="top">

URL needed to make an LDAP connection to an on-premise system or a cloud service

**Possible values:** `ldap://<host><port>`

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.proxyType` 

</td>
<td valign="top">

Proxy type for the LDAP connection

**Possible values:** *OnPremise*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.authentication` 

</td>
<td valign="top">

Authentication type for the LDAP connection

**Possible values:** *BasicAuthentication*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.user` 

</td>
<td valign="top">

User name for the LDAP Server

**Possible values:** Text/numeric string

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.password` 

</td>
<td valign="top">

\(Credential\) Password for the LDAP Server user

**Possible values:** Encrypted string

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.group.path` 

</td>
<td valign="top">

Enter the complete path to the node containing the groups in the LDAP tree.

> ### Remember:  
> We strongly recommend that you enter different paths for LDAP users and groups. That means, the value of `ldap.group.path` should be different than the value of `ldap.user.path`.

**Possible values:**

For example:

`ldap.group.path`=*OU=Groups,OU=IAS,DC=global,DC=corp,DC=mycompany*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.user.path` 

</td>
<td valign="top">

Enter the complete path to the users in the LDAP Server or Microsoft AD.

> ### Remember:  
> We strongly recommend that you enter different paths for LDAP users and groups. That means, the value of `ldap.users.path` should be different than the value of `ldap.group.path`.

**Possible values:**

For example:

`ldap.user.path`=*OU=Users,OU=IAS,DC=global,DC=corp,DC=mycompany*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.user.attributes` 

</td>
<td valign="top">

Shows which user attributes to be read from the LDAP server the source system, LDAP server or Microsoft AD\(and respectively, from the intermediate JSON data\). Separate the attributes by comma \(,\).

**Possible values:**

-   LDAP server version 1 or Microsoft AD version 1 - Even though you specify which user attributes you want to read from the LDAP server or Microsoft AD, all user attributes are read.

-   LDAP server version 2or Microsoft AD version 2 - Only the specified attributes will be read from the LDAP server.or Microsoft AD. *sAMAccountName* is always included as mandatory user attribute for Microsoft AD version 2.


If nothing is set, all attributes are read.

**System Role:** Source, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.group.attributes` 

</td>
<td valign="top">

Shows which group attributes to be read from the LDAP server the source system, LDAP server or Microsoft AD\(and respectively, from the intermediate JSON data\). Separate the attributes by comma \(,\).

**Possible values:**

-   LDAP server version 1 or Microsoft AD version 1- Even though you specify which group attributes you want to read from the LDAP serveror Microsoft AD, all user and group attributes are read.

-   LDAP server version 2or Microsoft AD version 2 - Only the specified attributes will be read from the LDAP serveror Microsoft AD.


If nothing is set, all attributes are read.

**System Role:** Source, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.user.object.class` 

</td>
<td valign="top">

Criteria for user. In the intermediate JSON data, the following LDAP filter is used: `(objectClass=user)`

For target LDAP systems: this property defines the set of supported and required attributes for an LDAP user entity.

**Possible values:**

Default value: *inetOrgPerson*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.group.object.class` 

</td>
<td valign="top">

Criteria for group. In the intermediate JSON data the following LDAP filter is used: `(objectClass=group)`

For target LDAP systems: this property defines the set of supported and required attributes for an LDAP group entity.

**Possible values:**

Default value: *groupOfNames*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.group.uniquename.attribute` 

</td>
<td valign="top">

By default, the *memberOf* array in the source JSON data contains the CN part of the complete distinguished name of the groups to which the entity belongs.

An administrator can use this property to change the default behavior and specify an attribute name to be used instead of CN.

> ### Note:  
> -   Any group that doesn't have the attribute specified, will not be part of the resulting *memberOf* JSON array.
> -   Any group that doesn't match the`ldap.group.path` property, will not be part of the resulting *memberOf* JSON array.

**Possible values:**

-   *cn* \(default for LDAP\)
-   *displayName* – this will produce a *memberOf* array which contains the *displayName* attribute value of the groups to which the entity belongs.

> ### Note:  
> Whatever value you choose for this property, it should correspond to the one in the JSON transformation of your LDAP system \(the *group* mapping\).

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.group.id` 

</td>
<td valign="top">

This property denotes the ID of a group.

-   When a user is a member of a group, this group is returned in the *memberOf* array for this user. This property evaluates the attribute used as ID of this group.
-   When a group is a member of another group, this property evaluates the attribute used as ID of the "parent group". In this case, the `ldap.attribute.group.id` property has a higher priority than `ldap.group.uniquename.attribute`.

**Possible values:**

-   *cn* \(default\)
-   *distinguishedName* – this will produce a *memberOf* array which contains the `distinguishedName` attribute value of the groups to which the entity belongs.

> ### Note:  
> Whatever value you choose for this property, it should correspond to the one in the JSON transformation of your LDAP system \(the *group* mapping\).

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.dn` 

</td>
<td valign="top">

This property denotes the distinguished name of a user or a group.

The distinguished name is auttomatically assigned and cannot be configured.

The behavior described below is valid only when Microsoft Active Directory is used as target system:

When the Identity Provisioning attempts to provision a user or a group to Microsoft Active Directory for the first time, it may detect that such a user or group already exists on the target system. Thus, the service needs to retrieve the entityId of the existing user or group by using this property for conflict resolution.

If the service finds such a user on the target system via this filter, the creation will fail. In this case, the conflicting user will overwrite the existing one.

If the service finds such a group on the target system via this filter, the creation will fail. In this case, the existing group only needs to be updated.

If the service does not find a user or a group via this filter, the creation will fail.

**Possible values:**

Default and only possible value: *distinguishedName*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.member.uniquename.attribute` 

</td>
<td valign="top">

Determines the value of the `member` attribute of groups in the intermediate JSON data.

This property can return either the common name \(CN\) of the user or the entire distinguished name \(DN\).

**Possible values:**

-   *cn* \(default for Microsoft AD\)
-   *uid* \(default for LDAP Server\)
-   *distinguishedName*

> ### Note:  
> Whatever value you choose for this property, it should correspond to the one in the JSON transformation of your system \(the *user* mapping\).

**System Role:** Source

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.id` 

</td>
<td valign="top">

This property denotes the ID of a user.

When a user is a member of a group, this property evaluates the attribute used as ID of this member. In this case, the `ldap.attribute.user.id` or `ldap.attribute.group.id` property has a higher priority than `ldap.member.uniquename.attribute`.

**Possible values:**

Possible values for LDAP Server:

-   *cn* \(default for Microsoft AD\)
-   *uid* \(default for LDAP Server\)
-   *distinguishedName*

> ### Note:  
> Whatever value you choose for this property, it should correspond to the one in the JSON transformation of your system \(the *user* mapping\).

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.group.member` 

</td>
<td valign="top">

Default value: *member*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.mail` 

</td>
<td valign="top">

Default value: *mail*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.mobile` 

</td>
<td valign="top">

Default value: *mobile*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.givenName` 

</td>
<td valign="top">

Default value: *givenName*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.surname` 

</td>
<td valign="top">

Default value: *sn*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.groups` 

</td>
<td valign="top">

Default value: *memberOf*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.telephoneNumber` 

</td>
<td valign="top">

Default value: *telephoneNumber*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.group.object.class.required` 

</td>
<td valign="top">

The LDAP object classes have attributes required for creation of entities.

-   For Open LDAP Server, the required attribute is the common name \(CN\) of the group.
-   For other implementations, it could be another attribute.

Default value: *cn*

**System Role:** Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.object.class.required` 

</td>
<td valign="top">

The LDAP object classes have attributes required for creation of entities.

-   For Open LDAP Server, the required attribute is the common name \(CN\) of the user.
-   For other implementations, it could be another attribute.

Default value: *cn*

**System Role:** Target, Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.respond.with.resource.after.create` 

</td>
<td valign="top">

When set to *true*, the SCIM `create` operation will read the created entity from the LDAP server.

Value *true* is required because the SCIM `create` operation must return the created entity.

Default value: *true*

**System Role:** Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.respond.with.resource.after.update` 

</td>
<td valign="top">

When set to *true*, the SCIM `update` operation will read the modified entity from the LDAP server.

When set to *false* or the property is missing, the `update` operation will respond with error *204* \(no content\).

Default value: *true*

**System Role:** Proxy

</td>
<td valign="top">

LDAP Server

</td>
</tr>
<tr>
<td valign="top">

`ldap.user.filter` 

</td>
<td valign="top">

You can optimize the search to return only particular users.

To enter correct user filters, stick to the standard LDAP specification. See: [LDAP Representation of Filters – Examples](https://tools.ietf.org/html/rfc4515#section-4).

**Possible values:**

For example:

Value *\(cn=123\*\)* will return only users whose UID starts with "123" \(such as *1234567689* or *1230011*\).

By default, this filter is empty. That is, if the property is not specified, the filter will search for every user.

**System Role:** Source

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.group.filter` 

</td>
<td valign="top">

You can optimize the search to return only particular groups.

To enter correct group filters, stick to the standard LDAP specification. See: [LDAP Representation of Filters – Examples](https://tools.ietf.org/html/rfc4515#section-4).

**Possible values:**

For example:

Value *\(cn=mar\*\)* will return only groups whose CN starts with "mar" \(such as *marked*, *March*, or *Marketing*\).

By default, this filter is empty. That is, if the property is not specified, the filter will search for every group.

**System Role:** Source

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`ldap.page.size` 

</td>
<td valign="top">

Use this property to configure the paging \(pagination\). That means, the number of entities to be read from the LDAP server at once.

**Possible values:**

Default value: *100* 

> ### Note:  
> It is not recommended to exceed 1000.

**System Role:** Source

</td>
<td valign="top">

-   LDAP Server

-   Microsoft Active Directory




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

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

LDAP Server

-   -   Microsoft Active Directory




</td>
</tr>
<tr>
<td valign="top">

`concur.page.size` 

</td>
<td valign="top">

Use this property to configure the paging. That means, the number of entities to be read from Concur at once.

**Possible values:**

Default value: *100* 

> ### Note:  
> The maximum allowed number is 100.

**System Role:** Source

</td>
<td valign="top">

SAP Concur

</td>
</tr>
<tr>
<td valign="top">

`msgraph-filter`

\(*Deprecated*\)

</td>
<td valign="top">

Use this property to filter users and groups by specific criteria, according to the API syntax of Microsoft Entra ID.

> ### Note:  
> This property is deprecated. Use `aаd.user.filter` and `aаd.group.filter` instead.

**Possible values:**

Default value: *null* 

To set a particular value, see [Microsoft Graph: filter parameter](https://developer.microsoft.com/en-us/graph/docs/concepts/query_parameters#filter-parameter).

**System Role:** Source

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`gsuite.page.size` 

</td>
<td valign="top">

Use this property to configure the paging. That means, the number of entities to be read from Google G Suite at once.

**Possible values:**

Default value: *100* 

> ### Note:  
> The maximum allowed number is 500.

**System Role:** Source

</td>
<td valign="top">

Google G Suite

</td>
</tr>
<tr>
<td valign="top">

`gsuite.get.deleted` 

</td>
<td valign="top">

This property determines whether recently deleted entities should be read.

> ### Note:  
> You can apply this property only for **users**. For groups it will be ignored.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Source

</td>
<td valign="top">

Google G Suite

</td>
</tr>
<tr>
<td valign="top">

`gsuite.domain` 

</td>
<td valign="top">

This property determines whether entities from a particular domain should be read.

**Possible values:**

For example: *myaccount.ondemand.com*

**System Role:** Source

</td>
<td valign="top">

Google G Suite

</td>
</tr>
<tr>
<td valign="top">

`gsuite.customer.id` 

</td>
<td valign="top">

This property determines whether entities for a particular customer ID to be read. This property takes precedence over `gsuite.domain`.

**Possible values:** Customer ID number

For more information, see [Google G Suite API: User Accounts](https://developers.google.com/admin-sdk/directory/v1/guides/manage-users).

**System Role:** Source

</td>
<td valign="top">

Google G Suite

</td>
</tr>
<tr>
<td valign="top">

`com.sun.jndi.ldap.read.timeout` 

</td>
<td valign="top">

Use this property if you want to specify the read timeout \(in milliseconds\) for an LDAP connection.

**Possible values:**

For example: *5000*

This value causes the LDAP service provider to abort the read attempt if the server does not respond within 5 seconds.

**System Role:** Source

</td>
<td valign="top">

-   LDAP Server
-   Microsoft Active Directory



</td>
</tr>
<tr>
<td valign="top">

`com.sun.jndi.ldap.connect.timeout` 

</td>
<td valign="top">

Use this property if you want to set the timeout \(in milliseconds\) for connecting to the LDAP server.

**Possible values:**

For example: *500*

This value causes the LDAP service provider to abort the connection attempt if a connection cannot be established in half a second.

**System Role:** Source

</td>
<td valign="top">

-   LDAP Server
-   Microsoft Active Directory



</td>
</tr>
<tr>
<td valign="top">

`oauth.resource.name` 

</td>
<td valign="top">

Enter the URL to the Microsoft Graph.

**Possible values:** *https://graph.microsoft.com*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`ad.group.flatten` 

</td>
<td valign="top">

There are target systems that do not support nested groups \(group structures\). Therefore, if your Microsoft AD system contains such groups, they will not be resolved properly during the provisioning job. Such target systems are:

-   *SAP Jam Collaboration*
-   *Identity Authentication*

To enable reading of group structures, you can use the `ad.group.flatten` property and set it to *true*. It will read the group structure recursively and will "flatten" it so that all users from all groups and subgroups will be resolved and written in the target system as members of the main parent group.

For best results, we recommend you also set the system property `ldap.group.filter` whose value is one or multiple Microsoft AD parent groups.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

Examples for filtering:

-   If your Microsoft AD system contains a parent group "*Canteen*", which contains nested subgroups, you have to set the filter like this: `ldap.group.filter` = *\(cn=Canteen\)*

    The Identity Provisioning will resolve all the direct users and groups of "*Canteen*", along with all the users of its subgroups \(and their subgroups\). In the target system, all users will be written in one parent group named also "*Canteen*".

-   If you have multiple parent groups \(for example, *Canteen*, *Finances*, and *Support\_Team*\) that contain nested subgroups, you have to set the filter like this:

    `ldap.group.filter` = *\(|\(cn=Canteen\)\(cn=Finance\)\(cn=Support\_Team\)\)* 


**System Role:** Source

</td>
<td valign="top">

Microsoft Active Directory

</td>
</tr>
<tr>
<td valign="top">

`aad.domain.name` 

</td>
<td valign="top">

Enter one of the verified domain names from the corresponding Microsoft Entra ID tenant.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`aad.group.member.attributes` 

</td>
<td valign="top">

This property defines the attributes of a group member to be read by the Identity Provisioning. By default, it always reads the *type* and the *id* of a member.

If you prefer the Identity Provisioning to read additional attributes, you can add them as a single or a comma-separated value. For example:

> ### Example:  
> -   If you want to read the e-mails too, enter: `aad.group.member.attributes`=*mail*
> 
>     This will read a member's type, ID and e-mail.
> 
> -   If you want to read multiple additional attributes, enter: `aad.group.member.attributes`=*mail,mobilePhone,displayName* 
> 
>     This will read a member's type, ID, e-mail, phone and display name.

See: [Microsoft Entra ID](microsoft-entra-id-f75f99c.md)

**Possible values:**

-   *type* \(default\)
-   *id* \(default\)
-   Any valid Microsoft Entra ID attribute of a group member
-   A comma-separated list of valid Microsoft Entra ID attributes of a group member

> ### Remember:  
> The Identity Provisioning service always retrieves the *id* and *type* attributes of a group member, regardless of the additional attributes you specify.

**System Role:** Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`aad.user.attributes.membership.active` 

</td>
<td valign="top">

Use this property if you want to get information about all the groups to which the users are assigned \(if any\).

-   If the property is missing, or is set to *false* – group membership details for the users will not be extracted.
-   If the property is set to *true* – group membership details for the users will be extracted.

If you set the property to *true*, you will get information about the group ID and its entity type \(group\) – default result. However, if you also set a value for property `aad.group.attributes`, you will get additional information relevant to this value.

For example:

If you set `aad.user.attributes.membership.active` = *true* and `aad.group.attributes` = *displayName*, you will receive the following exemplary data for a group as part of the user object:

```js

  "groups": [
    {
      "displayName": "Microsoft Entra ID Group 1",
      "id": "aaa111999-0000-444-123-777fff000",
      "type": "group"
    }
   ]

```

**Possible values:**

-   *true*
-   *false* \(default\)

**System Role:** Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`aad.user.filter` 

</td>
<td valign="top">

Via this property, you can filter users by specific criteria, according to the syntax of [Microsoft Graph REST API](https://docs.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#properties).

You can also filter out users with advanced query parameters, as described in [Advanced query capabilities on Microsoft Entra ID objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries?tabs=http)

> ### Note:  
> This property replaces the deprecated `msgraph-filter` property.

**Possible values:** Text/numeric string

For example:

-   Value = *Department eq 'Finance'*

-   Value = *displayName eq 'John Smith' and city eq 'Sofia'*

-   Value = *userPrincipalName ne 'Julie Armstrong'*


**System Role:** Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`aad.group.filter` 

</td>
<td valign="top">

Via this property, you can filter groups by specific criteria, according to the syntax of [Microsoft Graph REST API](https://docs.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties).

You can also filter out groups with advanced query parameters, as described in [Advanced query capabilities on Microsoft Entra ID objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries?tabs=http)

**Possible values:** Text/numeric string

For example:

-   Value = *displayName eq 'Employees 2020'*

-   Value = *displayName eq 'Service Administrators' and mail eq 'serviceadmins@abcd.onmicrosoft.com'*

-   Value = *startsWith\(displayName, 'ABC\_'\)*

-   Value = *displayName ne 'Service Administrators'*


**System Role:** Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`aad.user.attributes` 

</td>
<td valign="top">

Defines which user attributes are read from Microsoft Entra ID system.

The property is set during system creation with the following default value: *id,mail,userPrincipalName,displayName,mailNickname,givenName,surname,mobilePhone,businessPhones*

This means that by default, Identity Provisioning will read from Microsoft Entra ID the user attributes defined in the property value. Those attributes are also used in the default read transformation.

To check the complete set of user attributes \(properties\) supported by Microsoft Entra ID, see: [Microsoft Graph: User Properties](https://docs.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#properties)

If you want the Identity Provisioning to read additional user attributes, add them to the default list of attributes separated by comma and adapt the transformations.

For example, to read the *employeeId* of the Microsoft Entra ID users in addition to the default list of attributes, and provision them to Identity Authentication, proceed as follows:

1.  Add the attribute in the property value: id,mail,userPrincipalName,displayName,mailNickname,givenName,surname,mobilePhone,businessPhones*,employeeId*

2.  Extend the Microsoft Entra ID read transformation by adding the following mapping for the user resource:

    > ### Sample Code:  
    > ```json
    > {
    >  "sourcePath": "$.employeeId",
    >  "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >  "optional": true
    > },
    > ```

3.  Make sure the following mapping is present in the Identity Authentication write transformation:

    > ### Sample Code:  
    > ```json
    > {
    >  "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >  "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >  "optional": true
    > },
    > ```


In case you remove the default list of attributes from the value of this property and only add the additional attributes, Identity Provisioning will return the additional user attributes plus the mandatory ones: *id,mail, userPrincipalName*.

**System Role:** Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`aad.group.attributes` 

</td>
<td valign="top">

Defines which group attributes are read from Microsoft Entra ID system.

The property is set during system creation with the following default value: *id,displayName,mailNickname*

This means that by default, Identity Provisioning will read from Microsoft Entra ID the group attributes defined in the property value and will also return the *members* attribute. Those attributes are used in the default read transformation.

To check the complete set of group attributes \(properties\) supported by Microsoft Entra ID, see: [Microsoft Graph: Group Properties](https://docs.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#properties)

If you want the Identity Provisioning to read additional group attributes, add them to the default list of attributes separated by comma and adapt the transformations.

For example, to read the *description* of the Microsoft Entra ID groups in addition to the default list of attributes, and provision them to Identity Authentication, proceed as follows:

1.  Add the attribute in the property value: id,displayName,mailNickname*,description*

2.  Extend the Microsoft Entra ID read transformation by adding the following mapping for the group resource:

    > ### Code Syntax:  
    > ```
    > {
    >  "sourcePath": "$.description",
    >  "optional": true,
    >  "targetPath": "$.description"
    >  },
    > ```

3.  Extend the Identity Authentication write transformation by adding the following mapping for the group resource:

    > ### Code Syntax:  
    > ```
    > {
    >  "sourcePath": "$.description",
    >  "optional": true,
    >  "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['description']"
    > },
    > ```


In case you remove the default list of attributes from the value of this property and only add the additional attributes, Identity Provisioning will read from Microsoft Entra ID the additional group attributes, the group *id*, *displayName*, *mailNickname* and will also return the *members* attribute.

**System Role:** Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`aad.entities.top` 

</td>
<td valign="top">

This property defines the number of entities to be read per page.

Default value: *100*

**System Role:**Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`csrf.token.path` 

</td>
<td valign="top">

Path which is appended to the URL to retrieve the CSRF token.

The property is automatically added during system creation, when the system in use is SAP Analytics Cloud consuming SCIM API version 2.

Based on the version of the SCIM API consumed, the default value for the property is:

-   SAP Analytics Cloud SCIM API version 1: `/api/v1/scim/Users?count=1`

    > ### Note:  
    > The property is present only for systems created before December 3, 2024. Systems created after this date use the default value for the connector version without adding the property.

-   SAP Analytics Cloud SCIM API version 2: `/api/v1/scim2/Users?count=1`

    > ### Note:  
    > If you delete the property, the Identity Provisioning will use the default value for the property for SAP Analytics Cloud using SCIM API**version 1**.


**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.hr.switch.active` 

</td>
<td valign="top">

A default property, whose only possible value is *true*. That means, HR integration is enabled for your system.

> ### Caution:  
> Do not change this value! Otherwise, your provisioning job will fail.

**Possible value:** *true*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.roles.filter` 

</td>
<td valign="top">

Enter OData filtering for reading roles in the SAP S/4HANA Cloud system.

To learn what criteria you can use, see: [OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → 4.5 Filter System Query Option

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.api.version` 

</td>
<td valign="top">

This property defines the API version that your SAP S/4HANA Cloud system uses.

Version *1* means your SAP S/4HANA Cloud system uses *SAP\_COM\_0193* communication arrangement.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.hr.switch.dependent.role.codes` 

</td>
<td valign="top">

A default property.

Add the codes of the roles maintained by the HR integration. Make sure these role codes are part of your read and write transformations.

**Possible values:**

For example: *BUP003, BBP005*

That means, your HR integration will support *employees* and *contingent worker*.

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.skip.read.archived` 

</td>
<td valign="top">

In the event of archived \(disabled\) entities in a source SAP S/4HANA Cloud system, you can choose whether the provisioning jobs to continue reading such entities or to skip them.

In the source and proxy systems, this property is activated by default. If you want to always read disabled entities, set the property to *false*, or delete it.

**Possible values:**

-   *true*
-   *false*

Default value: *true* 

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.onprem.hr.switch.dependent.role.codes` 

</td>
<td valign="top">

Add the codes of the roles maintained by the HR integration. Make sure these role codes are part of your read and write transformations.

This property is applicable only if `s4hana.onprem.hr.switch.active` = *true*

**Possible values:**

For example: *BUP003, BBP005, BUP012, WFM001*

That means, your HR integration will support *employees*, *contingent workers*, *collaboration users*, and *resources*.

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP S/4HANA On-Premise

</td>
</tr>
<tr>
<td valign="top">

`s4hana.onprem.hr.switch.active` 

</td>
<td valign="top">

Defines whether the system should include HR integration or not.

This property is related to `s4hana.onprem.hr.switch.dependent.role.codes`.

**Possible values:**

-   *true* – HR integration is enabled for your system
-   *false* – HR integration is disabled for your system

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP S/4HANA On-Premise

</td>
</tr>
<tr>
<td valign="top">

`s4hana.onprem.skip.read.archived` 

</td>
<td valign="top">

In the event of archived \(disabled\) entities in a source SAP S/4HANA On-Premise system, you can choose whether the provisioning jobs to continue reading such entities or to skip them.

In the source and proxy systems, this property is activated by default. If you want to always read disabled entities, set the property to *false*, or delete it.

**Possible values:**

-   *true*
-   *false*

Default value: *true* 

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP S/4HANA On-Premise

</td>
</tr>
<tr>
<td valign="top">

`s4hana.onprem.sap-client` 

</td>
<td valign="top">

Use this property if you want to specify a particular AS ABAP client to use as the `sap-client` URL parameter.

AS ABAP client. To learn more, see: [Specifying the Client](https://help.sap.com/saphelp_ewm900/helpdata/en/48/cae5cc356c3254e10000000a42189b/frameset.htm)

For more information about `sap-client`, see: [SAP URL Parameters](https://help.sap.com/saphelp_ewm900/helpdata/en/8b/46468c433b40c3b87b2e07f34dea1b/frameset.htm)

**Possible values:** A three-digit integer number

For example: *102*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP S/4HANA On-Premise

</td>
</tr>
<tr>
<td valign="top">

`s4hana.onprem.support.bulk.operation` 

</td>
<td valign="top">

Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request.

For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP S/4HANA On-Premise

</td>
</tr>
<tr>
<td valign="top">

`s4hana.onprem.bulk.operations.max.count` 

</td>
<td valign="top">

If you have enabled the bulk operations, you can use this property to set the number of users to be provisioned per request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, the service will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP S/4HANA On-Premise

</td>
</tr>
<tr>
<td valign="top">

`fg.group.prefix` 

</td>
<td valign="top">

This property distinguishes SAP Fieldglass groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `FG_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Fieldglass source system and will be provisioned to the target system with the following name pattern: <code>FG_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Fieldglass groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Fieldglass groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `FG_` prefix in their display name will be provisioned to SAP Fieldglass. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Fieldglass.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Fieldglass

</td>
</tr>
<tr>
<td valign="top">

`fg.support.bulk.operation` 

</td>
<td valign="top">

Set this property to *true* if you want to enable bulk operations for provisioning users and groups. This means, the Identity Provisioning service can write, update, and delete multiple usersor update multiple group members in a single request.

For more information, see: [SAP Fieldglass Identity Management API](https://api.sap.com/api/scim/resource)

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP Fieldglass

</td>
</tr>
<tr>
<td valign="top">

`fg.bulk.operations.max.count` 

</td>
<td valign="top">

This property sets the number of operations to be performed in one bulk request.

**Possible values:**

Default value: *20*

Minimum value: *10* 

Maximum value: *100* 

If you provide a value outside of the minimum and maximum range, the service will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP Fieldglass

</td>
</tr>
<tr>
<td valign="top">

`a4c.skip.read.archived` 

</td>
<td valign="top">

In the event of archived \(disabled\) entities in a source SAP BTP ABAP environment system, you can choose whether the provisioning jobs to continue reading such entities or to skip them.

In the source and proxy systems, this property is activated by default. If you want to always read disabled entities, set the property to *false*, or delete it.

**Possible values:**

-   *true*
-   *false*

Default value: *true* 

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP BTP ABAP environment

</td>
</tr>
<tr>
<td valign="top">

`a4c.roles.filter` 

</td>
<td valign="top">

Enter OData filtering for reading roles in the SAP BTP ABAP environment system.

To learn what criteria you can use, see: [OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → 4.5 Filter System Query Option

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP BTP ABAP environment

</td>
</tr>
<tr>
<td valign="top">

`a4c.roles.prefix` 

</td>
<td valign="top">

This property distinguishes SAP BTP ABAP environment roles by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `A4C_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the roles that are read from the SAP BTP ABAP environment source system and will be provisioned to the target system with the following name pattern: <code>A4C_<i class="varname">&lt;role_name&gt;</i></code>. This way SAP BTP ABAP environment roles in the target system will be easily distinguished from roles provisioned from other applications.

    If the property is not set, the SAP BTP ABAP environment roles will be read and provisioned to the target system with their actual role names.

-   When **set in the target system**, only roles containing the `A4C_` prefix in their role name will be provisioned to SAP BTP ABAP environment. Roles without this prefix in their names won't be provisioned.

    If the property is not set, all roles will be be provisioned to SAP BTP ABAP environment.


**System Role:** Source and Target

</td>
<td valign="top">

SAP BTP ABAP environment

</td>
</tr>
<tr>
<td valign="top">

`a4c.user.roles.overwrite` 

</td>
<td valign="top">

This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP BTP ABAP environment target or proxy system.

See also: [Extended Explanation of the \*user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

**Possible values:**

-   *true* – the current user roles will be deleted in the proxy system, and the user will be updated only with the roles provisioned by the service.
-   *false* – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the proxy system.

Default value \(if the property is missing during system creation\): *true* 

Default value \(if the property appears during system creation\): *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP BTP ABAP environment

</td>
</tr>
<tr>
<td valign="top">

`ibp.roles.prefix` 

</td>
<td valign="top">

This property distinguishes SAP Integrated Business Planning for Supply Chain roles by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `IBP_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the roles that are read from the SAP Integrated Business Planning for Supply Chain source system and will be provisioned to the target system with the following name pattern: <code>IBP_<i class="varname">&lt;role_name&gt;</i></code>. This way SAP Integrated Business Planning for Supply Chain roles in the target system will be distinguished from roles provisioned from other applications.

    If the property is not set, the SAP Integrated Business Planning for Supply Chain roles will be read and provisioned to the target system with their actual role names.

-   When **set in the target system**, only roles containing the `IBP_` prefix in their role name will be provisioned to SAP Integrated Business Planning for Supply Chain. Roles without this prefix in the role name won't be provisioned.

    If the property is not set, all roles will be be provisioned to SAP Integrated Business Planning for Supply Chain.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Integrated Business Planning for Supply Chain

</td>
</tr>
<tr>
<td valign="top">

`ibp.user.roles.overwrite` 

</td>
<td valign="top">

This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP IBP target or proxy system.

See also: [Extended Explanation of the \*user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

**Possible values:**

-   *true* – the current user roles will be deleted in the proxy system, and the user will be updated only with the roles provisioned by the service.
-   *false* – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the proxy system.

Default value \(if the property is missing during system creation\): *true* 

Default value \(if the property appears during system creation\): *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Integrated Business Planning for Supply Chain

</td>
</tr>
<tr>
<td valign="top">

`marketing.cloud.user.roles.overwrite` 

</td>
<td valign="top">

This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP Marketing Cloud target or proxy system.

See also: [Extended Explanation of the \*user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

**Possible values:**

-   *true* – the current user roles will be deleted in the proxy system, and the user will be updated only with the roles provisioned by the service.
-   *false* – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the proxy system.

Default value \(if the property is missing during system creation\): *true* 

Default value \(if the property appears during system creation\): *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Marketing Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.roles.page.size` 

</td>
<td valign="top">

This property indicates how many business roles \(considered as *groups*\) per page to be read from your SAP S/4HANA Cloud source system.

**Possible values:** Integer number

For example, if you set the property's value = *30*, the Identity Provisioning will read 30 roles \(groups\) at once, then – another 30, and so on.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.support.bulk.operation` 

</td>
<td valign="top">

Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request.

For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.bulk.operations.max.count` 

</td>
<td valign="top">

If you have enabled the bulk operations, you can use this property to set the number of users to be provisioned per request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, the service will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`marketing.cloud.support.bulk.operation` 

</td>
<td valign="top">

Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request.

For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP Marketing Cloud

</td>
</tr>
<tr>
<td valign="top">

`marketing.cloud.bulk.operations.max.count` 

</td>
<td valign="top">

If you have enabled the bulk operations, you can use this property to set the number of users to be provisioned per request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, the service will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP Marketing Cloud

</td>
</tr>
<tr>
<td valign="top">

`a4c.support.bulk.operation` 

</td>
<td valign="top">

Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request.

For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP BTP ABAP environment

</td>
</tr>
<tr>
<td valign="top">

`a4c.bulk.operations.max.count` 

</td>
<td valign="top">

If you have enabled the bulk operations, you can use this property to set the number of users to be provisioned per request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, the service will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP BTP ABAP environment

</td>
</tr>
<tr>
<td valign="top">

`a4c.roles.page.size` 

</td>
<td valign="top">

This property indicates how many business roles \(considered as *groups*\) per page to be read from your SAP BTP ABAP environment source system.

**Possible values:** Integer number

For example, if you set the property's value = *30*, the Identity Provisioning will read 30 roles \(groups\) at once, then – another 30, and so on.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP BTP ABAP environment

</td>
</tr>
<tr>
<td valign="top">

`ibp.roles.page.size` 

</td>
<td valign="top">

This property indicates how many business roles \(considered as *groups*\) per page to be read from your SAP IBP source system.

**Possible values:** Integer number

For example, if you set the property's value = *30*, the Identity Provisioning will read 30 roles \(groups\) at once, then – another 30, and so on.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Integrated Business Planning for Supply Chain

</td>
</tr>
<tr>
<td valign="top">

`ibp.support.bulk.operation` 

</td>
<td valign="top">

Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request.

For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP Integrated Business Planning for Supply Chain

</td>
</tr>
<tr>
<td valign="top">

`ibp.bulk.operations.max.count` 

</td>
<td valign="top">

If you have enabled the bulk operations, you can use this property to set the number of users to be provisioned per request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, the service will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP Integrated Business Planning for Supply Chain

</td>
</tr>
<tr>
<td valign="top">

`marketing.cloud.roles.page.size` 

</td>
<td valign="top">

This property indicates how many business roles \(considered as *groups*\) per page to be read from your SAP Marketing Cloud source system.

**Possible values:** Integer number

For example, if you set the property's value = *30*, the Identity Provisioning will read 30 roles \(groups\) at once, then – another 30, and so on.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Marketing Cloud

</td>
</tr>
<tr>
<td valign="top">

`marketing.cloud.roles.prefix` 

</td>
<td valign="top">

This property distinguishes SAP Marketing Cloud roles by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `SMKC_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the roles that are read from the SAP Marketing Cloud source system and will be provisioned to the target system with the following name pattern: <code>SMKC_<i class="varname">&lt;role_name&gt;</i></code>. This way SAP Marketing Cloud roles in the target system will be distinguished from roles provisioned from other applications.

    If the property is not set, the SAP Marketing Cloud roles will be read and provisioned to the target system with their actual role names.

-   When **set in the target system**, only roles containing the `SMKC_` prefix in their role name will be provisioned to SAP Marketing Cloud. Roles without this prefix in the role name won't be provisioned.

    If the property is not set, all roles will be be provisioned to SAP Marketing Cloud.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Marketing Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.user.roles.overwrite` 

</td>
<td valign="top">

This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP S/4HANA Cloud target or proxy system.

See also: [Extended Explanation of the \*user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

**Possible values:**

-   *true* – the current user roles will be deleted in the proxy system, and the user will be updated only with the roles provisioned by the service.
-   *false* – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the proxy system.

Default value \(if the property is missing during system creation\): *true* 

Default value \(if the property appears during system creation\): *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`ibp.skip.read.archived` 

</td>
<td valign="top">

In the event of archived \(disabled\) entities in a source SAP IBP system, you can choose whether the provisioning jobs to continue reading such entities or to skip them.

In the source systems, this property is activated by default. If you want to always read disabled entities, set the property to *false*, or delete it.

**Possible values:**

-   *true*
-   *false*

Default value: *true*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Integrated Business Planning for Supply Chain

</td>
</tr>
<tr>
<td valign="top">

`ibp.roles.filter` 

</td>
<td valign="top">

Enter OData filtering for reading roles in the SAP IBP system.

To learn what criteria you can use, see: [OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → 4.5 Filter System Query Option

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Integrated Business Planning for Supply Chain

</td>
</tr>
<tr>
<td valign="top">

`marketing.cloud.skip.read.archived` 

</td>
<td valign="top">

In the event of archived \(disabled\) entities in a source SAP Marketing Cloud system, you can choose whether the provisioning jobs to continue reading such entities or to skip them.

In the source and proxy systems, this property is activated by default. If you want to always read disabled entities, set the property to *false*, or delete it.

**Possible values:**

-   *true*
-   *false*

Default value: *true*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Marketing Cloud

</td>
</tr>
<tr>
<td valign="top">

`marketing.cloud.roles.filter` 

</td>
<td valign="top">

Enter OData filtering for reading roles in the SAP Marketing Cloud system.

To learn what criteria you can use, see: [OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → 4.5 Filter System Query Option

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Marketing Cloud

</td>
</tr>
<tr>
<td valign="top">

`scim.api.csrf.protection` 

</td>
<td valign="top">

Specifies whether to fetch a CSRF token when sending requests to the system. The property is automatically added in the system, with default value: *enabled*.

**Possible values:**

-   *enabled*
-   *disabled*

Default value: *enabled*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.api.csrf.protection` 

</td>
<td valign="top">

Specifies whether to fetch a CSRF token when sending requests to the system. The property is automatically added in the system, with default value: *enabled*.

**Possible values:**

-   *enabled*
-   *disabled*

Default value: *enabled*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.support.bulk.operation` 

</td>
<td valign="top">

This property enables bulk operations for users.

When bulk operations are enabled \(set to *true*\), Identity Provisioning service creates, updates, and deletes multiple users in one request.

When bulk operations are not enabled \(set to *false*\), Identity Provisioning service creates, updates, and deletes one user at a time.

For more information, see: [SCIM Protocol: Bulk Operations](https://datatracker.ietf.org/doc/html/rfc7644#section-3.7)

> ### Note:  
> SCIM bulk operations are not supported for provisioning groups to SAP Analytics Cloud.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.bulk.operations.max.count` 

</td>
<td valign="top">

If you have enabled the SCIM bulk operations, you can use this property to set the number of users to be provisioned per request.

**Possible values:**

Default value:

-   *100* - when using SAP Analytics Cloud SCIM API version 1.

-   *30* - when using SAP Analytics Cloud SCIM API version 2.


> ### Note:  
> The value must not exceed the number of entities defined by the SAP Analytics Cloud system as a SCIM service provider. Otherwise, the provisioning job will fail with HTTP response code 413 \(*Payload Too Large*\).

**System Role:** Target

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`scim.user.filter` 

</td>
<td valign="top">

When specified, only those users matching the filter expression will be read.

**Possible values:**

For example:

*name.familyName eq "SmithJ" and addresses.country eq "US"*

**System Role:** Source

</td>
<td valign="top">

All SCIM-based systems

</td>
</tr>
<tr>
<td valign="top">

`scim.group.filter` 

</td>
<td valign="top">

When specified, only those groups matching the filter expression will be read.

**Possible values:**

For example:

*displayName eq "ProjectTeam1" or "Students2018"*

**System Role:** Source

</td>
<td valign="top">

-   Identity Authentication

-   Local Identity Directory

-   SAP Advanced Financial Closing

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP Ariba Central Invoice Management

-   SAP BTP Account Members \(Neo\)

-   SAP BTP Java/HTML5 apps \(Neo\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Build Work Zone, advanced edition

-   SAP Build Work Zone, standard edition

-   SAP Business Network

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP CPQ

-   SAP Data Custodian

-   SAP Enable Now

-   SAP Enterprise Portal

-   SAP Fieldglass

-   SAP Field Service Management

-   SAP HANA Cloud, SAP HANA Database

-   SAP Intelligent Agriculture

-   SAP Jam Collaboration

-   SAP Sales Cloud and SAP Service Cloud

-   SAP SuccessFactors version 2

-   SAP SuccessFactors Employee Central Payroll

-   SAP SuccessFactors Incentive Management

-   Sales Cloud – Analytics & AI

-   Cloud Foundry UAA Server

-   Procurement Data Warehouse

-   SCIM System

-   SSH Server \(Beta\)




</td>
</tr>
<tr>
<td valign="top">

`scim.content.type` 

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

All SCIM-based systems

</td>
</tr>
<tr>
<td valign="top">

`scim.user.unique.attribute` 

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). **If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one.** If the service does not find such a user, the creation will fail.

According to your use case and system type, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.

    > ### Note:  
    > Relevant only for *Identity Authentication* and *SAP Analytics Cloud*:
    > 
    > -   For systems created **before** `April 7, 2020`, this property is missing during system creation, and it has the default value, *userName*. If the service does not find an existing user with such a *userName*, it will try again to resolve the conflicting user – by *email*. If the second attempt for resolution is unsuccessful too, the creation of the conflicting user fails.
    > -   For systems created **after** `April 7, 2020`, this property appears by default during system creation, and its value is set to *userName*. If the service does not find an existing user with such a *userName*, the creation of the conflicting user fails.
    > 
    >     However, if you delete the property, the service will try again to resolve the conflicting user – by *email*. If the second attempt for resolution is unsuccessful too, the creation of the conflicting user fails.

-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*
-   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes

> ### Note:  
> -   *phoneNumbers\[0\].value* - supported unique attribute for Local Identity Directory \(when Identity Provisioning is running on SAP Cloud Identity Infrastructure\)

Default value: *userName*

**System Role:** Target

</td>
<td valign="top">

All SCIM-based systems

</td>
</tr>
<tr>
<td valign="top">

`scim.group.unique.attribute` 

</td>
<td valign="top">

If the service tries to create a group that already exists in the target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\).

To make the search filter by a specific attribute, specify this attribute as a value for the `scim.group.unique.attribute` property.

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

-   Identity Authentication

-   Local Identity Directory

-   SAP Advanced Financial Closing

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP Ariba Central Invoice Management

-   SAP BTP Account Members \(Neo\)

-   SAP BTP Java/HTML5 apps \(Neo\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Build Work Zone, advanced edition

-   SAP Build Work Zone, standard edition

-   SAP Business Network

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP CPQ

-   SAP Data Custodian

-   SAP Enable Now

-   SAP Enterprise Portal

-   SAP Fieldglass

-   SAP Field Service Management

-   SAP HANA Cloud, SAP HANA Database

-   SAP Intelligent Agriculture

-   SAP Jam Collaboration

-   SAP Sales Cloud and SAP Service Cloud

-   SAP SuccessFactors version 2

-   SAP SuccessFactors Employee Central Payroll

-   SAP SuccessFactors Incentive Management

-   Sales Cloud – Analytics & AI

-   Cloud Foundry UAA Server

-   Procurement Data Warehouse

-   SCIM System

-   SSH Server \(Beta\)




</td>
</tr>
<tr>
<td valign="top">

`scim.group.members.additional.attributes` 

</td>
<td valign="top">

Defines additional attributes you can request from an **Identity Authentication** source system when reading groups.

If you read groups through REST API, use the `GET` request. Add the additional attributes \(coma-separated\) as a value of the URL parameter `membersAdditionalAttributes`.

**Possible values:** a coma-separated list of attribute names

You can add the following attributes:

-   *emails*
-   *userName*
-   *displayName*
-   *urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber*

**System Role:** Source

</td>
<td valign="top">

Identity Authentication \(SCIM API version 1\)

</td>
</tr>
<tr>
<td valign="top">

`scim.include.if.match.wildcard.header` 

</td>
<td valign="top">

Makes the connector send the `If-Match` HTTP header with a value of “\*” for every request to the target system. This header could be used by a SCIM system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

All SCIM-based systems

</td>
</tr>
<tr>
<td valign="top">

`scim.support.patch.operation` 

</td>
<td valign="top">

If your target or proxy system is among the SCIM-based ones listed under *System Type* and supports `PATCH` operations, set this property to *true*. This way, when the Identity Provisioning identifies a changed entity in the source system, it will execute the updates as `PATCH` requests instead of `PUT`. That means, only the changes will be written in the target system, instead of provisioning the whole entity data.

Note that only attributes without `"scope"` in the attribute mappings in the write transformation will be updated. For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with scope, such as:

```
{
        "constant": "xsuaa-dummy-value",
        "targetPath": "$.id",
        "scope": "createEntity"
}
```

**Additional Information:**

There are different cases when an entity should be updated in the target system:

-   In the source system, some of the entity attributes have been changed, or new attributes have been added.

-   In the source system, a condition or a filter is set for this entity not to be read anymore.

-   The whole entity has been deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

-   Identity Authentication \(SCIM API version 2\)

-   Local Identity Directory

-   Cloud Foundry UAA Server

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SCIM System

-   SAP Ariba Applications

-   SAP Ariba Category Management

-   SAP Advanced Workflow

-   SAP Business Network

-   SAP Commerce Cloud

-   SAP Build Work Zone, standard edition

-   SAP Ariba Central Invoice Management

-   SAP Data Custodian

-   SAP Datasphere

-   SAP Jam Collaboration

-   SAP SuccessFactors Employee Central Payroll

-   SAP Field Service Management

-   SAP HANA Cloud, SAP HANA Database

-   SAP Intelligent Agriculture

-   SAP SuccessFactors \(SCIM API version 2\)

-   SAP SuccessFactors Learning

-   SAP Advanced Financial Closing

-   SAP Analytics Cloud

-   SAP Build Work Zone, advanced edition




</td>
</tr>
<tr>
<td valign="top">

`jam.group.prefix` 

</td>
<td valign="top">

This property distinguishes SAP Jam Collaboration groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `SJC_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Jam Collaboration source system and will be provisioned to the target system with the following name pattern: <code>SJC_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Jam Collaboration groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Jam Collaboration groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `SJC_` prefix in their display name will be provisioned to SAP Jam Collaboration. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Jam Collaboration.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Jam Collaboration

</td>
</tr>
<tr>
<td valign="top">

`scp.user.userbase` 

</td>
<td valign="top">

This property specifies the host to the identity provider to be used with this target system. All provisioned users can be authenticated only by this identity provider.

If you use another IdP, enter its value as configured in the SAP BTP cockpit. For example: `<account_ID>.accounts.ondemand.com`

**Possible values:**

Default value: *accounts.sap.com*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP BTP Account Members \(Neo\)

</td>
</tr>
<tr>
<td valign="top">

`AuthType` 

</td>
<td valign="top">

Enter the type of authentication used for access token retrieval for OAuth HTTP destinations.

**Possible values:**

-   *Basic*
-   *Form*

Default value: *Basic*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   SCIM System
-   SAP Analytics Cloud
-   SAP SuccessFactors Incentive Management
-   SAP Jam Collaboration
-   Identity Authentication
-   Local Identity Directory
-   Cloud Foundry UAA Server
-   SAP BTP XS Advanced UAA \(Cloud Foundry\)
-   Sales Cloud – Analytics & AI
-   SAP BTP Account Members \(Neo\)
-   SAP Fieldglass



</td>
</tr>
<tr>
<td valign="top">

`CloudConnectorLocationId` 

</td>
<td valign="top">

Relevant when the `ProxyType` property is set to *OnPremise*. Use it in case your SAP Business Technology Platform account uses more than one Cloud Connector or when the Cloud Connector uses `LocationID`.

**Possible values:** String

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   SSH Server \(Beta\)

-   SAP HANA Database \(Beta\)

-   LDAP Server

-   Microsoft Active Directory

-   SAP S/4HANA On-Premise

-   All HTTP systems




</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.db.user` 

</td>
<td valign="top">

Name of the SAP HANA Database user

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.db.password` 

</td>
<td valign="top">

\(Credential\)

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.db.host` 

</td>
<td valign="top">

SAP HANA Database host

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.db.port` 

</td>
<td valign="top">

SAP HANA Database port

**Possible values:** *30015*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.access.type` 

</td>
<td valign="top">

There are three types of SAP HANA access:

-   *direct* – It requires only `hana.jdbc.db.*` properties
-   *ssh.tunnel* – it requires `hana.jdbc.db.*` and `hana.jdbc.ssh.tunnel.*` properties.
-   *cf.app.ssh.tunnel* – It requires `hana.jdbc.ssh.tunnel.cf.*` properties to establish an SSH tunnel to the Cloud Foundry application, from which to access the JDBC SQL port of SAP HANA.

**Possible values:**

-   *direct*
-   *ssh.tunnel*
-   *cf.app.ssh.tunnel*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.username` 

</td>
<td valign="top">

The username used for opening the SSH Tunnel

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.technical.user.origin` 

</td>
<td valign="top">

This is the origin of the Cloud Foundry technical user, specified in property `hana.jdbc.ssh.tunnel.cf.username`.

If the origin is the same as of the other Cloud Foundry users, you don't need this property – leave it empty or delete it.

**Possible values:** Text/numeric string

For example: *uaa*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.host` 

</td>
<td valign="top">

SSH Tunnel’s host

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.port` 

</td>
<td valign="top">

SSH Tunnel’s port

**Possible values:** *22*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.auth.type` 

</td>
<td valign="top">

The authentication type for the SSH Tunnel.

**Possible values:**

Supported SSH authentication types:

-   *key*
-   *pwd*
-   *otp*
-   *key+otp*
-   *key+pwd*
-   *pwd+otp*
-   *key+pwd+otp*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.api.url` 

</td>
<td valign="top">

The URL of the Cloud Foundry API.

**Possible values:**

For example: *https://api.cf.mycloudfoundryhost.ondemand.com*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.oauth.token.url` 

</td>
<td valign="top">

The URL of the OAuth token endpoint.

> ### Remember:  
> Remove the */oauth/token* part at the end of the URL.

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.org` 

</td>
<td valign="top">

This is the Cloud Foundry organization.

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.space` 

</td>
<td valign="top">

This is the Cloud Foundry space.

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.app` 

</td>
<td valign="top">

This is the Cloud Foundry application to which the *SAP HANA Database \(Beta\)* system opens an SSH tunnel. For more information, see: [Cloud Foundry: Accessing apps with SSH](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html)

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.app.instance` 

</td>
<td valign="top">

This is the instance number of the Cloud Foundry application.

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.username` 

</td>
<td valign="top">

This is the Cloud Foundry user. It has the role **Developer** for the space where the application is deployed.

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.cf.password` 

</td>
<td valign="top">

\(Credential\) The password for property `hana.jdbc.ssh.tunnel.cf.username`

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.password` 

</td>
<td valign="top">

\(Credential\) Taken into account only if the authentication type includes **pwd**. That means any of the following:

-   `hana.jdbc.ssh.tunnel.auth.type` = *pwd*
-   `hana.jdbc.ssh.tunnel.auth.type` = *pwd+otp*
-   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd*
-   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd+otp*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.totp.secret.key` 

</td>
<td valign="top">

\(Credential\) Taken into account only if the authentication type includes **otp**. That means any of the following:

-   `hana.jdbc.ssh.tunnel.auth.type` = *otp*
-   `hana.jdbc.ssh.tunnel.auth.type` = *key+otp*
-   `hana.jdbc.ssh.tunnel.auth.type` = *pwd+otp*
-   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd+otp*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`hana.jdbc.ssh.tunnel.private.key` 

</td>
<td valign="top">

\(Credential\) Taken into account only if the authentication type includes **key**. That means any of the following:

-   `hana.jdbc.ssh.tunnel.auth.type` = *key*
-   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd*
-   `hana.jdbc.ssh.tunnel.auth.type` = *key+otp*
-   `hana.jdbc.ssh.tunnel.auth.type` = *key+pwd+otp*

**System Role:** Target

</td>
<td valign="top">

SAP HANA Database \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`sales.cloud.analytics_ai.user.filter` 

</td>
<td valign="top">

Use this property to filter users by specific criteria, according to the API syntax of SCAAI.

**Possible values:** Text/numeric string

For example: *externalId eq "John123"*

**System Role:** Source, Proxy

</td>
<td valign="top">

Sales Cloud – Analytics & AI

</td>
</tr>
<tr>
<td valign="top">

`sales.cloud.analytics_ai.group.filter` 

</td>
<td valign="top">

Use this property to filter groups by specific criteria, according to the API syntax of SCAAI.

**Possible values:** Text/numeric string

For example: *displayName eq "first\_group"*

**System Role:** Source, Proxy

</td>
<td valign="top">

Sales Cloud – Analytics & AI

</td>
</tr>
<tr>
<td valign="top">

`ssh.read.users.command` 

</td>
<td valign="top">

Path to the bash command you need to execute to read users.

**System Role:** Source

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.create.user.command` 

</td>
<td valign="top">

Path to the bash command you need to execute to create a user.

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.update.user.command` 

</td>
<td valign="top">

Path to the bash command you need to execute to update a user.

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.delete.user.command` 

</td>
<td valign="top">

Path to the bash command you need to execute to delete a user.

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.read.groups.command` 

</td>
<td valign="top">

Path to the bash command you need to execute to read groups.

**System Role:** Source

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.create.group.command` 

</td>
<td valign="top">

Path to the bash command you need to execute to create a group.

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.update.group.command` 

</td>
<td valign="top">

Path to the bash command you need to execute to update a group.

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.delete.group.command` 

</td>
<td valign="top">

Path to the bash command you need to execute to delete a group.

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.create.user.command.exit.code.already.exists` 

</td>
<td valign="top">

An exit code number

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.update.user.command.exit.code.not.found` 

</td>
<td valign="top">

An exit code number

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.delete.user.command.exit.code.not.found` 

</td>
<td valign="top">

An exit code number

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.create.group.command.exit.code.already.exists` 

</td>
<td valign="top">

An exit code number

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.update.group.command.exit.code.not.found` 

</td>
<td valign="top">

An exit code number

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.delete.group.command.exit.code.not.found` 

</td>
<td valign="top">

An exit code number

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.auth.type` 

</td>
<td valign="top">

Supported SSH authentication types:

-   *key*
-   *pwd*
-   *otp*
-   *key+otp*
-   *key+pwd*
-   *pwd+otp*
-   *key+pwd+otp*

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.host` 

</td>
<td valign="top">

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.port` 

</td>
<td valign="top">

**Possible values:** *22*

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.username` 

</td>
<td valign="top">

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.password` 

</td>
<td valign="top">

\(Credential\) Taken into account only if the authentication type includes **pwd**. That means any of the following:

-   `ssh.auth.type` = *pwd*
-   `ssh.auth.type` = *pwd+otp*
-   `ssh.auth.type` = *key+pwd*
-   `ssh.auth.type` = *key+pwd+otp*

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.totp.secret.key` 

</td>
<td valign="top">

\(Credential\) Taken into account only if the authentication type includes **otp**. That means any of the following:

-   `ssh.auth.type` = *otp*
-   `ssh.auth.type` = *key+otp*
-   `ssh.auth.type` = *pwd+otp*
-   `ssh.auth.type` = *key+pwd+otp*

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.private.key`

</td>
<td valign="top">

\(Credential\) Taken into account only if the authentication type includes **key**. That means any of the following:

-   `ssh.auth.type` = *key*
-   `ssh.auth.type` = *key+pwd*
-   `ssh.auth.type` = *key+otp*
-   `ssh.auth.type` = *key+pwd+otp*

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`ssh.private.key.type` 

</td>
<td valign="top">

The format of SSH private key.

**Possible values:**

-   *ssh-rsa*
-   *ssh-dsa*

Default value: *ssh-rsa*

**System Role:** Source, Target

</td>
<td valign="top">

SSH Server \(Beta\)

</td>
</tr>
<tr>
<td valign="top">

`sf.page.size` 

</td>
<td valign="top">

Use this property to configure the paging. That means, the number of entities to be read from SAP SuccessFactors at once.

Default value: *100*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP SuccessFactors \(using version 1 - SAP SuccessFactors HCM Suite OData API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.group.filter` 

</td>
<td valign="top">

The possible values of this property depend on the API version which your SAP SuccessFactors system consumes.

Use this property to filter dynamic groups from SAP SuccessFactors. The filter obtains values as described in the OData 2.0 syntax, except any statements with attribute `lastModifiedDateTime`. To learn more, see:

-   [OData version 2](http://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → **4.5. Filter System Query Option \($filter\)**
-   [SAP SuccessFactors HCM Suite OData API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?locale=en-US&version=latest)

    → **DynamicGroup**

-   [syntax, except anySAP SuccessFactors Workforce SCIM API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html)

**Possible values:**

If your system consumes SAP SuccessFactors Workforce SCIM API, you can filter groups only by `displayName`.

For example: *groupType eq 'permission'*

**System Role:** Source, Proxy

</td>
<td valign="top">

-   SAP SuccessFactors \(using version 1 - SAP SuccessFactors HCM Suite OData API\)

-   SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)




</td>
</tr>
<tr>
<td valign="top">

`sf.group.prefix` 

</td>
<td valign="top">

This property distinguishes SAP SuccessFactors groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `SF_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP SuccessFactors source system and will be provisioned to the target system with the following name pattern: <code>SF_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP SuccessFactors groups in the target system will be distinguished from groups provisioned from other applications.

-   When **set in the target system**, only groups containing the `SF_` prefix in their display name will be provisioned to SAP SuccessFactors. Groups without this prefix in the display name won't be provisioned.


If the property is not set, the SAP SuccessFactors groups will be read and provisioned to the target system with their actual display names.

**System Role:** Source, Target

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.user.filter` 

</td>
<td valign="top">

The possible values of this property depend on the API version which your SAP SuccessFactors system consumes.

This property takes values as described in the [OData version 2](http://www.odata.org/documentation/odata-version-2-0/uri-conventions/)`lastModifiedDateTime`.

> ### Caution:  
> Attribute `lastModifiedDateTime` is used internally by the Identity Provisioning service, for calculating the delta load from the SAP SuccessFactors system. You must not use it in your filter statements. If you do, your provisioning jobs will fail.

> ### Tip:  
> By default, only **active** users are read from SAP SuccessFactors. If you want to filter by another user status, you can set it in the value of this property, using either the *status value* or the *status text* parameters. See:
> 
> [SAP SuccessFactors HCM Suite OData API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?locale=en-US&version=latest)
> 
> → **Querying Different Types of Users**

**Possible values:**

-   If your system consumes SAP SuccessFactors Workforce SCIM API, you can use the supported filter attributes described in [SAP SuccessFactors Workforce SCIM API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html)

    For example: *userName eq "Sebastian"*

-   If your system consumes SAP SuccessFactors HCM Suite OData API, you can only use attributes supported as filterable by this API. See [SAP SuccessFactors HCM Suite OData API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?locale=en-US&version=latest).

    Some of these filterable attributes are: `firstName`, `lastName`, `department`, `division`, `jobCode`, `location`, `status`, `userId`, `username`.

    For example: *division eq 'Manufacturing \(MANU\)'*


**System Role:** Source, Proxy

</td>
<td valign="top">

-   SAP SuccessFactors \(using version 1 - SAP SuccessFactors HCM Suite OData API\)

-   SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)




</td>
</tr>
<tr>
<td valign="top">

`sf.user.attributes` 

</td>
<td valign="top">

The value of this property is a comma-separated list of user attributes that have to be loaded from/to the SAP SuccessFactors system.

**Possible values:**

Default value: *userId,username,status,email,lastName,firstName,lastModifiedDateTime,personKeyNav*

SAP SuccessFactors supports a huge amount of user information, which requires a lot of memory processing time and may even lead to time-out errors. That's why we recommend that you keep the default list of attributes, or specify only a few \(the most significant attributes\) for your provisioning scenario.

> ### Note:  
> If you want to add more attributes, make sure you have added:
> 
> -   the relevant extra attributes to the value of this property, separated by commas
> -   extra mappings for these attributes in the *user* transformation
> -   extra mappings for these attributes in the write transformation of the relevant target system

> ### Remember:  
> Always make sure that attribute `lastModifiedDateTime` is in the list. If you don't specify it, the provisioning from/to SAP SuccessFactors will fail.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors \(using version 1 - SAP SuccessFactors HCM Suite OData API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.user.attributes.expand` 

</td>
<td valign="top">

This property reads/writes additional user data related to *complex \(navigation\)* attributes, which are specified in the `sf.user.attributes` property.

**Possible values:**

Default value: *personKeyNav,personKeyNav/userAccountNav*

For example: If you also need to read the *username* of the manager of a company employee, enter the following configuration in the *Properties* tab:

`sf.user.attributes` = *username,firstName,lastName,manager/username* 

`sf.user.attributes.expand` = *personKeyNav,personKeyNav/userAccountNav,manager*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors \(using version 1 - SAP SuccessFactors HCM Suite OData API\)

</td>
</tr>
<tr>
<td valign="top">

`aad.user.attributes.expand` 

</td>
<td valign="top">

This property allows you to expand the list of attributes specified in the `aad.user.attributes` property with additional user attributes.

Once you provide the value of the additional attributes in the `aad.user.attributes.expand` property, you need to extend the read transformation of Microsoft Entra ID with attribute mappings based on the given value.

Currently, the read transformation of Microsoft Entra ID is extended with the attribute mappings for manager **id** and **displayName** as follows:

> ### Code Syntax:  
> ```
> {
>         "sourcePath": "$.manager.id",
>         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
>         "optional": true
>       },
>       {
>         "sourcePath": "$.manager.displayName",
>         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
>         "optional": true
>       }
> ```

To read the manager of the user, you need to provide the manager as a value of the `aad.user.attributes.expand` property in the following format: `manager($select=id,displayName)`

For more information on the attributes \(relationships\) that support the **$expand** query parameter, refer to [Microsoft Graph REST API v1.0](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0#relationships) → *Relationships*.

**System Role:** Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`aad.group.attributes.expand` 

</td>
<td valign="top">

This property allows you to expand the list of attributes specified in the `aad.group.attributes` property with additional group attributes.

Once you provide the value of the additional attributes in the `aad.group.attributes.expand` property, you need to extend the read transformation of Microsoft Entra ID with attribute mappings based on the given value.

For more information on the attributes \(relationships\) that support the **$expand** query parameter, refer to [Microsoft Graph REST API v1.0](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0#relationships) → *Relationships*.

**System Role:** Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`RemoteSystemID` 

</td>
<td valign="top">

> ### Note:  
> Only relevant to API **v.1**.

Enter the system instance ID, configured for the communication system setting in the SAP Sales Cloud and SAP Service Cloud system.

**Possible values:**

For example: *IPS*

**System Role:** Target

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`RecipientPartyID` 

</td>
<td valign="top">

> ### Note:  
> Only relevant to API **v.2**.

Enter the recipient system name.

**Possible values:**

For example: *0011SAP*

**System Role:** Target

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`SenderPartyID` 

</td>
<td valign="top">

> ### Note:  
> Only relevant to API **v.2**.

Enter the name of the sender system name. It's equal to the value of property `RemoteSystemID` from API v.1.

**Possible values:**

For example: *IPS*

**System Role:** Target

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`TrustAll` 

</td>
<td valign="top">

Use this property when you create a connectivity destination in SAP BTP cockpit with authentication type `BasicAuthentication` to configure your provisioning system. Use cases:

-   If this property is not specified or set to *false*, you need to add a truststore certificate to check for SSL connections. You can either use the default JDK truststore, or provide a custom truststore certificate – if you use a custom domain instead of the default Identity Authentication one. For more information, see:

    [Use Destination Certificates \(Cockpit\)](https://help.sap.com/viewer/b865ed651e414196b39f8922db2122c7/Cloud/en-US/d3dfd5052fb14a15aad87ebcdb2f23e2.html)

    [Use Custom Domain in Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/c4db840ff2464e12ab68d94efb0769c3.html)

-   If the property is enabled \(set to *true*\), the server certificate will be ignored, thus – not checked for SSL connections.


> ### Remember:  
> For productive scenarios, we recommend that you do not use this property \(or set it to *false*\) because the SSL server certificate cannot be verified, and thus the server is not authenticated.
> 
> Enable the property only for testing purposes.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`uaa.origin` 

</td>
<td valign="top">

It denotes the `origin` attribute in the system transformation.

The value of this property is the location of your Cloud Foundry identity provider. If not sure about the value, ask your Cloud Foundry system administrator.

**Possible values:** Text/numeric string

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

Cloud Foundry UAA Server

</td>
</tr>
<tr>
<td valign="top">

`uaa.origin.filter.enabled` 

</td>
<td valign="top">

This flag property depends on `uaa.origin`.

If the flag is set to *true*, the Identity Provisioning service will read only users whose identity provider is set as a value of `uaa.origin`.

**Possible values:** *true* or *false*

-   If set to *true*, the Identity Provisioning service will read only users whose identity provider is set as a value of `uaa.origin`.
-   If set to *false*, the Identity Provisioning service will read all users, regardless of their origin.
-   If set to *true* but the `uaa.origin` property is missing, the provisioning job will fail.

**System Role:** Source, Proxy

</td>
<td valign="top">

Cloud Foundry UAA Server

</td>
</tr>
<tr>
<td valign="top">

`uaa.patch.response.with.resource` 

</td>
<td valign="top">

Use this property if you want to retrieve a group whose membership was modified.

> ### Note:  
> This property is usable only when you have configured membership modifications via `Add/Remove Member` UAA endpoints. That is, when the `scim.support.patch.operation` property is set to *false*.

**Possible values:**

-   *true* – the Identity Provisioning service will return the modified group via the `GET /Groups` endpoint of UAA. To learn how, see [Retrieve](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#retrieve-2).
-   *false* – no modified groups will be returned by the service.

**System Role:** Proxy

</td>
<td valign="top">

Cloud Foundry UAA Server

</td>
</tr>
<tr>
<td valign="top">

`uaa.group.prefix`

</td>
<td valign="top">

This property distinguishes Cloud Foundry UAA Server groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `UAA_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the Cloud Foundry UAA Server source system and will be provisioned to the target system with the following name pattern: <code>UAA_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way Cloud Foundry UAA Server groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the Cloud Foundry UAA Server groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `UAA_` prefix in their display name will be provisioned to Cloud Foundry UAA Server. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to Cloud Foundry UAA Server.


**System Role:** Source and Target

</td>
<td valign="top">

Cloud Foundry UAA Server

</td>
</tr>
<tr>
<td valign="top">

`xsuaa.origin` 

</td>
<td valign="top">

Holds the identity provider of a user in SAP BTP XS Advanced UAA \(Cloud Foundry\).

You can find it in the SAP BTP cockpit. Go to your Cloud Foundry subaccount, choose *Trust Configuration* and see the value under *Origin Key*. For more information, see [Configure Single and Multiple Origins](configure-single-and-multiple-origins-aeaab63.md)

**Possible values:** Text/numeric string

For example: *myaccount-xsuaa.accounts.ondemand.com*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP BTP XS Advanced UAA \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`xsuaa.origin.filter.enabled` 

</td>
<td valign="top">

This flag property depends on `xsuaa.origin`.

If the flag is set to *true*, the Identity Provisioning service will read only users whose identity provider is set as a value of `xsuaa.origin`.

Possible values: *true* or *false*

-   If set to *true*, the Identity Provisioning service will read only users whose identity provider is set as a value of `xsuaa.origin`.
-   If set to *false*, the Identity Provisioning service will read all users, regardless of their origin.
-   If set to *true* but the `xsuaa.origin` property is missing, the provisioning job will fail.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP BTP XS Advanced UAA \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`xsuaa.patch.response.with.resource` 

</td>
<td valign="top">

Use this property if you want to retrieve a group whose membership was modified.

> ### Note:  
> This property is usable only when you have configured membership modifications via *Add/Remove Member* UAA endpoints. That is, when the `scim.support.patch.operation` property is set to *false*.

**Possible values:**

-   *true* – the Identity Provisioning service will return the modified group via the `GET /Groups` endpoint of UAA. To learn how, see [Retrieve](https://docs.cloudfoundry.org/api/uaa/version/4.20.0/index.html#retrieve-2).
-   *false* – no modified groups will be returned by the service.

**System Role:** Proxy

</td>
<td valign="top">

SAP BTP XS Advanced UAA \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`workzone.user.filter`

</td>
<td valign="top">

When specified, only those SAP Build Work Zone, advanced edition users matching the filter expression will be read.

**Possible values:**

For example: *userName eq "SmithJ"*

**System Role:** Source

</td>
<td valign="top">

SAP Build Work Zone, advanced edition

</td>
</tr>
<tr>
<td valign="top">

`workzone.group.filter`

</td>
<td valign="top">

When specified, only those SAP Build Work Zone, advanced edition groups matching the filter expression will be read.

**Possible values:**

For example: *displayName eq "ProjectTeam1"*

**System Role:** Source

</td>
<td valign="top">

SAP Build Work Zone, advanced edition

</td>
</tr>
<tr>
<td valign="top">

`workzone.content.type`

</td>
<td valign="top">

This property makes a SAP Build Work Zone, advanced edition connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP Build Work Zone, advanced edition could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Build Work Zone, advanced edition

</td>
</tr>
<tr>
<td valign="top">

`workzone.support.patch.operation`

</td>
<td valign="top">

The default value of this property is *false*. But for SAP Build Work Zone, advanced edition proxy systems, this property appears during creation and its predefined value is *true*. That means, when the Identity Provisioning identifies a changed entity in the back-end system, it will execute the updates as `PATCH` requests instead of `PUT`. That is, only changes will be written in SAP Build Work Zone, advanced edition, instead of provisioning the whole entity data.

**Additional Information:**

There are different cases when an entity should be updated in the target system:

-   In the source system, some of the entity attributes have been changed, or new attributes have been added.

-   In the source system, a condition or a filter is set for this entity not to be read anymore.

-   The whole entity has been deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value for proxy systems: *true* 

Default value for target systems: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Build Work Zone, advanced edition

</td>
</tr>
<tr>
<td valign="top">

`workzone.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Build Work Zone, advanced edition. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*
-   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Build Work Zone, advanced edition

</td>
</tr>
<tr>
<td valign="top">

`workzone.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists on the SAP Build Work Zone, advanced edition target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

**Possible values:**

Default value \(when not specified\): *displayName*

If the property is not specified, the search is done by the default attribute: `displayName`

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Build Work Zone, advanced edition

</td>
</tr>
<tr>
<td valign="top">

`fsm.group.filter`

</td>
<td valign="top">

When specified, only those SAP Field Service Management groups matching the filter expression will be read.

**Possible values:**

For example: *displayName eq "ProjectTeam1"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Field Service Management

</td>
</tr>
<tr>
<td valign="top">

`fsm.user.filter`

</td>
<td valign="top">

When specified, only those SAP Field Service Management users matching the filter expression will be read.

**Possible values:**

For example: *userName eq "SmithJ"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Field Service Management

</td>
</tr>
<tr>
<td valign="top">

`fsm.content.type`

</td>
<td valign="top">

This property makes the SAP Field Service Management connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP Field Service Management could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Field Service Management

</td>
</tr>
<tr>
<td valign="top">

`fsm.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists in the SAP Field Service Management target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

**Possible values:**

Default value \(when not specified\): *displayName*

If the property is not specified, the search is done by the default attribute: `displayName`.

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Field Service Management

</td>
</tr>
<tr>
<td valign="top">

`fsm.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP Field Service Management connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Field Service Management system for entity versioning.

**Possible values:**

-   *true*

-   *false*


Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Field Service Management

</td>
</tr>
<tr>
<td valign="top">

`fsm.support.patch.operation`

</td>
<td valign="top">

The default value of this property is *false*. But for SAP Field Service Management proxy systems, this property appears during creation and its predefined value is *true*. That means, when the Identity Provisioning identifies a changed entity in the back-end system, it will execute the updates as `PATCH` requests instead of `PUT`. That is, only changes will be written in SAP Field Service Management, instead of provisioning the whole entity data.

Note that only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated. For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

**Possible values:**

Default value: *false*

Predefined value \(during system creation\): *true*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Field Service Management

</td>
</tr>
<tr>
<td valign="top">

`fsm.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Field Service Management. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Field Service Management

</td>
</tr>
<tr>
<td valign="top">

`ias.api.version`

</td>
<td valign="top">

Defines the version of Identity Authentication SCIM API.

**Possible values:**

-   *1* - Identity Authentication SCIM API is used.

-   *2* - Identity Directory SCIM API is used.


Default value: *2*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

Identity Authentication

</td>
</tr>
<tr>
<td valign="top">

`ias.user.filter`

</td>
<td valign="top">

This property filters users by attributes from the SCIM core schema, the Enterprise user resource schema and the Custom defined schema. For example: `userName`, `emails.value`, `addresses.country`, `employeeNumber`, `costCenter`, `department` and others.

For more information on the attributes defined in the SCIM core schema and the Enterprise user resource schema, see [Identity Directory Service Schema View](https://api.sap.com/api/IdDS_SCIM/schema)

You can set a single attribute or multiple ones as search criteria in the following value pattern:

Single attribute:*<user\_attribute\> eq "<value\>"*

Multiple attributes: *<user\_attribute1\> eq "<value1\>" and/or <user\_attribute2\> eq "<value2\>"*

**Possible values:**

For example:

-   Single attribute:*userName eq "Sebastian"*

-   Multiple attributes \(with `OR`\): *userName eq "Sebastian" or addresses.country eq "France"*

-   Multiple attributes \(with `AND`\): *userName eq "Sebastian" and addresses.country eq "France"*

-   Multiple attributes \(with brackets\): *userName eq "Sebastian" or \(addresses.country eq "France" and emails.value eq "sebastian123@mail.com"\)*

-   Multiple attributes \(enterprise attributes\):*urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department eq "Dev" and urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization eq "Technology"*


**System Role:** Source, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.group.filter`

</td>
<td valign="top">

This property filters groups by display name.

You can set a single display name or multiple ones as filter criteria. If you enter multiple display names \(using `OR` operator\), the filter will search for any of them.

Single attribute: *displayName eq "<group\_name\>"*

Multiple attributes: *displayName eq "<group\_name1\>" or displayName eq "<group\_name2\>"*

**Possible values:**

For example:

-   Single attribute:*displayName eq "FellowshipTeam1"* 

-   Multiple attributes: *displayName eq "FellowshipTeam1" or displayName eq "JuniorTest3"*


**System Role:** Source, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.support.patch.operation`

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with "scope": "createEntity", such as:

    ```
    {
       "constant":true,
       "targetPath":"$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
       "scope":"createEntity"
    }
    ```

-   If set to *false*, Identity Provisioning sends a `PUT` request to the user or group resource in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


Users and groups can be updated in the target system in various cases, such as:

-   In the source system, some user or group attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users or groups not to be read anymore.

-   A user or a group is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.user.groups.paging.enabled`

</td>
<td valign="top">

This property enables paging of user’s groups.

The maximum number of user’s groups returned per request is 1000. To read more than 1000 user’s groups, paging must be enabled.

**Possible values:**

-   *true* - Paging is enabled. You can read more than 1000 user’s groups in one request.

-   *false* - Paging is disabled. You can read up to 1000 user’s groups in one request.


Default value: *false*

**System Role:** Source, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.group.members.paging.enabled`

</td>
<td valign="top">

This property enables paging of group members.

The maximum number of group members returned per request is 20 000. To read more than 20 000 group members, paging must be enabled.

**Possible values:**

-   *true* - Paging is enabled. You can read more than 20 000 group members in one request.

-   *false* - Paging is disabled. You can read up to 20 000 group members in one request.


Default value: *false*

**System Role:** Source, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by a SCIM system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.user.unique.attribute`

</td>
<td valign="top">

When Identity Provisioning attempts to provision a user for the first time, it may detect that this user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user will be searched and resolved. **If the service finds a user on the target system via this filter, then the conflicting user will overwrite the existing one.** If the service does not find a user on the target system via this filter, the creation will fail.

According to your use case and system type, choose how to set up this property:

-   Default behavior: This property is set during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *phoneNumbers\[0\].value*. If the service finds an existing user with such *phoneNumber*, it updates this user with the data of the conflicting one. If a user with such *phoneNumber* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName, phoneNumbers\[0\].value*. If the service finds an existing user with both these *userName* and *phoneNumber*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

-   Value = *userName, emails\[0\].value, phoneNumbers\[0\].value*. If the service finds an existing user with these *userName*, *email* and *phoneNumber*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


**Possible values:**

-   *userName*

-   *emails\[0\].value*

-   *userName,emails\[0\].value*

-   *phoneNumbers\[0\].value*

-   *userName, phoneNumbers\[0\].value*

-   *userName, emails\[0\].value, phoneNumbers\[0\].value*

-   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes


Default value: *userName* 

**System Role:** Target, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.group.unique.attribute`

</td>
<td valign="top">

If you try to provision a group that already exists in a target system, the group creation will fail. In this case, the existing group only needs to be updated.

This property defines by which unique attribute\(s\) the existing group will be searched and resolved. The default value is *displayName*. Currently, it is the only unique attribute that is supported. When set, you can expect the following behavior:

-   If a group with the given *displayName* is found in the target system, the group that you try to provision will overwrite the existing one.

-   If a group with the given *displayName* is not found in the target system, the group that you try to provision will not be created in the target system.


**Possible values:**

If the property is not specified, the search is done by the default attribute: `displayName`

**System Role:** Target, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.content.type`

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

Identity Authentication \(SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`aad.user.filter.group.filter.combine`

</td>
<td valign="top">

Filters Microsoft Entra ID users based on their group assignments.

When set to *true*, this property combines user and group filters defined on the `aad.user.filter` and `aad.group.filter` properties to further narrow the search results. This way, only users that meet the following filtering criteria are returned:

-   Users that match the user filter and at the same time are members of groups that match the group filter.

-   Members of the filtered groups that match the user filter.


> ### Note:  
> To make the `aad.user.filter.group.filter.combine` property work, ensure that both user and group entities are read, that is, neither of them is ignored in the transformation code.

> ### Example:  
> 1.  You have the following users, located in two cities with one or more assigned groups:
> 
>     **User**: David Thompson from London with assigned **Groups**: Marketing and Sales
> 
>     **User**: Julie Armstrong from New York with assigned **Groups**: Employee
> 
>     **User**: John Smith from New York with assigned **Groups**: Marketing and Sales
> 
> 2.  You have defined the following filtering criteria:
> 
>     `aad.user.filter` = *city eq "New York"*
> 
>     `aad.group.filter` = *displayName eq “Marketing”*
> 
>     `aad.user.filter.group.filter.combine` = *true*
> 
> 3.  You get the following result: Only user John Smith is returned as it matches the user filter and at the same time is a member of the group that matches the group filter.
> 
>     Although David Thompson matches the group filter, he doesn’t match the user filter. Although Julie Armstrong matches the user filter, shed doesn’t match the group filter.

When set to *false*, user and group filters are not combined.

For more information, see: [Identity Provisioning: How to Get Users Based on Group Assignments from MS Entra ID](https://blogs.sap.com/2021/09/28/identity-provisioning-how-to-get-users-based-on-group-assignments-from-ms-azure-ad/)

**Possible values:**

-   *true*

    When this property is set to **true**, it is expected that filtering criteria are defined for `aad.user.filter` and `aad.group.filter` properties. If one or both are not defined in the UI, be aware of the following behavior:

    -   Only `aad.user.filter` is defined: Users that match the user filter and are members of any group will be returned. If a user matches the user filter but is not a member of any group, this user will not be returned.

    -   Only `aad.group.filter` is defined: Users that are members of the groups matching the group filter will be returned.

    -   None of the properties are defined: Users that are members of any group will be returned.


    When this property is set to *true* and filtering criteria are defined for `aad.user.filter` and `aad.group.filter` properties, if you are searching for a specific user or group using Identity Provisioning service API, be aware of the following behavior:

    -   When searching for specific user with `GET .../Users/UserId` request, filtering criteria defined on both properties are not considered. The user is returned with all the groups he or she is a member of.

    -   When searching for specific group with `GET ...Groups/GroupId` request, filtering criteria defined on both properties are not considered. The group is returned with all its group members.


-   *false* - default value


**System Role**: Source, Proxy

</td>
<td valign="top">

Microsoft Entra ID

</td>
</tr>
<tr>
<td valign="top">

`s4hana.pp.user.filter`

</td>
<td valign="top">

When specified, only those SAP S/4HANA for procurement planning users matching the filter expression will be read.

**Possible values:**

Example: *name.familyName eq "Smith" and addresses.country eq "US"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP S/4HANA for procurement planning

</td>
</tr>
<tr>
<td valign="top">

`s4hana.pp.content.type`

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:**Target, Proxy

</td>
<td valign="top">

SAP S/4HANA for procurement planning

</td>
</tr>
<tr>
<td valign="top">

`s4hana.pp.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by a SCIM system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP S/4HANA for procurement planning

</td>
</tr>
<tr>
<td valign="top">

`s4hana.pp.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). **If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one.** If the service does not find such a user, the creation will fail.

According to your use case and system type, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*
-   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes

Default value: *userName*

**System Role:** Target

</td>
<td valign="top">

SAP S/4HANA for procurement planning

</td>
</tr>
<tr>
<td valign="top">

`ias.user.automatic.conflict.resolution`

</td>
<td valign="top">

Controls whether automatic conflict resolution is switched on or off in Identity Authentication \(target system\) when provisioning is triggered from source systems containing different users with the same user identifiers \(IDs\).

For example, when SAP SuccessFactors and SAP SuccessFactors Learning are configured as source systems for provisioning users to Identity Authentication, it could happen that different SAP SuccessFactors and SAP SuccessFactors Learning users have the same user IDs. In this case, when the first user is created in Identity Authentication, after triggering a provisioning job, the second \(conflicting\) user will either overwrite the already existing one \(automatic conflict resolution is switched on\) or will fail and won't be created \(automatic conflict resolution is switched off\).

To control this behavior, you can use the `ias.user.automatic.conflict.resolution` property in the target Identity Authentication system. This property is not added by default.

**Possible values:**

-   *true* - If the property is set to true, or is not set at all, the automatic conflict resolution is switched on. This means that Identity Provisioning takes into account the unique attribute\(s\) defined on the `scim.user.unique.attribute` property \(when using SCIM API version 1\) or `ias.user.unique.attribute` property \(when using SCIM API version 2\) and tries to find an already existing user in Identity Authentication matching these attributes.

    -   If a user is found, the provisioning of a new \(conflicting\) user is resolved as follows: the conflicting user overwrites the existing one.

    -   If a user is not found, the provisioning of a conflicting user fails, and it is not created in Identity Authentication.


-   *false* - If the property is set to false, the automatic conflict resolution is switched off. This means that Identity Provisioning does not take into account the unique attribute\(s\) defined on the `scim.user.unique.attribute` property \(when using SCIM API version 1\) or `ias.user.unique.attribute` property \(when using SCIM API version 2\) and fails the provisioning of a conflicting user. This user is not created in Identity Authentication and does not overwrite the existing one.

    In the Job Log, an error code ***409, uniqueness*** will be displayed.


Default value: *true*

**System Role:** Target

</td>
<td valign="top">

Identity Authentication

</td>
</tr>
<tr>
<td valign="top">

`ias.patch.group.members.above.threshold`

</td>
<td valign="top">

Defines the threshold number of group members above which they are provisioned on batches with PATCH requests, and below which they are provisioned with PUT request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

> ### Note:  
> You can use this property when Identity Authentication is based on Identity Directory SCIM API \(in short, SCIM API version 2\).

**Possible values**: integer

Default value: *20 000*

Minimum value: *1*

Maximum value: *20 000*

For example:

-   `PATCH` requests: If you have a group with 700 members and you update the group by adding another 1200 members, setting this property to 900 results in the following:

    As 1900 \(the target count of the members\) is above the threshold number of 900, 2 `PATCH` requests will be sent to the Identity Authentication target system. The first request will add 900 group members and the second request will add 300 group members.

    The threshold number you set defines the maximum number of group members processed per batch.

-   `PUT` request: If you have a group with 700 members and you update the group by adding another 100 members, setting this property to 900 results in the following:

    As 800 \(the target count of the members\) is below the threshold number of 900, 1 `PUT` request with 800 group members will be sent to the Identity Authentication target system to update the group.


> ### Note:  
> Regardless of the threshold number you define, when removing group members in Identity Authentication, the maximum number of members which can be removed per one `PATCH` request is 50.

**System Role:**Target

</td>
<td valign="top">

Identity Authentication 

</td>
</tr>
<tr>
<td valign="top">

`idds.patch.group.members.above.threshold`

</td>
<td valign="top">

Defines the threshold number of group members above which they are provisioned on batches with `PATCH` requests, and below which they are provisioned with `PUT` request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

> ### Note:  
> You can use this property when Identity Authentication and Identity Provisioning \(where Local Identity Directory is configured\), are running on the same infrastructure, that is, the infrastructure of Identity Authentication.

**Possible values**: integer

Default value: *20 000*

Minimum value: *1*

Maximum value: *200 000*

For example:

-   `PATCH` requests: If you have a group with 700 members and you update the group by adding another 1200 members, setting this property to 900 results in the following:

    As 1900 \(the target count of the members\) is above the threshold number of 900, 2 `PATCH` requests will be sent to the Local Identity Directory target system. The first request will add 900 group members and the second request will add 300 group members.

    The threshold number you set defines the maximum number of group members processed per batch.

-   `PUT` request: If you have a group with 700 members and you update the group by adding another 100 members, setting this property to 900 results in the following:

    As 800 \(the target count of the members\) is below the threshold number of 900, 1 `PUT` request with 800 group members will be sent to the Local Identity Directory target system to update the group.


> ### Note:  
> Regardless of the threshold number you define, when removing group members in Local Identity Directory, the maximum number of members which can be removed per one `PATCH` request is 50.

**System Role:** Target

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`xsuaa.patch.group.members.above.threshold`

</td>
<td valign="top">

Defines the threshold number of group members above which they are provisioned on batches with `PATCH` requests, and below which they are provisioned with `PUT` request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

**Possible values**: integer

Default value: *20 000*

Minimum value: *1*

Maximum value: *200 000*

For example:

-   `PATCH` requests: If you have a group with 700 members and you update the group by adding another 1200 members, setting this property to 900 results in the following:

    As 1900 \(the target count of the members\) is above the threshold number of 900, 2 `PATCH` requests will be sent to the XSUAA target system. The first request will add 900 group members and the second request will add 300 group members.

    The threshold number you set defines the maximum number of group members processed per batch.

-   `PUT` request: If you have a group with 700 members and you update the group by adding another 100 members, setting this property to 900 results in the following:

    As 800 \(the target count of the members\) is below the threshold number of 900, 1 `PUT` request with 800 group members will be sent to the XSUAA target system to update the group.


**System Role:** Target

</td>
<td valign="top">

SAP BTP XS Advanced UAA \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`ias.user.update.instead.delete`

</td>
<td valign="top">

When using SCIM API version 2, this property allows you to update user attributes with `PATCH` request in Identity Authentication target system and to preserve the user record instead of deleting it. This behavior is supported only when the scope of the attribute is set to **deleteEntity**.

In addition to configuring this property, you also need to adapt the write transformation. For example, if you want to disable a user account in Identity Authentication, you need to do the following:

1.  Set `ias.user.update.instead.delete`=*true*

2.  Adapt the write transformation as follows:

    ```
    {
       "user":{
          "mappings":[
             {
                "constant":"urn:ietf:params:scim:api:messages:2.0:PatchOp",
                "targetPath":"$.schemas[0]",
                "scope":"deleteEntity"
             },
             {
                "constant":"replace",
                "targetPath":"$.Operations[0].op",
                "scope":"deleteEntity"
             },
             {
                "constant":"active",
                "targetPath":"$.Operations[0].path",
                "scope":"deleteEntity"
             },
             {
                "constant":false,
                "targetPath":"$.Operations[0].value",
                "scope":"deleteEntity"
             },
    ...
    
    ```


In this case, the `PATCH` operation will replace *true* with *false* as the value of the `active` user attribute. As a result, when the `PATCH` operation is executed, the user record in the target system will no longer be managed by Identity Provisioning as it is considered deleted.

For more information, see: [Transformation Expressions](transformation-expressions-bb8537b.md) → *Scope* → *deleteEntity* → *Identity Authentication \(SCIM API version 2\)*

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

When the property is set to *true*, adapt the write transformation with the attribute name and the attribute value you want to update:

```
{
   "user":{
      "mappings":[
         {
            "constant":"urn:ietf:params:scim:api:messages:2.0:PatchOp",
            "targetPath":"$.schemas[0]",
            "scope":"deleteEntity"
         },
         {
            "constant":"replace",
            "targetPath":"$.Operations[0].op",
            "scope":"deleteEntity"
         },
         {
            "constant":"<attribute_name>",
            "targetPath":"$.Operations[0].path",
            "scope":"deleteEntity"
         },
         {
            "constant":<attribute_value>,
            "targetPath":"$.Operations[0].value",
            "scope":"deleteEntity"
         },
...

```

**System Role:** Target

</td>
<td valign="top">

Identity Authentication 

</td>
</tr>
<tr>
<td valign="top">

`lms.user.filter`

</td>
<td valign="top">

When specified, only those users matching the filter expression will be read.

**Possible values:**

-   *userName eq "testName"*

-   *externalID eq "testID"*

-   *active eq "true"*

-   *sourceSystem eq "Learning"* - indicates that the user is created directly in SAP SuccessFactors Learning with no involvement of Identity Provisioning.

-   *sourceSystem eq "Identity Provisioning"* - indicates that the user is created in SAP SuccessFactors Learning by Identity Provisioning.


**System Role:** Source

</td>
<td valign="top">

SAP SuccessFactors Learning

</td>
</tr>
<tr>
<td valign="top">

`lms.content.type`

</td>
<td valign="top">

This property makes the SAP SuccessFactors Learning connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP SuccessFactors Learning could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors Learning

</td>
</tr>
<tr>
<td valign="top">

`lms.user.unique.attribute`

</td>
<td valign="top">

When Identity Provisioning attempts to provision a user for the first time, it may detect that such user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). If the service finds such user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find such a user, the creation will fail.

**Default behavior**: The property is missing during system creation. Its default value is *userName*. This means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such *userName* is not found, the creation of the conflicting user fails.

**Possible values:**

Default value: *userName*

**System Role:** Target

</td>
<td valign="top">

SAP SuccessFactors Learning

</td>
</tr>
<tr>
<td valign="top">

`lms.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by a SCIM system for entity versioning.

**Possible values:**

-   *true*

-   *false*


**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors Learning

</td>
</tr>
<tr>
<td valign="top">

`lms.support.patch.operation`

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP SuccessFactors Learning

</td>
</tr>
<tr>
<td valign="top">

`lms.instance.host`

</td>
<td valign="top">

Enter the host of your SAP SuccessFactors Learning instance.

This property must be configured if you what to use client certificate authentication for the communication between Identity Provisioning and SAP SuccessFactors Learning.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors Learning

</td>
</tr>
<tr>
<td valign="top">

`ias.support.bulk.operation`

</td>
<td valign="top">

This property enables bulk operations for users and groups.

When bulk operations are enabled, Identity Provisioning creates, updates, and deletes multiple users and groups in one request.

When bulk operations are not enabled, Identity Provisioning creates, updates, and deletes one user at a time.

For more information, see: [Identity Directory SCIM API](https://api.sap.com/api/IdDS_SCIM/resource).

**Possible values:**

-   *true* - bulk operations are enabled

-   *false* - bulk operations are not enabled


Default value: *false*

**System Role:** Target

</td>
<td valign="top">

Identity Authentication \(using SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`ias.bulk.operations.max.count`

</td>
<td valign="top">

This property sets the number of operations to be performed in one bulk request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, Identity Provisioning will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

Identity Authentication \(using SCIM API version 2\)

</td>
</tr>
<tr>
<td valign="top">

`idds.support.bulk.operation`

</td>
<td valign="top">

This property enables bulk operations for users and groups.

When bulk operations are enabled, Identity Provisioning creates, updates, and deletes multiple users and groups in one request.

When bulk operations are not enabled, Identity Provisioning creates, updates, and deletes one user at a time.

For more information, see: [Identity Directory SCIM API](https://api.sap.com/api/IdDS_SCIM/resource).

**Possible values:**

-   *true* - bulk operations are enabled

-   *false* - bulk operations are not enabled


Default value: *false*

**System Role:** Target

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`idds.bulk.operations.max.count`

</td>
<td valign="top">

This property sets the number of operations to be performed in one bulk request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, Identity Provisioning will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

Local Identity Directory

</td>
</tr>
<tr>
<td valign="top">

`concur.user.filter`

</td>
<td valign="top">

When specified, only those users matching the filter expression will be read.

**Possible values:**

For example:

-   *userName eq "johnsmith@example.com"* 

    As the userName must be unique across SAP Concur, this filter returns only the user matching this userName.

-   *companyId eq "aa067ada-71a9-4f57-8e98-9300b1c3171d"* 

    This filter returns all users in the company with this companyId.

-   *externalId eq "0fe44868-31a7-4930-9ah30-757tg2513b64"* 

    This filter returns a user with the specified value, that is, the userUUID generated for the user in Identity Authentication.

-   *employeeNumber eq "Concur Administrator"*

    This filter returns a user with the specified employee number. The employeeNumber could also be a number having six or more digits.


**System Role:** Source

</td>
<td valign="top">

SAP Concur \(using SAP Concur Identity v4 API\)

</td>
</tr>
<tr>
<td valign="top">

`concur.content.type`

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Concur \(using SAP Concur Identity v4 API\)

</td>
</tr>
<tr>
<td valign="top">

`concur.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by a SCIM system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Concur \(using SAP Concur Identity v4 API\)

</td>
</tr>
<tr>
<td valign="top">

`concur.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). **If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one.** If the service does not find such a user, the creation will fail.

According to your use case and system type, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*
-   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes

Default value: *userName*

**System Role:** Target

</td>
<td valign="top">

SAP Concur \(using SAP Concur Identity v4 API\)

</td>
</tr>
<tr>
<td valign="top">

`concur.datacenter`

</td>
<td valign="top">

The SAP Concur data center your Identity Provisioning tenant belongs to.

Based on the provided data center, Identity Provisioning configures the URL of the User Provisioning Service \(UPS\) v4 API or the SAP Concur Identity v4 API.

For example, if you provide `us1`, the service will configure the URL in the following pattern: `us.api.concursolutions.com`.

**Possible values:**

The following SAP Concur data centers are available:

-   *us1*
-   *us2*
-   *eu1*
-   *eu2*
-   *emea*
-   *cn1*
-   *usg*
-   *int*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Concur

</td>
</tr>
<tr>
<td valign="top">

`concur.api.version`

</td>
<td valign="top">

Defines the version of SAP Concur API.

**Possible values:**

-   *1* - SAP Concur User Provisioning Service \(UPS\) v4 API is used.

-   *2* - SAP Concur Identity v4 API \(SCIM API\) is used.


Default value: *2*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Concur

</td>
</tr>
<tr>
<td valign="top">

`concur.authorization.code`

</td>
<td valign="top">

\(Credential\)

Enter the *Company Request Token* and run a provisioning job within 24 hours from generating the token in the SAP Concur Company Request Token self-service tool. Otherwise, the token will expire, and you’ll need a new one.

After the first run of the job, Identity Provisioning fills in automatically a refresh token as the value of the concur.refresh.token property. If a provisioning job has not been run for six months, you’ll again need to generate a new token.

> ### Remember:  
> The company request token has a 24 hour validity. If this token expires, you must request a new token.
> 
> The refresh token has a six month validity. Every time you run a provisioning job, the validity of the refresh token is extended with six months starting from the date of the last run. If you haven't run a provisioning job for six months, your refresh token will expire and you must request a new company request token.

The Company Request Token is generated in the SAP Concur Company Request Token self-service tool.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Concur

</td>
</tr>
<tr>
<td valign="top">

`concur.company.id`

</td>
<td valign="top">

Your company UUID

The Company ID is generated in the SAP Concur Company Request Token self-service tool.

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Concur

</td>
</tr>
<tr>
<td valign="top">

`concur.company.domain`

</td>
<td valign="top">

Your company domain

The username and the company domain are concatenated in the SAP Concur default transformations in the following format: user@domain

Your company domain is the part of your username behind the @ symbol. For example:*johnsmith@example.com*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Concur

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.patch.group.members.of.nested.groups`

</td>
<td valign="top">

If you set this property to *true*, Identity Provisioning will update only user members of a group in SAP Ariba Applications target system. The update will be executed on batches via PATCH requests. This will preserve the group hierarchy with nested groups in the SAP Ariba Applications backend.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`ariba.applications.patch.group.members.above.threshold`

</td>
<td valign="top">

This property is relevant only when `ariba.applications.patch.group.members.of.nested.groups` is set to *true*.

It defines the maximum number of user members of a group that are included in one PATCH request. If the maximum value of 200 000 is exceeded, the system sets automatically the default value.

**Possible values**: integer

Default value: *20 000*

Minimum value: *1*

Maximum value: *200 000*

**System Role:** Target

</td>
<td valign="top">

SAP Ariba Applications

</td>
</tr>
<tr>
<td valign="top">

`cflp.providerId`

</td>
<td valign="top">

Your SAP Build Work Zone, standard edition provider ID

The provider ID is specified in the Channel Manager of theSAP Build Work Zone, standard edition when defining a new content provider. For more information about configuring the content provider to use the Identity Provisioning service, see [Configure Integration with the Identity Provisioning Service](https://help.sap.com/docs/Launchpad_Service/8c8e1958338140699bd4811b37b82ece/1c231333f1d24ae0a8e60ce688c4f692.html)

**Possible values:**

The value of your SAP Build Work Zone, standard edition provider ID

For example: *ABC123*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`cflp.user.filter`

</td>
<td valign="top">

When specified, only those SAP Build Work Zone, standard edition users matching the filter expression will be read.

By default, users are always filtered by the *providerId*. If another filtering attribute is defined, for example the email of the user, both filters are combined.

**Possible values:**

-   *emails.value eq 'john.smith@example.com'*

    > ### Note:  
    > Although, the email is supported as a filtering attribute, it is not returned when searching for the user.

-   *urn:ietf:params:scim:schemas:extension:2.0:mapping.providerId eq 'ABC123'*


**System Role:** Proxy

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`cflp.group.filter`

</td>
<td valign="top">

When specified, only those SAP Build Work Zone, standard edition groups matching the filter expression will be read. By default, groups are always filtered by the *providerId*.

**Possible values:**

-   *externalId eq 12345678*

-   *urn:ietf:params:scim:schemas:extension:2.0:mapping.providerId eq 'ABC123'*

-   *meta.isIAG eq true*

    This filtering attribute indicates whether the group will be used in a hybrid scenario with SAP Cloud Identity Access Governance.


**System Role:** Proxy

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`cflp.user.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a user that already exists in the target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

**Possible values:**

SAP Build Work Zone, standard edition supports the following unique attributes which are automatically filled in when the target system is added in the service UI:

`emails[0].value,['urn:ietf:params:scim:schemas:extension:2.0:mapping']['providerId'],externalId`

-   If the user has an `externalId`, the conflict is resolved by `externalId` and `providerId`.

-   If the user doesn't have an `externalId`, the conflict is resolved by `email` and `providerId`.


For the conflict to be resolved, an existing user matching both unique attributes should be found.

Whether the existing user will be updated or a new one will be created by Identity Provisioning depends on the following conditions - was the user created by the Identity Provisioning service, what combination of unique attributes exist for the user, and has any of the provisioning systems \(source or target\) been reset. For more information, see Step 4 of the relevant SAP Build Work Zone, standard edition documentation.

> ### Recommendation:  
> We recommend that you do not modify the value of the `cflp.user.unique.attribute` property. Otherwise, user creation fails.

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`cflp.group.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a group that already exists in the target system \(a conflicting group\), this property defines the unique attributes by which the existing group will be searched and resolved.

**Possible values:**

SAP Build Work Zone, standard edition supports a pair of unique attributes which is automatically filled in when the target system is added in the service UI:

*externalId,\['urn:ietf:params:scim:schemas:extension:2.0:mapping'\]\['providerId'\]*

For the conflict to be resolved, an existing group matching both unique attributes should be found. In this case, Identity Provisioning updates the group. This means, the conflicting group overwrites the existing one. If the group matches only one of the unique attributes, the conflict is not resolved, and the group creation fails.

> ### Recommendation:  
> We recommend that you do not modify the value of the `cflp.group.unique.attribute` property. Otherwise, the group creation fails.

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`cflp.patch.group.members.above.threshold`

</td>
<td valign="top">

Defines the threshold number of group members above which they are provisioned on batches with `PATCH` requests, and below which they are provisioned with `PUT` request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

**Possible values:** integer

Default and maximum value: *5000*

Minimum value: *1*

For example:

-   `PATCH` requests: If you have a group with 700 members and you update the group by adding another 1200 members, setting this property to 900 results in the following:

    As 1900 \(the target count of the members\) is above the threshold number of 900, 2 `PATCH` requests will be sent to the SAP Build Work Zone, standard edition target system. The first request will add 900 group members and the second request will add 300 group members.

    The threshold number you set defines the maximum number of group members processed per batch.

-   `PUT` request: If you have a group with 700 members and you update the group by adding another 100 members, setting this property to 900 results in the following:

    As 800 \(the target count of the members\) is below the threshold number of 900, 1 `PUT` request with 800 group members will be sent to the SAP Build Work Zone, standard edition target system to update the group.


> ### Note:  
> If the maximum value of 5 000 is exceeded, the system will automatically use the default value.

**System Role:** Target

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`cflp.support.bulk.operation`

</td>
<td valign="top">

This property enables bulk operations for users and groups.

When the property is enabled \(set to *true*\), the following operations can be executed by Identity Provisioning service in a single request:

-   Create or delete multiple users

-   Create, update, or delete multiple groups


When the property is disabled \(set to *false*\), the following operations can be executed by Identity Provisioning service for a single entity at a time:

-   Create or delete a user

-   Create, update, or delete a group


**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`cflp.bulk.operations.max.count`

</td>
<td valign="top">

This property sets the number of operations to be performed in one bulk request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, the service will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`xsuaa.user.unique.attribute`

</td>
<td valign="top">

When Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find such a user, the creation will fail.

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.

-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both attributes: *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

-   Value = *userName,origin*. If the service finds an existing user with both attributes: *userName* and *origin*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*
-   *userName,origin*
-   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes

Default value: *userName*

**System Role:** Target

</td>
<td valign="top">

SAP BTP XS Advanced UAA \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`fsm.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP Field Service Management groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `FSM_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Field Service Management source system and will be provisioned to the target system with the following name pattern: <code>FSM_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Field Service Management groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Field Service Management groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `FSM_` prefix in their display name will be provisioned to SAP Field Service Management. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Field Service Management.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Field Service Management

</td>
</tr>
<tr>
<td valign="top">

`ips.trace.entity.content.unlimited`

</td>
<td valign="top">

This property controls the size of the `zip` archive, which you can download in the Identity Provisioning admin console to view the provisioning job logs for failed and skipped entities.

**Possible values:**

-   *true* - The amount of data in the *Content* section of the job log `zip` file is not limited.

-   *false* - The amount of data in the *Content* section of the job log `zip` file is limited to 150 000 symbols.

    This is the default value. If the property is not configured, *false* is considered by default.


To use this property, you need to set the following ones to *true*:

-   `ips.trace.skipped.entity`

-   `ips.trace.skipped.entity.content`

-   `ips.trace.failed.entity.content`


**System Role:** Source

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`sf.user.read.deactivatedafter`

</td>
<td valign="top">

This property filters SAP SuccessFactors inactive users from a particular date on. It is an optional property which does not appear by default at system creation. It accepts a value in the `yyyy-MM-dd` format. For example: `2023-07-17`

The `sf.user.read.deactivatedafter` property is supported for SAP SuccessFactors version 2 using SAP SuccessFactors Workforce SCIM API. It works together with the `sf.user.filter` property which is added at system creation with the default value: *active eq true*. Using it can further narrow down the filtering results.

To filter active users along with inactive ones from a particular date on, the following configuration must be in place:

-   Set the `sf.user.read.deactivatedafter` value to a date in the expected format. For example: *2023-07-17*

-   `sf.user.filter` = *active eq true*


As a result, Identity Provisioning reads SAP SuccessFactors active users and the users set to inactive from that date on using the 2023-07-17T00:00:00Z date-time format.

Depending on the value you define for `sf.user.filter`, expect the following results:

-   `sf.user.filter` = *active eq false*

    All inactive users will be returned.

-   `sf.user.filter` = *active eq false and userName sw "Test\_"*

    All inactive users with username starting with Test\_ will be returned.

    > ### Note:  
    > When you filter by `sf.user.filter` = *active eq false* along with the property `sf.user.read.deactivatedafter`, the users that match the two critera will be read twice.

-   `sf.user.filter` = *active eq true and userName sw "Test\_"*

    Inactive users from the provided date on and all active users with username starting with Test\_ will be returned.


**System Role:** Source, Proxy

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`cc.user.filter`

</td>
<td valign="top">

When specified, only those users matching the filter expression will be read. You can filter users by `userName`, `emails.value`, and `externalId`, according to the API syntax of SAP Commerce Cloud.

**Possible values:** text/ numeric string

For example:

-   *userName eq "johnbrown" and externalId eq "P000252"*
-   *userName eq "johnbrown" and emails.value eq "johnbrown@email.com"*
-   *userName eq "johnbrown" and emails.value eq "johnbrown@email.com" and externalId eq "P000252"*

    > ### Note:  
    > These combinations are valid for both 'or' and 'and' operators.


**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`cc.group.filter`

</td>
<td valign="top">

When specified, only those groups matching the filter expression will be read.

**Possible values:**

For example:

*displayName eq "ProjectTeam1" or "Students2018"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`cc.support.patch.operation`

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


> ### Note:  
> When executing a remove operation, all members of a group are removed without considering the number of deleted group members in the source system.

**Additional Information:**

There are different cases when an entity should be updated in the target system:

-   In the source system, some of the entity attributes have been changed, or new attributes have been added.

-   In the source system, a condition or a filter is set for this entity not to be read anymore.

-   The whole entity has been deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value for proxy systems: *true* 

Default value for target systems: *false*

**System Role:** Proxy, Target

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`cc.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP Commerce Cloud connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Commerce Cloud system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`cc.group.unique.attribute`

</td>
<td valign="top">

If you try to provision a group that already exists in a target system, the group creation will fail. In this case, the existing group only needs to be updated.

This property defines by which unique attribute\(s\) the existing group will be searched and resolved. The default value is *displayName*. Currently, it is the only unique attribute that is supported. When set, you can expect the following behavior:

-   If a group with the given *displayName* is found in the target system, the group that you try to provision will overwrite the existing one.

-   If a group with the given *displayName* is not found in the target system, the group that you try to provision will not be created in the target system.


**Possible values:**

If the property is not specified, the search is done by the default attribute: `displayName`

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`cc.user.unique.attribute`

</td>
<td valign="top">

When Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one. If the service does not find such a user, the creation will fail.

The property is automatically added during system creation. If the service finds an existing user by at least one of the uniqueness criteria, which are *email*, *userName*, or *externalId*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the update of the conflicting user fails. If more than one users with these unique attributes are found, the update fails.

**Possible values:***emails\[0\].value, userName, externalId*

Default value: *emails\[0\].value, userName, externalId*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`cc.content.type`

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`cc.patch.group.members.above.threshold`

</td>
<td valign="top">

Defines the threshold number of group members above which they are provisioned on batches with PATCH requests, and below which they are provisioned with PUT request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

> ### Note:  
> You can use this property when SAP Commerce Cloud is based on SAP Commerce Cloud SCIM API \(in short, SCIM API version 2\).

**Possible values**: integer

Default value: *20 000*

Minimum value: *1*

Maximum value: *200 000*

For example:

-   `PATCH` requests: If you have a group with 700 members and you update the group by adding another 1200 members, setting this property to 900 results in the following:

    As 1900 \(the target count of the members\) is above the threshold number of 900, 2 `PATCH` requests will be sent to the Identity Authentication target system. The first request will add 900 group members and the second request will add 300 group members.

    The threshold number you set defines the maximum number of group members processed per batch.

-   `PUT` request: If you have a group with 700 members and you update the group by adding another 100 members, setting this property to 900 results in the following:

    As 800 \(the target count of the members\) is below the threshold number of 900, 1 `PUT` request with 800 group members will be sent to the Identity Authentication target system to update the group.


> ### Note:  
> Regardless of the threshold number you define, when removing group members in SAP Commerce Cloud, the maximum number of members which can be removed per one `PATCH` request is 98.

**System Role:**Target

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`cc.patch.group.members.of.nested.groups`

</td>
<td valign="top">

If you set this property to *true*, Identity Provisioning will update only user members of a group in SAP Commerce Cloud target system. The update will be executed on batches via PATCH requests. This will preserve the group hierarchy with nested groups in the SAP Commerce Cloud backend.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target

</td>
<td valign="top">

SAP Commerce Cloud

</td>
</tr>
<tr>
<td valign="top">

`maco.roles.prefix` 

</td>
<td valign="top">

This property distinguishes SAP Market Communication for Utilities roles by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `SMC_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the roles that are read from the SAP Market Communication for Utilities source system and will be provisioned to the target system with the following name pattern: <code>SMC_<i class="varname">&lt;role_name&gt;</i></code>. This way SAP Market Communication for Utilities roles in the target system will be distinguished from roles provisioned from other applications.

    If the property is not set, the SAP Market Communication for Utilities roles will be read and provisioned to the target system with their actual role names.

-   When **set in the target system**, only roles containing the `SMC_` prefix in their role name will be provisioned to SAP Market Communication for Utilities. Roles without this prefix in the role name won't be provisioned.

    If the property is not set, all roles will be be provisioned to SAP Market Communication for Utilities.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Market Communication for Utilities 

</td>
</tr>
<tr>
<td valign="top">

`maco.user.roles.overwrite` 

</td>
<td valign="top">

This property defines whether the current roles of a user to be preserved or overwritten by the Identity Provisioning service within the SAP Market Communication for Utilities target or proxy system.

See also: [Extended Explanation of the \*user.roles.overwrite Properties](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111:29114:27412:35953:38590)

**Possible values:**

-   *true* – the current user roles will be deleted in the proxy system, and the user will be updated only with the roles provisioned by the service.
-   *false* – the current user roles will be preserved, and the new roles \(if any\) will be added for the relevant user in the proxy system.

Default value \(if the property is missing during system creation\): *true* 

Default value \(if the property appears during system creation\): *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Market Communication for Utilities 

</td>
</tr>
<tr>
<td valign="top">

`maco.roles.filter` 

</td>
<td valign="top">

Enter OData filtering for reading roles in the SAP Market Communication for Utilities system.

To learn what criteria you can use, see: [OData URI Conventions](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → 4.5 Filter System Query Option

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Market Communication for Utilities 

</td>
</tr>
<tr>
<td valign="top">

`maco.roles.page.size` 

</td>
<td valign="top">

This property indicates how many business roles \(considered as *groups*\) per page to be read from your SAP Market Communication for Utilities source system.

**Possible values:** Integer number

For example, if you set the property's value = *30*, the Identity Provisioning will read 30 roles \(groups\) at once, then – another 30, and so on.

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Market Communication for Utilities 

</td>
</tr>
<tr>
<td valign="top">

`maco.skip.read.archived` 

</td>
<td valign="top">

In the event of archived \(disabled\) entities in a source SAP Market Communication for Utilities system, you can choose whether the provisioning jobs to continue reading such entities or to skip them.

In the source systems, this property is activated by default. If you want to always read disabled entities, set the property to *false*, or delete it.

**Possible values:**

-   *true*
-   *false*

Default value: *true* 

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Market Communication for Utilities 

</td>
</tr>
<tr>
<td valign="top">

`maco.support.bulk.operation` 

</td>
<td valign="top">

Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request.

For more information, see: [APIs for Business User Management](https://help.sap.com/viewer/de55b3fdb209469397b4e1221c60b3e6/latest/en-US/65336618f50649ab944cd938ee5772be.html)

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP Market Communication for Utilities 

</td>
</tr>
<tr>
<td valign="top">

`maco.bulk.operations.max.count` 

</td>
<td valign="top">

If you have enabled the bulk operations, you can use this property to set the number of users to be provisioned per request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, the service will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP Market Communication for Utilities 

</td>
</tr>
<tr>
<td valign="top">

`sf.api.version`

</td>
<td valign="top">

Handles the version of the API which is consumed by the SAP SuccessFactors system.

**Possible values:**

-   *1* - SAP SuccessFactors HCM Suite OData API \(in short, OData API\) is used.

-   *2* - SAP SuccessFactors Workforce SCIM API \(in short, SCIM API\) is used.


Default value: *1*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   SAP SuccessFactors \(using version 1 - SAP SuccessFactors HCM Suite OData API\)

-   SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)




</td>
</tr>
<tr>
<td valign="top">

`sf.company.id` 

</td>
<td valign="top">

Enter the Company ID of your SAP SuccessFactors system.

The Company ID is a short string of characters that identifies each SAP SuccessFactors system. It is like a username for your organization. All users of the same system share the same Company ID.

This property must be configured if you what to use client certificate authentication for the communication between Identity Provisioning and SAP SuccessFactors.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

-   SAP SuccessFactors \(using version 1 - SAP SuccessFactors HCM Suite OData API\)

-   SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)




</td>
</tr>
<tr>
<td valign="top">

`sf.support.patch.operation` 

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


> ### Note:  
> Updating the user attributes: `name` and `manager`, is not supported with PATCH operation.

Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.include.if.match.wildcard.header` 

</td>
<td valign="top">

Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by a SCIM system for entity versioning.

**Possible values:**

-   *true*

-   *false*


**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.group.unique.attribute` 

</td>
<td valign="top">

If the service tries to create a group that already exists in the target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\).

To make the search filter by a specific attribute, specify this attribute as a value for the `sf.group.unique.attribute` property.

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.user.unique.attribute` 

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists on the target system. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\).

This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\). **If the service finds such a user on the target system via this filter, then the conflicting user will overwrite the existing one.** If the service does not find such a user, the creation will fail.

According to your use case and system type, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*
-   *externalId*, or another SCIM attribute, or a conjunction of SCIM attributes

Default value: *userName*

**System Role:** Target

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.content.type` 

</td>
<td valign="top">

This property makes the SAP SuccessFactors connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP SuccessFactors could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors \(using version 1 - SAP SuccessFactors HCM Suite OData API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.patch.group.members.above.threshold` 

</td>
<td valign="top">

Defines the threshold number of group members above which they are provisioned on batches with `PATCH` requests, and below which they are provisioned with `PUT` request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

> ### Note:  
> You can use this property when SAP SuccessFactors is based on SAP SuccessFactors Workforce SCIM API \(in short, SCIM API\).

**Possible values**: integer

Default value: *20 000*

Minimum value: *1*

Maximum value: *200 000*

For example:

-   `PATCH` requests: If you have a group with 700 members and you update the group by adding another 1200 members, setting this property to 900 results in the following:

    As 1900 \(the target count of the members\) is above the threshold number of 900, 2 `PATCH` requests will be sent to the Local Identity Directory target system. The first request will add 900 group members and the second request will add 300 group members.

    The threshold number you set defines the maximum number of group members processed per batch.

-   `PUT` request: If you have a group with 700 members and you update the group by adding another 100 members, setting this property to 900 results in the following:

    As 800 \(the target count of the members\) is below the threshold number of 900, 1 `PUT` request with 800 group members will be sent to the Local Identity Directory target system to update the group.


**System Role:** Target

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.group.members.paging.enabled`

</td>
<td valign="top">

This property enables paging of group members.

The maximum number of group members returned per request is 100. To read more than 100 group members, paging must be enabled.

**Possible values:**

-   *true* - Paging is enabled.
-   *false* - Paging is disabled.

Default value: *true*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`sf.patch.group.members.of.nested.groups`

</td>
<td valign="top">

If you set this property to *true*, Identity Provisioning will update only user members of a group in SAP SuccessFactors target system. The update will be executed on batches via PATCH requests. This will preserve the group hierarchy with nested groups in the SAP SuccessFactors backend.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target

</td>
<td valign="top">

SAP SuccessFactors \(using version 2 - SAP SuccessFactors Workforce SCIM API\)

</td>
</tr>
<tr>
<td valign="top">

`sac.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP Analytics Cloud groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `SAC_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Analytics Cloud source system and will be provisioned to the target system with the following name pattern: <code>SAC_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Analytics Cloud groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Analytics Cloud groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `SAC_` prefix in their display name will be provisioned to SAP Analytics Cloud. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be provisioned to SAP Analytics Cloud.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`cpq.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP CPQ groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `CPQ_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP CPQ source system and will be provisioned to the target system with the following name pattern: <code>CPQ_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP CPQ groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP CPQ groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `CPQ_` prefix in their display name will be provisioned to SAP CPQ. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be provisioned to SAP CPQ.


**System Role:** Source and Target

</td>
<td valign="top">

SAP CPQ

</td>
</tr>
<tr>
<td valign="top">

`cpq.user.filter`

</td>
<td valign="top">

When specified, only those SAP CPQ users matching the filter expression will be read.

Example: **name.familyName eq "Smith" and addresses.country eq "US"**

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP CPQ

</td>
</tr>
<tr>
<td valign="top">

`scp.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP BTP Account Members \(Neo\) groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `SCP_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP BTP Account Members \(Neo\) source system and will be provisioned to the target system with the following name pattern: <code>SCP_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP BTP Account Members \(Neo\) groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP BTP Account Members \(Neo\) groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `SCP_` prefix in their display name will be provisioned to SAP BTP Account Members \(Neo\). Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be provisioned to SAP BTP Account Members \(Neo\).


**System Role:** Source and Target

</td>
<td valign="top">

SAP BTP Account Members \(Neo\)

</td>
</tr>
<tr>
<td valign="top">

`c4c.user.filter`

</td>
<td valign="top">

When specified, only those SAP Sales Cloud and SAP Service Cloud users matching the filter expression will be read.

SAP Sales Cloud and SAP Service Cloud is formerly known as SAP Cloud for Customer \(in short, C4C\).

For example:

-   userName eq "Smith"

-   email eq "test@abc.com"

-   employeeNumber eq "56789"

-   addresses.country eq "USA"


**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`c4c.group.filter`

</td>
<td valign="top">

When specified, only those SAP Sales Cloud and SAP Service Cloud groups matching the filter expression will be read.

SAP Sales Cloud and SAP Service Cloud is formerly known as SAP Cloud for Customer \(in short, C4C\).

Example: **displayName eq "ProjectTeam1"**

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`c4c.patch.group.members.above.threshold`

</td>
<td valign="top">

Defines the threshold number of group members above which they are provisioned on batches with PATCH requests, and below which they are provisioned with PUT request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

**Possible values**: integer

Default value: *1 000*

Minimum value: *1*

Maximum value: *1 000*

For example:

-   `PATCH` requests: If you have a group with 700 members and you update the group by adding another 1200 members, setting this property to 900 results in the following:

    As 1900 \(the target count of the members\) is above the threshold number of 900, 2 PATCH requests will be sent to the SAP Sales Cloud and SAP Service Cloud target system. The first request will add 900 group members and the second request will add 300 group members.

    The threshold number you set defines the maximum number of group member changes processed per batch.

-   `PUT` request: If you have a group with 1000 members and the threshold is not set or its value is above 1000, one PUT request will be sent to SAP Sales Cloud and SAP Service Cloud. But if you set the threshold to 500, 2 PATCH requests will be sent instead, each adding 500 members.


> ### Note:  
> If the maximum value of 1 000 is exceeded, the system will automatically use the default value.

**System Role:** Target

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`xsuaa.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP BTP XS Advanced UAA \(Cloud Foundry\) groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `XSUAA_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP BTP XS Advanced UAA \(Cloud Foundry\) source system and will be provisioned to the target system with the following name pattern: <code>XSUAA_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP BTP XS Advanced UAA \(Cloud Foundry\) groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP BTP XS Advanced UAA \(Cloud Foundry\) groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `XSUAA_` prefix in their display name will be provisioned to SAP BTP XS Advanced UAA \(Cloud Foundry\). Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP BTP XS Advanced UAA \(Cloud Foundry\).


**System Role:** Source and Target

</td>
<td valign="top">

SAP BTP XS Advanced UAA \(Cloud Foundry\)

</td>
</tr>
<tr>
<td valign="top">

`cflp.support.patch.operation`

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


> ### Note:  
> Updating users and groups returns 404 Not Found.

Users and groups can be updated in the target system in various cases, such as:

-   In the source system, some user or group attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users or groups not to be read anymore.

-   A user or a group is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value for proxy systems: *true*

Default value for target systems: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Build Work Zone, standard edition 

</td>
</tr>
<tr>
<td valign="top">

`sac.api.version`

</td>
<td valign="top">

Defines the version of SAP Analytics Cloud SCIM API.

**Possible values:**

-   *1* - SAP Analytics Cloud SCIM API version 1 is used.

-   *2* - SAP Analytics Cloud SCIM API version 2 is used.


Default value: *1*

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.support.patch.operation`

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

> ### Note:  
> You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

-   If set to *true*, `PATCH` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, only these changes will be provisioned and applied in the target system.

-   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.include.if.match.wildcard.header`

</td>
<td valign="top">

This property makes the SAP Analytics Cloud connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. The header could be used by an SAP Analytics Cloud system for entity versioning.

> ### Note:  
> You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists in the SAP Analytics Cloud target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

> ### Note:  
> You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

**Possible values:**

Default value: *displayName*

If the property is not specified, the search is done by the default attribute: `displayName`.

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Analytics Cloud. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.content.type`

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

> ### Note:  
> You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.user.filter`

</td>
<td valign="top">

When specified, only those SAP Analytics Cloud users matching the filter expression will be read.

> ### Note:  
> You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

**Possible values:**

For example: *userName eq "SmithJ"*

**System Role:** Source

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.group.filter`

</td>
<td valign="top">

When specified, only those SAP Analytics Cloud groups matching the filter expression will be read.

> ### Note:  
> You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

**Possible values:**

For example: *displayName eq "ProjectTeam1"*

**System Role:** Source

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.patch.group.members.above.threshold`

</td>
<td valign="top">

Defines the threshold number of group members above which they are provisioned on batches with PATCH requests, and below which they are provisioned with PUT request. Setting this property allows you to avoid timeouts when updating groups with a large number of group members.

> ### Note:  
> You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

**Possible values**: integer

Default value: *20 000*

Minimum value: *1*

Maximum value: *200 000*

For example:

-   `PATCH` requests: If you have a group with 700 members and you update the group by adding another 1200 members, setting this property to 900 results in the following:

    As 1900 \(the target count of the members\) is above the threshold number of 900, 2 `PATCH` requests will be sent to the SAP Analytics Cloud target system. The first request will add 900 group members and the second request will add 300 group members.

    The threshold number you set defines the maximum number of group members processed per batch.

-   `PUT` request: If you have a group with 700 members and you update the group by adding another 100 members, setting this property to 900 results in the following:

    As 800 \(the target count of the members\) is below the threshold number of 900, 1 `PUT` request with 800 group members will be sent to the SAP Analytics Cloud target system to update the group.


> ### Note:  
> Regardless of the threshold number you define, when removing group members in SAP Analytics Cloud, the maximum number of members which can be removed per one `PATCH` request is 98.

**System Role:** Target

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`sac.patch.group.members.of.nested.groups`

</td>
<td valign="top">

If you set this property to *true*, Identity Provisioning will update only user members of a group in SAP Analytics Cloud target system. The update will be executed on batches via PATCH requests. This will preserve the group hierarchy with nested groups in the SAP Analytics Cloud backend.

> ### Note:  
> You can use this property when SAP Analytics Cloud is based on SCIM API version 2.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target

</td>
<td valign="top">

SAP Analytics Cloud

</td>
</tr>
<tr>
<td valign="top">

`ep.user.filter`

</td>
<td valign="top">

When specified, only those SAP Enterprise Portal users matching the filter expression will be read. For more information, see [Filtering](https://help.sap.com/docs/SAP_NETWEAVER_750/44a42f8a693e4498be42434d28ff3457/ccf9fe02648c40299e39775eb54011cf.html?version=7.5.22#filtering).

</td>
<td valign="top">

SAP Enterprise Portal

</td>
</tr>
<tr>
<td valign="top">

`ep.group.filter`

</td>
<td valign="top">

When specified, only those SAP Enterprise Portal groups matching the filter expression will be read. For more information, see [Filtering](https://help.sap.com/docs/SAP_NETWEAVER_750/44a42f8a693e4498be42434d28ff3457/ccf9fe02648c40299e39775eb54011cf.html?version=7.5.22#filtering).

</td>
<td valign="top">

SAP Enterprise Portal

</td>
</tr>
<tr>
<td valign="top">

`bn.user.filter`

</td>
<td valign="top">

When specified, only those SAP Business Network users matching the filter expression will be read.

**Possible values:**

-   *userName eq "Julie Armstrong"*

-   *userName sw "J"*

-   *name.familyName eq "Armstrong"*

-   *emails eq "julie.armstrong@example.com"*


**System Role:** Source

</td>
<td valign="top">

SAP Business Network

</td>
</tr>
<tr>
<td valign="top">

`bn.group.filter`

</td>
<td valign="top">

When specified, only those SAP Business Network groups matching the filter expression will be read.

**Possible values:**

*displayName eq "Employees"*

**System Role:** Source

</td>
<td valign="top">

SAP Business Network

</td>
</tr>
<tr>
<td valign="top">

`bn.user.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a user that already exists in the target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved. The property is not added automatically at system creation.

Default value: *userName*

If the service finds an existing user by userName, it updates this user with the data of the conflicting one. If the service does not find an existing user by userName, the creation of the conflicting user fails.

**System Role**: Target, Proxy

</td>
<td valign="top">

SAP Business Network

</td>
</tr>
<tr>
<td valign="top">

`bn.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the connector send the `If-Match` HTTP header with a value of “\*” for every request to the target system. This header could be used by a SCIM system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Business Network

</td>
</tr>
<tr>
<td valign="top">

`bn.support.patch.operation`

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set `"scope": "createEntity"`.

-   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


> ### Note:  
> Updating a group by removing all its members doesn’t work. When executing a remove operation, groups must have at least one member.

Users and groups can be updated in the target system in various cases, such as:

-   In the source system, some user or group attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users or groups not to be read anymore.

-   A user or a group is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity scope` in the transformation of your target or proxy system. See:[Transformation Expressions](transformation-expressions-bb8537b.md) → *deleteEntity*.

**Possible values:**

-   *true*

-   *false*


Default value for proxy systems: *true* 

Default value for target systems: *false* 

**System Role**: Target, Proxy

</td>
<td valign="top">

SAP Business Network

</td>
</tr>
<tr>
<td valign="top">

`bn.content.type`

</td>
<td valign="top">

This property makes SAP Business Network connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP Business Network could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Business Network

</td>
</tr>
<tr>
<td valign="top">

`bn.api.key`

</td>
<td valign="top">

An API Key represents the unique key that identifies a particular application as a legitimate consumer of an API.

**System Role:**Source, Target, Proxy

</td>
<td valign="top">

SAP Business Network

</td>
</tr>
<tr>
<td valign="top">

`bn.realm.id`

</td>
<td valign="top">

The realm name is part of the URL you use to access SAP Business Network.

**System Role:**Source, Target, Proxy

</td>
<td valign="top">

SAP Business Network

</td>
</tr>
<tr>
<td valign="top">

`abap.host.timezone`

</td>
<td valign="top">

Specifies the time zone of SAP Application Server ABAP on-premise systems. The value is used for calculating the correct assignments validity in case your SAP AS ABAP and Identity Provisioning tenant are running in different time zones.

**Possible values:**

The value should be provided in the following format: `UTC+/- offset`. For example: `UTC+02:00`, `UTC-04:00`, `UTC+03:30`.

Internet Assigned Numbers Authority \(IANA\) Time Zone database format is also supported. For more information, see [RFC 6557: Procedures for Maintaining the Time Zone Database](https://www.rfc-editor.org/rfc/rfc6557.html).

**System Role:** Source

</td>
<td valign="top">

SAP Application Server ABAP

</td>
</tr>
<tr>
<td valign="top">

`pdw.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in Procurement Data Warehouse. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

Default value: **userName**

Possible values:

-   **emails\[0\].value**
-   **userName,emails\[0\].value**

> ### Note:  
> If this property is missing, or you've deleted it, and the service does not find such a *userName*, it will try again to resolve the conflicting user – by *email*. If the second attempt for resolution is unsuccessful too, the creation of the conflicting user fails.

**System Role:** Target, Proxy

</td>
<td valign="top">

Procurement Data Warehouse

</td>
</tr>
<tr>
<td valign="top">

`pdw.group.prefix`

</td>
<td valign="top">

This property distinguishes procurement data warehouse groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `PDW_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the procurement data warehouse source system and will be provisioned to the target system with the following name pattern: <code>PDW_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way procurement data warehouse groups in the target system will be distinguished from groups provisioned from other applications.

-   When **set in the target system**, only groups containing the `PDW_` prefix in their display name will be provisioned to procurement data warehouse. Groups without this prefix in the display name won't be provisioned.


If the property is not set, the procurement data warehouse groups will be read and provisioned to the target system with their actual display names.

**System Role:** Source, Target

</td>
<td valign="top">

Procurement Data Warehouse

</td>
</tr>
<tr>
<td valign="top">

`pdw.support.bulk.operation`

</td>
<td valign="top">

Set this property to *true* if you want to enable SCIM bulk operations for provisioning users. That means, the Identity Provisioning service can write, update, and delete a potentially large collection of users in a single request. For more information, see: [SCIM Protocol: Bulk Operations](https://datatracker.ietf.org/doc/html/rfc7644#section-3.7)

If not specified, the default value is *false*.

> ### Note:  
> SCIM bulk operations are not supported for provisioning groups to procurement data warehouse.

**System Role:** Target

</td>
<td valign="top">

Procurement Data Warehouse

</td>
</tr>
<tr>
<td valign="top">

`pdw.bulk.operations.max.count`

</td>
<td valign="top">

If you have enabled the SCIM bulk operations, you can use this property to set the number of users to be provisioned per request.

Default value: `20`

> ### Note:  
> The value must not exceed the number of entities defined by the procurement data warehouse system as a SCIM service provider. Otherwise, the provisioning job will fail with HTTP response code 413 \(*Request Entity Too Large*\).

**System Role:** Target

</td>
<td valign="top">

Procurement Data Warehouse

</td>
</tr>
<tr>
<td valign="top">

`pdw.user.filter`

</td>
<td valign="top">

When specified, only those procurement data warehouse users matching the filter expression will be read. For example:

-   *userName eq "Julie Armstrong"*

-   *userName sw "J"*

-   *emails eq "julie.armstrong@example.com"*


**System Role:** Source

</td>
<td valign="top">

Procurement Data Warehouse

</td>
</tr>
<tr>
<td valign="top">

`pdw.content.type`

</td>
<td valign="top">

Makes the connector send a specified value for the *Content-Type* HTTP header. This is needed because a SCIM system could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the *Content-Type* header.

**Possible values:**

For example: *application/json*

If the property is not specified, the default value is taken: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

Procurement Data Warehouse

</td>
</tr>
<tr>
<td valign="top">

`s4hana.afc.group.filter`

</td>
<td valign="top">

When specified, only those SAP Advanced Financial Closing groups matching the filter expression will be read.

Supported operators: `eq` \(equal\), `sw` \(starts with\) and `co` \(contains\)

**Possible values:**

For example: *displayName eq "Administrators"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Advanced Financial Closing

</td>
</tr>
<tr>
<td valign="top">

`s4hana.afc.user.filter`

</td>
<td valign="top">

When specified, only those SAP Advanced Financial Closing users matching the filter expression will be read.

Supported operators: `eq` \(equal\), `sw` \(starts with\) and `co` \(contains\)

**Possible values:**

For example:

-   *userName eq "Julie Armstrong"*

-   *emails eq "julie.armstrong@example.com"*

-   *name.familyName sw "A"*

-   *name.givenName co "Ju"*


**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Advanced Financial Closing

</td>
</tr>
<tr>
<td valign="top">

`s4hana.afc.content.type`

</td>
<td valign="top">

This property makes a SAP Advanced Financial Closing connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP Advanced Financial Closing could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Advanced Financial Closing

</td>
</tr>
<tr>
<td valign="top">

`s4hana.afc.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists on the SAP Advanced Financial Closing target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

**Possible values:**

Default value: *displayName*

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Advanced Financial Closing

</td>
</tr>
<tr>
<td valign="top">

`s4hana.afc.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP Advanced Financial Closing connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Advanced Financial Closing system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Advanced Financial Closing

</td>
</tr>
<tr>
<td valign="top">

`s4hana.afc.support.patch.operation`

</td>
<td valign="top">

This property controls how modified entities \(users and groups\) in the source system are updated in the target system.

-   If set to *true*, `PATCH` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, only these changes will be provisioned and applied in the target system.

-   If set to *false*, `PUT` operations are used to update users and groups in the target system. This means, for example, that if a user attribute is modified or a group member is removed from a group, all user attributes and all group attributes are replaced in the target system, instead of updating only the modified ones.


**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Advanced Financial Closing

</td>
</tr>
<tr>
<td valign="top">

`s4hana.afc.user.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a user that already exists in the SAP Advanced Financial Closing target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

According to your use case, choose how to set up this property:

-   Default behavior: This property does not appear in the UI during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[0\].value*. If the service finds an existing user with such *email*, it updates this user with the data of the conflicting one. If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[0\].value*. If the service finds an existing user with both these *userName* and *email*, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

Possible values:

-   *userName*
-   *emails\[0\].value*
-   *userName,emails\[0\].value*

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Advanced Financial Closing

</td>
</tr>
<tr>
<td valign="top">

`s4hana.afc.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP Advanced Financial Closing groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `AFC_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Advanced Financial Closing source system and will be provisioned to the target system with the following name pattern: <code>AFC_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Advanced Financial Closing groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Advanced Financial Closing groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `AFC_` prefix in their display name will be provisioned to SAP Advanced Financial Closing. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be provisioned to SAP Advanced Financial Closing.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Advanced Financial Closing

</td>
</tr>
<tr>
<td valign="top">

`s4hana.pp.group.prefix`

</td>
<td valign="top">

> ### Note:  
> SAP S/4HANA for procurement planning does not support groups. Therefore, configuring the `s4hana.pp.group.prefix` property is irrelevant.

This property distinguishes the groups of a given provisioning system by specific prefix that you provide. It is optional and does not appear by default at system creation.

-   When **set in the source system**, the prefix is prepended to the name of the groups and they are provisioned to the target system with the following name pattern: <code><i class="varname">&lt;YOUR_PREFIX&gt;</i>_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way those groups are distinguished from groups provisioned from other applications.

    If the property is not set, the groups are read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing `YOUR_PREFIX_` prefix in their display name are provisioned there. Groups without this prefix in the display name are not provisioned.

    If the property is not set, all groups are provisioned to the target system.


**System Role:** Source and Target

</td>
<td valign="top">

SAP S/4HANA for procurement planning

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

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.onprem.user.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a user that already exists in the SAP S/4HANA On-Premise target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

According to your use case, choose how to set up this property:

-   Default behavior: This property does not appear in the UI during system creation. Its default value is *personExternalID*. That means, if the service finds an existing user by a *personExternalID*, it updates this user with the data of the conflicting one.

    If a user with such а *personExternalID* is not found, the creation of the conflicting user fails.

-   Value = *emails\[0\].value*. If the service finds an existing user matching both unique attributes *email* and *personExternalID*, it updates this user with the data of the conflicting one. If the service finds an existing user matching only the *email*, the update of the existing user fails.

    If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


Possible values:

-   *personExternalID*
-   *emails\[0\].value*

Default value: *personExternalID*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP S/4HANA On-Premise

</td>
</tr>
<tr>
<td valign="top">

`ibp.user.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a user that already exists in the SAP Integrated Business Planning for Supply Chain target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

According to your use case, choose how to set up this property:

-   Default behavior: This property does not appear in the UI during system creation. Its default value is *personExternalID*. That means, if the service finds an existing user by a *personExternalID*, it updates this user with the data of the conflicting one.

    If a user with such а *personExternalID* is not found, the creation of the conflicting user fails.

-   Value = *emails\[0\].value*. If the service finds an existing user matching both unique attributes *email* and *personExternalID*, it updates this user with the data of the conflicting one. If the service finds an existing user matching only the *email*, the update of the existing user fails.

    If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


Possible values:

-   *personExternalID*
-   *emails\[0\].value*

Default value: *personExternalID*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Integrated Business Planning for Supply Chain

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

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Market Communication for Utilities

</td>
</tr>
<tr>
<td valign="top">

`marketing.cloud.user.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a user that already exists in the SAP Marketing Cloud target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

According to your use case, choose how to set up this property:

-   Default behavior: This property does not appear in the UI during system creation. Its default value is *personExternalID*. That means, if the service finds an existing user by a *personExternalID*, it updates this user with the data of the conflicting one.

    If a user with such а *personExternalID* is not found, the creation of the conflicting user fails.

-   Value = *emails\[0\].value*. If the service finds an existing user matching both unique attributes *email* and *personExternalID*, it updates this user with the data of the conflicting one. If the service finds an existing user matching only the *email*, the update of the existing user fails.

    If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


Possible values:

-   *personExternalID*
-   *emails\[0\].value*

Default value: *personExternalID*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Marketing Cloud

</td>
</tr>
<tr>
<td valign="top">

`a4c.user.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a user that already exists in the SAP BTP ABAP environment target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved.

According to your use case, choose how to set up this property:

-   Default behavior: This property does not appear in the UI during system creation. Its default value is *personExternalID*. That means, if the service finds an existing user by a *personExternalID*, it updates this user with the data of the conflicting one.

    If a user with such а *personExternalID* is not found, the creation of the conflicting user fails.

-   Value = *emails\[0\].value*. If the service finds an existing user matching both unique attributes *email* and *personExternalID*, it updates this user with the data of the conflicting one. If the service finds an existing user matching only the *email*, the update of the existing user fails.

    If a user with such *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.


Possible values:

-   *personExternalID*
-   *emails\[0\].value*

Default value: *personExternalID*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP BTP ABAP environment

</td>
</tr>
<tr>
<td valign="top">

`c4c.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP Sales Cloud and SAP Service Cloud groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `C4C_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Sales Cloud and SAP Service Cloud source system and will be provisioned to the target system with the following name pattern: <code>C4C_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Sales Cloud and SAP Service Cloud groups in the target system will be distinguished from groups provisioned from other applications.

-   When **set in the target system**, only groups containing the `C4C_` prefix in their display name will be provisioned to SAP Sales Cloud and SAP Service Cloud. Groups without this prefix in the display name won't be provisioned.


If the property is not set, the SAP Sales Cloud and SAP Service Cloud groups will be read and provisioned to the target system with their actual display names.

**System Role:** Source, Target

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

`s4hana.cloud.roles.prefix`

</td>
<td valign="top">

This property distinguishes SAP S/4HANA Cloud roles by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `S4HANA_CLOUD_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the roles that are read from the SAP S/4HANA Cloud source system and will be provisioned to the target system with the following name pattern: <code>S4HANA_CLOUD_<i class="varname">&lt;role_name&gt;</i></code>. This way SAP S/4HANA Cloud roles in the target system will be distinguished from roles provisioned from other applications.

    If the property is not set, the SAP S/4HANA Cloud roles will be read and provisioned to the target system with their actual role names.

-   When **set in the target system**, only roles containing the `S4HANA_CLOUD_` prefix in their role name will be provisioned to SAP S/4HANA Cloud. Roles without this prefix in the role name won't be provisioned.

    If the property is not set, all roles will be be provisioned to SAP S/4HANA Cloud.


**System Role:** Source and Target

</td>
<td valign="top">

SAP S/4HANA Cloud

</td>
</tr>
<tr>
<td valign="top">

`ips.delete.threshold.users`

</td>
<td valign="top">

Use this property to control the number of users to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of users, for example by adding a filter or condition. For more information, see [Thresholds Prevent Unintended Deletion of Users when Provisioning with SAP Cloud Identity Services](https://community.sap.com/t5/technology-blogs-by-sap/thresholds-prevent-unintended-deletion-of-users-when-provisioning-with-sap/ba-p/13584176).

The property is optional and is defined on the target systems only. It is not added at system creation. Its value must be greater than "0".

Controlling the deletion works as follows:

1.  You add the `ips.delete.threshold.users` property on the target system before running a job and define a threshold value, for example: *500*.

2.  You run a read or resync job that is expected to delete a huge number of users.


As a result, expect the following behavior:

-   If the number of the users to be deleted is lower or equal \(for example: *400* or *500*\) to the defined threshold value of *500*, Identity Provisioning continues with the deletion.

-   If the number of the users to be deleted is greater \(for example: *1000*\) than the defined threshold value of *500*, Identity Provisioning does not delete any users. Instead, the service marks the expected to be deleted users as failed in the job statistics. An error message in the job logs explains that users cannot be deleted as the defined threshold is exceeded.


**System Role:** Target

</td>
<td valign="top">

All systems

</td>
</tr>
<tr>
<td valign="top">

`ips.delete.threshold.groups`

</td>
<td valign="top">

Use this property to control the number of groups or group assignments to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of groups or group assignments, for example by adding a filter or condition. For more information, see [Thresholds Prevent Unintended Deletion of Users when Provisioning with SAP Cloud Identity Services](https://community.sap.com/t5/technology-blogs-by-sap/thresholds-prevent-unintended-deletion-of-users-when-provisioning-with-sap/ba-p/13584176).

The property is optional and is defined on the target systems only. It is not added at system creation. Its value must be greater than "0".

Controlling the deletion works as follows:

1.  You add the `ips.delete.threshold.groups` property on the target system before running a job and define a threshold value, for example: *500*.

2.  You run a read or resync job that is expected to delete a huge number of groups.


As a result, expect the following behavior:

-   If the number of the groups to be deleted is lower or equal \(for example: *400* or *500*\) to the defined threshold value of *500*, Identity Provisioning continues with the deletion.

-   If the number of the groups to be deleted is greater \(for example: *1000*\) than the defined threshold value of *500*, Identity Provisioning does not delete any groups. Instead, the service marks the expected to be deleted groups as failed in the job statistics. An error message in the job logs explains that groups cannot be deleted as the defined threshold is exceeded.


**System Role:** Target

</td>
<td valign="top">

-   Identity Authentication

-   Local Identity Directory

-   SAP Advanced Financial Closing

-   SAP Advanced Workflow

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP BTP Account Members \(Neo\)

-   SAP BTP Java/HTML5 apps \(Neo\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Build Work Zone, advanced edition

-   SAP Build Work Zone, standard edition

-   SAP Business Network

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP SuccessFactors Incentive Management

-   SAP Concur

-   SAP CPQ

-   SAP Data Custodian

-   SAP Document Center

-   SAP Fieldglass

-   SAP Field Service Management

-   SAP HANA Database \(Beta\)

-   SAP Jam Collaboration

-   SAP S/4HANA for procurement planning

-   SAP Sales Cloud and SAP Service Cloud

-   SAP SuccessFactors

-   SAP SuccessFactors Learning

-   Sales Cloud – Analytics & AI

-   Cloud Foundry UAA Server

-   Google G Suite

-   LDAP Server

-   Microsoft Active Directory

-   Microsoft Entra ID

-   SCIM System

-   SSH Server \(Beta\)




</td>
</tr>
<tr>
<td valign="top">

`ips.delete.threshold.roles`

</td>
<td valign="top">

Use this property to control the number of roles or user assignments of a role to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of roles or user assignments of a role, for example by adding a filter or condition. For more information, see [Thresholds Prevent Unintended Deletion of Users when Provisioning with SAP Cloud Identity Services](https://community.sap.com/t5/technology-blogs-by-sap/thresholds-prevent-unintended-deletion-of-users-when-provisioning-with-sap/ba-p/13584176).

The property is optional and is defined on the target systems only. It is not added at system creation. Its value must be greater than "0".

Controlling the deletion works as follows:

1.  You add the `ips.delete.threshold.roles` property on the target system before running a job and define a threshold value, for example: *500*.

2.  You run a read or resync job that is expected to delete a huge number of roles.


As a result, expect the following behavior:

-   If the number of the roles to be deleted is lower or equal \(for example: *400* or *500*\) to the defined threshold value of *500*, Identity Provisioning continues with the deletion.

-   If the number of the roles to be deleted is greater \(for example: *1000*\) than the defined threshold value of *500*, Identity Provisioning does not delete any roles. Instead, the service marks the expected to be deleted roles as failed in the job statistics. An error message in the job logs explains that roles cannot be deleted as the defined threshold is exceeded.


**System Role:** Target

</td>
<td valign="top">

SAP BTP ABAP environment

SAP Application Server ABAP

SAP Integrated Business Planning for Supply Chain

SAP Market Communication for Utilities

SAP Marketing Cloud

SAP S/4HANA Cloud

SAP S/4HANA On-Premise

</td>
</tr>
<tr>
<td valign="top">

`ioa.content.type`

</td>
<td valign="top">

This property makes an intelligent opportunity analyzer connector to send a specified value for the *Content-Type* HTTP header. This is needed because intelligent opportunity analyzer could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

Intelligent Opportunity Analyzer

</td>
</tr>
<tr>
<td valign="top">

`ioa.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the intelligent opportunity analyzer connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an intelligent opportunity analyzer system for entity versioning.

**Possible values:**

-   *true*

-   *false*


Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

Intelligent Opportunity Analyzer

</td>
</tr>
<tr>
<td valign="top">

`ioa.user.filter`

</td>
<td valign="top">

When specified, only those intelligent opportunity analyzer users matching the filter expression will be read.

Supported operators: eq \(equal\) and sw \(starts with\).

For example:

-   *userName eq "SmithJ"*

-   *email eq "john.doe@example.com"*

-   
**System Role:** Source, Proxy

</td>
<td valign="top">

Intelligent Opportunity Analyzer

</td>
</tr>
<tr>
<td valign="top">

`ioa.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in intelligent opportynity analyzer. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attributes. This property defines by which unique attributes the existing user to be searched and resolved.

Intelligent opportynity analyzer supports two user unique attributes for managing conflict resolution: *username* and *email*. Both of the attributes are mandatory. The email is a multivalue attribute, indicating that a user may have multiple unique emails.

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[\*\].value*. If the service finds an existing user with such emails \(at least one identical email is needed\), it updates this user with the data of the conflicting one. If a user with such emails is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName, emails\[\*\].value*. If the service finds an existing user with both userName and email, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

> ### Note:  
> The uniqueness of a user in the target system is determined not only by the individual attributes or the combination of both, but also by considering whether one or multiple existing users in the target system share the same values for these unique attributes. For more information, see **User Update and Uniqueness** in [SAP Ariba Category Management](sap-ariba-category-management-e4c55e4.md).

**Possible values:**

-   *userName*
-   *emails\[\*\].value*
-   *userName, emails\[\*\].value*

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

Intelligent Opportunity Analyzer

</td>
</tr>
<tr>
<td valign="top">

`awf.domain`

</td>
<td valign="top">

The domain name is the name of your SAP Advanced Workflow tenant.

If you don't know your tenant name, contact your supervisor or administrator, or refer to the email notification you received when your account was created.

**System Role:** Source, Target, Proxy

</td>
<td valign="top">

SAP Advanced Workflow

</td>
</tr>
<tr>
<td valign="top">

`awf.user.filter`

</td>
<td valign="top">

When specified, only those SAP Advanced Workflow users matching the filter expression will be read.

**Possible values:**

-   *userName eq "Julie Armstrong"*

-   *userName sw "J"*

-   *name.familyName eq "Armstrong"*

-   *emails eq "julie.armstrong@example.com"*

-   *userName eq "Julie Armstrong" and emails.value eq "julie.armstrong@example.com"*


**System Role:** Source

</td>
<td valign="top">

SAP Advanced Workflow

</td>
</tr>
<tr>
<td valign="top">

`awf.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Advanced Workflow system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Advanced Workflow

</td>
</tr>
<tr>
<td valign="top">

`awf.support.patch.operation`

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Advanced Workflow

</td>
</tr>
<tr>
<td valign="top">

`awf.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Advanced Workflow. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

**Default behavior**: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.

**Possible values:**

Default value: *userName* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Advanced Workflow

</td>
</tr>
<tr>
<td valign="top">

`cim.user.filter`

</td>
<td valign="top">

When specified, only those users matching the filter expression will be read.

**Possible values:**

For example:

*name.familyName eq "SmithJ"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.group.filter`

</td>
<td valign="top">

When specified, only those groups matching the filter expression will be read.

**Possible values:**

For example:

*displayName eq "ProjectTeam1"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Ariba Central Invoice Management. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[\*\].value*. If the service finds an existing user with at least one of the emails of the user in the source system, it updates this existing user with the data of the conflicting one. If a user with such an email is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,emails\[\*\].value*. If the service finds an existing user by *userName* and at least one of the emails of the user in the source system, it updates this user with the data of the conflicting one. If a user with such *userName* and *email* is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   
**Possible values:**

-   *userName*
-   *emails\[\*\].value*
-   *userName,emails\[\*\].value*

Default value: *userName* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists on the SAP Central Invoice Management target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

**Possible values:**

Default value \(when not specified\): *displayName*

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.support.patch.operation`

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP Central Invoice Management connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Central Invoice Management system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.content.type`

</td>
<td valign="top">

This property makes a SAP Central Invoice Management connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP Central Invoice Management could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP Central Invoice Management groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `CIM_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Central Invoice Management source system and will be provisioned to the target system with the following name pattern: <code>CIM_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Central Invoice Management groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Central Invoice Management groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `CIM_` prefix in their display name will be provisioned to SAP Central Invoice Management. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Central Invoice Management.


**System Role:** Source and Target

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.bulk.operations.max.count`

</td>
<td valign="top">

This property sets the number of operations to be performed in one bulk request.

**Possible values:**

Default value: *20*

Maximum value: *100* 

If you enter a number larger than 100, Identity Provisioning will replace it with the default value \(20\).

**System Role:** Target

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`cim.support.bulk.operation`

</td>
<td valign="top">

Set this property to *true* if you want to enable bulk operations for provisioning entities. That means, the Identity Provisioning service can write, update, and delete multiple users or groups in a single request.

For more information, see: [User Management \(SCIM\) for SAP Ariba Central Invoice Management](https://api.sap.com/api/UserServiceV1/resource/Bulk)

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP Ariba Central Invoice Management

</td>
</tr>
<tr>
<td valign="top">

`ecp.user.filter`

</td>
<td valign="top">

When specified, only those SAP SuccessFactors Employee Central Payroll users matching the filter expression will be read.

Supported operators: eq \(equal\) and sw \(starts with\).

For example:

-   Value = *userName eq "JohnSmith"*

-   Value = *userName sw "J"*

-   Value = *emails.value eq "john.smith@example.com"*


**System Role:** Source, Proxy

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`ecp.group.filter`

</td>
<td valign="top">

When specified, only those groups matching the filter expression will be read.

Supported operators: eq \(equal\) and sw \(starts with\).

For example:

-   Value = *displayName eq "ProjectTeam1"*

-   Value = *displayName sw "P"*


**System Role:** Source, Proxy

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`ecp.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP SuccessFactors Employee Central Payroll. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.

Possible values: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`ecp.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists on the SAP SuccessFactors Employee Central Payroll target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

**Possible values:**

Default value \(when not specified\): *displayName*

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`ecp.support.patch.operation`

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*

-   *false*


Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`ecp.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP SuccessFactors Employee Central Payroll connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP SuccessFactors Employee Central Payroll system for entity versioning.

**Possible values:**

-   *true*

-   *false*


Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`ecp.content.type`

</td>
<td valign="top">

This property makes a SAP SuccessFactors Employee Central Payroll connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP SuccessFactors Employee Central Payroll could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`ecp.group.prefix`

</td>
<td valign="top">

This property distinguishes SAP SuccessFactors Employee Central Payroll groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `ECP_`

You can use the example value or provide your own.

-   When set in the source system, the prefix will be prepended to the name of the groups that are read from the SAP SuccessFactors Employee Central Payroll source system and will be provisioned to the target system with the following name pattern: ECP\_GroupDisplayName. This way SAP SuccessFactors Employee Central Payroll groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP SuccessFactors Employee Central Payroll groups will be read and provisioned to the target system with their actual display names.

-   When set in the target system, only groups containing the ECP\_ prefix in their display name will be provisioned to SAP SuccessFactors Employee Central Payroll. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP SuccessFactors Employee Central Payroll.


**System Role:** Source and Target

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`ecp.sap-client`

</td>
<td valign="top">

Use this property to specify the SAP client number \(a three-digit number\) of your SAP SuccessFactors Employee Central Payroll system.

For example: `102`

</td>
<td valign="top">

SAP SuccessFactors Employee Central Payroll

</td>
</tr>
<tr>
<td valign="top">

`cm.user.filter`

</td>
<td valign="top">

When specified, only those SAP Ariba Category Management users matching the filter expression will be read.

Supported operators: eq \(equal\) and sw \(starts with\).

For example:

-   *userName eq "SmithJ"*

-   *emails.value eq "john.doe@example.com"*

-   *emails.value eq "john.doe@example.com" or emails.value eq "john.d@example.com" or emails.value eq "j.doe@example.com"*


**System Role:** Source, Proxy

</td>
<td valign="top">

SAP Ariba Category Management

</td>
</tr>
<tr>
<td valign="top">

`cm.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP Ariba Category Management. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attributes. This property defines by which unique attributes the existing user to be searched and resolved.

SAP Ariba Category Management supports two user unique attributes for managing conflict resolution: *username* and *email*. The username is a mandatory attribute, while the email is an optional, multivalue attribute, indicating that a user may have multiple unique emails.

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.
-   Value = *emails\[\*\].value*. If the service finds an existing user with such emails \(at least one identical email is needed\), it updates this user with the data of the conflicting one. If a user with such emails is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName, emails\[\*\].value*. If the service finds an existing user with both userName and email, it updates this user with the data of the conflicting one. If such a user is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.

> ### Note:  
> The uniqueness of a user in the target system is determined not only by the individual attributes or the combination of both, but also by considering whether one or multiple existing users in the target system share the same values for these unique attributes. For more information, see **User Update and Uniqueness** in [SAP Ariba Category Management](sap-ariba-category-management-e4c55e4.md).

**Possible values:**

-   *userName*
-   *emails\[\*\].value*
-   *userName, emails\[\*\].value*

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Category Management

</td>
</tr>
<tr>
<td valign="top">

`cm.support.patch.operation`

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*

-   *false*


Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Category Management

</td>
</tr>
<tr>
<td valign="top">

`cm.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP Ariba Category Management connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Ariba Category Management system for entity versioning.

**Possible values:**

-   *true*

-   *false*


Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Category Management

</td>
</tr>
<tr>
<td valign="top">

`cm.content.type`

</td>
<td valign="top">

This property makes a SAP Ariba Category Management connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP Ariba Category Management could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Ariba Category Management

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.group.filter`

</td>
<td valign="top">

When specified, only those SAP HANA Cloud, SAP HANA Database groups matching the filter expression will be read.

For example: *displayName eq "ProjectTeam1"*

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.user.filter`

</td>
<td valign="top">

When specified, only those SAP HANA Cloud, SAP HANA Database users matching the filter expression will be read.

For example: *userName eq "SmithJ"* 

**System Role:** Source, Proxy

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.content.type`

</td>
<td valign="top">

This property makes a SAP HANA Cloud, SAP HANA Database connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP HANA Cloud, SAP HANA Database could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists on the SAP HANA Cloud, SAP HANA Database target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

**Possible values:**

Default value \(when not specified\): *displayName*

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP HANA Cloud, SAP HANA Database connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP HANA Cloud, SAP HANA Database system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.support.patch.operation`

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.user.unique.attribute`

</td>
<td valign="top">

When the Identity Provisioning attempts to provision a user for the first time, it may detect that such a user already exists in SAP HANA Cloud, SAP HANA Database. Thus, the service needs to retrieve the *entityId* of the existing user via filtering by user unique attribute\(s\). This property defines by which unique attribute\(s\) the existing user to be searched \(resolved\).

According to your use case, choose how to set up this property:

-   Default behavior: This property is missing during system creation. Its default value is *userName*. That means, if the service finds an existing user by a *userName*, it updates this user with the data of the conflicting one. If a user with such а *userName* is not found, the creation of the conflicting user fails.

-   Value = *urn:ietf:params:scim:schemas:extension:sap:2.0:U ser:userId*. If the service finds an existing user with such *urn:ietf:params:scim:schemas:extension:sap:2.0:U ser:userId*, it updates this user with the data of the conflicting one. If a user with such attribute value is not found, that means the conflict is due to another reason, so the creation of the conflicting user fails.
-   Value = *userName,urn:ietf:params:scim:schemas:extension:sap:2.0:User:userId*. If the service finds an existing user with such *userName* or *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userId*, it updates this user with the data of the conflicting one. If a user with such *userName* or *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userId* is not found, the creation of the conflicting user fails.

**Possible values:**

-   *userName*
-   *urn:ietf:params:scim:schemas:extension:sap:2.0:User:userId*
-   *userName,urn:ietf:params:scim:schemas:extension:sap:2.0:User:userId*

Default value: *userName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.authenticationType`

</td>
<td valign="top">

Specifies the method by which users authenticate when connecting to the database.

**Possible values:** JWT \( Users authenticate via JWT tokens issued by an identity provider.\)

**System Role:** Target

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.instance.id`

</td>
<td valign="top">

Refers to a unique identifier associated with a specific database instance within the SAP HANA Cloud.

**System Role:** Source, Target

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.instance.type`

</td>
<td valign="top">

Refers to the type of instance being configured or used within the SAP HANA Cloud.

The value is set to *hdb* at system creation.

**System Role:** Source, Target

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.providerName`

</td>
<td valign="top">

Specifies the identity provider \(IdP\) that is responsible for handling authentication requests.

**System Role:** Target

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`hana.cloud.db.group.prefix`

</td>
<td valign="top">

\(Optional\) This property distinguishes SAP HANA Cloud, SAP HANA Database groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `HANA_Cloud_DB_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP HANA Cloud, SAP HANA Database source system and will be provisioned to the target system with the following name pattern: <code>HANA_Cloud_DB_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP HANA Cloud, SAP HANA Database groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP HANA Cloud, SAP HANA Database groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `HANA_Cloud_DB_` prefix in their display name will be provisioned to SAP HANA Cloud, SAP HANA Database. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP HANA Cloud, SAP HANA Database.


**System Role:** Source, Target

</td>
<td valign="top">

SAP HANA Cloud, SAP HANA Database

</td>
</tr>
<tr>
<td valign="top">

`en.user.filter`

</td>
<td valign="top">

When specified, only those SAP Enable Now users matching the filter expression will be read.

**Possible values:**

For example: *userName eq "SmithJ"*

**System Role:**Source, Proxy

</td>
<td valign="top">

SAP Enable Now

</td>
</tr>
<tr>
<td valign="top">

`en.group.filter`

</td>
<td valign="top">

When specified, only those SAP Enable Now groups matching the filter expression will be read.

**Possible values:**

For example: *displayName eq "ProjectTeam1"*

**System Role:** Source

</td>
<td valign="top">

SAP Enable Now

</td>
</tr>
<tr>
<td valign="top">

`en.content.type`

</td>
<td valign="top">

This property makes a SAP Enable Now connector to send a specified value for the *Content-Type* HTTP header. This is needed because SAP Enable Now could potentially not implement the protocol in the specification, which states that a system must accept *application/scim+json* as a value of the*Content-Type* header.

**Possible values:**

For example: *application/json*

Default value: *application/scim+json*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Enable Now

</td>
</tr>
<tr>
<td valign="top">

`en.user.unique.attribute`

</td>
<td valign="top">

If Identity Provisioning tries to provision a user that already exists in the target system \(a conflicting user\), this property defines the unique attributes by which the existing user will be searched and resolved. The property is not added automatically at system creation.

Default value: *userName*

If the service finds an existing user by userName, it updates this user with the data of the conflicting one. If the service does not find an existing user by userName, the creation of the conflicting user fails.

**System Role**: Target, Proxy

</td>
<td valign="top">

SAP Enable Now

</td>
</tr>
<tr>
<td valign="top">

`en.group.unique.attribute`

</td>
<td valign="top">

If the Identity Provisioning tries to create a group that already exists on the SAP Enable Now target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\). To make the search filter by a specific attribute, specify this attribute as a value for this property.

**Possible values:**

Default value \(when not specified\): *displayName*

If the property is not specified, the search is done by the default attribute: *displayName*

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Enable Now

</td>
</tr>
<tr>
<td valign="top">

`en.include.if.match.wildcard.header`

</td>
<td valign="top">

Makes the SAP Enable Now connector send the *If-Match* HTTP header with a value of “\*” for every request to the target system. This header could be used by an SAP Enable Now system for entity versioning.

**Possible values:**

-   *true*
-   *false*

Default value: *false* 

**System Role:** Target, Proxy

</td>
<td valign="top">

SAP Enable Now

</td>
</tr>
<tr>
<td valign="top">

`en.support.patch.operation`

</td>
<td valign="top">

This property controls how modified users in the source system are updated in the target system.

-   If set to *true*, Identity Provisioning sends a `PATCH` request to the user or group resource in the target system. Only attributes without `"scope": "createEntity"` in the attribute mappings in the write transformation will be updated.

    For example, if the last name of a user is changed in the source system, the patch operation will update it in the target system and will leave unchanged other attributes with explicitly set "scope": "createEntity".

-   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


Users can be updated in the target system in various cases, such as:

-   In the source system, some user attributes are modified, or new attributes are added.

-   In the source system, a condition or a filter is set for users not to be read anymore.

-   A user is deleted from the source system.


In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

**Possible values:**

-   *true*
-   *false*

Default value: *false*

**System Role:** Target

</td>
<td valign="top">

SAP Enable Now

</td>
</tr>
<tr>
<td valign="top">

`en.group.prefix`

</td>
<td valign="top">

\(Optional\) This property distinguishes SAP Enable Now groups by specific prefix. It is an optional property which does not appear by default at system creation.

Example value: `EN_`

You can use the example value or provide your own.

-   When **set in the source system**, the prefix will be prepended to the name of the groups that are read from the SAP Enable Now source system and will be provisioned to the target system with the following name pattern: <code>EN_<i class="varname">&lt;GroupDisplayName&gt;</i></code>. This way SAP Enable Now groups in the target system will be distinguished from groups provisioned from other applications.

    If the property is not set, the SAP Enable Now groups will be read and provisioned to the target system with their actual display names.

-   When **set in the target system**, only groups containing the `EN_` prefix in their display name will be provisioned to SAP Enable Now. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, all groups will be be provisioned to SAP Enable Now.


**System Role:** Source, Target

</td>
<td valign="top">

SAP Enable Now

</td>
</tr>
</table>

