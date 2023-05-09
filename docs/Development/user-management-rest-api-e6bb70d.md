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

**Related Information**  


[Identity Directory SCIM REST API](identity-directory-scim-rest-api-5be5692.md "Manage users, groups and custom schemas in the cloud.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

[Invitation REST API](invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[Password Service REST API](password-service-rest-api-8d1016b.md "The password service is used for operations related to user passwords, such as verification of the user name and the password combination.")

[Forgot Password REST API](forgot-password-rest-api-d024fca.md "The forgot password REST API sends a reset password e-mail.")

[TOTP Validation Service](totp-validation-service-3e4c3cf.md "Validation of time-based one-time password (TOTP).")

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c "The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.")

[General Error Codes](general-error-codes-182352d.md "The following table lists error codes that may be returned from any method on any resource URI.")

