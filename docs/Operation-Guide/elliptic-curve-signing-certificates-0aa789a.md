<!-- loio0aa789ad41ab4380aab5d0b1d669087c -->

# Elliptic Curve Signing Certificates

SAP Cloud Identity Services supports elliptic curve \(EC\) signing certificates for use with OpenID Connect corporate identity providers that require EC-based signatures.



<a name="loio0aa789ad41ab4380aab5d0b1d669087c__section-what-are-ec-certs"/>

## What Are Elliptic Curve Signing Certificates

Signing certificates allow SAP Cloud Identity Services to sign tokens and requests using a private key so that the recipient can verify the signature using the corresponding public key. By default, SAP Cloud Identity Services uses RSA-based signing certificates \(RS256\).

Elliptic curve \(EC\) signing certificates use the ECDSA algorithm family. The following EC algorithms are supported:


<table>
<tr>
<th valign="top">

Algorithm

</th>
<th valign="top">

Standard Name

</th>
<th valign="top">

Curve

</th>
</tr>
<tr>
<td valign="top">

ES256

</td>
<td valign="top">

ECDSA using P-256 and SHA-256

</td>
<td valign="top">

P-256 \(secp256r1\)

</td>
</tr>
<tr>
<td valign="top">

ES384

</td>
<td valign="top">

ECDSA using P-384 and SHA-384

</td>
<td valign="top">

P-384 \(secp384r1\)

</td>
</tr>
<tr>
<td valign="top">

ES512

</td>
<td valign="top">

ECDSA using P-521 and SHA-512

</td>
<td valign="top">

P-521 \(secp521r1\)

</td>
</tr>
</table>

EC algorithms produce shorter signatures and keys than RSA at equivalent security levels. Some corporate identity providers, particularly those that follow national digital identity standards, accept only EC-signed tokens.

Once you create an EC certificate, you assign it as the *Active* signing certificate in the OpenID Connect configuration of a specific corporate identity provider. This design allows you to share a single EC certificate across multiple corporate identity providers, while each corporate identity provider can independently switch to a different certificate without affecting others.

You can also generate EC certificates through the SAP Cloud Identity Services REST API. Specify ***ES256***, ***ES384***, or ***ES512*** as the value of the algorithm parameter in the certificate generation request.



<a name="loio0aa789ad41ab4380aab5d0b1d669087c__section-scope-and-constraints"/>

## Scope and Constraints

EC signing certificates in SAP Cloud Identity Services have the following scope:

**Scope of EC Signing Certificates**


<table>
<tr>
<th valign="top">

Scope

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Supported use

</td>
<td valign="top">

Signing of tokens and requests sent toward an OpenID Connect corporate identity provider when you select the EC certificate as the active certificate for that corporate identity provider.

</td>
</tr>
<tr>
<td valign="top">

Not supported

</td>
<td valign="top">

You cannot use EC certificates for application token signing \(tokens issued to end-user applications\). They don't appear in application-level signing certificate lists.

> ### Note:  
> You cannot set EC certificates as the tenant default signing certificate. The tenant default must remain an RSA certificate \(RS256 or RS512\). If you don't explicitly select a certificate for a corporate identity provider, the system uses the tenant default RSA certificate.



</td>
</tr>
</table>



<a name="loio0aa789ad41ab4380aab5d0b1d669087c__section-configuration-overview"/>

## Configuration Overview

To use an EC signing certificate with a corporate identity provider:

1.  Generate an EC signing certificate at tenant level. See [Generate Elliptic Curve Signing Certificates](generate-elliptic-curve-signing-certificates-b780078.md).
2.  Assign the certificate as the active signing certificate for the corporate identity provider. See [Configure Identity Provider Certificates for Corporate Identity Providers](configure-identity-provider-certificates-for-corporate-identity-providers-d88b82b.md).
3.  Provide the public key of the certificate to the corporate identity provider for signature verification. The public key is available in the JWKS endpoint of your SAP Cloud Identity Services tenant.

