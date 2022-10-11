<!-- loiocb108c22162741e2a50b7cf8466148bf -->

# Restrict User Attributes Values via Exclude Lists

You can restrict the values that can be set on the e-mail, first and last name attributes of the user.



## Context

The configured exclude lists for e-mail, first and last name attributes are considered in the user creation and user update via the Identity Authentication SCIM API, Identity Directory SCIM API, the administration console for Identity Authentication, and user import.

If the exclude lists are empty, you can create and update a user with any value for e-mail, first and last name attributes.

To create exclude lists for e-mail, first and last name attributes, follow the procedure below:



<a name="loiocb108c22162741e2a50b7cf8466148bf__steps_af2_wl4_kpb"/>

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

2.  Under *Users & Authorizations*, choose the *Exclude Lists* tile.

3.  Choose the tab for the attribute that you want to restrict:

    -   First Name
    -   Last Name
    -   E-Mail

4.  Choose *Create* and enter the exclude terms as free text in the field.

    For multiple values, use comma between them.

5.  Confirm your changes by choosing *Create*.


**Related Information**  


[Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md "As a tenant administrator, you can import new users or update existing ones for a specific application with a CSV file. You can also send activation e-mails to the users that have not received activation e-mails for that application so far.")

[Create a New User](create-a-new-user-348deef.md "As a tenant administrator, you can create a new user in the administration console for Identity Authentication.")

[List and Edit User Details](list-and-edit-user-details-045cb01.md "As a tenant administrator, you can view detailed information about the users in the administration console for Identity Authentication. Optionally you can edit this information.")

[SCIM REST API \(Deprecated\)](../Development/scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

[Identity Directory Service SCIM API](https://api.sap.com/api/IdDS_SCIM/resource)

