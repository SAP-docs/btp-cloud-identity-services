<!-- loio6621ad5868a3429d8b79f0c3c188e585 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Rotate Signing Certificates for SAML 2.0 Applications

Tenant administrators must replace existing signing certificates with new ones before they expire. This ensures uninterrupted and secure communication between SAML 2.0 applications \(referred to as service providers\) and Identity Authentication as the identity provider.



## Context

You have received an email notification that your signing certificate is about to expire. The email is sent 30 days, 14 days, and 3 days before the certificate expires. You need to create a new one and configure the service provider to use it. Proceed as follows:



## Procedure

1.  Create a new signing certificate.

    1.  Sign in to the administration console for SAP Cloud Identity Services.

    2.  Navigate to *Applications and Resources* \> *Tenant Settings* \> *Single Sign-On* \> *SAML 2.0 Configuration* \> *Signing Certificates*.


2.  Choose the *\+Add* button on the right. You can choose from the following options:

    -   *Regenerate the existing certificate with new validity, reusing the same private key* \> *Next Step* \> *Choose validity from the drop down* \> *Next Step* \> *Finish*.

        > ### Note:  
        > The validity period can be 3, 5 and 10 years.

    -   *Create new a self-signed certificate with a new private key and the same Subject DN* \> *Next Step* \> *Select key size* \> *Choose validity from the drop down* \> *Next Step* \> *Finish*.

        > ### Note:  
        > The key size can be 2048, 3072 and 4096. The validity period can be 3, 5 and 10 years.

    -   *Download your Certificate Signing Request* \> *Next Step* \> *add Subject DN and select key size and validity from the options* \> *Next Step* \> *Download CSR*. Use the downloaded .csr file to generate a certificate from the trusted CA. Copy the newly generated certificate, choose :pencil2:, and paste the certificate as text in the *Certificate Information* field.

        > ### Note:  
        > The signing algorithm can be SHA-256 and SHA-384. The key size can be 2048, 3072 and 4096.


3.  Configure the service provider to use the new certificate.

    > ### Note:  
    > In case there are many applications, the recommended approach is to renew the certificate for one application at a time following this procedure, as this will minimize or reduce the potential for customer downtime.

    1.  Navigate to *Applications and Resources* \> *Applications* and select the application for which you want to update the trust configuration.

    2.  Under *Trust* \> *Single Sign-On* \> *SAML 2.0 Configuration* \> *Identity Provider Certificate* \> *disable the slider* \> *choose Activate next to the new certificate*.


4.  Upload the new certificate to the backend of the trusted application.

    1.  Navigate to *Applications and Resources* \> *Tenant Settings* \> *Single Sign-On* \> *SAML 2.0 Configuration*.

    2.  Proceed according to your use case below.



    <table>
    <tr>
    <th valign="top">

    Applications
    
    </th>
    <th valign="top">

    Procedure
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Your applications support metadata
    
    </td>
    <td valign="top">
    
    1.  Download the metadata with this certificate in one of the following ways:

        -   Get the SAML 2.0 tenant metadata containing the identity provider certificate by calling the `https://<tenant ID>.<tenant domain>/saml2/metadata` endpoint and provide the `sp_name` parameter, as described in [Get SAML 2.0 IdP Metadata via Parameter](get-saml-2-0-idp-metadata-via-parameter-2c76690.md).

        -   Download the metadata with the new certificate \(which is still a non-default one\), as described in [Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md) → *Step 4*


    2.  Upload this metadata to the backend of the application for which you have updated the trust configuration in step 2.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Your applications support certificate file
    
    </td>
    <td valign="top">
    
    1.  Under *Signing Certificates*, choose the *Download* icon next to the new certificate.

    2.  Upload this certificate file to the backend of the application for which you have updated the trust configuration in step 2.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Your applications support certificate as text
    
    </td>
    <td valign="top">
    
    1.  Under *Signing Certificates*, choose the *Display* icon next to the new certificate.

    2.  Copy and paste the certificate to the backend of the application for which you have updated the trust configuration in step 2.



    
    </td>
    </tr>
    </table>
    
5.  After updating the trust configuration for each application, set the new certificate as the default.

    Under *Tenant Settings* \> *Single Sign-On* \> *SAML 2.0 Configuration* \> *Signing Certificates*, select the new certificate as default and save your configuration.

6.  Navigate to *Applications and Resources* \> *Applications* \> *Trust* \> *Single Sign-On* \> *SAML 2.0 Configuration* \> *Identity Provider Certificate* \> *enable the slider*.

    > ### Note:  
    > It takes approximately 2 minutes for the new certificate to appear under the trust configuration of the given application.


