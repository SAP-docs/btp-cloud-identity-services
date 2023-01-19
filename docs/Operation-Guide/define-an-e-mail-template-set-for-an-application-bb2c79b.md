<!-- loiobb2c79b71f8d47ec877882d78e0ceb39 -->

# Define an E-Mail Template Set for an Application

Tenant administrators can define the e-mail template set that the application uses.



## Context

Initially, the application uses a default template set with an English language version for all the templates in the set. This template set is named *Default*. If you want to use another e-mail template set, assign it to the respective application.

> ### Note:  
> Both the HTML and TXT formats are included in the e-mails sent to a user. What the user sees, depends on the settings of his or her e-mail client.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Branding and Layout* tab.

5.  Under *E-MAIL CONFIGURATIONS*, choose *E-Mail Template Set*.

6.  Select the radio button of the e-mail template set the application will use.

7.  Save your selection.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.




<a name="loiobb2c79b71f8d47ec877882d78e0ceb39__postreq_pmk_qnc_ffb"/>

## Next Steps

\(Optional\) Configure custom mail server. To use own mail server for the e-mails sent for the different application processes, you should configure your mail server in the administration console for SAP Cloud Identity Services.

For more information, see [Configure Mail Server for Application Processes](configure-mail-server-for-application-processes-ccc7ba1.md).

