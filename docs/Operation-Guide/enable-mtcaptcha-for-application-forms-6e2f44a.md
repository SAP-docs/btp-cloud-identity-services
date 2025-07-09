<!-- loio6e2f44ad02554b40b575f8e37dacb280 -->

# Enable MTCaptcha for Application Forms

Enable MTCaptcha for the registration form, login page, and the phone verification pages of the application.



<a name="loio6e2f44ad02554b40b575f8e37dacb280__prereq_bcc_z2h_gcb"/>

## Prerequisites

-   You have registered the domain of the application and received a Site key and Private key from MTCaptcha. For more information, see [Get Site Key and Private Key for MTCaptcha](get-site-key-and-private-key-for-mtcaptcha-2f74e1c.md).

-   You have configured the *MTCaptcha* option in the administration console. For more information, see [Configure MTCaptcha in Administration Console](configure-mtcaptcha-in-administration-console-261d367.md).




<a name="loio6e2f44ad02554b40b575f8e37dacb280__context_psp_4nf_hnb"/>

## Context



<a name="loio6e2f44ad02554b40b575f8e37dacb280__steps_of2_by2_gcb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Branding and Layout* tab.

5.  Under *APPLICATION FORMS CUSTOMIZATION*, choose *CAPTCHA Protection*.

6.  Enable the CAPTCHA protection for the relevant application form:

    -   *Registration Form*

        > ### Remember:  
        > You must have allowed self-registration for the application. For more information, see [Configure User Access to the Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/configure-user-access-to-application). Choose Public access.

    -   *Login Page*
    -   *Phone Verification*

        > ### Remember:  
        > You must have enabled phone verification for the application. For more information, see [Enable Phone Verification for an Application](enable-phone-verification-for-an-application-24c9b51.md).


7.  Save your configuration.

    If the operation is successful, you receive the following message: ***Application <Application Name\> updated***. The slider next to enabled application form is switched to *ON*.

    > ### Note:  
    > If you do not want to use CAPTCHA protection for an application form, you can drag the slider next to it to *OFF*.


