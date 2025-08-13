<!-- loio5b9f9097b9c2490d9a57fecb3fa7ef0b -->

# Enable Users to Recover Password via Email

Users can choose to receive a link via email to reset their password.



<a name="loio5b9f9097b9c2490d9a57fecb3fa7ef0b__prereq_vnp_bcg_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

The *Email* option in the administration console is enabled by default. If the *Email* option is enabled and *Profile Page* option is disabled, users can choose to receive a link via email to reset their password when they click the *Forgot password* link when they sign-in.

When the *Email* option is enabled and *Profile Page* option is disabled, users can also change their password directly in the profile page. When accessing the profile page, they see the *Change* button. By choosing *Change*, the user needs to provide the current and the new passwords to the system.

> ### Remember:  
> If you disable the *Email* option, at least one of the other two password recovery options must be enabled for a user. Before you disable the email, view your other password recovery settings and select `All users` for *Target users*. For more information, see [Enable Users to Recover Password with Security Questions](enable-users-to-recover-password-with-security-questions-d9ae898.md) or [Enable Users to Recover Password with PIN Code](enable-users-to-recover-password-with-pin-code-046a235.md).

> ### Caution:  
> Be careful also that if you disable the *Email* option, when the *Profile Page* option is enabled, both options will be disabled. For more information, see [Enable Users to Reset Password via Profile Page](enable-users-to-reset-password-via-profile-page-22bd253.md).

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

To enable the *Email* option in the administration console, follow the procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Authentication*, choose the *Password Recovery* list item.

4.  Select the *Email* tab.

5.  Choose *Edit* and select *Enabled*.

6.  Save your configuration.

    You can see information about your settings.




<a name="loio5b9f9097b9c2490d9a57fecb3fa7ef0b__result_ons_2zh_hgc"/>

## Results

Users can choose to receive a link via email to reset their password when click the *Forgot password* link on the sign-in page.

> ### Caution:  
> Be careful if you disable the *Email* option. Disabling the *Email* option when the *Profile Page* option is enabled will disable both options. For more information, see [Enable Users to Reset Password via Profile Page](enable-users-to-reset-password-via-profile-page-22bd253.md).

**Related Information**  


[Enable Users to Recover Password with Security Questions](enable-users-to-recover-password-with-security-questions-d9ae898.md "Users can choose to answer security questions to reset their password.")

[Enable Users to Recover Password with PIN Code](enable-users-to-recover-password-with-pin-code-046a235.md "Users can choose to provide PIN code to reset their password.")

[Enable Users to Reset Password via Profile Page](enable-users-to-reset-password-via-profile-page-22bd253.md "Enable the users to trigger reset password process via the profile page.")

