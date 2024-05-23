<!-- loio8d1016b602704b9db38d55daa92c32e6 -->

# Password Service REST API

The password service is used for operations related to user passwords, such as verification of the user name and the password combination.



## Verify Username and Password Combination

Verify the username and password combination, or verify the thing ID and password combination.



## Request

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/service/users/password</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).

**HTTP Method:***POST*



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

`Basic` - Username and password are provided by the user.

> ### Note:  
> Depending on the allowed logon identifiers for the user, the username can be the `User ID`, `Login Name`, or `Email`. For more information, see [Configure Allowed Logon Identifiers](../Operation-Guide/configure-allowed-logon-identifiers-3adf1ff.md).

> ### Caution:  
> If the user provides wrong password, then each verification counts as a failed logon attempt. The password locks when the number of the allowed failed logon attempts is reached. The number depends on the password policy applied for the application. For more information, see [Configuring Password Policies](../Operation-Guide/configuring-password-policies-12b3395.md).



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

application/json

</td>
</tr>
</table>



### Request Example

```
POST /service/users/password
Authorization: Basic <Username/Password>
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

When the username and password combination or thing ID and password combination is verified.

</td>
</tr>
<tr>
<td valign="top" rowspan="9">

401 Unauthorized

</td>
<td valign="top">

PASSWORD\_LOCKED

</td>
<td valign="top">

When the password is locked for 60 minutes.

</td>
</tr>
<tr>
<td valign="top">

PASSWORD\_DISABLED

</td>
<td valign="top">

When the password is disabled.

</td>
</tr>
<tr>
<td valign="top">

USER\_INACTIVE

</td>
<td valign="top">

When the user is not in status active.

</td>
</tr>
<tr>
<td valign="top">

PASSWORD\_RESET\_REQUIRED

</td>
<td valign="top">

When the user must reset his or her password before logon.

</td>
</tr>
<tr>
<td valign="top">

PASSWORD\_CHANGE\_REQUIRED

</td>
<td valign="top">

When the user must change his or her password before logon.

</td>
</tr>
<tr>
<td valign="top">

INITIAL\_PASSWORD\_EXPIRED

</td>
<td valign="top">

When the initial password of the user has expired. After the validity of the initial password expires, the user can't log on to the application and must contact the administrator.

</td>
</tr>
<tr>
<td valign="top">

INVALID\_AUTHORIZATION\_HEADER\_LENGTH

</td>
<td valign="top">

The time-based one-time password \(TOTP\) code is not provided, but Two-Factor Authentication \(TFA\) with TOTP is enabled.

</td>
</tr>
<tr>
<td valign="top">

INVALID\_OTP\_CODE

</td>
<td valign="top">

Wrong TOTP code was provided.

</td>
</tr>
<tr>
<td valign="top">

RBA\_RULE\_ACTION\_DENY

</td>
<td valign="top">

Denied because of a risk-based authentication rule

</td>
</tr>
</table>



### Response Example

On success, the HTTP Response Body contains:

```
 {
       "uid": "P000000",
       "first_name": "Dona",
       "last_name": "Moore",
       "mail": "dona.moore@example.com"
       "type": "employee"
    }
```



**Related Information**  


[SAP Cloud Identity Services Application Directory REST API](sap-cloud-identity-services-application-directory-rest-api-a8fc935.md "Manage application configurations.")

[Identity Directory SCIM REST API](identity-directory-scim-rest-api-5be5692.md "Manage users, groups and custom schemas in the cloud.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

[Invitation REST API](invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

[Forgot Password REST API](forgot-password-rest-api-d024fca.md "The forgot password REST API sends a reset password email.")

[TOTP Validation Service](totp-validation-service-3e4c3cf.md "Validation of time-based one-time password (TOTP).")

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c "The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.")

[Configure Risk-Based Authentication for an Application](../Operation-Guide/configure-risk-based-authentication-for-an-application-bc52fbf.md#loiobc52fbf3d59447bbb6aa22f80d8b6056 "You can define rules for authentication according to different risk factors and apply actions like Allow, Deny, and Two-Factor Authentication.")

[Configure User Access to the Application](../Operation-Guide/configure-user-access-to-the-application-8b147c4.md "You can configure public access to the application allowing self-registration, or you can restrict the access to existing users or users registered by an application.")

[Error and Success Codes](error-and-success-codes-7f87a75.md "This section is to help developers with solutions to the REST API response codes.")

