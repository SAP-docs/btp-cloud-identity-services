<!-- loio80ead1a7d3cd4e298b0d32295a11889d -->

# Configure Concurrent User Access to the Application

Tenant administrator can allow or restrict user access to an application from one or more browsers or devices.



## Context

With the concurrent user access option, you as a tenant administrator can configure the system so that based on the requirements the application can allow or restrict multiple sign-ins by one and the same user.

The concurrent access offers three options:

-   **Allow**

    No restrictions are applied. The user can sign in from multiple devices and browsers. This is the default setting.

-   **Warning**
-   The user can sign in from only one device or browser at a time. If other sessions exist, the user receives a message and will have the option to terminate the other session and sign out.

    > ### Remember:  
    > If the user choose the option *Sign Out and Continue*, they can still choose to continue with the new session without terminating the previous one. The system will not terminate the session automatically. If you want to restrict concurrent access, then you should use the *Error* option terminate the other session and sign out.

    > ### Caution:  
    > If you have configured a *Warning* concurrent user access option, you must also have a Single Logout Endpoints \(SLO\) URL with a SOAP binding added for the SAML 2.0 application. Otherwise if a user chooses to sign out and continue to new session, an SLO request for the old session won't be sent to the application.. For more information, see [Configure SAML 2.0 Service Provider](configure-saml-2-0-service-provider-51f1f75.md).

-   **Error**

    The user can sign in from only one device or browser at a time. When the user try to sign in from another device or browser, they see an error message.




## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Authentication and Access* tab.

5.  Under *AUTHENTICATION*, choose *Concurrent Access*.

6.  Set the radio button for the users you want to allow to log on:

    -   Allow

    -   Warning

    -   Error

    If the application is updated, the system displays the message ***Application <name of application\> updated***.


