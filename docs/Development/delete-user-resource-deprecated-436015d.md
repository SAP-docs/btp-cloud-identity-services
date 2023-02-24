<!-- loio436015d66dad4c129a87604eda2f7134 -->

# Delete User Resource \(Deprecated\)

The delete user resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing user. Delete user resource is implemented as defined by the System for Cross-domain Identity Management \(SCIM\) protocol.



> ### Note:  
> This API will be deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead. For more information, see [Migrating Identity Authentication SCIM REST API to Identity Directory Service API](migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api-106dbe0.md).





## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/scim/Users/<id>`

**HTTP Method:***DELETE*

**Content-Type: application/scim+json**

**Authentication mechanisms:**

-   Client certificate

-   Basic authentication


> ### Note:  
> You must have a system as administrator with an assigned *Manage Users* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).

**Response Status Code**

**Success Codes**


<table>
<tr>
<th valign="top">

Response Code



</th>
<th valign="top">

Meaning



</th>
<th valign="top">

Response Description



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

User is successfully deleted.



</td>
</tr>
</table>

> ### Note:  
> Response code if user does not exist is **404 Not Found**. When user resource is deleted, it is not possible to get information about it via a **GET** request.

For more information about the general error codes that may be returned, see [General Error Codes](general-error-codes-182352d.md).

**Related Information**  


[Users Search \(Deprecated\)](users-search-deprecated-3af7dfa.md "The user search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for user search. User search is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol for querying and filtering resources.")

[User Resource \(Deprecated\)](user-resource-deprecated-7ae17a6.md "The user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known user.")

[Create User Resource \(Deprecated\)](create-user-resource-deprecated-cea8778.md "The create user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user.")

[Update User Resource \(Deprecated\)](update-user-resource-deprecated-9e36479.md "The update user method of the implementation of the SCIM REST API protocol provides information on the update of a known user. The method does not create a new user.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

