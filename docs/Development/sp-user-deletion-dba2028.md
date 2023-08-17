<!-- loiodba2028899cf462f9cfd97c9b8505de4 -->

# SP User Deletion

Delete an SP \(service provider\) user.



<a name="loiodba2028899cf462f9cfd97c9b8505de4__section_mbm_1xk_fdb"/>

## Prerequisites

You need to set up the authentication type to access the API. For more information about this configuration, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).



> ### Caution:  
> If the last SP user is deleted, and the user is of type `type` `public`, then the whole user profile is deleted.



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/users/<SP user ID>`

**HTTP Method:***DELETE*



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

`Basic Authorization`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

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

`applicationId`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

The ID of the subscribed application. The user is deleted for the application with the provided ID.



</td>
<td valign="top">

Query string



</td>
</tr>
</table>



### Request Example

```
DELETE /service/users/0800200c9a66
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

200



</td>
<td valign="top">

The operation is successful.



</td>
<td valign="top">

The SP user is deleted.



</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [Error and Success Codes](error-and-success-codes-7f87a75.md).



**Related Information**  


[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

