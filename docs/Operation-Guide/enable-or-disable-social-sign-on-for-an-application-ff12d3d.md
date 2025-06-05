<!-- loioff12d3da94914c95a29397270068d0e7 -->

# Enable or Disable Social Sign-On for an Application

Social sign-on allows users to link their Identity Authentication accounts with social network accounts.

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.

To link the accounts, users have to choose the social provider button on the logon page of a cloud application. When authenticated via their social identity provider, users are prompted to allow their accounts to be linked with the social network accounts. After this initial setup, users can log on to the application without additional authentication.



## Prerequisites

You have set the social providers on tenant level. For more information, see [Configuring Social Identity Providers](configuring-social-identity-providers-17d400d.md).



## Context

Identity Authentication allows account linking with the following social providers:

-   Apple
-   Facebook
-   Google
-   LinkedIn
-   X



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Authentication and Access* tab.

5.  Under *AUTHENTICATION*, enable or disable social sign-on.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.




## Results

With *Social Sign-On* users can log on to the application via one of the social providers. They can see this option on the logon page. Which social identity providers logos appear on the logon page of the application depends on the configurations you have made. For more information, see [Configuring Social Identity Providers](configuring-social-identity-providers-17d400d.md).

**Related Information**  


[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

