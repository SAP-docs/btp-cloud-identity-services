<!-- loio348deef7f29b40909b151c8dc9a11d53 -->

# Create a New User

As a tenant administrator, you can create a new user in the administration console for Identity Authentication.



## Prerequisites

You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

The tenant administrator creates the new user with a minimum set of attributes and can set an initial password.



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

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  Press *Add User*.

4.  Fill in the required fields in the dialog box.

    > ### Note:  
    > By default the *User Type* field is *Employee*. To change the default setting, choose user type from the drop-down list. The available user types are: *Customer*, *Employee*, *Partner*, *Public*, *External*, and *Onboardee*.

    *E-Mail* field can be skipped when *Set initial password* or *Set status active* is selected, and *E-Mail* is configured as not required in the *Logon Alias* view.

    Vaues for *E-Mail*, *First Name* and *Last Name* that are part of the respective exclude list cant' be used. For mor einformation, see [Restrict User Attributes Values via Exclude Lists](restrict-user-attributes-values-via-exclude-lists-cb108c2.md).

    > ### Tip:  
    > If e-mail is mandatory, for users without valid e-mail addresses or for testing purposes use the `sap-test.de` domain, for example `<username>@sap-test.de`. Do not use any other existing or non-existing domains.

5.  Select one of the following options:

    -   Send activation e-mail - The user receives an e-mail with instructions how to activate the user account.

    -   Set initial password - The tenant administrator sets the password for the user.

        > ### Restriction:  
        > The initial password can be valid between 1 and 365 days depending on the configuration made by the administrator. The default value is 14 days. The user is prompted to reset the password during the first authentication. After the validity of the initial password expires, the user can't log on to the application and must contact an administrator. For more information for more information about how to configure the initial password validity, see [Configure Initial Password and E-Mail Link Validity](configure-initial-password-and-e-mail-link-validity-f8093f4.md).

    -   Set status active - The tenant administrator creates a user with status `active`. The tenant administrator does not set an initial password for the user, and the user does not receive an e-mail with instructions how to activate the user account.

        This option can be used in the following scenarios:

        -   Identity Authentication acting as identity provider \(IdP\) proxy
        -   certificate authentication


6.  Save your entries.




<a name="loio348deef7f29b40909b151c8dc9a11d53__result_mfg_cxk_pkb"/>

## Results

If the operation is successful, the system displays the message: `User "<name of the user>" created`. Identity Authentication creates the new user and assigns `User ID` \(P user\) and `User UUID` \(universally unique identifier \(UUID\) format\). The `User ID` field is unique and not editable. The `User UUID`, on the other hand, is unique, but editable. You can change it via the the user management field in the administration console.

**Related Information**  


[Configure User Identifier Attributes](configure-user-identifier-attributes-8b9fa88.md "Tenant administrators can configure user identifier attributes as required and unique for the tenant.")

[Restrict User Attributes Values via Exclude Lists](restrict-user-attributes-values-via-exclude-lists-cb108c2.md "You can restrict the values that can be set on the e-mail, first and last name attributes of the user.")

[List and Edit User Details](list-and-edit-user-details-045cb01.md "As a tenant administrator, you can view detailed information about the users in the administration console for Identity Authentication. Optionally you can edit this information.")

