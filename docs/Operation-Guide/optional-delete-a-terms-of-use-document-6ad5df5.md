<!-- loio6ad5df5b1ab04a7bb416c5f5e998668f -->

# \(Optional\) Delete a Terms of Use Document

Delete a terms of use document set or a version of a terms of use document.



<a name="loio6ad5df5b1ab04a7bb416c5f5e998668f__context_uqs_f5f_rpb"/>

## Context

You can delete a specific language version or the entire set of terms of use documents. Deleting the entire set of terms of use documents, you delete all language versions for this set. The terms of use document set is removed from the list of the document sets in the administration console for SAP Cloud Identity Services, when you delete it.

The documents will be deleted no matter if they are accepted or not by any users.

> ### Note:  
> You can delete only documents that are not defined for applications. To delete a document version or entire document sett that is defined for an application, you first you must set another terms of use for the applications. For more information, see [Define a Terms of Use Document for an Application](define-a-terms-of-use-document-for-an-application-8a28c70.md).

<a name="task_stz_25j_3yb"/>

<!-- task\_stz\_25j\_3yb -->

## Delete Entire Documents Set



<a name="task_stz_25j_3yb__steps_ilm_3jj_3yb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Terms of Use Documents* tile.

    This operation opens a list of the terms of use documents.

3.  To delete the entire terms of use document set, choose that set from the list on the left.

    > ### Tip:  
    > Type the name of the document in the search field to filter the list items.

4.  Choose *Delete Set* button and confirm the operation in the pop-up that appears.

    If a document is defined for an application, define a new terms of use document for that application and repeat the step.

    If the document set is deleted, the system displays the message ***Terms of Use document set deleted***.


<a name="task_fg3_f5j_3yb"/>

<!-- task\_fg3\_f5j\_3yb -->

## Delete a Language Version



<a name="task_fg3_f5j_3yb__steps_scz_3kj_3yb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Terms of Use Documents* tile.

    This operation opens a list of the terms of use documents.

3.  To delete a language version to a terms of use document, choose that document from the list on the left.

    > ### Tip:  
    > Type the name of the document in the search field to filter the list items.

    1.  Select the version from the drop-down that you want to delete.

    2.  Select the language from the drop-down for that version that you want to delete.

    3.  Choose *Delete* button and confirm the operation in the pop-up that appears.

        If the document is defined for an application, define a new terms of use document for that application and repeat the step.


    If the document version is deleted, the system displays the message ***Terms of Use document deleted***.


