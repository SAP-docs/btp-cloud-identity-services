<!-- loio148568a0835949ac908a0d3d0facbfe4 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# View E-Mail Template Document

Tenant administrators can view language e-mail templates in the template set uploaded in the administration console for Identity Authentication.



<a name="loio148568a0835949ac908a0d3d0facbfe4__prereq_pf3_kcb_fbb"/>

## Prerequisites

-   You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have added the plain text and HTML template files in the e-mail template set. For more information, see [Edit or Add an E-Mail Template Set](edit-or-add-an-e-mail-template-set-3c4f397.md).

    > ### Note:  
    > Both the TXT and HTML formats are included in the e-mails sent to a user. What the user sees, depends on the settings of his or her e-mail client.




<a name="loio148568a0835949ac908a0d3d0facbfe4__context_plz_lq1_fbb"/>

## Context

You can view both the TXT and HTML formats of the e-mails sent to a user.

To view an e-mail template, follow the procedure below:



<a name="loio148568a0835949ac908a0d3d0facbfe4__steps_nrm_r5v_tfb"/>

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

2.  Choose the *E-Mail Template Sets* tile.

    This operation opens a list of the template sets.

3.  Choose the list item of the template set you want to view.

4.  Select the tab signifying the process, whose template you want to view.

5.  View the file:

    -   To view the plain text file, choose the plain text file icon <span class="SAP-icons"></span> next to the respective language version.
    -   To view the HTML file, choose the HTML file icon <span class="SAP-icons"></span> next to the respective language version.

    The file opens in a new tab.

    To view another template, repeat the procedure.


**Related Information**  


[Create a New E-Mail Template Set](create-a-new-e-mail-template-set-a6fca8b.md "Tenant administrators can create a new set of e-mail templates so that each template in the set can have a custom language version.")

[Edit or Add an E-Mail Template Set](edit-or-add-an-e-mail-template-set-3c4f397.md "Tenant administrators can configure language versions of each template in the template set. They can also set a custom template for each language, and change the name of each template set.")

[Define an E-Mail Template Set for an Application](define-an-e-mail-template-set-for-an-application-fc6b54a.md "Tenant administrators can define the e-mail template set that the application uses.")

[Delete an E-Mail Template Set](delete-an-e-mail-template-set-6fce69d.md "Tenant administrators can delete an e-mail template set or a language version for a specific application process.")

[Allowed Placeholders per E-Mail Template](allowed-placeholders-per-e-mail-template-c0d4a76.md "This document describes which placeholders can be used in each e-mail template.")

