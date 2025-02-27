<!-- loio424b64c0831b466cbf5680faa58e92b8 -->

# Configure User Authorizations

Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.



<a name="loio424b64c0831b466cbf5680faa58e92b8__prereq_yys_bdw_fzb"/>

## Prerequisites

You have enabled the authorizations based on policies option in the admin console for SAP Cloud Identity Services. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).



## Context

> ### Restriction:  
> This feature is relevant only for the Administration Console application.

Sometimes the administrator authorizations that are predefined in the tenant of SAP Cloud Identity Services aren't enough. The predefined administrator authorizations give unlimited data access. However, you may need to define authorization models with more complex instance restrictions for data access, as is the so-called attribute-based access control \(ABAC\). Administrators define authorization policies with user attributes and assign these policies to other administrators. Thus, one administrator can have access to a subset of the users in the tenant or to a subset of the attributes of the user.

Once it's enabled, it may take up to 60 seconds before the administrator can see the *Authorization Policies* tab when accessing the administration console application. Initially, only the base policies are visible: `CREATE_USERS` , `DELETE_USERS`, `MANAGE_USERS`, `READ_USERS`, `UPDATE_USERS`, `CREATE_SCIM_SCHEMAS`, `DELETE_SCIM_SCHEMAS`, `MANAGE_SCIM_SCHEMAS`, `READ_SCIM_SCHEMAS`, `CREATE_GROUPS`, `DELETE_GROUPS`, `MANAGE_GROUPS`, `READ_GROUPS`, and `UPDATE_GROUPS`. You can create new authorization policies on the base of these policies and assign them to administrators.

> ### Remember:  
> As of February 11, 2025, the **MANAGE\_USERS** policy does not contain the read applications permission. You must add the **READ\_APPLICATIONS** policy to the user or users if they need to see the *Import Users* tile in the administration console.

> ### Note:  
> The Read Users authorization overrides the READ\_USERS authorization policy, while the Manage Users authorization overrides all user authorization policies.

When you create a new policy, you can restrict the users on the basis of the following attributes: `user.name`, `user.addresses.country`, `user.costCenter`, `user.division`, `user.department`, `user.organization`, and `user.type`. The subsets of the user attributes are configured via the `user.attributes`.

**User Attributes**


<table>
<tr>
<th valign="top">

Attributes

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`user.userName`

</td>
<td valign="top">

The *Login Name* of the user as defined in the administration console.

</td>
</tr>
<tr>
<td valign="top">

`user.addresses.country`

</td>
<td valign="top">

The value must match the predefined master data one. See [Countries.properties](../Development/change-master-data-texts-rest-api-b10fc6a.md#loioe4e7e4c52cf04295bf94465eba7ceaaa).

The addresses must be marked as primary via the [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview). Users who don't have a primary address are excluded even if the `user.addresses.country` attribute matches the address of the user.

> ### Tip:  
> Use the key from the key-value pair for the value of the `user.country` attribute. For example, you must use `DE` from the key-value pair `DE=Germany`.



</td>
</tr>
<tr>
<td valign="top">

`user.costCenter`

</td>
<td valign="top">

The *Cost Center* of the user as defined in the administration console.

</td>
</tr>
<tr>
<td valign="top">

`user.division`

</td>
<td valign="top">

The *Division* of the user as defined in the administration console.

</td>
</tr>
<tr>
<td valign="top">

`user.department`

</td>
<td valign="top">

The value must match the predefined master data one. See [Departments.properties](../Development/change-master-data-texts-rest-api-b10fc6a.md#loiod13c638f0d5d4a8889debf278fcb0275)

</td>
</tr>
<tr>
<td valign="top">

`user.organization`

</td>
<td valign="top">

The *Company* of the user as defined in the administration console.

</td>
</tr>
<tr>
<td valign="top">

`user.type`

</td>
<td valign="top">

The *User Type* as defined in the administration console. The allowed values are `public`, `partner`, `customer`, `external`, `onboardee`, `employee` or `alumni`.

</td>
</tr>
<tr>
<td valign="top">

`user.attributes`

</td>
<td valign="top">

The policy allows you to see the attributes that are defined in the value field. The attributes' value format must be according to SCIM notation.

The supported attributes that can be defined in the policy are listed in the **Supported Attributes** section below this table.

> ### Note:  
> If the `user.аttributes` is used with the "=" operator, it supports only one attribute. For more attributes, use the "IN" operator adding each attribute separately.

> ### Note:  
> If you use the attribute `password`, you must also add the following two attributes: `active` and `urn:ietf:params:scim:schemas:extension:sap:2.0:User:status`. The attributes must be separated with comma, with no space between them.



</td>
</tr>
<tr>
<td valign="top">

*Deprecated*

`user.excludedAttributes`

</td>
<td valign="top">

> ### Note:  
> The `user.excludedAttributes` attribute is deprecated.
> 
> If you have a policy configured with the `user.excludedAttributes` attribute exchange the `user.excludedAttributes` with the `user.attributes` attribute in combination with the "NOT IN" operator.
> 
> If the policy is configured with the `user.аttributes` attribute used with the "=" operator, it supports only one attribute. For more attributes, use the "IN" operator adding each attribute separately.



</td>
</tr>
</table>

> ### Restriction:  
> The "NOT IN" operator can be used only with the `user.attributes` attribute. Do not use "NOT IN" in combination with other attributes.

Expand the **Supported Attributes** section below to see the user attributes that can be configured in the authorization policy:



### Supported Attributes

**Core Schema** 

-   `name.givenName`
-   `name.familyName`
-   `userName`
-   `displayName`
-   `addresses.country`
-   `addresses.streetAddress`
-   `addresses.streetAddress2`
-   `phoneNumbers.value`
-   `phoneNumbers.verified`
-   `emails.value`
-   `emails.verified`
-   `password`

> ### Note:  
> For the attributes defined in the core schema, the Schema URI notation `[urn:ietf:params:scim:schemas:core:2.0:User]` is not needed, for all the other attributes, schema URI and the attribute name is required. For example: `user.attributes IN displayName,addresses.country,emails.value;` 

**EnterpriseUuser Resource Schema**

-   `costCenter`
-   `organization`
-   `division`
-   `department`

> ### Note:  
> All Enterprise user resource schema attributes require the schema URI urn:ietf:params:scim:schemas:extension:enterprise:2.0:User and the attribute name.
> 
> For example:`user.attributes IN urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter, urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization;`

**SAP extension schema**

-   `userUuid`
-   `validFrom`
-   `validTo`

> ### Note:  
> All SAP extension schema attributes require the schema URI urn:ietf:params:scim:schemas:extension:sap:2.0:User and the attribute name. For example: user.excludedAttributes=urn:ietf:params:`scim:schemas:extension:sap:2.0:User:userUuid, urn:ietf:params:scim:schemas:extension:sap:2.0:User:validFrom;`

**Custom Defined Schema** 

All custom schema defined attributes require a fully qualified attribute name. For example: `user.attributes=urn:sap:cloud:scim:schemas:extension:custom:2.0:MyCustomSchema:CustomString` 

Groups of type `Authorization Policy` with names containing the names of the authorization policies are also created in the administration console. You can't delete these groups via the *Groups* section. The groups are related to the authorization policies, and when you delete a policy, the respective group is also removed.

> ### Restriction:  
> You need both read and update access rights to be able to update a field in the administration console. If you can't see a field because of a policy restriction, this field remains also disabled for editing even if update rights are granted to you.

> ### Remember:  
> To edit a custom schema custom attribute via the administration console, `users.MANAGE_USERS` without restriction is needed. If the policy has a restriction on the `users.MANAGE_USERS` base policy, you won't be able to edit the custom schema custom attribute.

> ### Example:  
> Michael Adams is an administrator at retail company A. He is located at the company's head office in Germany and as chief administrator of the company he has all the authorizations in the administration console for SAP Cloud Identity Services. Dona Moore is also an administrator at company A. She is responsible for the branch office in the USA. As such she needs to have access only to the users in the USA. Michael Adams creates an authorization policy for read-users access and assigns Dona Moore to that policy. He also removes the *Read Users* and *Manage Users* authorizations that Dona has as an administrator. As a result, now, when Dona accesses the *User Management* section of the administration console, she sees only the users that are located in the USA. All the other users are hidden.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Under *System Applications*, choose the list item for the administration console.

4.  Under the tab *Authorization Policies*, select a custom authorization policy.

    > ### Note:  
    > Type the name or package in the search field, filter the names or packages, or choose the policy from the list.
    > 
    > If you don’t have a created authorization policy in your list, you can create one. For more information, see [Create an Authorization Policy](create-an-authorization-policy-897fc30.md).

5.  Choose the *Edit* button.

    1.  To customize the rules of the authorization policy, choose the *Rules*.

    2.  To assign administrator or administrators to this policy, choose the *Assignments* tab.


6.  Save your changes.


**Related Information**  


[Configure Group Authorizations](configure-group-authorizations-7a09cad.md "Configure granular access and control over the groups in the administration console of SAP Cloud Identity Services.")

[Configure Application Authorizations](configure-application-authorizations-01cff18.md "Configure granular access and control over the applications in the administration console of SAP Cloud Identity Services.")

[Configure Provisioning Authorizations](configure-provisioning-authorizations-a8f8e31.md "Configure granular access control for the Identity Provisioning systems and logs in the SAP Cloud Identity Services administration console.")

