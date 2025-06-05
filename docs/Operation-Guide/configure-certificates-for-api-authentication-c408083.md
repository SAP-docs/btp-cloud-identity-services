<!-- loioc408083913f3487bb923e70575ac0793 -->

# Configure Certificates for API Authentication

This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.



<a name="loioc408083913f3487bb923e70575ac0793__prereq_gwy_nng_2cc"/>

## Prerequisites

[SAP Support Portal Home](https://support.sap.com/en/index.html)\(For trusted CA Scenario\) - If you want to configure a certificate, using your own trusted CA report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`. Attach to the incident the root and intermediate certificates and provide the Identity Authentication tenant ID.

> ### Note:  
> `Tenant ID` is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the `tenant ID`. For more information about your tenants, see [View Assigned Tenants and Admins](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/viewing-assigned-tenants-and-administrators?state=DRAFT&version=Dev).



## Context

You can use a certificate to authenticate when REST API calls \(Invitation REST API, User management REST API, Password Service Rest API, and Forgot Service REST API\) to the tenant of Identity Authentication are used. The certificate can also be used in the OpenID Connect scenarios of Identity Authentication.

For the configuration, you have to provide the base64-encoded certificate as a file or plain text, or you can generate a certificate via the administration console.

By default all scope options are selected and the *Scope* field is disabled. Your certificates are used for all scopes.

Identity Authentication, by default, supports the following as trusted certificate authorities \(CA\): SAP Passport CA G2, SAP SSO CA G2, SAP Cloud Root CA, SAP Global Root CA, DigiCert TLS RSA SHA256 2020 CA1, DigiCert Global Root CA, SAP Cloud Platform Client CA, ConnectivityCA.



<a name="loioc408083913f3487bb923e70575ac0793__steps_ksg_x2m_fp"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Application APIs*, choose *Client Authentication*.

6.  Choose the *Add* button in the *Certificates for API Authentication* section.

7.  **Optional:** Provide description for the certificate.

8.  Choose one of the following options:


    <table>
    <tr>
    <th valign="top">

    Certificate Options
    
    </th>
    <th valign="top">

    Notes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Generate Certificate**
    
    </td>
    <td valign="top">
    
    Fill in the fields under *Generate Certificate* and choose the *Generate* button.

    > ### Note:  
    > You must provide a Common Name \(CN\) and password to generate the certificate. Once the certificate is generated, it is saved as a *.p12* file. The system populates the *Insert as Text* field with it, and provides the certificate attributes in the Subject DN. The common name \(CN\) in the generated certificate is in the format `<common name>` \(`<admin user ID>`\), where common name is the CN provided by the administrator, and admin user ID is the administrator's user id. The maximum length of the combination of `<common name>` \(`<admin user ID>`\) is 64 characters.

    > ### Remember:  
    > You can generate up to 500 certificates per year. If you reach the limit, you can still upload your certificate, or insert it as a text.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Upload Certificate**
    
    </td>
    <td valign="top">
    
    You must use `.cer` or `.crt` files.

    > ### Note:  
    > Once the certificate is uploaded, the system populates the Insert as Text field with it


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Insert Certificate**
    
    </td>
    <td valign="top">
    
    Insert the certificate in the text field.
    
    </td>
    </tr>
    </table>
    
    > ### Restriction:  
    > You can't use one and the same certificate for application and system as administrator authentication.

9.  Choose the *Add* button at the bottom of the page.

    Once the certificate has been configured, the system displays the message ***Certificate for API authentication updated***.

    > ### Tip:  
    > When the certificate expires, follow the procedure again and configure a new one.




<a name="loioc408083913f3487bb923e70575ac0793__result_ngg_sqb_xkb"/>

## Results

Once your certificate is added you can see a table with all your certificates and information about them.

**Related Information**  


[Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md "This document describes how developers configure secrets with scopes and validity for client authentication.")

[Unlock Client ID](unlock-client-id-665b9e0.md "Unlock the client ID after five failed logon attempts before the automatic unlock time of 60 minutes has passed.")

[Disable Client ID Locking](disable-client-id-locking-f1dc77e.md "You can disable the automatic lock of the client ID after five failed logon attempts.")

[Configure JWT for OAuth Client Authentication](configure-jwt-for-oauth-client-authentication-db97a69.md "Configure the JSON Web Token (JWT) - the issuer and subject of tokens for JWT client authentication in token requests, or the URI for JSON web key retrieval for client authentication.")

[SCIM REST API \(Deprecated\) Authentication Mechanisms](scim-rest-api-deprecated-authentication-mechanisms-c599c89.md "See how to configure the authentication mechanisms for the Identity Authentication API (Deprecated) methods of Identity Authentication.")

[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

[Invitation REST API](../Development/invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Management REST API](../Development/user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

