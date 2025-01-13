<!-- loiod26427a2c503456bbdfec53d385e0433 -->

# Deactivate TOTP Two-Factor Authentication

This document shows you how to deactivate the TOTP two-factor authentication that you use to access applications requiring passcodes for stronger authentication.



## Context

You can deactivate TOTP two-factor authentication if you don't want to use it anymore to generate passcodes.

> ### Note:  
> If you deactivate the TOTP two-factor authentication, you won't be able to log on to applications that require only passcodes. To be able to access these applications again, you have to activate again TOTP. For more information, see [Activate TOTP Two-Factor Authentication](activate-totp-two-factor-authentication-ab8a323.md).
> 
> If your device that generates passcodes has been lost or stolen, or you can't provide a valid passcode, you can still deactivate the TOTP via the channels offered on the profile page, or contact your system administrator.

Based on the configuration of the account made by the administrator, you can choose among three deactivation channels:

-   *Existing Multi-Factor Authentication* - to verify your identity, choose a verification method:
    -   *TOTP Two-Factor Authentication* - use a passcode generated on your registered device
    -   \(if configured\) *WEB Two-Factor Authentication* - provide security key

-   *Passcode via SMS* - \(if configured\) use a passcode sent to you on your verified phone
-   *Passcode via Email* - \(if configured\) use a passcode sent to you on your verified email

    > ### Caution:  
    > The system can send you up to three emails within 24 hours. After that you won't be able to request a passcode for TOTP deactivation via email during these 24 hours.


To deactivate your mobile device that generates passcodes, proceed as follows:



## Procedure

1.  Access your profile page.

    > ### Note:  
    > If you don't know the URL of your profile page, contact your system administrator.

2.  Press the deactivate button next to *TOTP Two-Factor Authentication*.

3.  Select a deactivation channel:


    <table>
    <tr>
    <th valign="top">

     
    
    </th>
    <th valign="top">

     
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Existing Multi-Factor Authentication**
    
    </td>
    <td valign="top">
    
    Choose one of the verification methods:

    -   *TOTP Two-Factor Authentication* - This is the default choice. Provide the passcode and choose *Send* after selecting that option.
    -   *WEB Two-Factor Authentication* - Your security key \(if configured.\). Follow the onscreen instructions after selecting that option.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Passcode via SMS**
    
    </td>
    <td valign="top">
    
    Provide the passcode and choose *Send* after selecting that option.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Passcode via Email**
    
    </td>
    <td valign="top">
    
    Provide a passcode and choose *Send* after selecting that option.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > The deactivation channels depend on the configuration of the account made by the administrator. You may not see all deactivation channels.

4.  Press *Deactivate*.


**Related Information**  


[Always Authenticate with Second Factor](always-authenticate-with-second-factor-4063b26.md "This document provides information about how to enhance the security of your account by always providing second factor in addition to your primary credentials.")

[Activate TOTP Two-Factor Authentication](activate-totp-two-factor-authentication-ab8a323.md "To log on to applications that require time-based one-time password (TOTP) as two-factor authentication, first you have to activate a mobile device that will generate TOTP passcodes.")

[Add a Device for Web Two-Factor Authentication](add-a-device-for-web-two-factor-authentication-f7eb115.md "To log on to applications that require web two-factor authentication (FIDO2 standard), first you have to activate an authenticator device.")

[Remove Web Two-Factor Authentication](remove-web-two-factor-authentication-3f70669.md "This document shows you how to remove the web two-factor authentication (FIDO2 standard) that you use to access applications requiring it for stronger authentication.")

