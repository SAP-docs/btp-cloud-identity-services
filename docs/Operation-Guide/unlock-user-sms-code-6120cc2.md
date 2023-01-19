<!-- loio6120cc2c71114eb38758a5cea3fd699b -->

# Unlock User SMS Code

You can unlock a user SMS code when the user must log on to the application before the automatic unlock time of 60 minutes has passed.



## Context

The user locks his or her SMS code after submitting five incorrect codes when trying to log on to an application that requires SMS two-factor authentication. The code is unlocked automatically after 60 minutes.

> ### Note:  
> When the user locks his or her SMS code, he or she will not be able to log on only to applications that require SMS codes. The applications that do not require SMS two-factor authentication will be accessible only with the user password.

To unlock the user SMS code manually, proceed as follows:



## Procedure

1.  Find the user whose SMS code you want to unlock.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

2.  Select the user that you want to unlock.

    > ### Note:  
    > You can only unlock locked user SMS codes.

3.  Choose the *Authentication* tab.

4.  Choose the *Authentication* tab.

5.  Choose *Multi-Factor Authentication*.

6.  Press *Unlock* under *SMS Status*.

    The system displays the message ***Account <name of user\> unlocked***.


**Related Information**  


[Deactivate Two-Factor Authentication](deactivate-two-factor-authentication-15db825.md "You can deactivate the second factor (passcode or security key) if the user has activated it via the profile page.")

[Deactivate User Devices for TOTP Two-Factor Authentication](deactivate-user-devices-for-totp-two-factor-authentication-87324d5.md "This document shows you how to deactivate the mobile devices used by a user to generate passcodes for access to applications requiring time-based one-time (TOTP) as two-factor authentication. You deactivate the user mobile devices from the administration console for SAP Cloud Identity Services.")

[Unlock User TOTP Passcode](unlock-user-totp-passcode-cb6615d.md "You can unlock a user passcode when the user must log on to the application before the automatic unlock time of 60 minutes has passed.")

[Remove User Device for Web Two-Factor Authentication](remove-user-device-for-web-two-factor-authentication-9529d97.md "This document shows you how to remove the registered devices used by a user for access to applications requiring web two-factor authentication (FIDO2 standard).")

[Allow Users to Protect Accounts with Second Factor for Authentication](allow-users-to-protect-accounts-with-second-factor-for-authentication-d9cbb6d.md "Tenant administrator can allow users to decide whether to protect their own accounts with second factor for authentication or not.")

[Allow Users To Skip Two-Factor Authentication Setup](allow-users-to-skip-two-factor-authentication-setup-dfb08b3.md "You can set the number of days for which the users can postpone the enabling of second factor for authentication.")

