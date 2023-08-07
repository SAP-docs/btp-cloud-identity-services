<!-- loio7f87a75e546843da86d054e55f8818e2 -->

# Error and Success Codes

This section is to help developers with solutions to the REST API response codes.



## Error Codes

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

The requested resource resides on a URI other than the requested one.You need to set up the authentication type to access the API.



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

In addition to the general error codes, the REST APIs return one of the following detailed error codes as an *X-message-code* HTTP response header:

**Detailed Error Codes**


<table>
<tr>
<th valign="top">

REST API



</th>
<th valign="top">

X-message code



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="3">

Invitation REST API



</td>
<td valign="top">

INVITATION\_API\_PARAMETER\_INCORRECT



</td>
<td valign="top">

You have used an invalid parameter.



</td>
</tr>
<tr>
<td valign="top">

INVITATION\_API\_EMAIL\_INCORRECT



</td>
<td valign="top">

You have specified an incorrect address or the email address does not exist.



</td>
</tr>
<tr>
<td valign="top">

PASSWORD\_LOCKED



</td>
<td valign="top">

The password is locked for 60 minutes after 5 failed logon attempts with wrong value.



</td>
</tr>
<tr>
<td valign="top">

User Management REST API



</td>
<td valign="top">

PASSWORD\_LOCKED



</td>
<td valign="top">

The password is locked for 60 minutes after 5 failed logon attempts with wrong value.



</td>
</tr>
<tr>
<td valign="top">

Update Group Resource SCIM REST API



</td>
<td valign="top">

Mismatched group id



</td>
<td valign="top">

The **`id` of the group** in the URI and the `id` of the group in the request body are different. Make sure that the `id` of the group is one and the same in both places.



</td>
</tr>
</table>



## Success Codes


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

*200*



</td>
<td valign="top">

OK



</td>
<td valign="top">

Operation successful.



</td>
</tr>
<tr>
<td valign="top">

*201*



</td>
<td valign="top">

Created



</td>
<td valign="top">

Entity created successfully.



</td>
</tr>
<tr>
<td valign="top">

*204*



</td>
<td valign="top">

No Content



</td>
<td valign="top">

The service received and understood the request, but there is no need to send any content back.



</td>
</tr>
</table>



Check also the troubleshooting scenarios available in the Guided Answers tool.

See [Guided Answers](https://ga.support.sap.com/dtp/viewer/#/tree/2065/actions/26547:29111).

**Related Information**  


[Getting Support](../getting-support-06818b2.md "This document is to help users, administrators, and developers deal with issues from Identity Authentication.")

