<!-- loioe55429fdaf394acebe6ee950b80b11db -->

# Invitation REST API

The invitation service allows you to implement a request for user invitations. The invitees then receive an e-mail containing information about how to register.



## Prerequisites

-   [API Authentication](../Operation-Guide/api-authentication-9d200d5.md)



## Resources

To configure the invitation service, you use a `POST` request with the following URI: `https://<tenant ID>.accounts.ondemand.com/cps/invite/`.



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

The e-mail of the invitee

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

The URL for the invitation link in the e-mail sent to the invitee. The URL must be a public page.

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

The footer text of the invitation e-mail



</td>
</tr>
<tr>
<td valign="top">

`headerText`



</td>
<td valign="top">

The header text of the invitation e-mail



</td>
</tr>
<tr>
<td valign="top">

`language`



</td>
<td valign="top">

The preferred language for the invitation e-mail. The usage of this parameter does not affect the end-user screens.

Must be a string value specified by a two or four-letter code in one of the following formats: XX, xx, xx-XX or xx\_XX. Otherwise the invitation e-mail is in English.



</td>
</tr>
</table>



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


[Add Logon Overlays in Customer Applications](add-logon-overlays-in-customer-applications-5e98ecf.md "This document describes how service providers that delegate authentication to Identity Authentication can use embedded frames, also called overlays, for the logon pages of their applications.")

[Configure an Application's Home URL](../Operation-Guide/configure-an-application-s-home-url-be6d6f2.md "You can configure the Home URL of an application in the administration console for Identity Authentication.")

[Configure Certificates for API Authentication](../Operation-Guide/configure-certificates-for-api-authentication-c408083.md "This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.")

[Error and Success Codes](error-and-success-codes-7f87a75.md "This section is to help developers with solutions to the REST API response codes.")

