<!-- loio0c0e9d2363e2442f996e7a395c6d6b39 -->

# Enable or Disable Reload Parent Page Option

You can enable or disable the reload of the application's parent page after a successful logon.



<a name="loio0c0e9d2363e2442f996e7a395c6d6b39__prereq_y1l_v55_c2c"/>

## Prerequisites

You have an SAML 2.0 application. The *Reload Parent Page Option* is not visible for OpenID Connect applications.



## Context

The *Reload Parent Page* option specifies whether the application's parent page reloads or not after a successful logon via an overlay page.

> ### Note:  
> By default the *Reload Parent Page* option is enabled. Disable the option if you would like to embed the logon page in your custom iFrame.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Branding and Layout* tab.

5.  Under *LOGIN PAGE BEHAVIOR*, configure the *Reload Parent Page* option.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


