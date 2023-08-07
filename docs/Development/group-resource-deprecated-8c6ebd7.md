<!-- loio8c6ebd7c1c564d8e9eb4fa404641d6e7 -->

# Group Resource \(Deprecated\)

The group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known group.



> ### Note:  
> This API is deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead. For more information, see [Migrating Identity Authentication SCIM REST API to Identity Directory Service API](migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api-106dbe0.md).



> ### Note:  
> Group resource is implemented as defined by the SCIM protocol.



**Prerequisites:**

You have the `id` of the group whose resource you want to get.

> ### Note:  
> To get the `id` of the group, list all the groups in the tenant and copy the `id` value for the group whose resource you want to get. For more information, see [Groups Search \(Deprecated\)](groups-search-deprecated-77e6811.md).

> ### Caution:  
> `id` and `groupId` have different values. You must use the `id` value for the request.



<a name="loio8c6ebd7c1c564d8e9eb4fa404641d6e7__section_uvh_qc2_nbb"/>

## Request

**URI:**<code>https://&lt;tenant ID&gt;.accounts.ondemand.com/service/scim/Groups/&lt;<code>id</code> of the group&gt;</code>

**HTTP Method:***GET*

**Authentication mechanisms:**

-   Client certificate

-   Basic authentication


> ### Note:  
> You must have a system as administrator with an assigned *Manage Users* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).



### Request Headers


<table>
<tr>
<th valign="top">

Header



</th>
<th valign="top">

Required



</th>
<th valign="top">

Values



</th>
</tr>
<tr>
<td valign="top">

`Content-Type`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

application/scim+json



</td>
</tr>
</table>



### Request Example

```
GET /service/scim/Groups/<id of the group>
Content-Type: application/scim+json

```



<a name="loio8c6ebd7c1c564d8e9eb4fa404641d6e7__section_f1p_r2v_4bb"/>

## Response



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code



</th>
<th valign="top">

Reason



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

200



</td>
<td valign="top">

OK



</td>
<td valign="top">

List details for a specific group in a tenant of Identity Authentication.

> ### Note:  
> The maximum number of group members in a group returned in the response is limited to 100.
> 
> If you have more than 100 group members, and you want to get the full list, you have to perform multiple requests via the Users Search SCIM REST API. For more information, see [Users Search \(Deprecated\)](users-search-deprecated-3af7dfa.md).



</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [Error and Success Codes](error-and-success-codes-7f87a75.md).



### Response Example



## Example

```
{
  "id" : "57aadecee4b0c8e9241d1635",
  "displayName" : "Identity Authentication Admins",
  "schemas" : [ "urn:ietf:params:scim:schemas:core:2.0:Group", "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group" ],
  "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group" : {
    "name" : "Administrators"
    "description": "Group Administrators description"
    "groupId": "e56a7d8b-8a89-54k5-7s89-5689d681e381i"
  },
  "meta" : {
    "location" : "https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/57aadecee4b0c8e9241d1635",
    "resourceType" : "Group",
    "version" : "1.0"
  },
  "members" : [ {
    "value" : "P000001",
    "$ref" : "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000001",
    "display" : "Dona Moore"
  } ]
}
```





**Related Information**  


[Groups Search \(Deprecated\)](groups-search-deprecated-77e6811.md "The group search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for group search. Group search is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[Create Group Resource \(Deprecated\)](create-group-resource-deprecated-a831c94.md "The create group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user group.")

[Update Group Resource \(Deprecated\)](update-group-resource-deprecated-81ca50e.md "The update group method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the update of an existing group. The method does not create a new group.")

[Delete Group Resource \(Deprecated\)](delete-group-resource-deprecated-41bb519.md "The delete group resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing group. Delete group resource is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

