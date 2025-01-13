<!-- loio483d26cb9a844ff1890530f3e078f088 -->

# Enable Email Verification

Tenant administrators can configure applications to require verification of the user's email address.



## Context

Applications can be configured to require users to have their email addresses verified before they can log on. If you want to make sure that a user has a valid email address, even if the email address has not been verified, you should enable the email verification option in the administration console for SAP Cloud Identity Services.

> ### Note:  
> You can check whether the user's email address has been verified by choosing *User Management* \> *Details* \> *Personal Information* in the administration console. The *Email Verified* box is checked if the user's email address has been verified. For more information about the user details, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Authentication and Access* tab.

5.  Under *AUTHENTICATION*, enable *Email Verification*.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.




<a name="loio483d26cb9a844ff1890530f3e078f088__result_ovm_hqg_jdb"/>

## Results

When the user tries to log on, he or she is asked to verify the email address first. To verify the email, the user must click the link sent to him or her. Once the email address has been verified, the user can log on to the application.

> ### Remember:  
> Identity Authentication can send to the user up to three emails \(forgot password, reset password, locked password, email verification\) per 24 hours.
> 
> If the user must receive more than three emails, the administrator must reset the counter for email sending first. For more information, see [Reset Counter for Email Sending](reset-counter-for-email-sending-08f634b.md).

