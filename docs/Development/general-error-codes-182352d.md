<!-- loio182352d4cd814ae8be3dea41129b833e -->

# General Error Codes

The following table lists error codes that may be returned from any method on any resource URI.



<a name="loio182352d4cd814ae8be3dea41129b833e__table_dcv_5yj_qv"/>General Error Codes


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

