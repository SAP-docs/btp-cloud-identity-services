<!-- loio1a55c4b5012f4f529e5c6d53c8fe8872 -->

# Mobile Single Sign-On

This document provides information about the mobile single sign-on \(SSO\) option.

The mobile single sign-on \(SSO\) option allows users to access applications protected with two-factor authentication without manually entering the one-time password \(OTP\) via SAP Authenticator.

Mobile single sign-on is applicable only when the applications are accessed via identity provider \(IdP\)-initiated single sign-on \(SSO\). For more details about IdP-initiated SSO, see Related Information.

You also have to comply with the URL requirements for these applications. Users can add applications in SAP Authenticator by scanning a QR code. The code can be sent to them by the administrator, or by typing the application's URL. The URL must have the following format:

`https://<tenant_ID>.accounts.ondemand.com/saml2/idp/sso?sp=<sp_name>[&RelayState=<sp_specific_value>&index=<index_number>]&j_username=[username]&j_otpcode=[passcode]` 

> ### Note:  
> The QR code represents this URL. When SAP Authenticator calls the URL, it replaces \[username\] in the URL with the specified account name and \[passcode\] with two consecutive passcodes.

**Related Information**  


[Configure IdP-Initiated SSO](configure-idp-initiated-sso-5d59caa.md)

[Use the Remember Me Option](../User-Guide/use-the-remember-me-option-bc7c6c6.md "With the Remember me functionality enabled, you can log on to an application without the need to provide your credentials every time you access it.")

[One-Time Password Authentication User Guide](https://help.sap.com/viewer/a2ee572048674dd4bef257616560cc94/3.0/en-US/7028b8b842634767936040f1d16a7c50.html)

