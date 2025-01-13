<!-- loioe55429fdaf394acebe6ee950b80b11db -->

# Invitation REST API

The invitation service allows you to implement a request for user invitations. The invitees then receive an email containing information about how to register.



## Prerequisites

-   [API Authentication](../Operation-Guide/api-authentication-9d200d5.md)



## Resources

To configure the invitation service, you use a `POST` request with the following URI: <code>https://&lt;Cloud Identity Services domain&gt;/cps/invite/</code>.

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).



## Representation

You have to use a JSON representation of the invitation request by specifying *application/json* content type. All declared parameters in the request must also be JSON encoded.



## Parameters

**Required Parameters for the POST Method**


<table>
<tr>
<th valign="top">

Required Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`inviteeEmail`

</td>
<td valign="top">

The email of the invitee

> ### Note:  
> Only `inviteeEmail` or `inviteeUserId` should be used, not both.



</td>
</tr>
<tr>
<td valign="top">

`inviteeUserId`

</td>
<td valign="top">

The user ID of the invitee

> ### Note:  
> Only `inviteeEmail` or `inviteeUserId` should be used, not both.



</td>
</tr>
<tr>
<td valign="top">

`inviterName`

</td>
<td valign="top">

The display name of the user who sends the invitation.

</td>
</tr>
<tr>
<td valign="top">

`targetUrl`

</td>
<td valign="top">

The URL that the user is redirected to after registration.

> ### Recommendation:  
> From a usability perspective we recommend уоu to use URL of a protected page.

> ### Note:  
> The `targetUrl` parameter is optional if a *Home URL* is set for the application, and the application does not use overlay.
> 
> If `targetUrl` is not specified, or the application uses overlay, the user is redirected to the application's *Home URL*, which must be set.

For more information how to configure *Home URL*, see [Configure an Application's Home URL](../Operation-Guide/configure-an-application-s-home-url-be6d6f2.md).

</td>
</tr>
<tr>
<td valign="top">

`sourceUrl`

</td>
<td valign="top">

The URL for the invitation link in the email sent to the invitee. The URL must be a public page.

> ### Note:  
> The `sourceUrl` parameter is optional if a *`Home URL`* is set for the application, and the application does not use overlay.

If `sourceUrl` is not specified, or the application uses overlay, the user is redirected to the application's *Home URL*, which must be set.

For more information how to configure *Home URL*, see [Configure an Application's Home URL](../Operation-Guide/configure-an-application-s-home-url-be6d6f2.md).

</td>
</tr>
</table>

**Optional Parameters for the POST Method**


<table>
<tr>
<th valign="top">

Optional Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`inviteeFirstName`

</td>
<td valign="top">

The first name of the invitee

</td>
</tr>
<tr>
<td valign="top">

`inviteeLastName`

</td>
<td valign="top">

The last name of the invitee

</td>
</tr>
<tr>
<td valign="top">

`footerText`

</td>
<td valign="top">

The footer text of the invitation email

</td>
</tr>
<tr>
<td valign="top">

`headerText`

</td>
<td valign="top">

The header text of the invitation email

</td>
</tr>
<tr>
<td valign="top">

`language`

</td>
<td valign="top">

The preferred language for the invitation email. The usage of this parameter does not affect the end-user screens.

Must be a string value specified by a two or four-letter code in one of the following formats: XX, xx, xx-XX or xx\_XX. Otherwise the invitation email is in English.

</td>
</tr>
</table>



## Example

```
POST /cps/invite/
Content-Type: application/json
 {
  "inviteeEmail": "john.miller@company.com",
  "inviteeFirstName": "John",
  "inviteeLastName": "Miller",
  "inviterName": "Donna Moore",
  "footerText": "Invitation footer sample text",
  "headerText": "Invitation header sample text",
  "targetUrl": "http://www.myserviceprovider.com/protected_home_page/",
  "sourceUrl": "http://www.myserviceprovider.com/public_home_page/"
 }

```

**Related Information**  


[Application Configurations API](application-configurations-api-a8fc935.md "Manage application configurations.")

[Identity Directory API](identity-directory-api-5be5692.md "Manage users, groups and custom schemas in the cloud.")

[Identity Provisioning API](identity-provisioning-api-4433374.md "Manage identity lifecycle processes for cloud and on-premise systems.")

[Identity Authentication API \(Deprecated\)](identity-authentication-api-deprecated-2f21568.md "Deprecated.")

[Migrating Deprecated Identity Authentication API to Identity Directory API](migrating-deprecated-identity-authentication-api-to-identity-directory-api-106dbe0.md "Migrating from the Identity Authentication API to Identity Directory API.")

[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

[Password Service REST API](password-service-rest-api-8d1016b.md "The password service is used for operations related to user passwords, such as verification of the user name and the password combination.")

[Forgot Password REST API](forgot-password-rest-api-d024fca.md "The forgot password REST API sends a reset password email.")

[TOTP Validation Service](totp-validation-service-3e4c3cf.md "Validation of time-based one-time password (TOTP).")

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c "The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.")

[Add Logon Overlays in Customer Applications](add-logon-overlays-in-customer-applications-5e98ecf.md "This document describes how service providers that delegate authentication to Identity Authentication can use embedded frames, also called overlays, for the logon pages of their applications.")

[Configure an Application's Home URL](../Operation-Guide/configure-an-application-s-home-url-be6d6f2.md "You can configure the Home URL of an application in the administration console for SAP Cloud Identity Services.")

[Configure Certificates for API Authentication](../Operation-Guide/configure-certificates-for-api-authentication-c408083.md "This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.")

[Error and Success Codes](error-and-success-codes-7f87a75.md "This section is to help developers with solutions to the REST API response codes.")

