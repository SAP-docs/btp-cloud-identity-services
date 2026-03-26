<!-- loio230fc2ef550c4c79acee720b1dc3cad3 -->

# Permanently Delete User \(Restricted Availability\)

Permanently delete the soft-deleted \(blocked\) but not yet deleted from the system user whose `SCIM ID` is stated in the request.



<a name="loio230fc2ef550c4c79acee720b1dc3cad3__section_lyw_cqf_n2c"/>

## Prerequisites

-   You are a tenant administrator of SAP Cloud Identity Services with а *Manage Users* role. For more information, see [Edit Administrator Authorizations \(Restricted Availability\)](edit-administrator-authorizations-restricted-availability-297b3b2.md).

-   You have the *Soft Delete Users* option enabled in the *Tenant Settings* for your tenant. For more information, see [Enable Soft Delete for Users in Administration Console \(Restricted Availability\)](enable-soft-delete-for-users-in-administration-console-restricted-availability-25a6175.md).




## Request

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/scim/Users/{scim id of the deleted user}?blocked=true</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

**HTTP Method:***DELETE*



### Authentication

Any authentication supported by the [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview) can be used.



### Request Parameters


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Required

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Additional Information

</th>
<th valign="top">

Parameter Type

</th>
</tr>
<tr>
<td valign="top">

`blocked`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The required value is `true`

</td>
<td valign="top">

Query

</td>
</tr>
<tr>
<td valign="top">

SCIM ID number

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The SCIM ID number of the deleted user.

</td>
<td valign="top">

Query

</td>
</tr>
</table>



### Request Example

```

DELETE
https://my-tenant.ondemand.com/scim/Users/1v40869v-asd1-48c7-bedb-1bbdpf51bbc56?blocked=true
```



## Response

If the operation is successful, the response returns code *204 No Content*.



### Response Codes

[Identity Directory API Reference](https://api.sap.com/api/IdDS_SCIM/path/deleteUser)

**Related Information**  


[Enable Soft Delete for Users in Administration Console \(Restricted Availability\)](enable-soft-delete-for-users-in-administration-console-restricted-availability-25a6175.md "Enable soft deletion (blocking) of users in SAP Cloud Identity Services.")

[Read Single Soft-Deleted User \(Restricted Availability\)](read-single-soft-deleted-user-restricted-availability-5adef17.md "Read the soft-deleted (blocked) but not permanently deleted user.")

[Read All Soft-Deleted Users \(Restricted Availability\)](read-all-soft-deleted-users-restricted-availability-89a99b9.md "Get a list of all soft-deleted (blocked) but not deleted users in the tenant of SAP Cloud Identity Services.")

[Restore Soft-Deleted User \(Restricted Availability\)](restore-soft-deleted-user-restricted-availability-114076d.md "Restore a user that is soft-deleted (blocked) in the tenant of SAP Cloud Identity Services.")

[Edit Administrator Authorizations \(Restricted Availability\)](edit-administrator-authorizations-restricted-availability-297b3b2.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

