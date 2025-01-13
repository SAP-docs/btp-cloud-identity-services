<!-- loio952e7c78c3bd465a864a52b3a0786fa5 -->

# Manage Certificates for Inbound Connection

Identity Provisioning handles the following tasks related to X.509 client certificates for inbound connection: importing and deleting.



Importing client certificates for inbound connection to Identity Provisioning is used in two scenarios: configuring real-time provisioning and configuring proxy systems for provisioning user data to and from a central identity management solution. Therefore, inbound client certificates can be configured for source and proxy systems only.

Certificate files with the following filename extensions are supported: `.crt`, `.pem` and `.der`.

Depending on the infrastructure/environment your Identity Provisioning tenant is running, you manage the inbound certificates in the administration console of Identity Provisioning or SAP Cloud Identity Services.



<a name="loio952e7c78c3bd465a864a52b3a0786fa5__section_tll_xqh_gtb"/>

## SAP Cloud Identity Infrastructure

Bundle or standalone tenants running on SAP Cloud Identity infrastructure manage certificates for inbound connections in the SAP Cloud Identity Services admin console, where the certificate must be uploaded for the technical user of type *System*. For more information, see [Add System as Administrator](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/bbbdbdd3899942ce874f3aae9ba9e21d.html?version=Cloud#add-system-as-administrator).

If this technical user will be used to connect to Identity Provisioning proxy system, enable the *Access Proxy System API* permission.



<a name="loio952e7c78c3bd465a864a52b3a0786fa5__section_jx2_vd3_gtb"/>

## SAP BTP, Neo Environment

Bundle or standalone tenants running on SAP BTP, Neo environment manage certificates for inbound connections in the Identity Provisioning admin console.



### Prerequisites

For standalone tenants, the following requirements must have been fulfilled in SAP BTP cockpit in the consumer subaccount:

1.  Create an OAuth client for Platform API and choose the *Keystore*, the*Configuration Service*, and *Authorization Management* API options. Save the generated client credentials. For more information, see [Using Platform APIs](https://help.sap.com/docs/BTP/ea72206b834e4ace9cd834feed6c0e09/392af9d162694d6595499f1549978aa6.html)

2.  Create a destination with the following properties:

    -   *Name*: `IPS_MANAGE_AUTHORIZATIONS`

    -   *URL*: <code>https://oauthasservices.<i class="varname">&lt;neo-region-host&gt;</i>/oauth2/apitoken?grant_type=client_credentials</code>

    -   *ProxyType*: `Internet`

    -   *Type*: `HTTP`

    -   *Authentication*: `BasicAuthentication`

    -   *User*: <code><i class="varname">&lt;client-id-platform-api-client&gt;</i></code>

    -   *Password*: <code><i class="varname">&lt;client-secret-platform-api-client&gt;</i></code>





### Procedure

You can import client certificates from various systems to establish a trusted inbound connection to a given source or proxy system. You are allowed to import and manage as many certificates as you need for your scenarios.

To import a certificate, proceed as follows:

1.  In the Identity Provisioning admin console, select your source or proxy system.

2.  Select the *Inbound Certificates* tab and choose *Import*.

    The name of the imported certificate is generated following the pattern: <code>cert_client_<i class="varname">&lt;fingerprint&gt;</i></code>.

3.  View the details of the certificate and periodically check its validity.

    Each certificate contains fields specifying the subject name, the issuer, the algorithm used by the issuer to sign the certificate, validity period, key size and the fingerprint, which is the certificate unique identifier.


> ### Note:  
> Delete a certificate when it is expired.

