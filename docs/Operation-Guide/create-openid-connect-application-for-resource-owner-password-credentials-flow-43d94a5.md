<!-- copy43d94a5d87c34e4db93873b90b27a013 -->

# Create OpenID Connect Application for Resource Owner Password Credentials Flow

You can create a new OpenID Connect application.



## Context

To create a new OpenID Connect application you have to add a new application to the list of applications in Identity Authentication, and then set the protocol of application to OpenID Connect.

To create a new OpenID Connect application, choose your scenario and follow the procedure there.



<a name="copy43d94a5d87c34e4db93873b90b27a013__steps_qqh_hfk_q4"/>

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
    > Newly created applications with an assigned parent application will inherit all the configurations from the parent with the except of the `Client ID` and `Consumed Services`. The inherited configurations will be marked as such.


    
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
    > -   [Enable E-Mail Verification](enable-e-mail-verification-483d26c.md)
    > -   [Configuring Password Policies](configuring-password-policies-12b3395.md)


**Related Information**  


[OpenID Connect](openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

