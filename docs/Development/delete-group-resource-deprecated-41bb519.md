<!-- loio41bb51961c274db18c82cc4182025a42 -->

# Delete Group Resource \(Deprecated\)

The delete group resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing group. Delete group resource is implemented as defined by the System for Cross-domain Identity Management \(SCIM\) protocol.



> ### Note:  
> This API is deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead. For more information, see [Migrating Identity Authentication SCIM REST API to Identity Directory Service API](migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api-106dbe0.md).



**Prerequisites:**

You have the `id` of the group whose resource you want to delete.

> ### Note:  
> To get the `id` of the group, list all the groups in the tenant and copy the `id` of the group whose resource you want to get. For more information, see [Groups Search \(Deprecated\)](groups-search-deprecated-77e6811.md).

> ### Caution:  
> `id` and `groupId` have different values. You must use the `id` value for the request.



<a name="loio41bb51961c274db18c82cc4182025a42__section_ckx_gsz_zcb"/>

## Request

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/service/scim/Groups/&lt;id of the group&gt;</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).

**HTTP Method:***DELETE*

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



> ### Note:  
> The delete group resource method removes the user group and unassign all users from them.
> 
> When group resource is deleted, it is not possible to get information about it via a **GET** request.
> 
> If selected groups are used in Risk-Based Authentication or Conditional Authentication rules, then these rules may not work as expected after deletion.





### Request Example

```
DELETE /service/scim/Groups/<id of the group>
Content-Type: application/scim+json

```



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

204

</td>
<td valign="top">

No Content

</td>
<td valign="top">

Group is successfully deleted.

</td>
</tr>
<tr>
<td valign="top">

404

</td>
<td valign="top">

Not Found

</td>
<td valign="top">

The group does not exist

</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [Error and Success Codes](error-and-success-codes-7f87a75.md).



**Related Information**  


[Groups Search \(Deprecated\)](groups-search-deprecated-77e6811.md "The group search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for group search. Group search is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[Group Resource \(Deprecated\)](group-resource-deprecated-8c6ebd7.md "The group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known group.")

[Create Group Resource \(Deprecated\)](create-group-resource-deprecated-a831c94.md "The create group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user group.")

[Update Group Resource \(Deprecated\)](update-group-resource-deprecated-81ca50e.md "The update group method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the update of an existing group. The method does not create a new group.")

