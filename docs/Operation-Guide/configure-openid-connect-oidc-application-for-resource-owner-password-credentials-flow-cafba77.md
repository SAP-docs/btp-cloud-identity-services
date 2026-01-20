<!-- copycafba7730eeb4d4bbfaa0b200e8cfbac -->

# Configure OpenID Connect \(OIDC\) Application for Resource Owner Password Credentials Flow

This document is intended to help you configure an OpenID Connect \(OIDC\) application in the administration console for SAP Cloud Identity Services for the resource owner password credentials flow.



<a name="copycafba7730eeb4d4bbfaa0b200e8cfbac__prereq_grq_3jn_v2b"/>

## Prerequisites

You have an OpenID Connect \(OIDC\) application in the administration console for SAP Cloud Identity Services. For more information, see [Create OpenID Connect \(OIDC\) Application](create-openid-connect-oidc-application-62fb1c3.md).



## Context

The trust is configured by entering the information manually. You can enter manually the name of the client \(relying party\).

To configure an OpenID Connect \(OIDC\) trusted application in the administration console for SAP Cloud Identity Services, proceed as follows:



<a name="copycafba7730eeb4d4bbfaa0b200e8cfbac__steps_ksg_x2m_fp"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *OpenID Connect \(OIDC\) Configuration*.

6.  Under the *Configure Manually* section provide a name of your choice.

7.  **Optional:** \(If you have added a second signing certificate in *Tenant Settings* or an application certificate in *Applications*\) Under *Identity Provider Certificates*, choose the certificate to be used when a request to the application is signed.


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

    > ### Tip:  
    > To add an application certificate for the specific application, go to *Applications* \> *choose the application you want to edit* \> *Single Sign-On* \> *Identity Provider Certificates* \> *\+Add*.

    > ### Caution:  
    > The application will stop working if the configuration of the application is not updated with the new certificate.

    > ### Note:  
    > Your choice of *Active* certificate in the list is not related with the choice of *Default* certificate in *Tenant Settings* \> *SAML 2.0 Configuration* \> *SAML 2.0* \> *Signing Certificates*.


    
    </td>
    </tr>
    </table>
    
    > ### Tip:  
    > When the default identity provider certificate is changed with a new one, and the old one is not used anymore, we recommend you to delete the old certificate.

8.  Select the *Password*

    > ### Note:  
    > Beware that for each flow the respective grant type must be selected. All other grant types can be deselected if they aren't required by the application.

9.  Save your selection. Once the application has been changed, the system displays the message ***Application <name of application\> updated***.

    > ### Remember:  
    > Configure trust on the client side. See the client documentation for more information about how to configure the trust.




<a name="copycafba7730eeb4d4bbfaa0b200e8cfbac__postreq_yqs_gkf_5fb"/>

## Next Steps

-   Configure HTTP basic authentication for the application. For more information about the configuration, see [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md).

-   Enable the public client flows option for this application. In the administration console, choose *the OpenID Connect \(OIDC\) application* \> *Client Authentication under the Trust tab* \> *Enable Public Client Flows under Public Client*. Optionally, you can configure the API permission groups. For more information, see [Consuming APIs from Other Applications](../Development/consuming-apis-from-other-applications-29e204d.md) .

    > ### Note:  
    > The *Public* client type is used for environments where it is difficult to protect the client credential, such as mobile and desktop applications, and client-side parts of web applications.


**Related Information**  


[Configure OpenID Connect \(OIDC\) Application for Authorization Code Flow](configure-openid-connect-oidc-application-for-authorization-code-flow-72c478e.md "This document is intended to help you configure an OpenID Connect (OIDC) application in the administration console for SAP Cloud Identity Services for the authorization code flow.")

[Configure OpenID Connect \(OIDC\) Application for Client Credentials Flow](configure-openid-connect-oidc-application-for-client-credentials-flow-3e409d8.md "This document is intended to help you configure an OpenID Connect (OIDC) application in the administration console for SAP Cloud Identity Services for the client credentials flow.")

[Configure OpenID Connect Application for Implicit Flow](configure-openid-connect-application-for-implicit-flow-26090fd.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the implicit flow.")

[Configure OpenID Connect \(OIDC\) Application for JWT Bearer Flow](configure-openid-connect-oidc-application-for-jwt-bearer-flow-e42fb4d.md "This document is intended to help you configure an OpenID Connect (OIDC) application in the administration console for SAP Cloud Identity Services for the JWT bearer flow.")

[Configure OpenID Connect Application for Token Exchange](configure-openid-connect-application-for-token-exchange-351866e.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the Token Exchange flow.")

