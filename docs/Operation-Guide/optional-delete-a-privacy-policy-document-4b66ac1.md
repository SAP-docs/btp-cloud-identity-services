<!-- loio4b66ac17c6514b1281a5d005fe09aeb6 -->

# \(Optional\) Delete a Privacy Policy Document

Delete a privacy policy document or a version of a privacy policy document.



<a name="loio4b66ac17c6514b1281a5d005fe09aeb6__context_uqs_f5f_rpb"/>

## Context

You can delete a specific language version or the entire set of privacy policy documents. To delete the entire of privacy policy documents, you must delete all language versions for this set. The privacy policy document set is removed from the list of the privacy policy documents in the administration console for SAP Cloud Identity Services, when you delete the last language version of a privacy policy set.

The documents will be deleted no matter if they are accepted or not by any users.

> ### Note:  
> You can delete only documents that are not defined for applications. To delete a document that is defined for an application, you first you must set another privacy policy for the applications. For more information, see [Define a Privacy Policy Document for an Application](define-a-privacy-policy-document-for-an-application-9611118.md).

To delete a privacy policy document, follow the procedure below:



<a name="loio4b66ac17c6514b1281a5d005fe09aeb6__steps_rmd_q15_r4"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Privacy Policy Documents* tile.

    This operation opens a list of the privacy policy documents.

3.  To delete a language version to a privacy policy document, choose that document from the list on the left.

    > ### Tip:  
    > Type the name of the document in the search field to filter the list items.

    1.  Select the version from the drop-down that you want to delete.

    2.  Select the language from the drop-down for that version that you want to delete.

    3.  Choose *Delete* button and confirm the operation in the pop up that appears.

        If the document is defined for an application, define a new privacy policy document for that application and repeat the step.


    If the document is deleted, the system displays the message ***Privacy Policy document deleted***.

4.  Repeat the procedure for the language versions that you want to delete.


