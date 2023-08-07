<!-- loio348deef7f29b40909b151c8dc9a11d53 -->

# Create a New User

As a tenant administrator, you can create a new user in the administration console for SAP Cloud Identity Services.



## Prerequisites

You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

The tenant administrator creates the new user with a minimum set of attributes and can set an initial password.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  Press *Add*.

4.  Fill in the required fields in the dialog box.

    > ### Note:  
    > By default the *User Type* field is *Employee*. To change the default setting, choose user type from the drop-down list. The available user types are: *Customer*, *Employee*, *Partner*, *Public*, *External*, and *Onboardee*.

    *Email* field can be skipped when *Set initial password* or *Set status active* is selected, and *Email* is configured as not required in the *Logon Alias* view.

    Vaues for *Email*, *First Name* and *Last Name* that are part of the respective exclude list cant' be used. For mor einformation, see [Restrict User Attributes Values via Exclude Lists](restrict-user-attributes-values-via-exclude-lists-cb108c2.md).

    > ### Tip:  
    > If email is mandatory, for users without valid email addresses or for testing purposes use the `sap-test.de` domain, for example `<username>@sap-test.de`. Do not use any other existing or nonexisting domains.

5.  Select one of the following options:

    -   Send activation email - The tenant administrator creates a user with status `New`. The user receives an email with instructions how to activate the user account. After activating the account, the user status changes to `Active`.

    -   Set initial password - The tenant administrator creates a user with status `Active` and sets the password for the user.

        > ### Restriction:  
        > The initial password can be valid between 1 and 365 days depending on the configuration made by the administrator. The default value is 14 days. The user is prompted to reset the password during the first authentication. After the validity of the initial password expires, the user can't log on to the application and must contact an administrator. For more information for more information about how to configure the initial password validity, see [Configure Initial Password and Email Link Validity](configure-initial-password-and-email-link-validity-f8093f4.md).

    -   Set status active - The tenant administrator creates a user with status `Active`. The tenant administrator does not set an initial password for the user, and the user does not receive an email with instructions how to activate the user account.

        This option can be used in the following scenarios:

        -   Identity Authentication acting as identity provider \(IdP\) proxy
        -   certificate authentication


6.  Save your entries.




<a name="loio348deef7f29b40909b151c8dc9a11d53__result_mfg_cxk_pkb"/>

## Results

If the operation is successful, the system displays the message: `User "<name of the user>" created`. Identity Authentication creates the new user and assigns `User ID` \(P user\) and `Global User ID` \(universally unique identifier \(UUID\) format\). The `User ID` field is unique and not editable. The `Global User ID`, on the other hand, is unique, but editable. You can change it via the the user management field in the administration console.

**Related Information**  


[Configure User Identifier Attributes](configure-user-identifier-attributes-8b9fa88.md "Tenant administrators can configure user identifier attributes as required and unique for the tenant.")

[Restrict User Attributes Values via Exclude Lists](restrict-user-attributes-values-via-exclude-lists-cb108c2.md "You can restrict the values that can be set on the email, first and last name attributes of the user.")

[List and Edit User Details](list-and-edit-user-details-045cb01.md "As a tenant administrator, you can view detailed information about the users in the administration console for SAP Cloud Identity Services. Optionally you can edit this information.")

