<!-- loio12b33953a9164b6084319f4785808a8e -->

# Configuring Password Policies

Passwords for the authentication of users are subject to certain rules. These rules are defined in the password policy. Identity Authentication provides you with two predefined password policies, in addition to which you can create and configure up to three custom password policies.



You have the following options for a password policy:

-   Standard

    \(Predefined\) Use this option to set special rules for changing, resetting, and locking a password.

    > ### Note:  
    > This is the default setting. It meets the minimum strength requirements.

-   Enterprise

    \(Predefined\) Use this option to set enhanced password management features. It’s stronger than the standard policy, but weaker than the custom one.

-   Custom

    \(Configurable\) Use this option to set the strongest password management features for the password policy. It's the responsibility of the tenant administrator to configure the custom password policy stronger than the standard and enterprise ones.

    > ### Remember:  
    > This option is only possible if you’ve configured a custom password policy in the administration console for SAP Cloud Identity Services. For more information, see [Configure Custom Password Policy](configure-custom-password-policy-67bece2.md).


**Password Policy Requirements**


<table>
<tr>
<th valign="top">

Requirement

</th>
<th valign="top">

Standard

</th>
<th valign="top">

Enterprise

</th>
<th valign="top">

Custom

</th>
</tr>
<tr>
<td valign="top">

Content of password

</td>
<td valign="top">

-   Minimum length of 8 characters;
-   Maximum length of 255 characters;
-   Characters from at least three of the following groups:
    -   Lower-case Latin characters \(a-z\)
    -   Upper-case Latin characters \(A-Z\)
    -   Base 10 digits \(0-9\)
    -   Non-alphabetic characters




</td>
<td valign="top">

-   Minimum length of 8 characters;
-   Maximum length of 255 characters;
-   Characters from at least three of the following groups:
    -   Lower-case Latin characters \(a-z\)
    -   Upper-case Latin characters \(A-Z\);
    -   Base 10 digits \(0-9\)
    -   Non-alphabetic characters




</td>
<td valign="top">

-   Minimum length of 8 characters;
-   Maximum length of 255 characters;
-   Characters from between 1 and 4 of the following groups:

    -   Lower-case Latin characters \(a-z\);
    -   Upper-case Latin characters \(A-Z\);
    -   Base 10 digits \(0-9\);
    -   Non-alphabetic characters

    > ### Note:  
    > The default is at least three of the groups.




</td>
</tr>
<tr>
<td valign="top">

Session time limit

Indicates when the current session expires.

</td>
<td valign="top">

Yes, 12 hours

</td>
<td valign="top">

Yes, 12 hours

</td>
<td valign="top">

Yes, 12 hours

</td>
</tr>
<tr>
<td valign="top">

"Remember me" option

Indicates whether the browser can store a cookie with the credentials.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Forgot password deactivation period

Indicates the period during which users can initiate the number of forgot password emails specified by the forgot password counter.

</td>
<td valign="top">

Yes, 24 hours

</td>
<td valign="top">

Yes, 24 hours

</td>
<td valign="top">

Yes, 24 hours

</td>
</tr>
<tr>
<td valign="top">

Forgot password counter

Indicates how many times a user can initiate forgot password emails during the deactivation period. For example, a user can initiate up to 3 forgot password emails within 24 hours.

</td>
<td valign="top">

Yes, 3

</td>
<td valign="top">

Yes, 3

</td>
<td valign="top">

Yes, 3

</td>
</tr>
<tr>
<td valign="top">

Minimum password age

Shows the minimum lifetime of a password before it can be changed.

</td>
<td valign="top">

Unlimited

</td>
<td valign="top">

Yes, 24 hours

</td>
<td valign="top">

Yes, minimum 1 hour, maximum 48 hours

</td>
</tr>
<tr>
<td valign="top">

Maximum failed logon attempts

Indicates how many logon attempts are allowed before the user password is locked.

</td>
<td valign="top">

Yes, 5

</td>
<td valign="top">

Yes, 5

</td>
<td valign="top">

Yes, minimum 1, maximum 6, default choice 5

</td>
</tr>
<tr>
<td valign="top">

Password locked period

Indicates how long a password is locked for.

</td>
<td valign="top">

Yes, 1 hour

</td>
<td valign="top">

Yes, 1 hour

</td>
<td valign="top">

Yes, minimum 1 hour, maximum *unlimited*

> ### Note:  
> If *unlimited* is set, the password can be unlocked only by the tenant administrator. For more information, see [Unlock User Password](unlock-user-password-9172552.md).

> ### Caution:  
> If *unlimited* is selected, email template set must also be changed. Otherwise, the user will receive an email stating that password logon to the account was disabled for - 1 hour. For more information, see [Configuring Email Templates](configuring-email-templates-b2afbcd.md).



</td>
</tr>
<tr>
<td valign="top">

Maximum password age

Shows the maximum lifetime of a password before it has to be changed.

</td>
<td valign="top">

Unlimited

</td>
<td valign="top">

Yes, 6 months

</td>
<td valign="top">

Yes, minimum 1 month, maximum *unlimited*

Possible values: 1 month, 2 months, … 6 months; 1 year, 2 years, 3 years; unlimited

</td>
</tr>
<tr>
<td valign="top">

Password history

Indicates whether a password history is retained, and how many passwords from the history are retained.

</td>
<td valign="top">

Unlimited

</td>
<td valign="top">

Yes, the last 5 passwords are retained.

</td>
<td valign="top">

Yes, minimum the last 5 passwords, and maximum the last 20 passwords are retained.

</td>
</tr>
<tr>
<td valign="top">

Maximum unused period

Indicates how long the system retains unused passwords for.

</td>
<td valign="top">

Unlimited

</td>
<td valign="top">

Yes, 6 months

</td>
<td valign="top">

Yes, minimum 1 month, maximum 6 months

</td>
</tr>
<tr>
<td valign="top">

Password behavior

Indicates possibility to force the user to reset or change password if the applied password policy requires stronger password than the current one.

</td>
<td valign="top">

Not Applicable

</td>
<td valign="top">

Scenario Based

-   *Reset password* - If a user hasn’t used the password during the set user inactivity period, the system will force a password reset at the first logon after the inactivity period expires.
-   *Change password* - If a user hasn't changed the password within the password lifetime, the system will force a password change at the first logon after the maximum password age period expires.



</td>
<td valign="top">

Yes, administrator can choose from:

-   *Reset password*
-   *Change password*



</td>
</tr>
</table>

> ### Note:  
> The non-alphabetic characters are all characters that are not lower-case Latin characters \(a-z\), upper-case Latin characters \(A-Z\), or base 10 digits \(0-9\).

As a tenant administrator, you can do the following:

**Related Information**  


[Configuring Applications](configuring-applications-61ad3b0.md "This section describes how you can configure the user authentication, access to an application, and use a branding style in accordance with your company requirements. It also explains the trust configuration between Identity Authentication and a service provider or client (relying party).")

[Configuring Tenant Settings](configuring-tenant-settings-d4d6fdc.md "Initially, the tenants are configured to use default settings. This section describes how you as a tenant administrator can make custom tenant configurations.")

[Configuring Privacy Policies](configuring-privacy-policies-ed48466.md "You can configure a custom privacy policy document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Configuring Authorization Policies](configuring-authorization-policies-982ac5f.md "Authorization Management enables SAP Cloud Identity Services administrators to use authorization policies, customize them, and assign them to users.")

[Configuring Terms of Use](configuring-terms-of-use-61d3a86.md "You can configure a custom terms of use document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Configuring Email Templates](configuring-email-templates-b2afbcd.md "Tenant administrators can use the default or a custom email template set for the application processes.")

[Managing Administrators](managing-administrators-786eea2.md "This section describes how, as a tenant administrator, you can list all administrators in the administration console for SAP Cloud Identity Services, add new administrators, and edit the administrator authorizations. You can also remove administrators.")

[Managing Users](managing-users-228428f.md "Tenant administrators can manage user accounts via the administration console for SAP Cloud Identity Services, and via APIs.")

[Managing Groups](managing-groups-ddd067c.md "Tenant administrators can create groups, and assign and unassign these groups to users via the administration console for SAP Cloud Identity Services.")

[Configuring Provisioning Systems](configuring-provisioning-systems-f149f76.md "Configure provisioning systems for synchronizing users and groups between business applications.")

[Configuring Real-Time Provisioning](configuring-real-time-provisioning-617dd4b.md "As a tenant administrator, you can configure real-time provisioning to immediately provision entities from source to target systems.")

[Configuring Social Identity Providers](configuring-social-identity-providers-17d400d.md "By configuring a social provider, users can log on to applications with their social media credentials by linking their accounts in Identity Authentication to the social media account.")

[Integrating with Existing Customer Landscape](integrating-with-existing-customer-landscape-cf29ea1.md "Identity Authentication can be integrated with already existing customer landscape and supports different types of delegated authentication.")

[Configuring External Authentication Providers](configuring-external-authentication-providers-4f02f94.md "Configure authentication providers in the administration console for SAP Cloud Identity Services to manage users from external providers.")

[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

