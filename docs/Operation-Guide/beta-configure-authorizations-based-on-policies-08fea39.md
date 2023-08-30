<!-- loio08fea393a4b54fa4867c47520f088ab8 -->

# \(Beta\) Configure Authorizations Based on Policies

Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.



## Context

> ### Note:  
> This is a beta feature available on Identity Authentication. You as a tenant administrator can request this feature by reporting an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with component `BC-IAM-IDS`.

> ### Restriction:  
> This feature is relevant only for the Administration Console application.

Sometimes the administrator authorizations that are predefined in the tenant of SAP Cloud Identity Services aren't enough. The predefined administrator authorizations give unlimited data access. However, you may need to define authorization models with more complex instance restrictions for data access, as is the so-called attribute-based access control \(ABAC\). Administrators define authorization policies with user attributes and assign these policies to other administrators. Thus, one administrator can have access to a subset of the users in the tenant or to a subset of the attributes of the user.

The option to configure authorization policies for the administration console is available only upon request via [SAP Support Portal Home](https://support.sap.com/en/index.html) under the component `BC-IAM-IDS`. Once it's granted, it may take up to 60 seconds before the administrator can see the *Authorization Policies* tab when accessing the administration console application. Initially, only the base policies are visible: `CREATE_USERS` , `DELETE_USERS`, `MANAGE_USERS`, `READ_USERS`, `UPDATE_USERS`, `CREATE_SCIM_SCHEMAS`, `DELETE_SCIM_SCHEMAS`, `MANAGE_SCIM_SCHEMAS`, `READ_SCIM_SCHEMAS`, `CREATE_GROUPS`, `DELETE_GROUPS`, `MANAGE_GROUPS`, `READ_GROUPS`, and `UPDATE_GROUPS`. You can create new authorization policies on the base of these policies and assign them to administrators.

When you create a new policy, you can restrict the users on the basis of the following attributes: `user.name`, `country`, `costCenter`, `division`, `department`, and `organization`. The subsets of the user attributes are configured via `user.attributes`, and `user.excludedAttributes`.

> ### Remember:  
> You can use only the equal \(`=` \) operator . If you use other operators, this could result in not having access to the administration console.

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

`user.name`



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

`user.attributes`



</td>
<td valign="top">

The policy allows you to see the attributes that are defined in the value field. The attributes' value format must be according to SCIM notation.

The supported attributes that can be defined in the policy are listed in the **Supported Attributes** section below this table.

> ### Note:  
> If you use the attribute `password`, you must also add the following two attributes: `active` and `urn:ietf:params:scim:schemas:extension:sap:2.0:User:status`. The attributes must be separated with comma, with no space between them.



</td>
</tr>
<tr>
<td valign="top">

`user.excludedAttributes`



</td>
<td valign="top">

The policy allows you to exclude the attributes that are defined in the value field. The attributes' value format must be according to the SCIM notation.

The supported attributes that can be defined in the policy are listed in the **Supported Attributes** section below this table.



</td>
</tr>
</table>

Expand the **Supported Attributes** section below to see the user attributes that can be configured in the authorization policy:



### Supported Attributes

**Core Schema** 

-   `firstName`
-   `lastName`
-   `loginName`
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
> For the attributes defined in the core schema, the Schema URI notation `[urn:ietf:params:scim:schemas:core:2.0:User]` is not needed, for all the other attributes, schema URI and the attribute name is required. For example: `user.attributes = displayName,addresses.country,emails.value;` 

**EnterpriseUuser Resource Schema**

-   `costCenter`
-   `organization`
-   `division`
-   `department`

> ### Note:  
> All Enterprise user resource schema attributes require the schema URI urn:ietf:params:scim:schemas:extension:enterprise:2.0:User and the attribute name.
> 
> For example:`user.attributes=urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter, urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization;`

**SAP extension schema**

-   `globalUserId`
-   `validFrom`
-   `validTo`

> ### Note:  
> All SAP extension schema attributes require the schema URI urn:ietf:params:scim:schemas:extension:sap:2.0:User and the attribute name. For example: user.excludedAttributes=urn:ietf:params:`scim:schemas:extension:sap:2.0:User:userUuid, urn:ietf:params:scim:schemas:extension:sap:2.0:User:validFrom;`

**Custom Defined Schema** 

All custom schema defined attributes require fully qualified attribute name. For example: `user.attributes=urn:sap:cloud:scim:schemas:extension:custom:2.0:MyCustomSchema:CustomString` 

Groups of type `Authorization Policy` with names containing the names of the authorization policies are also created in the administration console. You can't delete these groups via the *Groups* section. The groups are related to the authorization policies, and when you delete a policy, the respective group is also removed.

> ### Caution:  
> If you create a read user policy that restricts certain attributes, you must be careful not to update attributes that you don't see in the admin console.
> 
> If you create an update user policy that restricts certain attributes, when you update an attribute that is restricted, the update won't be applied. The current value of the attribute remains unchanged.

> ### Tip:  
> To eliminate the risk of updating an attribute that is restricted, keep the read and update policies equal.

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

    1.  To customise the rules of the authorization policy, choose the *Rules*.

    2.  To assign administrator or administrators to this policy, choose the *Assignments* tab.


6.  Save your changes.




<a name="loio08fea393a4b54fa4867c47520f088ab8__postreq_qwy_wcj_ywb"/>

## Next Steps

\(If the administrators have *Read Users* and *Manage Users* authorizations\) Remove the *Read Users* and *Manage Users* authorizations for those administrator or administrators that are assigned to the policy. For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

> ### Remember:  
> If you don't remove the *Read Users* and *Manage Users* authorizations, the configured and assigned authorization policies for the administration console won't be applied. *Read Users* overrides the `READ_USERS` authorization policy while *Manage Users* overrides all user authorization policies.

**Related Information**  


[List Administrators](list-administrators-c79a5c6.md "As a tenant administrator, you can list the administrators and their authorizations in the administration console for SAP Cloud Identity Services.")

[Add Administrators](add-administrators-bbbdbdd.md#loiobbbdbdd3899942ce874f3aae9ba9e21d "As a tenant administrator, you can add new administrators in the administration console for SAP Cloud Identity Services.")

[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

