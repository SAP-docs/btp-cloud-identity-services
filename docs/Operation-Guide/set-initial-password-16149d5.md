<!-- loio16149d5f80a34c88884d0950cc14b023 -->

# Set Initial Password

You can set initial password for a user that has already activated his or her account.



<a name="loio16149d5f80a34c88884d0950cc14b023__prereq_cqc_43x_jrb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* and *Manage Users* roles. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

Tenant administrator can set an initial password for a user that has already activated the account. When the user logs on with the new password, he or she is prompted to change the password with a new one.

> ### Restriction:  
> The initial password can be valid between 1 and 365 days depending on the configuration made by the administrator. The default value is 14 days. The user is prompted to reset the password during the first authentication. After the validity of the initial password expires, the user can't log on to the application and must contact an administrator. For more information for more information about how to configure the initial password validity, see [Configure Initial Password and Email Link Validity](configure-initial-password-and-email-link-validity-f8093f4.md).

> ### Tip:  
> [Configure SAML 2.0 Service Provider](configure-saml-2-0-service-provider-51f1f75.md).

> ### Restriction:  
> When a user is with a status `Inactive`, setting initial password to that user is disabled. For more information, see [Deactivate Users](deactivate-users-99cf468.md).

To set an initial password, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  Choose the user who needs an initial password.

    For more information about how to find a user in Identity Authentication, see [Search Users](search-users-06078a6.md).

4.  Choose *Password Details* under the *Authentication* tab.

5.  Press *Set Initial*.




<a name="loio16149d5f80a34c88884d0950cc14b023__result_fwb_4vw_t1b"/>

## Results

The user logs on to the application with the new password set by the tenant administrator. He or she is prompted to change the password with a new one. After changing the password, the user is able to log on to the application.

