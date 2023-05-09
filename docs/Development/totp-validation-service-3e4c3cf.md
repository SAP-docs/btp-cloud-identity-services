<!-- loio3e4c3cfb56fa48819cfe19209fa38b1f -->

# TOTP Validation Service

Validation of time-based one-time password \(TOTP\).



The API is called on behalf of an application \(\(service provider \(SP\)\).



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/users/otp`

**HTTP Method:***POST*

**Authentication mechanisms:**

-   Client certificate

-   Basic authentication


> ### Note:  
> For more information about the authentication mechanisms, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).



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

`Content Type`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

application/json



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

`userName`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

String



</td>
<td valign="top">

Provided by the user. The `userName` can be either the user e-mail, the user login name, or the user profile ID.



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

`otpCode`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

String



</td>
<td valign="top">

Provided by the user. The `otpCode` is the time-based one-time password \(TOTP\) to be validated.



</td>
<td valign="top">

Request body



</td>
</tr>
</table>



### Request Example

```

POST /service/users/otp
Content-Type: application/json
{   
 "userName": "michael.adams@example.com",
 "otpCode": "123456"
}

```



## Response



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code



</th>
<th valign="top">

Result or X-Message Code



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

200 OK



</td>
<td valign="top">

Success



</td>
<td valign="top">

The one-time password is valid.



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

401 Unauthorized



</td>
<td valign="top">

BAD\_CREDENTIALS



</td>
<td valign="top">

The user isn't authenticated or the authentication failed due to wrong credentials.



</td>
</tr>
<tr>
<td valign="top">

INVALID\_OTP\_CODE



</td>
<td valign="top">

The TOTP isn’t valid.



</td>
</tr>
<tr>
<td valign="top">

LOCKED\_OTP\_CODE



</td>
<td valign="top">

The user provided wrong TOTP five times. The user's passcode authentication is locked.



</td>
</tr>
<tr>
<td valign="top">

USED\_OTP\_CODE



</td>
<td valign="top">

The TOTP is already used.



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

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c "The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.")

[General Error Codes](general-error-codes-182352d.md "The following table lists error codes that may be returned from any method on any resource URI.")

[General Error Codes](general-error-codes-182352d.md "The following table lists error codes that may be returned from any method on any resource URI.")

