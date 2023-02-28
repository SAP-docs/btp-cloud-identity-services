<!-- loio33832e58695345eea2cd91a2cc8ab24c -->

# Configure Trust with SAML 2.0 Corporate Identity Provider

This document is intended to help you configure trust with a SAML 2.0 corporate identity provider. In this scenario Identity Authentication acts as a proxy to delegate the authentication to the SAML 2.0 corporate identity provider.



## Context

Identity Authentication can use a SAML 2.0 identity provider as an external authenticating authority. Identity Authentication thus acts as a proxy to delegate authentication to the external corporate identity provider. The requests for authentication sent by a service provider will be forwarded to the corporate identity provider.

As an identity provider proxy, Identity Authentication will act as an SAML 2.0 identity provider to the service provider, and as an SAML 2.0 service provider to the corporate identity provider. Once a user is authenticated at the corporate identity provider, successive authentication requests from service providers, which use the same corporate identity provider will not be forwarded to it as long as the session at Identity Authentication is active. Identity Authentication will issue assertions based on the user data received during the first authentication.

> ### Note:  
> If an application requires force authentication \(ForceAuthn="true"\), users have to authenticate themselves against the corporate identity provider each time they access the application even if single sign-on \(SSO\) is enabled.

To use Identity Authentication as a proxy to delegate authentication to an external corporate identity provider you have to configure trust with that corporate identity provider.

To configure trust with the corporate identity provider, follow the procedures below:

 <a name="task_jlj_2rm_qgb"/>

<!-- task\_jlj\_2rm\_qgb -->

## 1. Configure Trust on the Corporate Identity Provider Side

Set up trust with Identity Authentication as a service provider.



<a name="task_jlj_2rm_qgb__prereq_pyl_55m_qgb"/>

## Prerequisites

You have the SAML 2.0 metadata of Identity Authentication. For more information how to download the metadata, see [Tenant SAML 2.0 Configuration](tenant-saml-2-0-configuration-e81a19b.md).



<a name="task_jlj_2rm_qgb__context_ryl_55m_qgb"/>

## Context



<a name="task_jlj_2rm_qgb__steps_syl_55m_qgb"/>

## Procedure

1.  Register Identity Authentication as a service provider at the corporate identity provider.

    > ### Remember:  
    > If you want to use IdP-initiated single sign-on \(SSO\) from your corporate identity provider, you have to add the parameter `sp=<sp_name>` to the assertion consumer service \(ACS\) endpoint configured on your corporate identity provider side for Identity Authentication.
    > 
    > > ### Example:  
    > > https://<the current ACS endpoint URL\>?sp=<sp\_name\>\>
    > > 
    > > `sp` is the name of the SAML 2 service provider for which SSO is performed.
    > 
    > To see how to download the SAML 2.0 metadata of Identity Authentication read [Tenant SAML 2.0 Configuration](tenant-saml-2-0-configuration-e81a19b.md).

2.  **Optional:** Download the corporate identity provider SAML 2.0 metadata.

    You need the corporate SAML 2.0 metadata for the setup of the trust on Identity Authentication. Optionally, you can make the configurations manually.


 <a name="task_rkw_frm_qgb"/>

<!-- task\_rkw\_frm\_qgb -->

## 2. Configure Trust on Identity Authentication Side

Set up trust with a corporate identity provider in the administration console for SAP Cloud Identity Services.



<a name="task_rkw_frm_qgb__prereq_z15_55m_qgb"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have registered Identity Authentication as service provider at the corporate identity provider.

-   You have the corporate identity provider SAML 2.0 metadata.




<a name="task_rkw_frm_qgb__steps_cb5_55m_qgb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md)..

4.  Under *SAML 2.0*, choose *SAML 2.0 Configuration*.

5.  Upload the corporate identity provider metadata XML file, use metadata URL, or manually enter the communication settings negotiated between Identity Authentication and the identity provider.

    > ### Note:  
    > Use a file with an extension `.xml`.

    When the identity provider metadata is uploaded, or the metadata URL is used, the fields are populated automatically with the parsed data from the XML file. The minimum configuration is to complete the *Name* field, add at least one single sign-on endpoint, and provide a signing certificate.

    You can add up to two signing certificates. Both signing certificates are accepted according to the certificate validity.


    <table>
    <tr>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Choose:

    -   Metadata File
    -   Metadata URL


    
    </td>
    <td valign="top">

    -   The metadata XML file of the identity provider.
    -   The URL with identity provider metadata.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Name


    
    </td>
    <td valign="top">

    The entity ID of the identity provider.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Single Sign-On Endpoint URL


    
    </td>
    <td valign="top">

    The URL of the identity provider single sign-on endpoint that receives authentication requests.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Single Logout Endpoint URL


    
    </td>
    <td valign="top">

    The URL of the identity provider's single logout endpoint that receives logout messages.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Binding


    
    </td>
    <td valign="top">

    The SAML-specified HTTP binding used by the identity provider showing how the various SAML protocol messages can be carried over underlying transport protocols.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Signing Certificate


    
    </td>
    <td valign="top">

    A base64-encoded certificate used by the service provider to sign digitally SAML protocol messages sent to Identity Authentication.

    Use the *Add* button to add a second signing certificate.

    > ### Note:  
    > If you have two certificates, you can choose a default one, to mark your primary certificate.


    
    </td>
    </tr>
    </table>
    
6.  **Optional:** Choose the digest algorithm for signing outgoing messages from the dropdown list in the *Algorithm* section. You have the following options:

    -   *SHA-1* 
    -   *SHA-256* - the default option

        > ### Remember:  
        > The algorithm must be *SHA-256* if the Identity provider type is set at *Microsoft ADFS / Azure AD*.

    -   *SHA-512*

7.  **Optional:** Sign SAML 2.0 authentication requests. You have the following options:


    <table>
    <tr>
    <th valign="top">

    Option


    
    </th>
    <th valign="top">

    Notes


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    **Sign authentication requests**


    
    </td>
    <td valign="top">

    Enabled - default configuration


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Sign single logout messages**


    
    </td>
    <td valign="top">

    Enabled - default configuration


    
    </td>
    </tr>
    </table>
    
8.  **Optional:** Enable or disable the *Include scoping* attribute to include or exclude the Scoping element in the SAML 2.0 request.

    > ### Remember:  
    > The default setting for the *Include scoping* is enabled. The Scoping element sent in the SAML 2.0 request is 1.
    > 
    > If the identity provider type is set at *Microsoft ADFS / Azure AD* the default setting for the *Include scoping* is disabled and the Scoping element is not sent in the SAML 2.0 request.

9.  Save your selection.

    Once the identity provider has been updated, the system displays the message ***Identity provider <name of identity provider\> updated***.




<a name="task_rkw_frm_qgb__postreq_eb5_55m_qgb"/>

## Next Steps

-   Select the configured identity provider as the authenticating identity provider for the application. For more information, see [Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md).

-   [\(Optional\) Configure the Name ID Format and AllowCreate Attribute Sent to the SAML 2.0 Corporate IdP](optional-configure-the-name-id-format-and-allowcreate-attribute-sent-to-the-saml-2-0-corp-4fcc090.md) 

**Related Information**  


[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

[Configure IdP-Initiated SSO](configure-idp-initiated-sso-5d59caa.md)

[Choose Identity Provider Type](choose-identity-provider-type-0838379.md "This topic shows you how to choose a type for the corporate identity provider.")

