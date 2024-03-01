<!-- loiod024fcabb2f042d08b1c00c3d408e107 -->

# Forgot Password REST API

The forgot password REST API sends a reset password email.



The language of the reset password email is defined in the following order of importance:

**Custom Template Sets Configured for Application**

1.  If the user is set with a specific language:
    1.  if the language exists in the custom template, the system sends the reset password email in that language
    2.  if the language does not exist in the custom template, the system sends the reset password email in English, if English exists in the custom template set
    3.  if the language of the user, and the English language do not exist in the custom template, the system sends the reset password email in English from the *Default* template set

2.  If the user is not set with a specific language:
    1.  if English exists in the custom template set, the system sends the reset password email in English from the custom template set
    2.  if English does not exist in the custom template set, the system sends the reset password email in English from the *Default* template set


**Default Template Set Configured for Application**

If the user is set with a specific language, the system sends the reset password email in that language, if it exists in the *Default* set. Otherwise, it sends the reset password email in English from the *Default* template set.

For more information about the email template sets, see [Configuring Email Templates](../Operation-Guide/configuring-email-templates-b2afbcd.md).

> ### Tip:  
> [Configure SAML 2.0 Service Provider](../Operation-Guide/configure-saml-2-0-service-provider-51f1f75.md).



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/users/forgotPassword`

> ### Note:  
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).

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

`identifier`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

supported attributes:

-   email

    > ### Tip:  
    > If email is mandatory, for users without valid email addresses or for testing purposes use the `sap-test.de` domain, for example `<username>@sap-test.de`. Do not use any other existing or nonexisting domains.

-   loginName
-   uid



</td>
<td valign="top">

Request body

</td>
</tr>
</table>



### Request Example

```
{
    "identifier": "dona.moore@example.com"
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

Reason

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

The user exists and password reset is allowed for the user profile.

</td>
<td valign="top">

Forgot password email is sent to the provided user.

> ### Note:  
> Forgot password email is not sent when the response is **200 OK** in following cases:
> 
> -   the user does not exist
> -   the limit of three forgot password e-mails sent for the last 24 hours has been reached



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

400 Bad Request

</td>
<td valign="top">

PASSWORD\_TOO\_NEW

</td>
<td valign="top">

When the password has already been changed for the last 24 hours..

</td>
</tr>
<tr>
<td valign="top">

USER\_INACTIVE

</td>
<td valign="top">

When the user status is `inactive`.

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
</table>



**Related Information**  


[SAP Cloud Identity Services Application Directory REST API](sap-cloud-identity-services-application-directory-rest-api-a8fc935.md "Manage application configurations.")

[Identity Directory SCIM REST API](identity-directory-scim-rest-api-5be5692.md "Manage users, groups and custom schemas in the cloud.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

[Invitation REST API](invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

[Password Service REST API](password-service-rest-api-8d1016b.md "The password service is used for operations related to user passwords, such as verification of the user name and the password combination.")

[TOTP Validation Service](totp-validation-service-3e4c3cf.md "Validation of time-based one-time password (TOTP).")

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c "The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.")

[List and Edit User Details](../Operation-Guide/list-and-edit-user-details-045cb01.md "As a tenant administrator, you can view detailed information about the users in the administration console for SAP Cloud Identity Services. Optionally you can edit this information.")

[Error and Success Codes](error-and-success-codes-7f87a75.md "This section is to help developers with solutions to the REST API response codes.")

