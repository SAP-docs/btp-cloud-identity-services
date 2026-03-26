<!-- loiofe3102ad92d94baa955ffa06b86d2cfa -->

# Create SAML 2.0 Application

You can create a new SAML 2.0 application and customize it to comply with your company requirements.



## Context

To create a new SAML 2.0 application, you have to add a new application to the list of applications in Identity Authentication, and make sure that the protocol of the application is set to SAML 2.0.

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
    
    Optional. Users are redirected to the *Home URL* after activating their accounts, when they're created via a CSV file import or the user registration service of Identity Authentication.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Type*
    
    </td>
    <td valign="top">
    
    Optional.

    > ### Caution:  
    > If the type of the application is not the correct one, the system may change it automatically without a warning.


    
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

    -   If you are an administrator with the *Manage Applications* role, the newly created applications can have as parent any of the parent applications in the administration console. Choose the parent application from the list that pops up.

    -   If you are an administrator with authorizations based on policies, you can assign as parent only the application to which you have read or manage applications rights. The applications to which you have read or manage rights are restricted on the basis of the `application.organization` attribute in the policy. Choose the parent application from the list that pops up. For more information about how to assign authorizations based on policies, see [Configure Application Authorizations](configure-application-authorizations-01cff18.md).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Organization ID*
    
    </td>
    <td valign="top">
    
    Optional.

    This field allows you to group the applications under a specific organization and on the basis of the *Organization ID* to restrict the access to these applications.

    -   If you are an administrator with *Manage Applications* role, the newly created applications by default are in the `global` *Organization ID*. You can change the *Organization ID* during the creation of the new application by entering a new name or later you can edit it.

    -   If your authorizations are based on policies, the newly created applications can take the *Organization ID* of the applications to which you have manage rights on the basis of the `application.organization` attribute in the policy. Choose the allowed *Organization ID* from the drop-down.


    > ### Note:  
    > Applications created either as subscriptions within or with the Identity service of an SAP BTP subaccount receive the *Organization ID* of the application that represents the trust configuration of that subaccount.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Protocol Type*
    
    </td>
    <td valign="top">
    
    Select the *SAML 2.0* radio-button.

    > ### Remember:  
    > Newly created applications with an assigned parent application will inherit the protocol from the parent. To change the protocol, first create the new application and then edit it.


    
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


[Create OpenID Connect \(OIDC\) Application](create-openid-connect-oidc-application-62fb1c3.md "You can create a new OpenID Connect (OIDC) application.")

