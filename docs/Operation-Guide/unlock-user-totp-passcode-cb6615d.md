<!-- loiocb6615de96df4a1fa33d13d208f29905 -->

# Unlock User TOTP Passcode

You can unlock a user passcode when the user must log on to the application before the automatic unlock time of 60 minutes has passed.



## Context

The user locks his or her passcode after submitting five incorrect passcodes when trying to log on to an application that requires time-based one-time \(TOTO\) two-factor authentication. The passcode is unlocked automatically after 60 minutes.

> ### Note:  
> When the user locks his or her TOTP passcode, he or she will not be able to log on only to applications that require TOTP passcodes. The applications that do not require two-factor authentication will be accessible only with the user password.

To unlock the user TOTP passcode manually, proceed as follows:



## Procedure

1.  Find the user whose TOTP passcode you want to unlock.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

2.  Select the user that you want to unlock.

    > ### Note:  
    > You can only unlock locked user TOTP passcodes.

3.  Choose the *Authentication* tab.

4.  Choose *Multi-Factor Authentication*.

5.  Press *Unlock* under *Passcode Status*.

    The system displays the message ***Account <name of user\> unlocked***.


**Related Information**  


[Deactivate Two-Factor Authentication](deactivate-two-factor-authentication-15db825.md "You can deactivate the second factor (passcode or security key) if the user has activated it via the profile page.")

[Deactivate User Devices for TOTP Two-Factor Authentication](deactivate-user-devices-for-totp-two-factor-authentication-87324d5.md "This document shows you how to deactivate the mobile devices used by a user to generate passcodes for access to applications requiring time-based one-time (TOTP) as two-factor authentication. You deactivate the user mobile devices from the administration console for Identity Authentication")

[Remove User Device for Web Two-Factor Authentication](remove-user-device-for-web-two-factor-authentication-9529d97.md "This document shows you how to remove the registered devices used by a user for access to applications requiring web two-factor authentication (FIDO2 standard).")

[Unlock User SMS Code](unlock-user-sms-code-6120cc2.md "You can unlock a user SMS code when the user must log on to the application before the automatic unlock time of 60 minutes has passed.")

