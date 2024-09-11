<!-- loio228428f9f476449cafd841a68d75b234 -->

# Managing Users

Tenant administrators can manage user accounts via the administration console for SAP Cloud Identity Services, and via APIs.

The user management enables you to create, modify, and delete users and their attributes, and manage the user accounts in the user store of Identity Authentication.

> ### Note:  
> For more information about the users that are authenticated with their corporate credentials from the corporate user store, see [Corporate User Store \(Neo Environment\)](corporate-user-store-neo-environment-461d71c.md#loio461d71c148594608b9c8b6d016e0a0c5).

> ### Remember:  
> To perform user management operations, you must be assigned an administrator role or roles that include the relevant authorizations for the operation. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

With user management, you can perform the following activities:

****


<table>
<tr>
<th valign="top">

Activity

</th>
<th valign="top">

Description

</th>
<th valign="top">

Procedure

</th>
</tr>
<tr>
<td valign="top" rowspan="3">

Create user

</td>
<td valign="top">

Create users via the *Add* option in the administration console

</td>
<td valign="top">

[Create a New User](create-a-new-user-348deef.md) 

</td>
</tr>
<tr>
<td valign="top">

Create users via a CSV file import in the administration console

</td>
<td valign="top">

[Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md) 

</td>
</tr>
<tr>
<td valign="top">

Create users programmatically via API

</td>
<td valign="top">

[Create User Resource \(Deprecated\)](../Development/create-user-resource-deprecated-cea8778.md) 

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Search users

</td>
<td valign="top">

Search users in the administration console

</td>
<td valign="top">

[Search Users](search-users-06078a6.md) 

</td>
</tr>
<tr>
<td valign="top">

Search users via API

</td>
<td valign="top">

[Users Search \(Deprecated\)](../Development/users-search-deprecated-3af7dfa.md) 

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

List and edit user details

</td>
<td valign="top">

List a specific user and edit the information about that user via the administration console

</td>
<td valign="top">

[List and Edit User Details](list-and-edit-user-details-045cb01.md) 

</td>
</tr>
<tr>
<td valign="top">

List and update user details via API

</td>
<td valign="top">

-   [User Resource \(Deprecated\)](../Development/user-resource-deprecated-7ae17a6.md)
-   [Update User Resource \(Deprecated\)](../Development/update-user-resource-deprecated-9e36479.md)



</td>
</tr>
<tr>
<td valign="top">

Update user details via a CSV file import

</td>
<td valign="top">

[Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md) 

</td>
</tr>
<tr>
<td valign="top">

Manage user password via the administration console

</td>
<td valign="top">

-   [Unlock User Password](unlock-user-password-9172552.md)

-   [Send Reset Password Email](send-reset-password-email-da55abf.md)

-   [Reset Counter for Email Sending](reset-counter-for-email-sending-08f634b.md)

-   [Set Initial Password](set-initial-password-16149d5.md)




</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Delete users

</td>
<td valign="top">

Delete users via the administration console

</td>
<td valign="top">

[Delete Users](delete-users-bbfaf5f.md) 

</td>
</tr>
<tr>
<td valign="top">

Delete users programmatically via API

</td>
<td valign="top">

[Delete User Resource \(Deprecated\)](../Development/delete-user-resource-deprecated-436015d.md) 

</td>
</tr>
<tr>
<td valign="top">

Manage the user group assignment

</td>
<td valign="top">

Assign and unassign groups via the administration console

</td>
<td valign="top">

-   [Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md)
-   [Unassign Groups from a User](unassign-groups-from-a-user-4353735.md)



</td>
</tr>
</table>

**Related Information**  


[Configuring Applications](configuring-applications-61ad3b0.md "This section describes how you can configure the user authentication, access to an application, and use a branding style in accordance with your company requirements. It also explains the trust configuration between Identity Authentication and a service provider or client (relying party).")

[Configuring Tenant Settings](configuring-tenant-settings-d4d6fdc.md "Initially, the tenants are configured to use default settings. This section describes how you as a tenant administrator can make custom tenant configurations.")

[Configuring Password Policies](configuring-password-policies-12b3395.md "Passwords for the authentication of users are subject to certain rules. These rules are defined in the password policy. Identity Authentication provides you with two predefined password policies, in addition to which you can create and configure up to three custom password policies.")

[Configuring Privacy Policies](configuring-privacy-policies-ed48466.md "You can configure a custom privacy policy document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Configuring Authorization Policies](configuring-authorization-policies-982ac5f.md "Authorization management enables SAP Cloud Identity Services administrators to use authorization policies, customize them, and assign them to users.")

[Configuring Terms of Use](configuring-terms-of-use-61d3a86.md "You can configure a custom terms of use document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Configuring Email Templates](configuring-email-templates-b2afbcd.md "Tenant administrators can use the default or a custom email template set for the application processes.")

[Managing Administrators](managing-administrators-786eea2.md "This section describes how, as a tenant administrator, you can list all administrators in the administration console for SAP Cloud Identity Services, add new administrators, and edit the administrator authorizations. You can also remove administrators.")

[Managing Groups](managing-groups-ddd067c.md "Tenant administrators can create groups, and assign and unassign these groups to users via the administration console for SAP Cloud Identity Services.")

[Configuring Provisioning Systems](configuring-provisioning-systems-f149f76.md "Configure provisioning systems for synchronizing users and groups between business applications.")

[Configuring Real-Time Provisioning](configuring-real-time-provisioning-617dd4b.md "As a tenant administrator, you can configure real-time provisioning to immediately provision entities from source to target systems.")

[Configuring Social Identity Providers](configuring-social-identity-providers-17d400d.md "By configuring a social provider, users can log on to applications with their social media credentials by linking their accounts in Identity Authentication to the social media account.")

[Integrating with Existing Customer Landscape](integrating-with-existing-customer-landscape-cf29ea1.md "Identity Authentication can be integrated with already existing customer landscape and supports different types of delegated authentication.")

[Configuring External Authentication Providers](configuring-external-authentication-providers-4f02f94.md "Configure authentication providers in the administration console for SAP Cloud Identity Services to manage users from external providers.")

[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

[Troubleshooting for Administrators](troubleshooting-for-administrators-f80beb5.md "This section is intended to help administrators deal with error messages in the administration console for SAP Cloud Identity Services.")

