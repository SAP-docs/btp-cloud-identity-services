<!-- loio04a6e45997164a53b65e15374e2b2c2c -->

# Set a Password Policy for an Application

As a tenant administrator, you can set a password policy that matches your application logon requirements.



## Context

You can choose from standard, enterprise, and custom password policies. The standard and enterprise password policies are predefined, and you cannot configure them. You can configure only the custom password policy.

The strength of the policies grows from standard to custom.

When a user is authenticated for specific application, or there is already an active session with that application, Identity Authentication checks the application's requirement for password policy and the current user's password policy and always applies the stronger policy. Thus even if the application doesn't require an enterprise password policy if the user has already authenticated in application which requires enterprise password policy then the enterprise password policy rules will be applied even if the user accesses an application that doesn't require it.

> ### Tip:  
> To see the configuration of the password policies in the tenant, go to *Password Polices* tile and choose the ![](images/DisplayPassPolicy_38584e8.png) icon next to the policy you want to view.

To set a password policy for an application, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Authentication and Access* tab.

5.  Under *POLICIES*, choose *Password Policy*.

6.  Select the radio button for the password policy.

7.  Save your selection.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.

    > ### Note:  
    > Changes may take up to 2 minutes. Users will then sign in according to the new policy. When the user tries to sign in to the application whose password policy has been updated, he or she is prompted to change the password if the current one does not meet the requirements in the updated password policy.


**Related Information**  


[Configure Custom Password Policy](configure-custom-password-policy-67bece2.md "Tenant administrators can create and configure a custom password policy for scenarios where Identity Authentication is the authenticating authority.")

[Delete Custom Password Policy](delete-custom-password-policy-697fd2b.md "As a tenant administrator, you can delete the custom password policy that you have created.")

[Configure Password Exclude List](configure-password-exclude-list-159c09d.md "As a tenant administrator, you can create a password exclude list to restrict their usage.")

[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

[Configure Custom Password Policy](configure-custom-password-policy-67bece2.md "Tenant administrators can create and configure a custom password policy for scenarios where Identity Authentication is the authenticating authority.")

