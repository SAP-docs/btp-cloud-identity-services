<!-- loiob0c7ec883b384eecb833776503e53509 -->

# Configure Source System To Migrate User Passwords from SAP Fieldglass to Identity Authentication



<a name="loiob0c7ec883b384eecb833776503e53509__prereq_ibr_d4t_lgb"/>

## Prerequisites

-   You have provisioned the users from SAP Fieldglass to Identity Authentication.
-   Users provisioned to Identity Authentication have the `sourceSystem` attribute with value `102`, and the `sourceSystemId` with value equal to the SAP Fieldglass tenant ID.

    You can find information about the user's source system type and source system ID under the legal tab in the user details section. For more information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).




## Context

In this scenario, you have an SAP Fieldglass instance integrated with Identity Authentication. In the SAP Fieldglass instance there are users that log on with username and password. The source system opportunity gives the possibility these users to be migrated and to use Identity Authentication without the need to change the passwords that they already have. The password of each SAP Fieldglass user is migrated once only during his or her first successful logon after the configuration of the source system scenario in Identity Authentication. After that the user passwords are managed by Identity Authentication.

> ### Remember:  
> If a user has enabled the *Remember me* option, when that user changes his or her password in the external source system, the remember me cookie is not invalidated. For more information, see [Use the Remember Me Option](../User-Guide/use-the-remember-me-option-bc7c6c6.md).

To configure a source system, follow the steps below:



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

2.  Under *Identity Providers*, choose the *Source Systems* tile.

3.  Press the *Create* button on the left-hand panel to add a new source system to the list.

4.  Make the corresponding entries in the configuration for the target system you want to add:

    -   *Source System*

        <a name="loiob0c7ec883b384eecb833776503e53509__table_pcc_qmv_jgb"/>Source System


        <table>
        <tr>
        <th valign="top">

        Configuration


        
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

        \(optional\) The name of the configuration.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Type*


        
        </td>
        <td valign="top">

        Select the ***Fieldglass*** type.


        
        </td>
        </tr>
        </table>
        

    -   *Configuration*


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

        *Company Code*


        
        </td>
        <td valign="top">

        The company code of the source system.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Password Validation URL*


        
        </td>
        <td valign="top">

        The URL endpoint for validation of the users name and password. It must have the following pattern: `https://<fieldglass_host>/api/v1/ias/passwordsync`

        Plain HTTP is supported for testing purposes only. Make sure that you use the encrypted HTTPS protocol for productive systems.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Technical User*


        
        </td>
        <td valign="top">

        Technical user added in the source system that has administrator permissions to access the OData API. It can be provided by the external source system administrator.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Technical User Secret*


        
        </td>
        <td valign="top">

        Secret set on the technical user. It can be provided by the source system administrator.

        > ### Tip:  
        > For productive systems, we recommend that you use passwords that are difficult to be guessed.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Token URL*


        
        </td>
        <td valign="top">

        Token endpoint to which the technical user is authenticated.


        
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

    The system displays the message ***Source system <id of the system\> created***.

6.  Choose *Test Connection* to test the source system configuration.


**Related Information**  


[Configure Source System To Migrate User Passwords from SAP SuccessFactors Systems to Identity Authentication](configure-source-system-to-migrate-user-passwords-from-sap-successfactors-systems-to-iden-671d2e6.md)

[Configure Source System To Migrate User Passwords from SAP Learning Management System to Identity Authentication](configure-source-system-to-migrate-user-passwords-from-sap-learning-management-system-to-0d85eb7.md)

[SAP SuccessFactors Data Centers Mapping to Authentication URL](sap-successfactors-data-centers-mapping-to-authentication-url-f38bb6b.md)

