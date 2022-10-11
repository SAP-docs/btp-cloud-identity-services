<!-- loio6e2f44ad02554b40b575f8e37dacb280 -->

# Enable MTCaptcha for Application Forms

Enable Google reCAPTCHA for the registration form and login page of the application.



<a name="loio6e2f44ad02554b40b575f8e37dacb280__prereq_bcc_z2h_gcb"/>

## Prerequisites

-   You have registered the domain of the application and received a Site key and Private key from MTCaptcha. For more information, see [Get Site Key and Private Key for MTCaptcha](get-site-key-and-private-key-for-mtcaptcha-2f74e1c.md).

-   You have configured the *MTCaptcha* option in the administration console for Identity Authentication. For more information, see [Configure MTCaptcha in Administration Console](configure-mtcaptcha-in-administration-console-261d367.md).




<a name="loio6e2f44ad02554b40b575f8e37dacb280__context_psp_4nf_hnb"/>

## Context



<a name="loio6e2f44ad02554b40b575f8e37dacb280__steps_of2_by2_gcb"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Branding and Layout* tab.

5.  Under *APPLICATION FORMS CUSTOMIZATION*, choose *CAPTCHA Protection*.

6.  Enable the CAPTCHA protection for the relevant application form:

    -   *Registration Form*
    -   *Login Page*

7.  Save your configuration.

    If the operation is successful, you receive the following message: ***Application <Application Name\> updated***. The slider next to enabled application form is switched to *ON*.

    > ### Note:  
    > If you do not want to use CAPTCHA protection for an application form, you can drag the slider next to it to *OFF*.


