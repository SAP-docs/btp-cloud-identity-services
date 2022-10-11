<!-- copy47e9866e3d1b47d4adc319538296c296 -->

# Configure Certificates for API Authentication

This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.



## Context

You can use a certificate to authenticate when REST API calls \(Invitation REST API, User management REST API, Password Service Rest API, and Forgot Service REST API\) to the tenant of Identity Authentication are used. The certificate can also be used in the OpenID Connect scenarios of Identity Authentication.

For the configuration, you have to provide the base64-encoded certificate as a file or plain text, or you can generate a certificate via the administration console.

By default all scope options are selected and the *Scope* field is disabled. Your certificates are used for all scopes.

Identity Authentication supports SAP Passport CA as trusted certificate authority \(CA\).



<a name="copy47e9866e3d1b47d4adc319538296c296__steps_ksg_x2m_fp"/>

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

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](../Operation-Guide/create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Application APIs*, choose *Client Authentication*.

6.  Choose the *Add* button in the *Certificates for API Authentication* section.

7.  Provide description for the certificate.

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
    > You must provide a Common Name \(CN\) and password to generate the certificate. The maximum length of the CN is 64 characters. Once the certificate is generated it is saved as a *.p12* file. The system populates the *Insert as Text* field with it, and provides the certificate attributes in the Subject DN. The common name \(CN\) in the generated certificate is in the format `<common name>` \(`<admin user ID>`\), where common name is the CN provided by the administrator, and admin user ID is the administrator's user id.

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
    
9.  Choose the *Add* button at the bottom of the page.

    Once the certificate has been configured, the system displays the message ***Certificate for API authentication updated***.

    > ### Tip:  
    > When the certificate expires, follow the procedure again and configure a new one.




<a name="copy47e9866e3d1b47d4adc319538296c296__result_ngg_sqb_xkb"/>

## Results

Once your certificate is added you can see a table with all your certificates and information about them.

**Related Information**  


[Configure Secrets for API Authentication](configure-secrets-for-api-authentication-9ea13fe.md "This document describes how developers configure secrets with scopes and validity for client authentication.")

[Unlock Client ID](unlock-client-id-e5a6b85.md "Unlock the client ID after five failed logon attempts before the automatic unlock time of 60 minutes has passed.")

[Disable Client ID Locking](disable-client-id-locking-aa38152.md "You can disable the automatic lock of the client ID after five failed logon attempts.")

[Configure JWT for OAuth Client Authentication](configure-jwt-for-oauth-client-authentication-1bdc729.md "Configure the issuer and subject of tokens for JSON Web Token (JWT) client authentication in token requests to OpenID Connect applications.")

[SCIM REST API Authentication Mechanisms](scim-rest-api-authentication-mechanisms-e3f31bd.md "See how to configure the authentication mechanisms for the SCIM REST API methods of Identity Authentication.")

[Create a New Application](../Operation-Guide/create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

[Invitation REST API](invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

