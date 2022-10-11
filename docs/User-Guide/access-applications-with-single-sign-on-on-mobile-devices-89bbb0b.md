<!-- loio89bbb0b282594043bbc61536baddc63b -->

# Access Applications with Single Sign-On on Mobile Devices

You can access trusted applications that require two-factor authentication via your mobile devices using single sign-on \(SSO\).



## Prerequisites

-   The application requires passcode as additional protection.
-   You have a mobile device.
-   You have installed and configured an SAP Authenticator on your mobile device. For more details see, [One-Time Password Authentication User Guide](https://help.sap.com/viewer/a2ee572048674dd4bef257616560cc94/3.0/en-US/7028b8b842634767936040f1d16a7c50.html). SAP Authenticator runs on both iOS and Android mobile operating systems.

-   You have activated your mobile device for two-factor authentication. For more details about how to activate a device for two-factor authentication, see [Activate TOTP Two-Factor Authentication](activate-totp-two-factor-authentication-ab8a323.md).



## Context

This feature allows you to access applications via your mobile device without the need to type manually your username, password, and passcode. The first time you access the application, you will be prompted to provide your credentials. If you have enabled the *Remember me* functionality, you will be logged on next time based on the cookie saved in the browser. For more details about the *Remember me* functionality, see Related Information.



<a name="loio89bbb0b282594043bbc61536baddc63b__steps_plz_2yx_3t"/>

## Procedure

1.  Launch SAP Authenticator on your mobile device.

2.  Add the application in the SAP Authenticator.

    To add the application, you need to scan a QR code or type the application's link manually. Your administrator should provide you with the QR code or the application's link. The link follows the following pattern:

    `https://<tenant_ID>.accounts.ondemand.com/saml2/idp/sso?sp=<sp_name>[&RelayState=<sp_specific_value>&index=<index_number>]&j_username=[username]&j_otpcode=[passcode]` 

    > ### Note:  
    > If you don't know the URL of your profile page, contact your system administrator.

3.  Log on to the application via SAP Authenticator.

4.  Select the *Remember me* checkbox.

5.  Provide your credentials.




## Results

You are now logged on to the application. Next time you try to log on to this application via SAP Authenticator, you will not have to provide your credentials and a passcode. The system will log you on automatically.

**Related Information**  


[Multi-Factor Authentication](multi-factor-authentication-0d41cd4.md "This document provides information about the second factor for authentication or how to log on if you are asked to provide a second factor to your primary credentials.")

[Use the Remember Me Option](use-the-remember-me-option-bc7c6c6.md "With the Remember me functionality enabled, you can log on to an application without the need to provide your credentials every time you access it.")

