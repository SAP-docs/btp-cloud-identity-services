<!-- loio028cee2589fd418896ae0235b0aeac40 -->

# Configure Authentication Context

Tenant administrator can configure the authentication context in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.



<a name="loio028cee2589fd418896ae0235b0aeac40__steps_exl_bpk_f4b"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Conditional Authentication*, choose *Configure Requests to Corporate Identity Providers*.

6.  You have the following options:


    <table>
    <tr>
    <th valign="top">

    Protocol
    
    </th>
    <th valign="top">

    Configuration
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **SAML 2.0**
    
    </td>
    <td valign="top">
    
    Choose one of the following and save your changes.

    -   *None* - Authentication context is not sent. The requested authentication context from the service provider is ignored.
    -   \(Available only for SAML 2.0 applications\) *Service Provider Authentication Context* - The received authentication context from the service provider is sent.
    -   *Password Protected Transport* - Authentication context class `urn:oasis:names:tc:SAML:2.0:ac:classes:PasswordProtectedTransport` is sent. The requested authentication context from the service provider is ignored.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **OpenID Connect**
    
    </td>
    <td valign="top">
    
    Add the authentication context class references and save your changes.

    > ### Note:  
    > You can add up to 20 authentication context class references with a length of up to 99 characters each.


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Configure Different Trust Configurations for the Same Identity Authentication](configure-different-trust-configurations-for-the-same-identity-authentication-ba2faa9.md "Tenant administrator can configure the issuer name in the request sent to the corporate identity providers when Identity Authentication acts as a proxy identity provider.")

