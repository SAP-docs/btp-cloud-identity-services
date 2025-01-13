<!-- loio671d2e6de90e44caaa6dede4ab315b48 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure Authentication Provider To Migrate User Passwords from SAP SuccessFactors Systems to Identity Authentication



<a name="loio671d2e6de90e44caaa6dede4ab315b48__prereq_ibr_d4t_lgb"/>

## Prerequisites

-   You have provisioned the users from `SAP SuccessFactors` to Identity Authentication.
-   Users provisioned to Identity Authentication have the `sourceSystem` attribute with value `100`, and the `sourceSystemId` with value equal to the SAP SuccessFactors company ID.

    You can find information about the user's authentication provider type and system ID under the legal tab in the user details section. For more information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).




## Context

In this scenario, you have an SAP SuccessFactors instance integrated with Identity Authentication. In the SAP SuccessFactors instance, there are users that log on with username and password \(also known as password or non-sso users\). The authentication provider opportunity gives the possibility these users to be migrated and to use Identity Authentication without the need to change the passwords that they already have. The password of each SAP SuccessFactors user is migrated once only during his or her first successful logon after the configuration of the authentication provider scenario in Identity Authentication. After that the user passwords are managed by Identity Authentication.

The first logon after the migration must be with a username and password. After this first successful logon, the user can use any other allowed logon identifier.

> ### Remember:  
> If a user has enabled the *Remember me* option, when that user changes his or her password in the external authentication provider, the remember me cookie isn't invalidated. For more information, see [Use the Remember Me Option](../User-Guide/use-the-remember-me-option-bc7c6c6.md).

To configure a authentication provider, follow the steps below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Authentication Providers* tile.

3.  Press the *Create* button on the left-hand panel to add a new authentication provider to the list.

4.  Under *Configuration*, make the corresponding entries in the configuration for the target system you want to create:


    <table>
    <tr>
    <th valign="top">

    Configurations
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Display Name*
    
    </td>
    <td valign="top">
    
    The name of the configuration.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Type*
    
    </td>
    <td valign="top">
    
    Select the *SuccessFactors* type.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Company ID*
    
    </td>
    <td valign="top">
    
    The company of the authentication provider.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Password Validation URL*
    
    </td>
    <td valign="top">
    
    The URL endpoint for validation of the users name and password. It can be provided by the authentication provider administrator.

    > ### Note:  
    > The URl must have the following pattern: `https://<SuccessFactors_API_Host>/odata/v2/restricted/validateUser`
    > 
    > Replace the host `<SuccessFactors_API_host>` with the Authentication URL host from the [SAP SuccessFactors Data Centers Mapping to Authentication URL](sap-successfactors-data-centers-mapping-to-authentication-url-f38bb6b.md) document.
    > 
    > Plain HTTP is supported for testing purposes only. Make sure that you use the encrypted HTTPS protocol for productive systems.
    > 
    > For more information about the mapping between theSAP SuccessFactors data centers and the password validation URL, see [SAP SuccessFactors Data Centers Mapping to Authentication URL](sap-successfactors-data-centers-mapping-to-authentication-url-f38bb6b.md).

    > ### Remember:  
    > If you choose the *X.509* certificate as your *Authentication Type*, you'll need to add ".cert" after the subdomain part of the URL. For example:
    > 
    > `https://exampleapi.cert.sapsf.com/odata/v2/restricted/validateUser`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    -   *Authentication Type*


    
    </td>
    <td valign="top">
    
    Choose:

    -   *Basic* - provide *Technical User* and *Technical User Secret*:

        *Technical User*

        Technical user added in the authentication provider that has administrator permissions to access the OData API. It can be provided by the external authentication provider administrator.

        For more information of the permission settings of the user, see [Setting Up an API User for Sync Jobs in SAP SuccessFactors](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/0a6e6705d89e42649e3aa8732f2b0724.html?version=2311).

        *Technical User Secret*

        Password set on the technical user. It can be provided by the authentication provider administrator.

        > ### Tip:  
        > For productive systems, we recommend that you use passwords that are difficult to be guessed.

    -   *X.509*

        Enter CN for the certificate in the provided field.

        Once the certificate is generated, you can view its details. The validity of the certificate is 1 year.

        > ### Note:  
        > You can choose the option for automatic regeneration of the certificate by selecting the *Automatic Renewal* checkbox. Two weeks before the expiry of the certificate, it is regenerated. The renewed certificate will have the same DN.

        > ### Remember:  
        > If you choose the *X.509* certificate as your *Authentication Type*, you'll need to upload that certificate into SAP SuccessFactors to register Identity Authentication for incoming calls using *X.509* certificate-based authentication. Refer to [Upgrade to X.509 Certificate-Based Authentication for Incoming Calls](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/2b8f220f51ce455da3f349ef851d264c.html) for the steps to complete the upload.

        > ### Tip:  
        > To create a *X.509* certificate to use it as *Authentication Type* for the authentication provider:
        > 
        > 1.  Open the authentication provider created in the administration console.
        > 
        > 2.  Choose the :eyeglasses: under the *Actions* column.
        > 3.  Copy content of the *X.509* certificate from the popup window.
        > 4.  Create a `cer.` file in the following way:
        > 
        >     > ### Sample Code:  
        >     > ```
        >     > 
        >     > -----BEGIN CERTIFICATE-----
        >     > <Copied content of the X.509 certificate>
        >     > -----END CERTIFICATE-----
        >     > ```



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *First Logon Behavior*
    
    </td>
    <td valign="top">
    
    Choose if a user whose password doesn't meet the password policy requirements of the application must reset or change it after the first successful logon.

    -   *Change password* - The user will be presented a dialog to change their password. The new password must meet the current password policy.

        This is the default choice.

    -   *Reset password* - The user receives the reset password link by email.


    
    </td>
    </tr>
    </table>
    
5.  Save your configuration.

    The system displays the message ***Authentication provider <id of the system\> created***.

    If you have chosen *Authentication Type - X.509*, the certificate is generated after saving the configuration.

6.  **Optional:** Choose *Test Connection* to test the authentication provider configuration.




<a name="loio671d2e6de90e44caaa6dede4ab315b48__postreq_pks_twy_3zb"/>

## Next Steps

> ### Note:  
> If an application requires force authentication \(ForceAuthn="true"\), users have to authenticate themselves against the corporate identity provider each time they access the application even if single sign-on \(SSO\) is enabled.

-   \(Optional\) To edit an existing authentication provider configuration, select *provider you want to edit* \> *Edit button* \> *make the necessary changes* \> *Save*.
-   \(Optional\) To change the display name of an existing authentication provider, select the authentication provider whose name you want to change, choose the :pencil2:, provide the new name, and save your changes.

**Related Information**  


[Configure Authentication Provider To Migrate User Passwords fromSAP Learning Management System to Identity Authentication](configure-authentication-provider-to-migrate-user-passwords-fromsap-learning-management-s-0d85eb7.md)

[Configure Authentication Provider To Migrate User Passwords from SAP Fieldglass to Identity Authentication](configure-authentication-provider-to-migrate-user-passwords-from-sap-fieldglass-to-identi-b0c7ec8.md)

[SAP SuccessFactors Data Centers Mapping to Authentication URL](sap-successfactors-data-centers-mapping-to-authentication-url-f38bb6b.md)

[Migrating Passwords from SAP SuccessFactors to Identity Authentication Service](https://help.sap.com/viewer/568fdf1f14f14fd089a3cd15194d19cc/latest/en-US/b25f3f36deed40ddb3aee14c6818df06.html)

