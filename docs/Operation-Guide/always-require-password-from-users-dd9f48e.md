<!-- loiodd9f48e7cbd5435ca47aea25cf87b3e8 -->

# Always Require Password from Users

Always require users to provide password when accessing an application.



<a name="loiodd9f48e7cbd5435ca47aea25cf87b3e8__context_sb5_44x_zqb"/>

## Context

By enabling the *Force Authentication* option users must always provide a password when accessing an application. The configuration is per application. The option is switched off by default.

Force authentication can be enabled for both OpenID Connect and SAML 2.0 applications.

To enable force authentication for an application, proceed as follows:



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

4.  Choose the *Authentication and Access* tab.

5.  Еnable the *Force Authentication* option under *Authentication*.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


