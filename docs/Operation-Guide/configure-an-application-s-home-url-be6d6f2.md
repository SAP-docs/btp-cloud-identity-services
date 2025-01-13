<!-- loiobe6d6f210d30404d827f8c9e78ec4489 -->

# Configure an Application's Home URL

You can configure the *Home URL* of an application in the administration console for SAP Cloud Identity Services.



## Context

Users are redirected to the *Home URL* after activating their accounts, when they are created via a CSV file import or the user registration service of Identity Authentication. Initially, the *Home URL* for an application is not configured in the administration console for SAP Cloud Identity Services. Once the *Home URL* has been set, you can change it.

> ### Recommendation:  
> From a usability perspective we recommend you to use URL of a protected page.

> ### Remember:  
> *Home URL* is necessary when you import new users in Identity Authentication. Identity Authentication needs to send activation emails to the new users and the home URL has to be mentioned in the e-mails. To access the application, the users have to activate their accounts. For more information see [Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md).

To configure the *Home URL*, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Edit* button on the top right corner.

5.  Type the address in the *Application Home URL* field in the dialog box that appears.

    > ### Tip:  
    > From a usability perspective we recommend you to use URL for a protected page.

6.  Save your changes.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


**Related Information**  


[Invitation REST API](../Development/invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Registration](../Development/user-registration-0aa433c.md "The user registration is used for registration of new users or for on-behalf registration of partners.")

