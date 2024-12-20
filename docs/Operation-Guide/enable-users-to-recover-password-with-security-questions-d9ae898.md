<!-- loiod9ae898222f04a689440bc7fd2cab182 -->

# Enable Users to Recover Password with Security Questions

Users can choose to answer security questions to reset their password.



<a name="loiod9ae898222f04a689440bc7fd2cab182__prereq_vjp_ybg_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

You can configure the applications in the tenant to allow users to answer security questions to reset their password instead of receiving an email with a reset password link.

For this setup, you as a tenant administrator, configure the security questions option in the *Tenant Settings* section in the administration console, and the users configure their answers in the profile page. Once the security questions and answers are configured, the user can use this option to reset the password. The user must have configured their answers in the profile page to be able to reset password via security questions.

If the security questions option is configured in the admin console, end users that haven't set up their security questions are triggered to do it as a post logon step. Optionally, they can choose to set up the security questions later. If end users choose the *Don't ask me again* check box, the prompt won't be shown anymore. End users still can set up the security questions in their profile page.

> ### Note:  
> You can choose whether the *Setup later* and *Don't ask me again* options are visible for the end users.

Tenant administrator can offer up to 10 predefined questions, and can choose which target users to be able to reset their password via security questions. There are three options:

-   *None* - the security questions option isn’t offered to the users and all security questions configurations in the administration console are disabled
-   *Users without email* - only users that don't have emails can reset password via security questions.
-   *All users* - everyone can choose this option to reset the password
-   *Specific groups* - only users that belong to the selected groups can reset password via security questions.

If *Home URL* is configured, users are redirected to the URL defined in the *Home URL* after resetting their passwords via Security Questions. If *Home URL* is not configured users are redirected to the profile page.

> ### Caution:  
> The security questions option locks after five wrong answers to the security questions. To unlock it, set an initial password for the user. For more information, see [Set Initial Password](set-initial-password-16149d5.md).

> ### Remember:  
> It takes 2 minutes for the configuration changes to take place.

To configure security questions in the administration console, follow the procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Under *Authentication*, choose the *Password Recovery* list item.

4.  Choose the *Security Questions* tab.

5.  Choose *Edit* \> *Enabled*.

6.  Under *Target Users*, choose users that can reset passwords with security questions:

    -   *None* - default choice

        > ### Note:  
        > If selected, the security questions configurations in the administration console are disabled

    -   *Users without email*
    -   *All users*
    -   *Specific groups*

        > ### Restriction:  
        > The administrator must be assigned the *Manage Groups* role or be part of a policy that allows reading groups to be able to view the groups in the list. For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md) or [Configure Group Authorizations](configure-group-authorizations-7a09cad.md).

        > ### Note:  
        > When you select this option, you must specify the specific group or groups for which you enable password recovery via security questions.


7.  Under *Number of Security Questions*, choose how many questions the user must answer.

8.  **Optional:** Under *User Options*, select the *Show "Setup later"* check box.

    When selected, the end users see the option to setup the security questions later.

9.  **Optional:** Under *User Options*, select the *Show "Don't ask again"* check box.

    When selected, the end users see the option to hide the prompt to setup their security questions later.

10. Save your configuration.

    You can see information about your settings and the 10 predefined questions the user can choose from..


**Related Information**  


[Enable Users to Recover Password with PIN Code](enable-users-to-recover-password-with-pin-code-046a235.md "Users can choose to provide PIN code to reset their password.")

[Enable Users to Recover Password via Email](enable-users-to-recover-password-via-email-5b9f909.md "Users can choose to receive a link via email to reset their password.")

