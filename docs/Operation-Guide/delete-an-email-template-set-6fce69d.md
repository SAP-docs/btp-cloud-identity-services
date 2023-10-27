<!-- loio6fce69d5b6c34d1589160ad7f6df67ed -->

# Delete an Email Template Set

Tenant administrators can delete an email template set or a language version for a specific application process.



## Context

You can delete only email template sets that aren’t assigned to applications. If you want to delete an email template that is assigned to an application, first you must choose another email template set for the applications.

You can’t delete the default template set.

If you delete a language version for specific application process, users receive the email from the default template set for this process. If you delete the email template for the self-registration process, for example, users receive the default activation email when they complete the registration.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Email Template Sets* tile.

    This operation opens a list of the template sets.

3.  Choose the list item of the template set you want to edit.


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Result
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Select the tab signifying the process, and delete the respective language version of the template. Repeat the operation as many times as necessary.**
    
    </td>
    <td valign="top">
    
    Deletes a language version for specific application process.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Choose the *Delete* button at the lower right corner of the screen.
    
    </td>
    <td valign="top">
    
    Deletes the entire email template set
    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Create a New Email Template Set](create-a-new-email-template-set-a6fca8b.md "Tenant administrators can create a new set of email templates so that each template in the set can have a custom language version.")

[View Email Template Document](view-email-template-document-148568a.md "Tenant administrators can view language email templates in the template set uploaded in the administration console for SAP Cloud Identity Services.")

[Edit or Add an Email Template Set](edit-or-add-an-email-template-set-3c4f397.md "Tenant administrators can configure language versions of each template in the template set. They can also set a custom template for each language, and change the name of each template set.")

[Define an Email Template Set for an Application](define-an-email-template-set-for-an-application-fc6b54a.md "Tenant administrators can define the email template set that the application uses.")

[Allowed Placeholders per Email Template](allowed-placeholders-per-email-template-c0d4a76.md "This document describes which placeholders can be used in each email template.")

