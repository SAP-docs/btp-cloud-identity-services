<!-- loiodfb08b3fe61d4469bf26d15b31914c04 -->

# Allow Users To Skip Two-Factor Authentication Setup

You can set the number of days for which the users can postpone the enabling of second factor for authentication.



<a name="loiodfb08b3fe61d4469bf26d15b31914c04__prereq_jwn_jnl_lvb"/>

## Prerequisites

-   You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have configured the application or the tenant to require two-factor authentication. For more information, see [Configure Risk-Based Authentication for an Application](configure-risk-based-authentication-for-an-application-bc52fbf.md#loiobc52fbf3d59447bbb6aa22f80d8b6056) or [Configure Default Risk-Based Authentication for All Applications in the Tenant](configure-default-risk-based-authentication-for-all-applications-in-the-tenant-1aab51a.md#loio1aab51ae62b94f79b4c6dac7a00857c2).




## Context

The number of days for which users can postpone the enabling of second factor can be set between 1 and 14 days. The configuration is valid for all applications in the tenant.

If the tenant or application requires two-factor authentication, and the users don't have an enabled two-factor authentication method, or the method that is enabled is not among the ones required by the application, at sign-in users can choose to skip the enabling of two-factor authentication for the period defined by the tenant administrator. The users can sign in without providing a second factor until the grace period expires.

Users can be notified for their choice, if the security alert notification is switched on. They receive a security alert email after they first skip the enabling of two-factor. For more information about how to configure the e-mail alerts, see [Send Security Alert Emails](send-security-alert-emails-c977464.md).



<a name="loiodfb08b3fe61d4469bf26d15b31914c04__steps_efc_qml_lvb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Choose the *Multi-Factor Authentication* list item.

4.  Under *Additional Settings for Multi-Factor Authentication*, manually configure the number of days for which users can postpone the enabling of second factor.

    If the operation is successful, the system displays the message ***Additional Multi-Factor Authentication Settings updated***.


**Related Information**  


[Deactivate Two-Factor Authentication](deactivate-two-factor-authentication-15db825.md "You can deactivate the second factor (passcode or security key) if the user has activated it via the profile page.")

[Deactivate User Devices for TOTP Two-Factor Authentication](deactivate-user-devices-for-totp-two-factor-authentication-87324d5.md "This document shows you how to deactivate the mobile devices used by a user to generate passcodes for access to applications requiring time-based one-time (TOTP) as two-factor authentication. You deactivate the user mobile devices from the administration console for SAP Cloud Identity Services.")

[Unlock User TOTP Passcode](unlock-user-totp-passcode-cb6615d.md "You can unlock a user passcode when the user must log on to the application before the automatic unlock time of 60 minutes has passed.")

[Remove User Device for Web Two-Factor Authentication](remove-user-device-for-web-two-factor-authentication-9529d97.md "This document shows you how to remove the registered devices used by a user for access to applications requiring web two-factor authentication (FIDO2 standard).")

[Unlock User SMS Code](unlock-user-sms-code-6120cc2.md "You can unlock a user SMS code when the user must log on to the application before the automatic unlock time of 60 minutes has passed.")

[Allow Users to Protect Accounts with Second Factor for Authentication](allow-users-to-protect-accounts-with-second-factor-for-authentication-d9cbb6d.md "Tenant administrator can allow users to decide whether to protect their own accounts with second factor for authentication or not.")

