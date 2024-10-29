<!-- loiocb108c22162741e2a50b7cf8466148bf -->

# Restrict User Attributes Values via Exclude Lists

You can restrict the values that can be set on the email, first and last name attributes of the user.



## Context

The configured exclude lists for email, first and last name attributes are considered in the user creation and user update via the Identity Authentication SCIM API, Identity Directory SCIM API, the administration console for SAP Cloud Identity Services, and user import.

If the exclude lists are empty, you can create and update a user with any value for email, first and last name attributes.

To create exclude lists for email, first and last name attributes, follow the procedure below:



<a name="loiocb108c22162741e2a50b7cf8466148bf__steps_af2_wl4_kpb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Exclude Lists* tile.

3.  Choose the tab for the attribute that you want to restrict:

    -   First Name
    -   Last Name
    -   Email

4.  Choose *Create* and enter the exclude terms as free text in the field.

    For multiple values, use comma between them.

5.  Confirm your changes by choosing *Create*.


**Related Information**  


[Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md "As a tenant administrator, you can import new users or update existing ones for a specific application with a CSV file. You can also send activation emails to the users that have not received activation emails for that application so far.")

[Create a New User](create-a-new-user-348deef.md "As a tenant administrator, you can create a new user in the administration console for SAP Cloud Identity Services.")

[List and Edit User Details](list-and-edit-user-details-045cb01.md "As a tenant administrator, you can view detailed information about the users in the administration console for SAP Cloud Identity Services. Optionally you can edit this information.")

[Identity Authentication API \(Deprecated\)](../Development/identity-authentication-api-deprecated-2f21568.md "Deprecated.")

[Identity Directory Service SCIM API](https://api.sap.com/api/IdDS_SCIM/resource)

