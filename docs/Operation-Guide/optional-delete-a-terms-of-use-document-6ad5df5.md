<!-- loio6ad5df5b1ab04a7bb416c5f5e998668f -->

# \(Optional\) Delete a Terms of Use Document

Delete a terms of use document or a version of a terms of use document.



<a name="loio6ad5df5b1ab04a7bb416c5f5e998668f__context_uqs_f5f_rpb"/>

## Context

You can delete a specific language version or the entire set of terms of use documents. To delete the entire of terms of use documents, you must delete all language versions for this set. The terms of use document set is removed from the list of the terms of use documents in the administration console for Identity Authentication, when you delete the last language version of a terms of use set.

The documents will be deleted no matter if they are accepted or not by any users.

> ### Note:  
> You can delete only documents that are not defined for applications. To delete a document that is defined for an application, you first you must set another terms of use for the applications. For more information, see [Define a Privacy Policy Document for an Application](define-a-privacy-policy-document-for-an-application-9611118.md).

To delete a terms of use document, follow the procedure below:



<a name="loio6ad5df5b1ab04a7bb416c5f5e998668f__steps_rmd_q15_r4"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Choose the *Terms of Use Documents* tile.

    This operation opens a list of the terms of use documents.

3.  To delete a language version to a terms of use document, choose that document from the list on the left.

    > ### Tip:  
    > Type the name of the document in the search field to filter the list items.

    1.  Select the version from the drop-down that you want to delete.

    2.  Select the language from the drop-down for that version that you want to delete.

    3.  Choose *Delete* button and confirm the operation in the pop up that appears.

        If the document is defined for an application, define a new terms of use document for that application and repeat the step.


    If the document is deleted, the system displays the message ***Terms of Use document deleted***.

4.  Repeat the procedure for the language versions that you want to delete.


