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
    -   Lower-case Latin characters \(a-z\);
    -   Upper-case Latin characters \(A-Z\);
    -   Base 10 digits \(0-9\);
    -   Non-alphabetic characters \(!@\#$%...\);




</td>
<td valign="top">

-   Minimum length of 8 characters;
-   Maximum length of 255 characters;
-   Characters from at least three of the following groups:
    -   Lower-case Latin characters \(a-z\);
    -   Upper-case Latin characters \(A-Z\);
    -   Base 10 digits \(0-9\);
    -   Non-alphabetic characters \(!@\#$%...\);




</td>
<td valign="top">

-   Minimum length of 8 characters;
-   Maximum length of 255 characters;
-   Characters from between 1 and 4 of the following groups:

    -   Lower-case Latin characters \(a-z\);
    -   Upper-case Latin characters \(A-Z\);
    -   Base 10 digits \(0-9\);
    -   Non-alphabetic characters \(!@\#$%...\);

    > ### Note:  
    > The default is at least three of the the groups.




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

Indicates the period during which users can initiate the number of forgot password e-mails specified by the forgot password counter.



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

Indicates how many times a user can initiate forgot password e-mails during the deactivation period. For example, a user can initiate up to 3 forgot password e-mails within 24 hours.



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

No



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

Indicates how long a password is locked for. Indicates how many logon attempts are allowed before the user password is locked.



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
> If *unlimited* is selected, e-mail template set must also be changed. Otherwise, the user will receive an e-mail stating that password logon to the account was disabled for - 1 hour. For more information, see [Configuring E-Mail Templates](configuring-e-mail-templates-b2afbcd.md).



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

No



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

No



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

No



</td>
<td valign="top">

No



</td>
<td valign="top">

Yes, administrator can choose from:

-   *Reset password*
-   *Change password*



</td>
</tr>
</table>

As a tenant administrator, you can do the following:

