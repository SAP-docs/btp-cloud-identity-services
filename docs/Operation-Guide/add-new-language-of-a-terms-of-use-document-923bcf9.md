<!-- loio923bcf96f6334477a1101b710d9dd899 -->

# Add New Language of a Terms of Use Document

To add a new language of a terms of use document, you must upload a UTF-8 encoded plain text file containing the terms of use statement.



<a name="loio923bcf96f6334477a1101b710d9dd899__prereq_nzn_dpl_rpb"/>

## Prerequisites

You have created a terms of use document in the administration console. For more information, see[Create a New Terms of Use Document](create-a-new-terms-of-use-document-dabde05.md) .



<a name="loio923bcf96f6334477a1101b710d9dd899__context_hc5_zbl_vpb"/>

## Context

You can add one or more languages of the document.

> ### Note:  
> If there is only one language for the document, it is recommended to be *English \(United States\)*.
> 
> If the languages are more than one, one of them must be *English \(United States\)*.

The plain text document can include the following tags: `<a>`, `<strong>`, and `<em>`.

> ### Example:  
> -   `See <a href="https://www.example.com">Subscription conditions</a>`
> -   `<strong>Additional requirements</strong>`
> -   `<em>Important:</em>`

To open the link from the document in the preview in the admin console, right click the link and open it in a new tab.



<a name="loio923bcf96f6334477a1101b710d9dd899__steps_rmd_q15_r4"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Terms of Use Documents* tile.

    This operation opens a list of the terms of use documents.

3.  To add a language to a terms of use document, choose that document from the list on the left.

    > ### Tip:  
    > Type the name of the document in the search field to filter the list items.

4.  Choose the *Add* button in the details view on the top right-hand corner.

    1.  Choose the *Active Language Version* radio button.

    2.  Select the language from the drop-down.

    3.  Specify the plain text file for the language.

        > ### Note:  
        > Use a file with an extension `.txt`.

    4.  Choose *Add* to save your selection

        Once the file has been uploaded, the system displays the message ***Terms of use file uploaded***.



