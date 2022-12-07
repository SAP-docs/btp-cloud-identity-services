<!-- loio3e409d85ee784ec184d6442331b645fe -->

# Configure OpenID Connect Application for Client Credentials Flow

This document is intended to help you configure an OpenID Connect application in the administration console for Identity Authentication for the client credentials flow.



<a name="loio3e409d85ee784ec184d6442331b645fe__prereq_grq_3jn_v2b"/>

## Prerequisites

You have an OpenID Connect application in the administration console for Identity Authentication. For more information, see [Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md).



## Context

The trust is configured by entering the information manually. You can enter manually the name of the client \(relying party\), and its redirect URIs.

To configure an OpenID Connect trusted application in the administration console for Identity Authentication, proceed as follows:



<a name="loio3e409d85ee784ec184d6442331b645fe__steps_ksg_x2m_fp"/>

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
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *OpenID Connect Configuration*.

6.  Manually enter the communication settings negotiated between Identity Authentication and the client.


    <table>
    <tr>
    <th valign="top">

    Setting


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    *Name \(mandatory\)*


    
    </td>
    <td valign="top">

    Provide a name of your choice.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Redirect URIs \(optional\)*


    
    </td>
    <td valign="top">

    The redirection URIs to which the response can be sent. You can add up to 20 redirect URIs.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Post Logout Redirect URIs \(optional\)*


    
    </td>
    <td valign="top">

    The redirection URIs where the user can be forwarded after logout. You can add up to 20 redirect URIs.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Front-Channel Logout URIs \(optional\)*


    
    </td>
    <td valign="top">

    URIs which will be requested for logout. You can add up to 20 URIs.


    
    </td>
    </tr>
    </table>
    
    > ### Tip:  
    > The *Redirect URI* and *Post Logout Redirect URI* configuration can be skipped for the Client Credentials Flow, Resource Owner Password Credentials Flow, and JWT Bearer Flow.
    > 
    > For more information about the format of the redirect URIs and post logout redirect URIs, see [OpenID Connect Application Configurations](openid-connect-application-configurations-1ae324e.md).

7.  \(If you added second signing certificate in tenant settings\) Under *Identity Provider Certificate*, choose the certificate to be used.

    > ### Tip:  
    > When the default identity provider certificate is changed with a new one, and the old one is not used anymore, we recommend you to delete the old certificate.

8.  Configure the allowed grant types for the application.


    <table>
    <tr>
    <th valign="top">

    Grant Type


    
    </th>
    <th valign="top">

    Default Behavior


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    **Authorization Code**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Authorization Code / Enforce PKCE \(S256\)**


    
    </td>
    <td valign="top">

    not-selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Password**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **JWT Bearer**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Implicit**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Refresh**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Client Credentials**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Token Exchange \(RFC 8693\)**


    
    </td>
    <td valign="top">

    not-selected


    
    </td>
    </tr>
    </table>
    
    Beware that for each flow the respective grant type must be selected. The Client Credential grant type must be selected for the client credentials flow.

9.  Save your selection. Once the application has been changed, the system displays the message ***Application <name of application\> updated***.

    > ### Remember:  
    > Configure trust on the client side. See the client documentation for more information about how to configure the trust. For more information how to view the OpenID Connect settings of \(For SAML 2.0 Applications\) To log out the user from all active session, when a new password is set, configure the SOAP endpoint. For more information, see Identity Authentication, see [Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md).




<a name="loio3e409d85ee784ec184d6442331b645fe__postreq_yqs_gkf_5fb"/>

## Next Steps

Configure HTTP basic authentication for the application. For more information about the configuration, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

**Related Information**  


[Configure OpenID Connect Application for Authorization Code Flow](configure-openid-connect-application-for-authorization-code-flow-72c478e.md "This document is intended to help you configure an OpenID Connect application in the administration console for Identity Authentication for the authorization code flow.")

[Configure OpenID Connect Application for Resource Owner Password Credentials Flow](configure-openid-connect-application-for-resource-owner-password-credentials-flow-cafba77.md "This document is intended to help you configure an OpenID Connect application in the administration console for Identity Authentication for the resource owner password credentials flow.")

[Configure OpenID Connect Application for Implicit Flow](configure-openid-connect-application-for-implicit-flow-26090fd.md "This document is intended to help you configure an OpenID Connect application in the administration console for Identity Authentication for the implicit flow.")

[Configure OpenID Connect Application for JWT Bearer Flow](configure-openid-connect-application-for-jwt-bearer-flow-e42fb4d.md "This document is intended to help you configure an OpenID Connect application in the administration console for Identity Authentication for the JWT bearer flow.")

[Configure OpenID Connect Application for Token Exchange](configure-openid-connect-application-for-token-exchange-351866e.md "This document is intended to help you configure an OpenID Connect application in the administration console for Identity Authentication for the Token Exchange flow.")

[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

