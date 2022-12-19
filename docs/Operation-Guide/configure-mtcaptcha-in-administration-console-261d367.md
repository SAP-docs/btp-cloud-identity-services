<!-- loio261d3674357d4485b9bfcdb1fabc122c -->

# Configure MTCaptcha in Administration Console

Configure MTCaptcha for your Identity Authentication tenant.



<a name="loio261d3674357d4485b9bfcdb1fabc122c__prereq_xhh_ndh_gcb"/>

## Prerequisites

You have registered the domain of the application and received a Site key and Private key from MTCaptcha.



<a name="loio261d3674357d4485b9bfcdb1fabc122c__context_jks_knf_hnb"/>

## Context



<a name="loio261d3674357d4485b9bfcdb1fabc122c__steps_nyg_xdh_gcb"/>

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

4.  Choose the *MTCaptcha* service.

5.  Enter the information in the provided fields:

    -   ***Site Key*** - enter the Site Key provided from MTCaptcha
    -   ***Secret Key*** - enter the Private Key provided from MTCaptcha

6.  Save your changes.


