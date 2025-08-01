<!-- copy26090fd09c064d898032da50037e5bec -->

# Configure OpenID Connect Application for Implicit Flow

This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the implicit flow.



<a name="copy26090fd09c064d898032da50037e5bec__prereq_grq_3jn_v2b"/>

## Prerequisites

You have an OpenID Connect application in the administration console for SAP Cloud Identity Services. For more information, see [Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md).



## Context

The trust is configured by entering the information manually. You can enter manually the name of the client \(relying party\), and its redirect URIs.

To configure an OpenID Connect trusted application in the administration console for SAP Cloud Identity Services, proceed as follows:



<a name="copy26090fd09c064d898032da50037e5bec__steps_ksg_x2m_fp"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
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
    > For more information about the format of the redirect URIs and post logout redirect URIs, see [OpenID Connect Application Configurations](openid-connect-application-configurations-1ae324e.md).

7.  **Optional:** \(If you have added a second signing certificate in tenant settings\) Under *IdP Certificates*, choose the certificate to be used when a request to the application is signed.


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **ON**
    
    </td>
    <td valign="top">
    
    This is the default setting. When the option is enabled, the certificate that is set as *Default* in *Tenant Settings* \> *SAML 2.0 Configuration* \> *Signing Certificates* is used when a request to the application is signed.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **OFF**
    
    </td>
    <td valign="top">
    
    When the option is disabled, the certificate that is set as *Active* in the list is used when a request to the application is signed. You can choose the active certificate from the list.

    > ### Note:  
    > Your choice of *Active* certificate in the list is not related with the choice of *Default* certificate in *Tenant Settings* \> *SAML 2.0 Configuration* \> *Signing Certificates*.


    
    </td>
    </tr>
    </table>
    
    > ### Tip:  
    > When the default identity provider certificate is changed with a new one, and the old one is not used anymore, we recommend you to delete the old certificate.

8.  Selct the *Implicit* grant type.

    > ### Note:  
    > Beware that for each flow the respective grant type must be selected. All other grant types can be deselected if they aren't required by the application.

9.  Save your selection. Once the application has been changed, the system displays the message ***Application <name of application\> updated***.

    > ### Remember:  
    > Configure trust on the client side. See the client documentation for more information about how to configure the trust.




<a name="copy26090fd09c064d898032da50037e5bec__postreq_yqs_gkf_5fb"/>

## Next Steps

Configure HTTP basic authentication for the application. For more information about the configuration, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

**Related Information**  


[Configure OpenID Connect Application for Authorization Code Flow](configure-openid-connect-application-for-authorization-code-flow-72c478e.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the authorization code flow.")

[Configure OpenID Connect Application for Client Credentials Flow](configure-openid-connect-application-for-client-credentials-flow-3e409d8.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the client credentials flow.")

[Configure OpenID Connect Application for Resource Owner Password Credentials Flow](configure-openid-connect-application-for-resource-owner-password-credentials-flow-cafba77.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the resource owner password credentials flow.")

[Configure OpenID Connect Application for JWT Bearer Flow](configure-openid-connect-application-for-jwt-bearer-flow-e42fb4d.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the JWT bearer flow.")

[Configure OpenID Connect Application for Token Exchange](configure-openid-connect-application-for-token-exchange-351866e.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the Token Exchange flow.")

[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

