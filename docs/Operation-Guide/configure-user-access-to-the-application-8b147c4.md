<!-- loio8b147c46269243dd8e5a42feb8b5a2ef -->

# Configure User Access to the Application

You can configure public access to the application allowing self-registration, or you can restrict the access to existing users or users registered by an application.



## Context

You can configure the application to restrict access to specific users only. The following access configurations are possible:

-   **Public**

    All users are allowed to log on. Unregistered users start the self-registration process by choosing the *Register Now* link on the logon page.

    > ### Note:  
    > You have to add as trusted the domains for those applications that allow self-registration to the users. For more information, see [Configure Trusted Domains](configure-trusted-domains-08fa1fe.md).

    > ### Tip:  
    > You can protect the self-registration form against machine registrations via reCAPTCHA. For more information, see [Protecting Application Forms with Google reCAPTCHA](protecting-application-forms-with-google-recaptcha-b84ce17.md). The content in this section is not relevant for China \(Shanghai\) region.

-   **Internal** - this is the default setting.

    Only existing users are allowed to log on. Users that are not in the user store of Identity Authentication cannot log on.

    When this option is chosen, self-registration is not possible.

    > ### Tip:  
    > For more information how to add new users in the user store of Identity Authentication, see [Create a New User](create-a-new-user-348deef.md).
    > 
    > You can also import new users in Identity Authentication via a CSV file. For more information, see [Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md).

-   **Private**

    Only users registered by an application can log on. To register users for a specific application, you have to import these users via a CSV file. For more information, about the user import, see [Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md).




## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Authentication and Access* tab.

5.  Under *AUTHENTICATION*, choose *User Application Access*.

6.  Set the radio button for the users you want to allow to log on:

    -   Public

    -   Internal

    -   Private

7.  Save your selection.

    If the application is updated, the system displays the message ***Application <name of application\> updated***.


**Related Information**  


[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

[Risk-Based Authentication as an Alternative to Restrict User Access Option in Identity Authentication Service](https://scn.sap.com/community/developer-center/cloud-platform/blog/2016/07/13/risk-based-authentication-as-an-alternative-to-the-restrict-user-access-option-in-sap-cloud-identity-service)

