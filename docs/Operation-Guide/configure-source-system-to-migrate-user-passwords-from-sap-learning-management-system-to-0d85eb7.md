<!-- loio0d85eb7175ee43d8af51d2edc29ca415 -->

# Configure Source System To Migrate User Passwords from SAP Learning Management System to Identity Authentication



<a name="loio0d85eb7175ee43d8af51d2edc29ca415__prereq_ibr_d4t_lgb"/>

## Prerequisites

-   You have provisioned the users from `SAP Learning Management System` to Identity Authentication.
-   Users provisioned to Identity Authentication have the `sourceSystem` attribute with value `101`, and the `sourceSystemId` with value equal to the SAP Learning Management System tenant ID.

    You can find information about the user's source system type and source system ID under the legal tab in the user details section. For more information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).




## Context

In this scenario, you have an SAP Learning Management System instance integrated with Identity Authentication. In the SAP Learning Management System instance there are users that log on with username and password \(also known as External Learners\). The source system opportunity gives the possibility these users to be migrated and to use Identity Authentication without the need to change the passwords that they already have. The password of each SAP Learning Management System user is migrated once only during his or her first successful logon after the configuration of the source system scenario in Identity Authentication. After that the user passwords are managed by Identity Authentication.

> ### Remember:  
> If a user has enabled the *Remember me* option, when that user changes his or her password in the external source system, the remember me cookie is not invalidated. For more information, see [Use the Remember Me Option](../User-Guide/use-the-remember-me-option-bc7c6c6.md).

To configure a source system, follow the steps below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Source Systems* tile.

3.  Press the *Create* button on the left-hand panel to add a new source system to the list.

4.  Make the corresponding entries in the configuration for the target system you want to add:

    -   *Source System*

        **Source System**


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

        Select the *Learning Management System* type.


        
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

        *System ID*


        
        </td>
        <td valign="top">

        The ID of the source system.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Password Validation URL*


        
        </td>
        <td valign="top">

        The URL endpoint for validation of the users name and password. It is automatically generated and has the following pattern: `https://<lms-system-id>.plateau.com/learning/rest/integrated/admin/Learner.svc/ias/v1/~validateCredentials`

        The *Password Validation URL* can be provided also by the source system administrator. It must have the following pattern: `https://<lms-system-id>.plateau.com/learning/rest/integrated/admin/Learner.svc/ias/v1/~validateCredentials`

        Plain HTTP is supported for testing purposes only. Make sure that you use the encrypted HTTPS protocol for productive systems.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Authentication Type*


        
        </td>
        <td valign="top">

        Choose:

        -   *Basic* - provide *Technical User* and *Technical User Secret*:

            *Technical User*

            Technical user added in the source system that has administrator permissions to access the OData API. It can be provided by the external source system administrator.

            *Technical User Secret*

            Secret set on the technical user. It can be provided by the source system administrator.

            > ### Tip:  
            > For productive systems, we recommend that you use passwords that are difficult to be guessed.

        -   *X.509*

            Enter CN for the certificate in the provided field.

            Once the certificate is generated, you can view its details. The validity of the certificate is one year.

            > ### Note:  
            > You can choose the option for automatic regeneration of the certificate by selecting the *Automatic Renewal* checkbox. Two weeks before the expiry of the certificate, it will be regenerated. The renewed certificate will have the same DN.



        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *First Logon Behavior*


        
        </td>
        <td valign="top">

        Choose:

        -   if a user whose password does not meet the password policy requirements of the application must reset or change it after the first successful logon.
        -   if a user whose LMS password is expired must reset or change it after the first successful logon.

        The default choice is *Change password*.


        
        </td>
        </tr>
        </table>
        

5.  Save your configuration.

    The system displays the message ***Source system <id of the system\> created***.

    If you have chosen *Authentication Type - X.509*, the certificate is generated after saving the configuration.

6.  **Optional:** Choose *Test Connection* to test the source system configuration.


**Related Information**  


[Configure Source System To Migrate User Passwords from SAP SuccessFactors Systems to Identity Authentication](configure-source-system-to-migrate-user-passwords-from-sap-successfactors-systems-to-iden-671d2e6.md)

[Configure Source System To Migrate User Passwords from SAP Fieldglass to Identity Authentication](configure-source-system-to-migrate-user-passwords-from-sap-fieldglass-to-identity-authent-b0c7ec8.md)

[SAP SuccessFactors Data Centers Mapping to Authentication URL](sap-successfactors-data-centers-mapping-to-authentication-url-f38bb6b.md)

