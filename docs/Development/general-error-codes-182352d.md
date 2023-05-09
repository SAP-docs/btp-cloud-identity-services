<!-- loio182352d4cd814ae8be3dea41129b833e -->

# General Error Codes

The following table lists error codes that may be returned from any method on any resource URI.



**General Error Codes**


<table>
<tr>
<th valign="top">

Response Code



</th>
<th valign="top">

Meaning



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

*301*



</td>
<td valign="top">

Permanent Location



</td>
<td valign="top">

The requested resource resides on a URI other than the requested one.You need to set up the authentication type to access the API. For more information about this configuration, see



</td>
</tr>
<tr>
<td valign="top">

*400*



</td>
<td valign="top">

Bad Request



</td>
<td valign="top">

The requested operation cannot be executed because the service cannot understand the data sent in the entity body of the request.



</td>
</tr>
<tr>
<td valign="top">

*401*



</td>
<td valign="top">

Unauthorized



</td>
<td valign="top">

The client is not authenticated.



</td>
</tr>
<tr>
<td valign="top">

*403*



</td>
<td valign="top">

Forbidden



</td>
<td valign="top">

Access to the resource is denied.



</td>
</tr>
<tr>
<td valign="top">

*404*



</td>
<td valign="top">

Not Found



</td>
<td valign="top">

The requested resource cannot be found.



</td>
</tr>
<tr>
<td valign="top">

*405*



</td>
<td valign="top">

Method Not Allowed



</td>
<td valign="top">

The requested method is not supported for the given resource.



</td>
</tr>
<tr>
<td valign="top">

*406*



</td>
<td valign="top">

Not Acceptable



</td>
<td valign="top">

You need to set up the authentication type to access the API.The requested method does not produce any of the media types requested in the HTTP request.



</td>
</tr>
<tr>
<td valign="top">

*409*



</td>
<td valign="top">

Conflict



</td>
<td valign="top">

The operation cannot be completed because it conflicts with an existing resource.



</td>
</tr>
<tr>
<td valign="top">

*415*



</td>
<td valign="top">

Unsupported Media Type



</td>
<td valign="top">

The REST service does not support the API version requested by the REST client.



</td>
</tr>
<tr>
<td valign="top">

*500*



</td>
<td valign="top">

Internal Server Error



</td>
<td valign="top">

The operation cannot be completed due to a service error.



</td>
</tr>
<tr>
<td valign="top">

*503*



</td>
<td valign="top">

 



</td>
<td valign="top">

The service is currently unavailable.



</td>
</tr>
</table>

**Related Information**  


[Identity Directory SCIM REST API](identity-directory-scim-rest-api-5be5692.md "Manage users, groups and custom schemas in the cloud.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

[Invitation REST API](invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

[Password Service REST API](password-service-rest-api-8d1016b.md "The password service is used for operations related to user passwords, such as verification of the user name and the password combination.")

[Forgot Password REST API](forgot-password-rest-api-d024fca.md "The forgot password REST API sends a reset password e-mail.")

[TOTP Validation Service](totp-validation-service-3e4c3cf.md "Validation of time-based one-time password (TOTP).")

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c "The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.")

