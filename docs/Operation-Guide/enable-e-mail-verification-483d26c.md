<!-- loio483d26cb9a844ff1890530f3e078f088 -->

# Enable E-Mail Verification

Tenant administrators can configure applications to require verification of the user's e-mail address.



## Context

Applications can be configured to require users to have their e-mail addresses verified before they can log on. In some cases, when you can create new users. If you want to make sure that a user has a valid e-mail address, even if the e-mail address has not been verified, you should enable the e-mail verification option in the administration console for SAP Cloud Identity Services.

> ### Note:  
> You can check whether the user's e-mail address has been verified by choosing *User Management* \> *User Details* \> *Personal Information* in the administration console. The *E-Mail Verified* box is checked if the user's e-mail address has been verified. For more information about the user details, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

3.  Choose the *Authentication and Access* tab.

4.  Under *AUTHENTICATION*, enable *E-Mail Verification*.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.




<a name="loio483d26cb9a844ff1890530f3e078f088__result_ovm_hqg_jdb"/>

## Results

When the user tries to log on, he or she is asked to verify the e-mail address first. To verify the e-mail, the user must click the link sent to him or her. Once the e-mail address has been verified, the user can log on to the application.

> ### Remember:  
> Identity Authentication can send to the user up to three e-mails \(forgot password, reset password, locked password, e-mail verification\) per 24 hours.
> 
> If the user must receive more than three e-mails, the administrator must reset the counter for e-mail sending first. For more information, see [Reset Counter for E-Mail Sending](reset-counter-for-e-mail-sending-08f634b.md).

