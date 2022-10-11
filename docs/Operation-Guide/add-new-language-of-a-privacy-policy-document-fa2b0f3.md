<!-- loiofa2b0f35825b4309a5bf02586cad88d0 -->

# Add New Language of a Privacy Policy Document

To add a language version of a privacy policy document, you must upload a UTF-8 encoded plain text file containing the privacy policy text.



<a name="loiofa2b0f35825b4309a5bf02586cad88d0__prereq_nzn_dpl_rpb"/>

## Prerequisites

You have created a privacy policy document in the administration console. For more information, see[Create a New Privacy Policy Document](create-a-new-privacy-policy-document-e73cf2d.md) .



<a name="loiofa2b0f35825b4309a5bf02586cad88d0__context_eyg_ybl_vpb"/>

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



<a name="loiofa2b0f35825b4309a5bf02586cad88d0__steps_rmd_q15_r4"/>

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

2.  Choose the *Privacy Policy Documents* tile.

    This operation opens a list of the privacy policy documents.

3.  To add a language to a privacy policy document, choose that document from the list on the left.

    > ### Tip:  
    > Type the name of the document in the search field to filter the list items.

4.  Choose the *Add* button in the details view on the top right-hand corner.

    1.  Choose the *Active Language Version* radio button.

    2.  Select the language from the drop-down.

    3.  Specify the plain text file for the language.

        > ### Note:  
        > Use a file with an extension `.txt`.

    4.  Choose *Add* to save your selection

        Once the file has been uploaded, the system displays the message ***Privacy policy file uploaded***.



