<!-- loio046a2352009f45b9a87eb9dc7478a8df -->

# Enable Users to Recover Password with PIN Code

Users can choose to provide PIN code to reset their password.



<a name="loio046a2352009f45b9a87eb9dc7478a8df__prereq_vnp_bcg_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

> ### Caution:  
> For security reasons, the PIN Code is not a recommended password recovery method. The users can follow the *Forgot Password* link on the sign in page to reset their password via email.

You can configure the applications in the tenant to allow users to provide PIN code to reset their password instead of receiving an email with a reset password link.

For this setup, you as a tenant administrator, configure the PIN code option in the *Tenant Settings* section in the administration console, and the users set their PIN code in the profile page.

Once the PIN code is configured, the user can use this option to reset the password. The user must have set their PIN code in the profile page to be able to reset password via this option.

If the PIN code option is configured in the admin console, end users that haven't set up their PIN code are triggered to do it as a post logon step. Optionally, they can choose to set up the PIN code later.

If end users choose the *Don't ask me again* check box, the prompt won't be shown anymore. End users still can set up the PIN code in their profile page.

**PIN Code Characteristics**


<table>
<tr>
<th valign="top">

Characteristics

</th>
<th valign="top">

Notes

</th>
</tr>
<tr>
<td valign="top">

Allowed Characters

</td>
<td valign="top">

Base 10 digits \(0-9\)

</td>
</tr>
<tr>
<td valign="top">

Min Length

</td>
<td valign="top">

Between 4 and 32 characters; configurable on tenant level

</td>
</tr>
<tr>
<td valign="top">

Max Length

</td>
<td valign="top">

32 characters

</td>
</tr>
<tr>
<td valign="top">

Required

</td>
<td valign="top">

*Setup later* and *Don't ask me again* are configurable

</td>
</tr>
<tr>
<td valign="top">

Target Users

</td>
<td valign="top">

-   *Users without email* - only users that don't have emails are able to reset password via PIN code
-   *All users* - everyone can choose this option to reset the password
-   *Specific groups* - only users that belong to the selected groups can reset password via PIN code.



</td>
</tr>
<tr>
<td valign="top">

Lock

</td>
<td valign="top">

The reset password action with PIN code locks after 5 failed attempts. The logon with correct username and password is not interrupted.

</td>
</tr>
<tr>
<td valign="top">

Unlock

</td>
<td valign="top">

To unlock the PIN code, set an initial password for the user.

</td>
</tr>
</table>

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

To configure PIN code option in the administration console, follow the procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Authentication*, choose the *Password Recovery* list item.

4.  Select the *PIN Code* tab.

5.  Choose *Edit* \> *Enabled*.

6.  Under *Target Users*, choose users that can reset passwords with PIN code:

    -   *Users without email*
    -   *All users* - default choice
    -   *Specific groups*

        > ### Restriction:  
        > The administrator must be assigned the *Manage Groups* role or be part of a policy that allows reading groups to be able to view the groups in the list. For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md) or [Configure Group Authorizations](configure-group-authorizations-7a09cad.md).

        > ### Note:  
        > When you select this option, you must specify the specific group or groups for which you enable password recovery via PIN code.


7.  Under *PIN Length*, choose the minimum required length of the PIN code.

8.  **Optional:** Under *User Options*, select the *Show "Setup later"* check box.

    When selected, the end users see the option to set up the PIN code later.

9.  **Optional:** Under *User Options*, select the *Show "Don't ask again"* check box.

    When selected, the end users see the option to hide the prompt to set up their PIN code.

10. Save your configuration.

    You can see information about your settings.


**Related Information**  


[Enable Users to Recover Password with Security Questions](enable-users-to-recover-password-with-security-questions-d9ae898.md "Users can choose to answer security questions to reset their password.")

[Enable Users to Recover Password via Email](enable-users-to-recover-password-via-email-5b9f909.md "Users can choose to receive a link via email to reset their password.")

[Enable Users to Reset Password via Profile Page](enable-users-to-reset-password-via-profile-page-22bd253.md "Enable the users to trigger reset password process via the profile page.")

