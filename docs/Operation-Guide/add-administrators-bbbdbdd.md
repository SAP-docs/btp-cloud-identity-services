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

 <a name="loio1dc498bff0674743a1a3a0ec3f0bf298"/>

<!-- loio1dc498bff0674743a1a3a0ec3f0bf298 -->

## Add User as Administrator



## Context

To add a person as a new tenant administrator, proceed as follows:



<a name="loio1dc498bff0674743a1a3a0ec3f0bf298__steps_ebj_gln_tt"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Administrators* tile.

    This operation opens a list of all administrators in alphabetical order.

    > ### Note:  
    > The list also includes the SAP BTP system, which by default has authorizations to set up the trust with Identity Authentication.

3.  Press the *\+Add* button on the left-hand panel to add a new administrator to the list.

4.  Choose *Add User*.

5.  Make the appropriate entries in the *Email*, *First Name*, and *Last Name* fields for the user you want to add as an administrator.

    The *E-Mail* must be unique for the tenant.

    The *First Name*, and *Last Name* fields will be prefilled automatically for users that already exist in system.

    > ### Remember:  
    > Once the administrator is created, the *First Name*, *Last Name*, and *Email* fields are not editable from the administrator section. If you want to change the information you must go to the *User Management* section. For more information about how to edit the user information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).

6.  Assign the required administrator roles for the user.

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
    </table>
    
7.  Save your changes.


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

3.  On the left-hand panel press *\+Add* \> *System*.

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
    </table>
    
6.  Configure the method for authentication when the system is used. You can choose from the following two options:

    -   *Certificate*

        > ### Note:  
        > You can upload a certificate, generate a new one, or insert it as a text.
        > 
        > You must provide a Common Name \(CN\) and password to generate the certificate. The maximum length of the CN is 64 characters. Once the certificate is generated it is saved as a *.p12* file. The system populates the *Insert as Text* field with it, and provides the certificate attributes in the Subject DN. The common name \(CN\) in the generated certificate is in the format `<common name>` \(`<admin user ID>`\), where common name is the CN provided by the administrator, and admin user ID is the administrator's user id.
        > 
        > Identity Authentication supports SAP Passport CA as trusted certificate authority \(CA\).

    -   *Secrets*

        > ### Note:  
        > You need a *Client ID* and *Secret* for system authentication. You can see the *Client ID* generated automatically for the chosen system. The client ID is in the universally unique identifier \(UUID\) format. For example, `1ab7c243-5de5-4530-8g14-1234h26373ab`.

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



