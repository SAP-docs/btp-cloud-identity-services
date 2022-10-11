<!-- loiodc96d56f2a234a129a4be6eed9a1d5e0 -->

# SP User Information

To retrieve information for an SP \(service provider\) user, you use a `GET` method.



<a name="loiodc96d56f2a234a129a4be6eed9a1d5e0__section_mbm_1xk_fdb"/>

## Prerequisites

You need to set up the authentication type to access the API. For more information about this configuration, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/users/<SP user id>`

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

`<SP user ID>`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

String



</td>
<td valign="top">

The SP user id.



</td>
<td valign="top">

Path



</td>
</tr>
</table>



### Request Example

```
GET /service/users/<the ID of the SP user>
```



## Response



### Response Attributes

The response returns the following attributes. Only the attributes that exist for the user are returned.

> ### Note:  
> The value of the attributes can be updated via *PUT* request through the [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/resource).

-   user\_profile\_id
-   name\_id
-   status
-   profile\_status
-   valid\_from
-   valid\_to
-   activation\_time
-   email
-   language
-   first\_name
-   last\_name
-   sp\_name
-   login\_name
-   country
-   city
-   company\_city



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

The information for the user is returned in the response.



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

The SP user with the provided ID does not exist.



</td>
</tr>
</table>

 

**Related Information**  


[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

