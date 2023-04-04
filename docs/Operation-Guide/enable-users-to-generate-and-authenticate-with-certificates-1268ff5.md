<!-- loio1268ff5987d8484698f77cd24c91efa5 -->

# Enable Users to Generate and Authenticate with Certificates

Allow users to generate and authenticate with certificates.



<a name="loio1268ff5987d8484698f77cd24c91efa5__prereq_k4x_cmg_ppb"/>

## Prerequisites

You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

By enabling certificate generate and authentication for the users, they can log on to applications with the generated certificate without the need to provide username and password.

The tenant administrator can configure the system to allow the following types of users to generate their own certificates via the profile page and to authenticate with them:

-   *Public*
-   *Customer*
-   *Partner*
-   *Employee*

The certificate generation and authentication is disabled by default for all user types. When you allow it for a user type, the user of this type should go to the profile page and generate a certificate for authentication. Once the certificate is generated, it's downloaded to the user's system. When the user imports it to the certificate store or browser, the newly generated certificate is ready for authentication. When the user navigates to the logon page of the application, he or she is automatically authenticated with the certificate. If the authentication fails, the user is prompted to provide username and password.

To allow certificate generation and authentication, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Choose the *Certificate Authentication* list item.

4.  Use the slider next to a user type to enable certificate authentication.

    If the operation is successful, you receive a confirmation message.




<a name="loio1268ff5987d8484698f77cd24c91efa5__postreq_lhn_f2r_brb"/>

## Next Steps

Enable the *Credential change* security alert e-mailing to inform the user when a certificate generated or removed. For more information, see [Send Security Alert E-Mails](send-security-alert-e-mails-c977464.md).

