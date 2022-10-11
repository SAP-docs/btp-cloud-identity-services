<!-- loio77c87ba6c5254d7aaac6a710838000a8 -->

# Configure Google reCAPTCHA in Administration Console

Configure Google reCAPTCHA for your Identity Authentication tenant.



<a name="loio77c87ba6c5254d7aaac6a710838000a8__prereq_xhh_ndh_gcb"/>

## Prerequisites

You have registered the domain of the application and received a Site key and Secret key from Google. For more information, see [Get Site Key and Secret Key from Google for reCAPTCHA](get-site-key-and-secret-key-from-google-for-recaptcha-4cbf06c.md).



<a name="loio77c87ba6c5254d7aaac6a710838000a8__context_jks_knf_hnb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.



<a name="loio77c87ba6c5254d7aaac6a710838000a8__steps_nyg_xdh_gcb"/>

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

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page you can view the administrative and license relevant information of the tenant.

3.  Choose the *CAPTCHA Service* list item.

4.  Choose the*Google reCAPTCHA* service.

5.  Enter the ***Site Key*** and ***Secret Key*** you received from Google for reCAPTCHA.

6.  Save your changes.


