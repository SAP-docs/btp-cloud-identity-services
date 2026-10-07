<!-- loiod88b82b4203f4f028a21cab5032f3cc8 -->

# Configure Identity Provider Certificates for Corporate Identity Providers

Select the signing certificate that SAP Cloud Identity Services uses when communicating with a specific OpenID Connect corporate identity provider.



<a name="loiod88b82b4203f4f028a21cab5032f3cc8__prereq-idp-cert"/>

## Prerequisites

Generate the signing certificate you want to use. The certificate must exist in the tenant-level signing certificate list before you can assign it here. For more information, see the following:

-   For RSA certificates \(RS256, RS512\): [Tenant OpenID Connect \(OIDC\) Configurations](tenant-openid-connect-oidc-configurations-3d6abcc.md).
-   For elliptic curve certificates \(ES256, ES384, ES512\): [Generate Elliptic Curve Signing Certificates](generate-elliptic-curve-signing-certificates-b780078.md).



<a name="loiod88b82b4203f4f028a21cab5032f3cc8__context-idp-cert"/>

## Context

The *Identity Provider Certificates* section in the OpenID Connect configuration of a corporate identity provider controls which signing certificate SAP Cloud Identity Services uses when sending signed requests or tokens to that corporate identity provider. All signing certificates created at tenant level are available for selection here, regardless of algorithm.

Select an elliptic curve certificate \(ES256, ES384, or ES512\) to meet the signing algorithm requirements of corporate identity providers that only accept EC-based signatures.

> ### Note:  
> You cannot generate new signing certificates from this section. Certificate generation is only available at tenant level under *Tenant Settings* \> *Single Sign-On* \> *OpenID Connect Configuration*.



## Procedure

1.  In the SAP Cloud Identity Services admin console, go to *Applications and Resources* \> *Identity Providers*.

2.  Select the corporate identity provider whose signing certificate you want to configure.

3.  Choose the *OpenID Connect Configuration* tab.

4.  In the *Identity Provider Certificates* section, review the list of available signing certificates.

    The table displays all signing certificates configured at tenant level. Each row includes the following information:


    <table>
    <tr>
    <th valign="top">

    Column
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Certificate*
    
    </td>
    <td valign="top">
    
    The subject name or thumbprint of the certificate.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Algorithm*
    
    </td>
    <td valign="top">
    
    The signing algorithm, such as RS256, RS512, ES256, ES384, or ES512.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Valid Until*
    
    </td>
    <td valign="top">
    
    The expiry date of the certificate.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Active*
    
    </td>
    <td valign="top">
    
    Indicates the certificate currently selected as active for this corporate identity provider.
    
    </td>
    </tr>
    </table>
    
5.  Select *Active* for the certificate you want to assign to this corporate identity provider.

    > ### Note:  
    > Only one certificate can be active at a time for a given corporate identity provider. When you select a new certificate, the system deactivates the previously active one for this identity provider.

6.  Save your changes.




<a name="loiod88b82b4203f4f028a21cab5032f3cc8__result-idp-cert"/>

## Results

SAP Cloud Identity Services uses the selected certificate when signing requests sent to this corporate identity provider. If you selected an elliptic curve certificate, the system uses the EC algorithm defined by that certificate \(ES256, ES384, or ES512\) for signing.

The tenant *Default* certificate continues to be used for all other signing operations not covered by a corporate identity provider-specific selection, such as application token signing.



<a name="loiod88b82b4203f4f028a21cab5032f3cc8__postreq-idp-cert"/>

## Next Steps

Verify that the corporate identity provider accepts tokens signed with the selected algorithm by testing the authentication flow.

**Related Information**  


[Generate an Elliptic Curve Signing Certificate](generate-elliptic-curve-signing-certificates-b780078.md "Generate a signing certificate that uses an elliptic curve (EC) algorithm so that it can be assigned as the active signing certificate for a specific corporate identity provider.")

 <?sap-ot O2O class="- topic/link " href="#loiod88b82b4203f4f028a21cab5032f3cc8" text="Elliptic Curve Signing Certificates" desc="" xtrc="link:2" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/d88b82b4203f4f028a21cab5032f3cc8.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[API Reference: Certificate Generation — Algorithm Parameter](https://api.sap.com/)

