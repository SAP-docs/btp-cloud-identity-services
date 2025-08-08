<!-- loio3e409d85ee784ec184d6442331b645fe -->

# Configure OpenID Connect Application for Client Credentials Flow

This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the client credentials flow.



<a name="loio3e409d85ee784ec184d6442331b645fe__prereq_grq_3jn_v2b"/>

## Prerequisites

You have an OpenID Connect application in the administration console for SAP Cloud Identity Services. For more information, see [Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md).



## Context

The trust is configured by entering the information manually. You can enter manually the name of the client \(relying party\).

To configure an OpenID Connect trusted application in the administration console for SAP Cloud Identity Services, proceed as follows:



<a name="loio3e409d85ee784ec184d6442331b645fe__steps_ksg_x2m_fp"/>

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

6.  **Optional:** \(If you have added a second signing certificate in tenant settings\) Under *Identity Provider Certificates*, choose the certificate to be used when a request to the application is signed.


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

7.  Select the *Client Credentials* grant type.

    > ### Note:  
    > Beware that for each flow the respective grant type must be selected. All other grant types can be deselected if they aren't required by the application.

8.  Save your selection. Once the application has been changed, the system displays the message ***Application <name of application\> updated***.

    > ### Remember:  
    > Configure trust on the client side. See the client documentation for more information about how to configure the trust.




<a name="loio3e409d85ee784ec184d6442331b645fe__postreq_yqs_gkf_5fb"/>

## Next Steps

1.  Configure authentication for the application. For more information about the configuration, see [API Authentication](api-authentication-9d200d5.md).

2.  Invalidate the tokens that are no longer need. For more information, see [Call Identity Authentication Revoke Token Endpoint](call-identity-authentication-revoke-token-endpoint-3501e42.md).

**Related Information**  


[Configure OpenID Connect Application for Authorization Code Flow](configure-openid-connect-application-for-authorization-code-flow-72c478e.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the authorization code flow.")

[Configure OpenID Connect Application for Resource Owner Password Credentials Flow](configure-openid-connect-application-for-resource-owner-password-credentials-flow-cafba77.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the resource owner password credentials flow.")

[Configure OpenID Connect Application for Implicit Flow](configure-openid-connect-application-for-implicit-flow-26090fd.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the implicit flow.")

[Configure OpenID Connect Application for JWT Bearer Flow](configure-openid-connect-application-for-jwt-bearer-flow-e42fb4d.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the JWT bearer flow.")

[Configure OpenID Connect Application for Token Exchange](configure-openid-connect-application-for-token-exchange-351866e.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services for the Token Exchange flow.")

[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

