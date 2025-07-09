<!-- loio3db7c1ecbf874fbeb6b07cdfb57bd2ab -->

# Enable Google reCAPTCHA for Application Forms

Enable Google reCAPTCHA for the registration form, login page, and the phone verification pages of the application.



<a name="loio3db7c1ecbf874fbeb6b07cdfb57bd2ab__prereq_bcc_z2h_gcb"/>

## Prerequisites

-   You have registered the domain of the application and received a Site key and Secret key from Google. For more information, see [Get Site Key and Secret Key from Google for reCAPTCHA](get-site-key-and-secret-key-from-google-for-recaptcha-4cbf06c.md).

-   You have configured the *Google reCAPTCHA* option in the administration console for SAP Cloud Identity Services. For more information, see [Configure Google reCAPTCHA in Administration Console](configure-google-recaptcha-in-administration-console-77c87ba.md).




<a name="loio3db7c1ecbf874fbeb6b07cdfb57bd2ab__context_psp_4nf_hnb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.



<a name="loio3db7c1ecbf874fbeb6b07cdfb57bd2ab__steps_of2_by2_gcb"/>

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


