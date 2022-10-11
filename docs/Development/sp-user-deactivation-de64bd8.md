<!-- loiode64bd81c6b044fa9f4e795e01218daa -->

# SP User Deactivation

To deactivate an SP \(service provider\) user, you use a `PUT` method.



<a name="loiode64bd81c6b044fa9f4e795e01218daa__section_mbm_1xk_fdb"/>

## Prerequisites

You need to set up the authentication type to access the API. For more information about this configuration, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/users/<SP user ID>`

**HTTP Method:***PUT*



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

`status`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

String



</td>
<td valign="top">

When the user activates his or her e-mail, the `status` is set to **active**. To deactivate the SP user, update the `status` parameter by setting it to **inactive**. To activate the SP user, set it to **active**.



</td>
<td valign="top">

Request body



</td>
</tr>
</table>



### Request Example

```
PUT /service/users/<the ID of the SP user>
Content-type: application/vnd.sap-id-service.sp-user-id+xml; version=1.0

<user>
  <status>inactive</status>
</user>


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

Deactivated



</td>
<td valign="top">

SP user is successfully deactivated



</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [General Error Codes](general-error-codes-182352d.md).

> ### Note:  
> If a user logs into an application he or she is deactivated for, the identity provider will block the logon and notify the application.



### Response Example

```
<Response Consent="urn:oasis:names:tc:SAML:2.0:consent:unspecified"
          Destination="https://example.com/saml2/acs"
          Version="2.0"
          xmlns:ns2="urn:oasis:names:tc:SAML:2.0:assertion"
          xmlns="urn:oasis:names:tc:SAML:2.0:protocol"
          xmlns:ns4="http://www.w3.org/2001/04/xmlenc#"
          xmlns:ns3="http://www.w3.org/2000/09/xmldsig#"
          >
  <ns2:Issuer>accounts.sap.com</ns2:Issuer>
  <Status>
    <StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Responder">
      <StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:AuthnFailed" />
    </StatusCode>
    <StatusMessage>The SP user [URI of the sp user] is with status inactive for Service Provider [example.com]</StatusMessage>
  </Status>
</Response>
```

 

**Related Information**  


[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

