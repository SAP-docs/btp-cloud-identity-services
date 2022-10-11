<!-- loio11121c96ba9143b280e13568638b457a -->

# Enable or Disable Kerberos Authentication for an Application

You enable Kerberos authentication to allow users to log on to an application from the corporate network without entering their username and password.



## Prerequisites

You have configured Kerberos authentication for the tenant. For more information, see [Configure Kerberos Authentication](configure-kerberos-authentication-b030165.md#loiob0301657df074ab081ab7556854aca56).



<a name="loio11121c96ba9143b280e13568638b457a__steps_exh_cyr_4t"/>

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

5.  Under *AUTHENTICATION*, enable or disable SPNEGO authentication.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


**Related Information**  


[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

