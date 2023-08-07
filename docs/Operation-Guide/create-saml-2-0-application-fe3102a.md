<!-- loiofe3102ad92d94baa955ffa06b86d2cfa -->

# Create SAML 2.0 Application

You can create a new SAML 2.0 application and customize it to comply with your company requirements.



## Context

When you create a new application. It is set as SAML 2.0 by default.

To create a new SAML 2.0 application, proceed as follows:



<a name="loiofe3102ad92d94baa955ffa06b86d2cfa__steps_qqh_hfk_q4"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

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
    



<a name="loiofe3102ad92d94baa955ffa06b86d2cfa__result_dpz_23k_r2b"/>

## Results

Once the application has been created, the system displays the message ***Application <name of application\> created***.

The newly created application appears on the list with the applications on the left. It is selected and you can proceed with its configuration.



<a name="loiofe3102ad92d94baa955ffa06b86d2cfa__postreq_nhs_nh3_r2b"/>

## Next Steps

1.  Configure the SAML 2.0 trust with the service provider. For more information, see [Configure SAML 2.0 Service Provider](configure-saml-2-0-service-provider-51f1f75.md).
2.  \(Optional\) If necessary, configure the application. For more information about application configuration options, see [Configuring Applications](configuring-applications-61ad3b0.md).

**Related Information**  


[Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md "You can create a new OpenID Connect application.")

[Troubleshooting for Administrators](troubleshooting-for-administrators-f80beb5.md "This section is intended to help administrators deal with error messages in the administration console for SAP Cloud Identity Services.")

