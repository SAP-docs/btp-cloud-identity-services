<!-- loio4fcc0905ea3e442fb33f4cc759399646 -->

# \(Optional\) Configure the Name ID Format and AllowCreate Attribute Sent to the SAML 2.0 Corporate IdP



## Context

When Identity Authentication uses a SAML 2.0 identity provider \(IdP\) as an external authenticating authority it acts as a proxy to delegate authentication to that external corporate identity provider. As an identity provider proxy, Identity Authentication acts as a SAML 2.0 identity provider to the service provider, and as a SAML 2.0 service provider to the corporate identity provider. The requests for authentication sent by the service provider are forwarded by Identity Authentication to the corporate identity provider.

In this scenario, the tenant administrator can configure the name ID format that is sent to the corporate identity provider. The name ID format is used in the `Format` attribute of the `NameID` element that Identity Authentication sends to the corporate identity provider with the SAML 2.0 authentication request.

The tenant administrator can also configure if and how the `AllowCreate` attribute is sent to the corporate identity provider.

> ### Remember:  
> To use Identity Authentication as a proxy to delegate authentication to an external corporate identity provider you have to configure trust with that corporate identity provider. For more information, see [Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md).

To set the name ID format to be sent to the corporate identity provider, proceed as follows:



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

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md)..

4.  Under *SAML 2.0*, choose *Name ID Policy*.

5.  Select the name ID format from the following:

    -   *None* - Name ID format is not sent. Corporate identity provider decides which attribute to use.
    -   *Default* - The name ID format received from the application is sent.
    -   *Unspecified* - The name ID format `urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified` is always sent.
    -   *E-Mail* - The name ID format `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress` is always sent.

6.  Select the AllowCreate configuration from the following:

    -   *None* - `AllowCreate` attribute sent by the Service Provider is ignored.
    -   *Default* - `AllowCreate` attribute sent by the Service Provider is forwarded to the Corporate IdP.
    -   *True* - `AllowCreate` attribute with value "true" is always forwarded to the Corporate IdP.
    -   *False* - `AllowCreate` attribute with value "false" is always forwarded to the Corporate IdP.

7.  Save your selection.

    Once the identity provider has been updated, the system displays the message ***Identity provider <name of identity provider\> updated***.


**Related Information**  


[Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md "This document is intended to help you configure trust with a SAML 2.0 corporate identity provider. In this scenario Identity Authentication acts as a proxy to delegate the authentication to the SAML 2.0 corporate identity provider.")

[Choose Identity Provider Type](choose-identity-provider-type-0838379.md "This topic shows you how to choose a type for the corporate identity provider.")

