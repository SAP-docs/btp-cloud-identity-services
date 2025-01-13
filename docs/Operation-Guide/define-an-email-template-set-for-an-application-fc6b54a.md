<!-- copyfc6b54a4b81140a5ab5489bc48a9ecd4 -->

# Define an Email Template Set for an Application

Tenant administrators can define the email template set that the application uses.



## Context

Initially, the application uses a default template set with an English language version for all the templates in the set. This template set is named *Default*. If you want to use another email template set, assign it to the respective application.

> ### Note:  
> Both the HTML and TXT formats are included in the emails sent to a user. What the user sees, depends on the settings of his or her email client.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Branding and Layout* tab.

5.  Under *EMAIL CONFIGURATIONS*, choose *Email Template Set*.

6.  Select the radio button of the email template set the application will use.

7.  Save your selection.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.




<a name="copyfc6b54a4b81140a5ab5489bc48a9ecd4__postreq_pmk_qnc_ffb"/>

## Next Steps

\(Optional\) Configure custom mail server. To use own mail server for the emails sent for the different application processes, you should configure your mail server in the administration console for SAP Cloud Identity Services.

For more information, see [Configure Mail Server for Application Processes](configure-mail-server-for-application-processes-ccc7ba1.md).

**Related Information**  


[Create a New Email Template Set](create-a-new-email-template-set-a6fca8b.md "Tenant administrators can create a new set of email templates so that each template in the set can have a custom language version.")

[View Email Template Document](view-email-template-document-148568a.md "Tenant administrators can view language email templates in the template set uploaded in the administration console for SAP Cloud Identity Services.")

[Edit or Add an Email Template Set](edit-or-add-an-email-template-set-3c4f397.md "Tenant administrators can configure language versions of each template in the template set. They can also set a custom template for each language, and change the name of each template set.")

[Delete an Email Template Set](delete-an-email-template-set-6fce69d.md "Tenant administrators can delete an email template set or a language version for a specific application process.")

[Allowed Placeholders per Email Template](allowed-placeholders-per-email-template-c0d4a76.md "This document describes which placeholders can be used in each email template.")

