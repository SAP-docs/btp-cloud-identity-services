<!-- loio434a207df6ff4a12923b8f9c5dcff041 -->

# Configure Microsoft Azure AD as Corporate Identity Provider at Identity Authentication

Create and configure Azure AD as a corporate identity provider in the administration console for SAP Cloud Identity Services.



## Prerequisites

-   You have a subscription for Identity Authentication. For more information how to get Identity Authentication, see [Initial Setup](../initial-setup-31af7da.md).
-   You have configured Microsoft Azure AD.



## Context

To use Identity Authentication as a proxy, create, and configure Azure AD as a corporate identity provider in the administration console for SAP Cloud Identity Services. This corporate identity provider is used as an authenticating authority for the applications.



<a name="loio434a207df6ff4a12923b8f9c5dcff041__steps_rc4_rjf_tx"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Choose the *Add* button to create an Azure AD corporate identity provider.

    > ### Note:  
    > If you have an Azure AD corporate identity provider in your list, choose it, and proceed with its configuration. Type the name of the identity provider in the search field to filter the list items.

4.  Under *SAML 2.0*, choose *SAML 2.0 Configuration*.

5.  Upload Azure AD metadata XML file or configure manually the following fields:


    <table>
    <tr>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Information


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Name


    
    </td>
    <td valign="top">
    
    Provide the `entity ID` of the corporate identity provider.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Single Sign-On Endpoint URL


    
    </td>
    <td valign="top">
    
    Provide the URL of the identity provider single sign-on endpoint that receives authentication requests. For *Binding*, choose the one that corresponds to respective single sign-on endpoint.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Single Logout Endpoint URL


    
    </td>
    <td valign="top">
    
    Provide the URL of the identity provider's single logout endpoint that receives logout messages. For *Binding*, choose the one that corresponds to respective single logout endpoint.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Signing Certificate


    
    </td>
    <td valign="top">
    
    Provide the base64-encoded certificate used by the identity provider to digitally sign SAML protocol messages sent to Identity Authentication.


    
    </td>
    </tr>
    </table>
    
    > ### Tip:  
    > The information for the manual configuration is in the metadata XML file of Azure AD.




## Next Steps

1.  Choose **Microsoft ADFS / Azure AD** as the type for the configured corporate identity provider. For more information, see [Choose Identity Provider Type](../Operation-Guide/choose-identity-provider-type-0838379.md).
2.  Select the configured identity provider as the authenticating identity provider for the desired application. For more information, see [Choose Default Identity Provider for an Application](../Operation-Guide/choose-default-identity-provider-for-an-application-e9d8274.md).

