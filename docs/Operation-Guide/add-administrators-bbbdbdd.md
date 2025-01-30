<!-- loiobbbdbdd3899942ce874f3aae9ba9e21d -->

# Add Administrators

As a tenant administrator, you can add new administrators in the administration console for SAP Cloud Identity Services.



## Prerequisites

To add new tenant administrators, you must be assigned the Manage Tenant Configuration role.



## Context

You can add both a person and a system in the administration console to act as administrators. The system can receive the same roles and can perform the same actions as the human administrator.

**Related Information**  


[List Administrators](list-administrators-c79a5c6.md "As a tenant administrator, you can list the administrators and their authorizations in the administration console for SAP Cloud Identity Services.")

[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

[Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md "Enable admin authorizations based on policies to configure a granular access control for the administrators of SAP Cloud Identity Services.")

[Add Administrators via SAP for Me](https://support.sap.com/content/s4m/help/systems/systems/details/ias.html)

<a name="loio1dc498bff0674743a1a3a0ec3f0bf298"/>

<!-- loio1dc498bff0674743a1a3a0ec3f0bf298 -->

## Add User as Administrator



## Context

> ### Tip:  
> If you are not a tenant administrator, or you don't have the Manage Tenant Configuration role, as an alternative, you can view the tenant administrators of the tenants that are assigned to you and add new administrators in SAP Cloud Identity Services via the [SAP for Me](https://me.sap.com/home) portal. For more information see [Cloud Identity Services Administrators Card](https://support.sap.com/content/s4m/help/systems/systems/details/ias.html).

To add a person as a new tenant administrator, proceed as follows:



<a name="loio1dc498bff0674743a1a3a0ec3f0bf298__steps_ebj_gln_tt"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Administrators* tile.

    This operation opens a list of all administrators in alphabetical order.

    > ### Note:  
    > The list also includes the SAP BTP system, which by default has authorizations to set up the trust with Identity Authentication.

3.  On the left-hand panel press *Add* \> *User*.

4.  Make the appropriate entries in the *Identifier*, *First Name*, and *Last Name* fields for the user you want to add as an administrator.

    The *Identifier* field can take user `email` or `login name`:

    -   If `email` is used, it must be unique for the tenant.

    -   If `login name` is used, an existing user with that login name must exist.

    > ### Remember:  
    > Once the administrator is created, the *First Name*, *Last Name*, and *Identifier* fields are not editable from the administrator section. If you want to change the information you must go to the *User Management* section. For more information about how to edit the user information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).

5.  Assign the required administrator roles for the user.

    To be a tenant administrator, a user must be assigned at least one of the following roles.

    **Administrator Roles**


    <table>
    <tr>
    <th valign="top">

    Authorization
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Applications
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to configure applications and their authorization policies via the administration console.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Corporate Identity Providers
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to configure the identity providers via the administration console.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Users
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to manage, import, and export users via the administration console.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Read Users
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to retrieve user data and export users via the administration console and the SCIM REST API of Identity Authentication.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Groups
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to create, edit, and delete groups via the administration console.The tenant administrator can also assign authorization policies to users.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Tenant Configuration
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to manage tenant configuration and authorization assignment to users. Tenant administrators with that role can add additional roles to themselves or to other administrators.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Identity Provisioning
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to configure identity provisioning. The tenant administrator is granted the main IPS\_ADMIN role.
    
    </td>
    </tr>
    </table>
    
6.  Save your changes.


<a name="loiocefb742a36754b18bbe5c3503ac6d87c"/>

<!-- loiocefb742a36754b18bbe5c3503ac6d87c -->

## Add System as Administrator



## Context

To add a system as a new tenant administrator, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Administrators* tile.

    This operation opens a list of all administrators in alphabetical order.

    > ### Note:  
    > The list also includes the SAP BTP system, which by default has authorizations to set up the trust with Identity Authentication.

3.  On the left-hand panel press *Add* \> *System*.

4.  Enter the name of the system in the provided field.

    > ### Caution:  
    > Be careful when you choose a name for your system as administrator. Once created, the name cannot be changed.

5.  Assign the required administrator roles for the system and save your changes.

    To be a tenant administrator, a user must be assigned at least one of the following roles.

    **Administrator Roles**


    <table>
    <tr>
    <th valign="top">

    Authorization
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Applications
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to configure the applications via the administration console.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Corporate Identity Providers
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to configure the identity providers via the administration console.This role gives the tenant administrator permission to configure the applications via the administration console.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Users
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to manage, import, and export users via the administration console.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Read Users
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to retrieve user data and import users via the administration console and the SCIM REST API of Identity Authentication.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Groups
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to create, edit, and delete user groups via the administration console.The tenant administrator can also assign authorization policies.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Manage Tenant Configuration
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to manage tenant configuration and authorization assignment to users. Tenant administrators with that role can add additional roles to themselves or to other administrators.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Access Proxy System API
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to access API for provisioning identities via proxy systems.

    This role is needed for provisioning scenarios where proxy systems in the Identity Provisioning admin console are configured for synchronizing user data to and from central identity management solutions \(such as, the on-premise SAP Identity Management\).

    In this case, you use the credentials of the admin user with *Access Proxy System API* role assigned for setting up the technical user in the identity management solution for communicating with Identity Provisioning.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Access Real-Time Provisioning API
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to access API for real-time provisioning of identities.

    This role is needed for provisioning scenarios where user data is provisioned real-time without running jobs \(manual or scheduled ones\) in Identity Provisioning.

    In this case, you use the credentials of the admin user with *Access Real-Time Provisioning API* role assigned for setting up the authentication mechanism of the provisioning system defined on the *Real-Time Provisioning* tile of the administration console for SAP Cloud Identity Services.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Access Identity Provisioning Tenant Admin API
    
    </td>
    <td valign="top">
    
    This role gives the tenant administrator permission to access tenant API for running provisioning jobs.

    This role is needed for running provisioning jobs from an API client.

    The API is available on the SAP Business Accelerator Hub: [SAP Cloud Identity Services](https://api.sap.com/package/SCPIdentityServices/rest) *Identity Provisioning Service* \> *API Reference* \> *Jobs*. The URL for accessing the Tenant Admin API follows the pattern: `https://<IPS tenant host>/ips/publicapi/v1/startJob/{SourceSystemId}/jobs/{JobType}`.
    
    </td>
    </tr>
    </table>
    
6.  Configure the method for authentication when the system is used. You can choose from the following two options:

    -   *Certificate*

        You can upload a certificate, generate a new one, or insert it as a text.

        You must provide a Common Name \(CN\) and password to generate the certificate. Once the certificate is generated, it is saved as a *.p12* file. The system populates the *Insert as Text* field with it, and provides the certificate attributes in the Subject DN. The common name \(CN\) in the generated certificate is in the format `<common name>` \(`<admin user ID>`\), where common name is the CN provided by the administrator, and admin user ID is the administrator's user id. The maximum length of the combination of `<common name>` \(`<admin user ID>`\) is 64 characters.

        > ### Tip:  
        > Identity Authentication, by default, supports the following as trusted certificate authorities \(CA\): SAP Passport CA G2, SAP SSO CA G2, SAP Cloud Root CA, SAP Global Root CA, DigiCert TLS RSA SHA256 2020 CA1, DigiCert Global Root CA, SAP Cloud Platform Client CA, ConnectivityCA.

        > ### Restriction:  
        > You can't use one and the same certificate for application and system as administrator authentication.

        > ### Note:  
        > For real-time provisioning scenarios, you need to upload the certificate generated from the source application that initiated the immediate sync. If Identity Authentication acts as the source application, simply upload the certificate generated in the *Authentication Mechanism* screen under *Users & Authorizations* \> *Real-Time Provisioning* \> *Add Target System*.

    -   *Secrets*

        > ### Note:  
        > You need a *Client ID* and *Secret* for system authentication. It is generated automatically with the creation of the system. The client ID is in the universally unique identifier \(UUID\) format. For example, `1ab7c243-5de5-4530-8g14-1234h26373ab`.

        Choose the *\+Add* button in the *Secrets* section, provide the required info in the pop-up, and save your entries.


        <table>
        <tr>
        <th valign="top">

        Field
        
        </th>
        <th valign="top">

        Info
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        *Description*
        
        </td>
        <td valign="top">
        
        This field is optional.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Expire in
        
        </td>
        <td valign="top">
        
        You can choose from three options:

        -   1 year
        -   2 years
        -   Never


        
        </td>
        </tr>
        </table>
        
        Make sure you save your client secret. You won't be able to retrieve it from the system later.

        Once your secret is generated you can see a table with your secrets and information about them. You can generate up to 2 secrets per system.



