<!-- loioebf830604b334e09a0b0a7d553f4bd9f -->

# Enable or Disable FIDO2 Biometric Authentication for an Application

Allow users to log on to applications with biometric information without the need to provide username and password.



<a name="loioebf830604b334e09a0b0a7d553f4bd9f__context_sb5_44x_zqb"/>

## Context

By configuring FIDO2 biometric authentication, users can log on to applications with their biometric information such as fingerprint, face scan, etc., without the need to provide username and password.

Once the biometric authentication is enabled, the user can choose the *Biometric Authentication* button on the logon page. If the user has a configured biometric authentication device, the logon process will require authentication with the registered device. If biometric authentication isn't configured, the user is required to log on with username and password first. After that he or she should visit their profile page and register a device in the *WEB Two-Factor Authentication* section. This is a onetime configuration.

> ### Note:  
> The user can add more than one device, but can't add a device that has already been added, either for biometric authentication or for two-factor authentication. He or she can remove a device from the list on the profile page. The removal of a device is password protected.

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

The user can manage the biometric authentication settings at the profile page.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Authentication and Access* tab.

5.  Under *AUTHENTICATION*, enable or disable biometric authentication.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.




<a name="loioebf830604b334e09a0b0a7d553f4bd9f__postreq_lhn_f2r_brb"/>

## Next Steps

Enable the *Credential change* security alert emailing to inform the user when a biometric authentication device is activated or deactivated. For more information, see [Send Security Alert Emails](send-security-alert-emails-c977464.md).

**Related Information**  


[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

