<!-- loio22bd253aa231464d84dc500cc00cf6e2 -->

# Enable Users to Reset Password via Profile Page

Enable the users to trigger reset password process via the profile page.



<a name="loio22bd253aa231464d84dc500cc00cf6e2__prereq_vnp_bcg_ppb"/>

## Prerequisites

-   You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have enabled the *Email* option for password recovery in the administration console. For more information, see [Enable Users to Recover Password via Email](enable-users-to-recover-password-via-email-5b9f909.md)



## Context

The *Profile Page* option is disabled by default. If the *Email* option is enabled and *Profile Page* option is disabled, users can change their password directly in the profile page. When accessing the profile page, they see the *Change* button. By choosing *Change*, the user needs to provide the current and the new passwords to the system.

Your scenario may require additional confirmation of the password change via email, before the new password is applied. You can do this by enabling the *Profile Page* option, which is visible only when the *Email* option is enabled. When accessing the profile page, users see the *Reset* button. By choosing *Reset*, the user triggers a manual password reset from the profile page. To reset the password the user must have an access to the email.

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

To enable the *Profile Page* option in the administration console, follow the procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Authentication*, choose the *Password Recovery* list item.

4.  Select the *Email* tab.

    > ### Remember:  
    > Make sure that the *Email* option is enabled. If not, choose *Edit*, enable it, and save your changes.

5.  Next to *Profile Page*, choose *Edit* and select *Enabled*.

6.  Save your configuration.

    You can see information about your settings.




<a name="loio22bd253aa231464d84dc500cc00cf6e2__result_pqp_133_hgc"/>

## Results

When accessing the profile page, users see the *Change* button in the *Password* section.

**Related Information**  


[Enable Users to Recover Password with Security Questions](enable-users-to-recover-password-with-security-questions-d9ae898.md "Users can choose to answer security questions to reset their password.")

[Enable Users to Recover Password with PIN Code](enable-users-to-recover-password-with-pin-code-046a235.md "Users can choose to provide PIN code to reset their password.")

[Enable Users to Recover Password via Email](enable-users-to-recover-password-via-email-5b9f909.md "Users can choose to receive a link via email to reset their password.")

