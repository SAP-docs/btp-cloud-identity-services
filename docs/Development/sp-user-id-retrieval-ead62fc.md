<!-- loioead62fcd8a8c4d97980bcdd102725a14 -->

# SP User ID Retrieval

To retrieve an SP \(service provider\) user's ID, you use the `GET` method.



<a name="loioead62fcd8a8c4d97980bcdd102725a14__section_mbm_1xk_fdb"/>

## Prerequisites

You need to set up the authentication type to access the API. For more information about this configuration, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).



## Request

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/service/users</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

**HTTP Method:***GET*



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

`Authorization`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

`Basic`

-   via application \(\(service provider \(SP\)\) Authentication certificate

-   via SP REST API username and password


For more information, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).

</td>
</tr>
<tr>
<td valign="top">

`Content-Type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

application/vnd.sap-id-service.sp-user-id+xml

</td>
</tr>
</table>



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

Description

</th>
<th valign="top">

Parameter Type

</th>
</tr>
<tr>
<td valign="top">

`name_id`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

String

</td>
<td valign="top">

The name ID of the user you register. The `name_id` can be retrieved via the [SP User Information](sp-user-information-dc96d56.md) API. It can be a User ID, Login name, etc.

</td>
<td valign="top">

Query string

</td>
</tr>
<tr>
<td valign="top">

`applicationId`

</td>
<td valign="top">

No

</td>
<td valign="top">

String

</td>
<td valign="top">

The ID of the subscribed application. The user is retrieved for the application with the provided ID.

</td>
<td valign="top">

Query string

</td>
</tr>
</table>



### Request Example

```
GET /service/users?name_id=johns
```



## Response



### Response Headers


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`Location`

</td>
<td valign="top">

The ID of the created SP user is in the location header of the HTTP Response.

</td>
</tr>
</table>



### Response Example

```
Location: https://<tenant ID>.accounts.ondemand.com/service/users/<SP user ID>
```



**Related Information**  


[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

