<!-- copy7ea233bdd2c84f1c9a10dd47dc030fc0 -->

# Configure OpenID Connect \(OIDC\) Application for Client Credentials Flow

This document is intended to help you configure an OpenID Connect \(OIDC\) application in the administration console for SAP Cloud Identity Services for the client credentials flow.



<a name="copy7ea233bdd2c84f1c9a10dd47dc030fc0__prereq_grq_3jn_v2b"/>

## Prerequisites

You have an OpenID Connect \(OIDC\) application in the administration console for SAP Cloud Identity Services. For more information, see [Create OpenID Connect \(OIDC\) Application](create-openid-connect-oidc-application-62fb1c3.md).



## Context

The trust is configured by entering the information manually. You can enter manually the name of the client \(relying party\).

To configure an OpenID Connect \(OIDC\) trusted application in the administration console for SAP Cloud Identity Services, proceed as follows:



<a name="copy7ea233bdd2c84f1c9a10dd47dc030fc0__steps_ksg_x2m_fp"/>

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

6.  **Optional:** \(If you have added a second signing certificate in *Tenant Settings* or an application certificate in *Applications*\) Under *Identity Provider Certificates*, choose the certificate to be used when a request to the application is signed.


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

7.  Select the *Client Credentials* grant type.

    > ### Note:  
    > Beware that for each flow the respective grant type must be selected. All other grant types can be deselected if they aren't required by the application.

8.  Save your selection. Once the application has been changed, the system displays the message ***Application <name of application\> updated***.

    > ### Remember:  
    > Configure trust on the client side. See the client documentation for more information about how to configure the trust.




<a name="copy7ea233bdd2c84f1c9a10dd47dc030fc0__postreq_yqs_gkf_5fb"/>

## Next Steps

1.  Configure authentication for the application. For more information about the configuration, see [API Authentication](api-authentication-9d200d5.md).

2.  Invalidate the tokens that are no longer need. For more information, see [Call Identity Authentication Revoke Token Endpoint](call-identity-authentication-revoke-token-endpoint-3501e42.md).

**Related Information**  


[Configuring OpenID Connect \(OIDC\)](configuring-openid-connect-oidc-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect (OIDC) protected applications.")

