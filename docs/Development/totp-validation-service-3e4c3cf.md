<!-- loio3e4c3cfb56fa48819cfe19209fa38b1f -->

# TOTP Validation Service

Validation of time-based one-time password \(TOTP\).



The API is called on behalf of an application \(\(service provider \(SP\)\).



## Request

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/service/users/otp</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).

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

Provided by the user. The `userName` can be either the user email, the user login name, or the user profile ID.

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


[Application Configurations API](application-configurations-api-a8fc935.md "Manage application configurations.")

[Identity Directory API](identity-directory-api-5be5692.md "Manage users, groups and custom schemas in the cloud.")

[Identity Provisioning API](identity-provisioning-api-4433374.md "Manage identity lifecycle processes for cloud and on-premise systems.")

[Identity Authentication API \(Deprecated\)](identity-authentication-api-deprecated-2f21568.md "Deprecated.")

[Migrating Deprecated Identity Authentication API to Identity Directory API](migrating-deprecated-identity-authentication-api-to-identity-directory-api-106dbe0.md "Migrating from the Identity Authentication API to Identity Directory API.")

[Invitation REST API](invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

[Password Service REST API](password-service-rest-api-8d1016b.md "The password service is used for operations related to user passwords, such as verification of the user name and the password combination.")

[Forgot Password REST API](forgot-password-rest-api-d024fca.md "The forgot password REST API sends a reset password email.")

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c "The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.")

[Error and Success Codes](error-and-success-codes-7f87a75.md "This section is to help developers with solutions to the REST API response codes.")

