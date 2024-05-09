<!-- loio51f1f7550dc24aa99cbf84d1e96e2ad5 -->

# Configure SAML 2.0 Service Provider

This document is intended to help you configure a SAML 2.0 service provider \(SP\) in the administration console for SAP Cloud Identity Services.



## Prerequisites

You have the service provider metadata. See the service provider documentation for more information or contact the administrator of the service provider.

> ### Tip:  
> For more information how to download the metadata for SAP BTP when it acts as a service provider \(SP\), see [Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dc618538d97610148155d97dcd123c24.html). The content in this section is only relevant for SAP BTP Neo environment. The content in this section isn’t relevant for China \(Shanghai\) region.

> ### Remember:  
> If your scenario includes the enabling of the *Trust All Corporate Identity Providers* option in the administration console, the service provider metadata must contain the assertion consumer \(ACS\) endpoint that can process unsolicited SAML responses.
> 
> With SAP BTP, the endpoint is the URL of the application's protected page. This endpoint must be either set as a default ACS endpoint of the service provider in Identity Authentication, or chosen by its index when performing IdP-initiated SSO. For more information, see [Configure IdP-Initiated SSO](configure-idp-initiated-sso-5d59caa.md).
> 
> > ### Example:  
> > ```
> > <ns3:AssertionConsumerService index="1" isDefault="false" Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST" Location="https://<application URL>/protected.jsp"
> > />
> > ```



## Context

The trust is configured by uploading the service provider metadata, or by entering the information manually.

You can enter manually the name of the service provider, its endpoints, and its signing certificate.

You can add up to two signing certificates. Both signing certificates are accepted according to the certificate validity.

You can choose the identity provider certificate to be used for signing for each application. For more information about the identity provider certificates, see [Tenant SAML 2.0 Configuration](tenant-saml-2-0-configuration-e81a19b.md).

The idea behind the ability to choose the IdP certificate is that when you want to change the default IdP certificate all applications will have downtime since the applications have trust with the current default application on the application side. So, when adding new IdP certificate you can change the applications one by one to trust the new certificate.

To configure a SAML 2.0 trusted service provider in the administration console for SAP Cloud Identity Services, proceed as follows:



<a name="loio51f1f7550dc24aa99cbf84d1e96e2ad5__steps_ksg_x2m_fp"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *SAML 2.0 Configuration*.

6.  Upload the service provider metadata XML file, use the metadata URL, or manually enter the communication settings negotiated between Identity Authentication and the service provider.

    > ### Remember:  
    > If your scenario includes the enabling of the *Trust All Corporate Identity Providers* option, the assertion consumer \(ACS\) endpoint with the URL of the application's protected page, and the index must be included in the service provider metadata.

    > ### Note:  
    > Use a file with an extension `.xml`.
    > 
    > If you use SAP BTP as a service provider, see [Integrating the Service with SAP Business Technology Platform, Neo Environment](../Integrating-the-Service/integrating-the-service-with-sap-business-technology-platform-neo-environment-fe84459.md#loiofe84459e688c43698591d3b9e1aac828) for more information how to download its metadata. The content in this section is only relevant for SAP BTP Neo environment. The content in this section is relevant for China \(Shanghai\) region.

    When the identity provider metadata is uploaded, or the metadata URL is used, the fields are populated with the parsed data from the XML file. The minimum configuration is to complete the *Name* field.


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
    
    -   The metadata XML file of the service provider.
    -   The URL with service provider metadata.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Name
    
    </td>
    <td valign="top">
    
    The entity ID of the service provider.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Assertion Consumer Service Endpoint
    
    </td>
    <td valign="top">
    
    The SP's endpoint URL that receives the response with the SAML assertion from Identity Authentication.

    The following options are possible:

    -   *URLs for Browser Flow* - the allowed domain for browser flows.
    -   *URL for Principal Propagation* - URL is required for principal propagation scenarios to ABAP applications according to RFC 7522. For the proper URL consult the documentation of the providing application.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Single Logout Endpoint
    
    </td>
    <td valign="top">
    
    The SP's endpoint URL that receives the logout response or request \(for a multiple SPs scenario\) from Identity Authentication for the termination of all current sessions.

    This field has the following attributes:

    -   *Binding* - specifies the SAML binding supported by the logout endpoint.
        -   HTTP-POST
        -   HTTP-REDIRECT
        -   SOAP - The SOAP Endpoint is called only when the user password is changed.

            > ### Note:  
            > If you have configured a *Warning* concurrent user access option, you must also have a Single Logout Endpoints \(SLO\) URL with a SOAP binding added for the SAML 2.0 application. Otherwise if a user chooses to sign out and continue to new session, an SLO request for the old session won't be sent to the application. For more information, see [Configure Concurrent User Access to the Application](configure-concurrent-user-access-to-the-application-80ead1a.md).


    -   *URL* - specifies the location of the logout endpoint.
    -   *Response URL* - \(optional\) specifies a different location to which logout response messages should be sent.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Signing Certificate
    
    </td>
    <td valign="top">
    
    A base64-encoded certificate used by the identity provider to verify the signatures of the SAML protocol messages created by the service provider.

    Use the *Add* button to add a second signing certificate.

    > ### Note:  
    > If you have two certificates, you can choose a default one, to mark your primary certificate.
    > 
    > The primary certificate is always validated first. If its validation isn't successful, then the secondary certificate is used. The certificate marked as primary is your main certificate. When it's time to rotate the certificates we recommend you to add a second certificate. When the first certificate expires, and you have a second one, you can safely remove the first one.


    
    </td>
    </tr>
    </table>
    
    > ### Restriction:  
    > The *Metadata File*, *Name*, *Assertion Consumer Service Endpoint*, and *Single Logout Endpoint* fields are not editable for the system applications.

7.  **Optional:** Choose the digest algorithm for signing outgoing messages from the dropdown list in the *Algorithm* section. You have the following options:

    -   *SHA-1*
    -   *SHA-256* - the default option \(for applications created after Jun 28, 2021\)
    -   *SHA-512*

8.  **Optional:** Configure the signing options for the application. You have the following possibilities:


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Default Configuration
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Sign assertions*
    
    </td>
    <td valign="top">
    
    *On*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Sign authentication responses*
    
    </td>
    <td valign="top">
    
    *Off*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Sign single logout messages*
    
    </td>
    <td valign="top">
    
    *On*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Require signed authentication requests*
    
    </td>
    <td valign="top">
    
    *Off*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Require signed single logout messages*
    
    </td>
    <td valign="top">
    
    *On*
    
    </td>
    </tr>
    </table>
    
9.  **Optional:** Configure the encryption of the SAML 2.0 response

    1.  Under *Encryption Certificate* add a certificate, if there is no encryption certificates added or you want to add a new certificate.

    2.  Choose the elements to encrypt from the drop-down:

        -   *None* - the default option
        -   *Whole Assertion*
        -   *Subject Name ID*
        -   *Subject Name ID and Attributes*
        -   *Attributes*

        The method for encryption is `aes-128-cbc`.


10. **Optional:** \(If you added second signing certificate in tenant settings\) Under *Identity Provider Certificate*, choose the certificate to be used.

    > ### Tip:  
    > When the default identity provider certificate is changed with a new one, and the old one is not used anymore, we recommend you to delete the old certificate.

11. Save your selection.

    Once the application has been changed, the system displays the message ***Application <name of application\> updated***.




## Next Steps

Configure trust on the service provider side.

1.  Download the SAML 2.0 metadata of Identity Authentication.

    > ### Note:  
    > For more information about how to download the SAML 2.0 metadata describing Identity Authentication as identity provider see [Tenant SAML 2.0 Configuration](tenant-saml-2-0-configuration-e81a19b.md).

2.  Configure the service provider to trust Identity Authentication.

    > ### Note:  
    > See the service provider documentation for more information about how to configure the trust.

    > ### Tip:  
    > If you use SAP BTP as a service provider, see [Integrating the Service with SAP Business Technology Platform, Neo Environment](../Integrating-the-Service/integrating-the-service-with-sap-business-technology-platform-neo-environment-fe84459.md#loiofe84459e688c43698591d3b9e1aac828).
    > 
    > The content in this section is only relevant for SAP BTP Neo environment.
    > 
    > The content in this section is not relevant for China \(Shanghai\) region.


**Related Information**  


[Configure OpenID Connect Application](configure-openid-connect-application-8a0aa2e.md "This document is intended to help you configure an OpenID Connect application in the administration console for SAP Cloud Identity Services.")

[Integrating the Service with SAP Business Technology Platform, Neo Environment](../Integrating-the-Service/integrating-the-service-with-sap-business-technology-platform-neo-environment-fe84459.md#loiofe84459e688c43698591d3b9e1aac828 "SAP BTP acts as a service provider, and Identity Authentication acts as an identity provider in this setup.")

