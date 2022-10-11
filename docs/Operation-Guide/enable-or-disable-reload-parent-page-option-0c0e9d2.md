<!-- loio0c0e9d2363e2442f996e7a395c6d6b39 -->

# Enable or Disable Reload Parent Page Option

You can enable or disable the reload of the application's parent page after a successful logon.



## Context

The *Reload Parent Page* option specifies whether the application's parent page reloads or not after a successful logon via an overlay page.

> ### Note:  
> By default the *Reload Parent Page* option is enabled. Disable the option if you would like to embed the logon page in your custom iFrame.



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

5.  Under *LOGIN PAGE BEHAVIOR*, configure the *Reload Parent Page* option.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


