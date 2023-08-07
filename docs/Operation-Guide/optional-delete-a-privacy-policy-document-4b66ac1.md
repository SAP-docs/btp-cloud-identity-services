<!-- loio4b66ac17c6514b1281a5d005fe09aeb6 -->

# \(Optional\) Delete a Privacy Policy Document

Delete a privacy policy document set or a version of a privacy policy document.



<a name="loio4b66ac17c6514b1281a5d005fe09aeb6__context_uqs_f5f_rpb"/>

## Context

You can delete a specific language version or the entire set of privacy policy documents. Deleting the entire set of privacy policy documents, you delete all language versions for this set. The privacy policy document set is removed from the list of the privacy policy documents in the administration console for SAP Cloud Identity Services, when you delete it.

The documents will be deleted no matter if they are accepted or not by any users.

> ### Note:  
> You can delete only documents that are not defined for applications. To delete a document version or entire document set that is defined for an application, you first you must set another privacy policy for the applications. For more information, see [Define a Privacy Policy Document for an Application](define-a-privacy-policy-document-for-an-application-9611118.md).

To delete a privacy policy document set or a specific language version, follow the procedure below:

<a name="task_r42_2jj_3yb"/>

<!-- task\_r42\_2jj\_3yb -->

## Delete Entire Documents Set



<a name="task_r42_2jj_3yb__steps_ilm_3jj_3yb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Privacy Policy Documents* tile.

    This operation opens a list of the privacy policy documents.

3.  To delete the entire privacy policy document set, choose that set from the list on the left.

    > ### Tip:  
    > Type the name of the document in the search field to filter the list items.

4.  Choose *Delete Set* button and confirm the operation in the pop-up that appears.

    If a document is defined for an application, define a new privacy policy document for that application and repeat the step.

    If the document set is deleted, the system displays the message ***Privacy Policy document set deleted***.


<a name="task_q3p_2jj_3yb"/>

<!-- task\_q3p\_2jj\_3yb -->

## Delete a Language Version



<a name="task_q3p_2jj_3yb__steps_scz_3kj_3yb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Privacy Policy Documents* tile.

    This operation opens a list of the privacy policy documents.

3.  To delete a language version to a privacy policy document, choose that document from the list on the left.

    > ### Tip:  
    > Type the name of the document in the search field to filter the list items.

    1.  Select the version from the drop-down that you want to delete.

    2.  Select the language from the drop-down for that version that you want to delete.

    3.  Choose *Delete* button and confirm the operation in the pop-up that appears.

        If the document is defined for an application, define a new privacy policy document for that application and repeat the step.


    If the document version is deleted, the system displays the message ***Privacy Policy document deleted***.


