<!-- loio0a6727d07b5b42219a337c7db82336b4 -->

# Passwordless Authentication

This document provides information about the passwordless authentication option.

Based on the configurations for the application, you may authenticate with a certificate or biometric information \(something that you are\) without the need to provide your username and password.



<a name="loio0a6727d07b5b42219a337c7db82336b4__section_nrx_tx5_brb"/>

## FIDO2 Biometric Authentication

If biometric authentication is allowed for the application, you can choose the *Biometric Authentication* button on the logon page. If you have a configured FIDO2 biometric authentication device, the logon process will require authentication with the registered device. If biometric authentication isn't configured, you are required to register a device by providing your username and password first. This is a one time configuration.

> ### Note:  
> You can add more than one device via your profile page, but you can't add a device that has already been added, either for biometric authentication or for two-factor authentication.
> 
> You can also remove a device from the list on the profile page. The removal of a device is password protected.

Identity Authentication supports the following:


<table>
<tr>
<th valign="top">

Device

</th>
<th valign="top">

OS

</th>
<th valign="top">

Browser

</th>
</tr>
<tr>
<td valign="top">

Face ID

</td>
<td valign="top">

Latest iOS

</td>
<td valign="top">

-   Latest Chrome
-   Latest Safari



</td>
</tr>
<tr>
<td valign="top">

Touch ID

</td>
<td valign="top">

Latest macOS

</td>
<td valign="top">

-   Latest Chrome
-   Latest Safari



</td>
</tr>
<tr>
<td valign="top">

Windows Hello

</td>
<td valign="top">

Windows 10

</td>
<td valign="top">

-   Latest Edge
-   Latest Chrome



</td>
</tr>
</table>



<a name="loio0a6727d07b5b42219a337c7db82336b4__section_zzk_5x5_brb"/>

## Certificate Authentication

If certificate authentication is allowed for the application, you can generate your own certificate and authenticate with it without the need to provide your username and password.

When certificate authentication is allowed, you can see the *Certificates* section on your profile page. You should go to the profile page and under the *Certificates* section generate your certificate for authentication. You must provide your user password, then the certificate password, and the certificate validity. You can choose from 12 months, three months, and one month.

Once the certificate is generated, it's downloaded to your device. Import the certificate to your certificate store, and it is ready for authentication. Now, when you navigate to the logon page of the application, you are automatically authenticated with the certificate. If the authentication fails, you’re prompted to provide username and password.

