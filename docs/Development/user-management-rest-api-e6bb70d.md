<!-- loioe6bb70d5e43c4ff89ff700beb82b25fe -->

# User Management REST API

This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.



<a name="loioe6bb70d5e43c4ff89ff700beb82b25fe__section_mbm_1xk_fdb"/>

## Prerequisites

You need to set up the authentication type to access the API. For more information about this configuration, see [API Authentication](../Operation-Guide/api-authentication-9d200d5.md).



## Methods

 


<table>
<tr>
<th valign="top">

HTTP Method



</th>
<th valign="top">

Action



</th>
<th valign="top">

URI



</th>
</tr>
<tr>
<td valign="top">

*POST*



</td>
<td valign="top">

[User Registration](user-registration-0aa433c.md)



</td>
<td valign="top">

`https://<tenant ID>.accounts.ondemand.com/service/users`



</td>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

[SP User ID Retrieval](sp-user-id-retrieval-ead62fc.md)



</td>
<td valign="top">

`https://<tenant ID>.accounts.ondemand.com/service/users`



</td>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

[SP User Information](sp-user-information-dc96d56.md)



</td>
<td valign="top">

`https://<tenant ID>.accounts.ondemand.com/service/users/<SP user ID>`



</td>
</tr>
<tr>
<td valign="top">

*PUT*



</td>
<td valign="top">

[SP User Deactivation](sp-user-deactivation-de64bd8.md)



</td>
<td valign="top">

`https://<tenant ID>.accounts.ondemand.com/service/users/<SP user ID>`



</td>
</tr>
<tr>
<td valign="top">

*DELETE*



</td>
<td valign="top">

[SP User Deletion](sp-user-deletion-dba2028.md)



</td>
<td valign="top">

`https://<tenant ID>.accounts.ondemand.com/service/users/<SP user ID>`



</td>
</tr>
</table>

