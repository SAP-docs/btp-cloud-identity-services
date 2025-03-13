<!-- loio7cecbdf34f7f4ed5ba294d80bb0be075 -->

# Make a New Trust Configuration

Configure trust from the service provider metadata by uploading it or by accessing it from a URL, or by entering the information manually. .



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

The trust is configured from the service provider metadata by uploading it or by accessing it from a URL, or by entering the information manually.

You can enter manually the name of the service provider, its endpoints, and certificates.

To configure a SAML 2.0 trusted service provider in the administration console for SAP Cloud Identity Services, proceed as follows:



<a name="loio7cecbdf34f7f4ed5ba294d80bb0be075__steps_ksg_x2m_fp"/>

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

    When the identity provider metadata is uploaded, or the metadata URL is used, the fields are populated with the parsed data from the XML file.


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

        > ### Restriction:  
        > The metadata URL must not contain query parameter.

        > ### Remember:  
        > The SAML 2.0 metadata URL is required for the automatic renewal of the automatic renewal of the signing and encryption certificates of the application. When the metadata URL is provide, Identity Authentication will update automatically the expired encryption certificate, and the SAML 2.0 certificate during the first sign in attempt that fails due to the expired certificate.



    
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
    
    Assertion Consumer Service Endpoints
    
    </td>
    <td valign="top">
    
    The SP's endpoint URL that receives the response with the SAML assertion from Identity Authentication.

    The following options are possible:

    -   *URLs for Browser Flow* 

        Choose *Add* and enter the allowed domain for browser flows.

    -   *Logout Endpoints*

        Choose *Add* and enter the SP's endpoint URL that receives the logout response or request \(for a multiple SPs scenario\) from Identity Authentication for the termination of all current sessions.

        This field has the following attributes:

        -   *Binding* - specifies the SAML binding supported by the logout endpoint.
            -   HTTP-POST
            -   HTTP-REDIRECT
            -   SOAP - The SOAP Endpoint is called only when the user password is changed.

                > ### Note:  
                > If you have configured a *Warning* concurrent user access option, you must also have a Single Logout Endpoints \(SLO\) URL with a SOAP binding added for the SAML 2.0 application. Otherwise if a user chooses to sign out and continue to new session, an SLO request for the old session won't be sent to the application. For more information, see [Configure Concurrent User Access to the Application](configure-concurrent-user-access-to-the-application-80ead1a.md).


        -   *URL* - specifies the location of the logout endpoint.
        -   *Response URL* - \(optional\) specifies a different location to which logout response messages should be sent.

    -   *URL for Principal Propagation* - URL is required for principal propagation scenarios to ABAP applications according to RFC 7522. For the proper URL consult the documentation of the providing application.

    > ### Note:  
    > During authentication the ACS endpoint is provided with the request. Through the flow, Identity Authentication is removing the query attributes, and during the response it compares the ACS endpoint with what is configured in the SAML 2.0 configuration of the application.
    > 
    > Identity Authentication is looking for an exact match and If there is no such match the authentication will fail.


    
    </td>
    </tr>
    </table>
    
    > ### Restriction:  
    > The *Metadata File*, *Name*, *Assertion Consumer Service Endpoint*, and *Single Logout Endpoint* fields are not editable for the system applications.




## Next Steps

Configure trust on the service provider side.

1.  Download the SAML 2.0 metadata of Identity Authentication.

    > ### Note:  
    > For more information about how to download the SAML 2.0 metadata describing Identity Authentication as identity provider see [Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md).

2.  Configure the service provider to trust Identity Authentication.

    > ### Note:  
    > See the service provider documentation for more information about how to configure the trust.

    > ### Tip:  
    > If you use SAP BTP as a service provider, see [Integrating the Service with SAP Business Technology Platform, Neo Environment](../Integrating-the-Service/integrating-the-service-with-sap-business-technology-platform-neo-environment-fe84459.md#loiofe84459e688c43698591d3b9e1aac828).
    > 
    > The content in this section is only relevant for SAP BTP Neo environment.
    > 
    > The content in this section is not relevant for China \(Shanghai\) region.

3.  Configure the certificates in the administration console for Cloud Identity Services. For more information, see [Configure Signing Certificates and Certificate Options](configure-signing-certificates-and-certificate-options-9a8eade.md).

**Related Information**  


[Configure Signing Certificates and Certificate Options](configure-signing-certificates-and-certificate-options-9a8eade.md "You can add up to two signing certificates per application in the administration console for Cloud Identity Services.")

