<!-- loioe5b761a6237b449cb718ab47eb915b3c -->

# Create OpenID Connect Application for Resource Owner Password Credentials Flow

You can create a new OpenID Connect application.



## Context

To create a new OpenID Connect application you have to add a new application to the list of applications in Identity Authentication, and then set the protocol of application to OpenID Connect.

To create a new OpenID Connect application, choose your scenario and follow the procedure there.



<a name="loioe5b761a6237b449cb718ab47eb915b3c__steps_qqh_hfk_q4"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Applications* tile.

3.  Choose the *Create* button on the left-hand panel and fill in the information in the dialog box.

4.  Provide the following information and save your configuration:


    <table>
    <tr>
    <th valign="top">

    Fields


    
    </th>
    <th valign="top">

    Notes


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Display Name*


    
    </td>
    <td valign="top">
    
    Required. The display name of the application appears on the logon and registration pages.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Home URL*


    
    </td>
    <td valign="top">
    
    Optional. Users are redirected to the *Home URL* after activating their accounts, when they are created via a CSV file import or the user registration service of Identity Authentication.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Type*


    
    </td>
    <td valign="top">
    
    Optional.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Parent Application*


    
    </td>
    <td valign="top">
    
    Optional.

    > ### Remember:  
    > Newly created applications with an assigned parent application will inherit all the configurations from the parent except for the `Client ID` and `Secrets`. The inherited configurations will be marked as such.


    
    </td>
    </tr>
    </table>
    
    Once the application has been created, the system displays the message ***Application <name of application\> created***.

    The newly created application appears on the list with the applications on the left. It is selected and you can set its protocol to OpenID Connect.

5.  Choose *Trust* \> *SINGLE SIGN-ON* \> *Protocol* 

    > ### Caution:  
    > Make sure that the application you want to configure as OpenID connect is selected on the left.

6.  Select *OpenID Connect*.

7.  Save your selection.

    The system displays the message ***Application <name of application\> updated***.

    > ### Note:  
    > \(Optional\) If necessary, configure additional settings for the application. For more information about the supported configurations for the OpenID Connect applications, see the following links:
    > 
    > -   [Configure the User Attributes Sent to the Application](configure-the-user-attributes-sent-to-the-application-d361407.md)
    > -   [Configure the Default Attributes Sent to the Application](configure-the-default-attributes-sent-to-the-application-a2f1e46.md)
    > -   [Configure Secrets for API Authentication](configure-secrets-for-api-authentication-5c3c35e.md)
    > -   [Configure Certificates for API Authentication](configure-certificates-for-api-authentication-c408083.md)
    > -   [Configure Risk-Based Authentication for an Application](configure-risk-based-authentication-for-an-application-bc52fbf.md#loiobc52fbf3d59447bbb6aa22f80d8b6056)
    > -   [Configure User Access to the Application](configure-user-access-to-the-application-8b147c4.md)
    > -   [Enable Email Verification](enable-email-verification-483d26c.md)
    > -   [Configuring Password Policies](configuring-password-policies-12b3395.md)


**Related Information**  


[Create OpenID Connect Application for Authorization Code Flow](create-openid-connect-application-for-authorization-code-flow-8445e3f.md "Create a new OpenID Connect application for authorization code flow.")

[Create OpenID Connect Application for Client Credentials Flow](create-openid-connect-application-for-client-credentials-flow-98015c8.md "You can create a new OpenID Connect application.")

[Create OpenID Connect Application for Implicit Flow](create-openid-connect-application-for-implicit-flow-b19f5e3.md "Create a new OpenID Connect application for implicit flow.")

[Create OpenID Connect Application for JWT Bearer Flow](create-openid-connect-application-for-jwt-bearer-flow-b099d8c.md "Create a new OpenID Connect application for JWT bearer flow.")

[Create OpenID Connect Application for Token Exchange](create-openid-connect-application-for-token-exchange-e3baf39.md "Create a new OpenID Connect application for Token Exchange flow.")

[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

