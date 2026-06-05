<!-- loio4d71887bf33a4d6ab27ad03a25dafbb2 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure Authentication Provider To Migrate User Passwords from SAP Concur to Identity Authentication



<a name="loio4d71887bf33a4d6ab27ad03a25dafbb2__prereq_ibr_d4t_lgb"/>

## Prerequisites

-   You have provisioned the users from SAP Concur to Identity Authentication.
-   Users provisioned to Identity Authentication have the `sourceSystem` attribute with value `103`, and the `sourceSystemId` with value equal to the SAP Concur tenant ID.

    You can find information about the user's authentication provider type and system ID under the legal tab in the user details section. For more information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).




## Context

> ### Remember:  
> If you have completed automated identity provisioning with SAP Cloud Identity Services for your organization, skip the procedure below. For more information, see [Process](https://help.sap.com/docs/SAP_CONCUR/83c94f03f949423a8f76158375832747/3e4fd835e6554ca3bd103ea578ab664b.html?version=latest).

In this scenario, you have an SAP Concur instance integrated with Identity Authentication. In the SAP Concur instance, there are users that log on with username and password. The authentication provider opportunity gives the possibility these users to be migrated and to use Identity Authentication without the need to change the passwords that they already have. The password of each SAP Concur user is migrated once only during his or her first successful logon after the configuration of the authentication provider scenario in Identity Authentication. After that the user passwords are managed by Identity Authentication.

> ### Remember:  
> -   If a user has enabled the *Remember me* option, when that user changes his or her password in the external authentication provider, the remember me cookie is not invalidated. For more information, see [Use the Remember Me Option](../User-Guide/use-the-remember-me-option-bc7c6c6.md).
> 
> -   ​If a user has a second-factor authentication configured for his profile, they will be asked to provide it together with the password.

To configure an authentication provider, follow the steps below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Authentication Providers* tile.

3.  Press the *Create* button on the left-hand panel to add a new authentication provider to the list.

4.  Under *Configuration*, make the corresponding entries in the configuration for the target system you want to add:


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
    
    Select the `Concur` type.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Company ID*
    
    </td>
    <td valign="top">
    
    The company ID of the authentication provider.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Password validation URL*
    
    </td>
    <td valign="top">
    
    The URL endpoint for validation of the users name and password. It must have the following pattern: `https://<concur_host>/password/v0/ias/passwordcheck`

    Plain HTTP is supported for testing purposes only. Make sure that you use the encrypted HTTPS protocol for productive systems.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Common Name \(CN\)*
    
    </td>
    <td valign="top">
    

    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *First Logon Behavior*
    
    </td>
    <td valign="top">
    
    Choose if a user whose password does not meet the password policy requirements of the application must reset or change it after the first successful logon. The default choice is *Change password*.
    
    </td>
    </tr>
    </table>
    
5.  Save your configuration.

    The system displays the message ***Authentication provider <id of the system\> created***.

6.  **Optional:** Choose *Test Connection* to test the authentication provider configuration.




<a name="loio4d71887bf33a4d6ab27ad03a25dafbb2__postreq_pgw_ywy_3zb"/>

## Next Steps

> ### Note:  
> If an application requires force authentication \(ForceAuthn="true"\), users have to authenticate themselves against the corporate identity provider each time they access the application even if single sign-on \(SSO\) is enabled.

-   \(Optional\) To edit an existing authentication provider configuration, select *provider you want to edit* \> *Edit button* \> *make the necessary changes* \> *Save*.
-   \(Optional\) To change the display name of an existing authentication provider, select the authentication provider whose name you want to change, choose the :pencil2:, provide the new name, and save your changes.

**Related Information**  


[Configure Authentication Provider To Migrate User Passwords from SAP SuccessFactors Systems to Identity Authentication](configure-authentication-provider-to-migrate-user-passwords-from-sap-successfactors-syste-671d2e6.md)

[Configure Authentication Provider To Migrate User Passwords from SAP Learning Management System to Identity Authentication](configure-authentication-provider-to-migrate-user-passwords-from-sap-learning-management-0d85eb7.md)

[Configure Authentication Provider To Migrate User Passwords from SAP Fieldglass to Identity Authentication](configure-authentication-provider-to-migrate-user-passwords-from-sap-fieldglass-to-identi-b0c7ec8.md)

[SAP SuccessFactors Data Centers Mapping to Authentication URL](sap-successfactors-data-centers-mapping-to-authentication-url-f38bb6b.md)

