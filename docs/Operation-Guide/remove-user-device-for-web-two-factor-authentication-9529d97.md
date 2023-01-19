<!-- loio9529d97ddd5f4d6bbba71d30d8356a8c -->

# Remove User Device for Web Two-Factor Authentication

This document shows you how to remove the registered devices used by a user for access to applications requiring web two-factor authentication \(FIDO2 standard\).



## Context

You remove the user's device by deleting it from the administration console for SAP Cloud Identity Services.

> ### Note:  
> When you remove the device, the user will no longer be able to log on to applications that require web authentication. To be able to access them again the user has to activate a new device on the user profile page or when prompted when logging on to an application. For more information, see the Related Information.

To remove the devices registered for web authentication, proceed as follows:



## Procedure

1.  Find and select the user whose device you want to remove.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

2.  Choose the *Authentication* tab.

3.  Choose *Multi-Factor Authentication*.

4.  Under *Web* delete the device that you want to remove.


**Related Information**  


[Deactivate Two-Factor Authentication](deactivate-two-factor-authentication-15db825.md "You can deactivate the second factor (passcode or security key) if the user has activated it via the profile page.")

[Deactivate User Devices for TOTP Two-Factor Authentication](deactivate-user-devices-for-totp-two-factor-authentication-87324d5.md "This document shows you how to deactivate the mobile devices used by a user to generate passcodes for access to applications requiring time-based one-time (TOTP) as two-factor authentication. You deactivate the user mobile devices from the administration console for SAP Cloud Identity Services.")

[Unlock User TOTP Passcode](unlock-user-totp-passcode-cb6615d.md "You can unlock a user passcode when the user must log on to the application before the automatic unlock time of 60 minutes has passed.")

[Unlock User SMS Code](unlock-user-sms-code-6120cc2.md "You can unlock a user SMS code when the user must log on to the application before the automatic unlock time of 60 minutes has passed.")

[Allow Users to Protect Accounts with Second Factor for Authentication](allow-users-to-protect-accounts-with-second-factor-for-authentication-d9cbb6d.md "Tenant administrator can allow users to decide whether to protect their own accounts with second factor for authentication or not.")

[Allow Users To Skip Two-Factor Authentication Setup](allow-users-to-skip-two-factor-authentication-setup-dfb08b3.md "You can set the number of days for which the users can postpone the enabling of second factor for authentication.")

