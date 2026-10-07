<!-- loiob7800786f270435bb66b3a6ee9b0e824 -->

# Generate Elliptic Curve Signing Certificates

Generate a signing certificate that uses an elliptic curve \(EC\) algorithm so that it can be assigned as the active signing certificate for a specific corporate identity provider.



<a name="loiob7800786f270435bb66b3a6ee9b0e824__prereq-ec-cert"/>

## Prerequisites

You understand the following constraints before generating an EC certificate:

-   EC signing certificates can only be used as the active signing certificate for corporate identity providers. They are not available for application token signing and cannot be set as the tenant default.
-   To assign the generated certificate to a corporate identity provider, see [Configure Identity Provider Certificates for Corporate Identity Providers](configure-identity-provider-certificates-for-corporate-identity-providers-d88b82b.md).



<a name="loiob7800786f270435bb66b3a6ee9b0e824__context-ec-cert"/>

## Context

SAP Cloud Identity Services supports elliptic curve \(EC\) signing certificates at the tenant level. EC certificates use the ECDSA algorithm family \(ES256, ES384, ES512\) and can be assigned per corporate identity provider, allowing each corporate identity provider to use a different signing algorithm and key if required.

> ### Restriction:  
> EC certificates cannot be configured as the *Default* signing certificate on tenant level. The tenant default must use an RSA algorithm \(RS256 or RS512\). EC certificates are only applied when explicitly assigned as the active certificate in the configuration of a specific corporate identity provider.



## Procedure

1.  In the SAP Cloud Identity Services admin console, go to *Tenant Settings* \> *Single Sign-On*.

2.  Under *OpenID Connect Configuration*, find the *Signing Certificates* section and choose *Generate New Certificate*.

3.  From the *Algorithm* dropdown list, select the elliptic curve algorithm to use.


    <table>
    <tr>
    <th valign="top">

    Algorithm
    
    </th>
    <th valign="top">

    Curve
    
    </th>
    <th valign="top">

    Hash
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *ES256*
    
    </td>
    <td valign="top">
    
    P-256
    
    </td>
    <td valign="top">
    
    SHA-256
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *ES384*
    
    </td>
    <td valign="top">
    
    P-384
    
    </td>
    <td valign="top">
    
    SHA-384
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *ES512*
    
    </td>
    <td valign="top">
    
    P-521
    
    </td>
    <td valign="top">
    
    SHA-512
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > For elliptic curve algorithms, the *Key Size* field is not applicable. The key size is determined by the selected curve and is not configurable.

4.  Select the certificate *Validity* \(3, 5, or 10 years\).

5.  Choose *Generate* to create the certificate.




<a name="loiob7800786f270435bb66b3a6ee9b0e824__result-ec-cert"/>

## Results

The new certificate appears in the *Signing Certificates* list with its algorithm \(for example, *ES256*\) shown in the *Algorithm* column. The certificate is not set as *Default* and is not shown in application-level signing certificate lists.

You can now assign this certificate as the active signing certificate for a corporate identity provider.



<a name="loiob7800786f270435bb66b3a6ee9b0e824__postreq-ec-cert"/>

## Next Steps

Assign the certificate to one or more corporate identity providers. See [Configure Identity Provider Certificates for Corporate Identity Providers](configure-identity-provider-certificates-for-corporate-identity-providers-d88b82b.md).

