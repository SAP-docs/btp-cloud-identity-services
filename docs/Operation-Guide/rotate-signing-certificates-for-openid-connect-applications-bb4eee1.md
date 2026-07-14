<!-- loiobb4eee1e517f48a5999a38b27a43a6f8 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Rotate Signing Certificates for OpenID Connect Applications

Components of SAP Cloud Identity Services use the digital signature of access tokens to verify their validity. Rotate the signing certificates of access tokens periodically to ensure uninterrupted and secure communication between OpenID Connect \(OIDC\) applications \(referred to as relying parties\) and Identity Authentication as the identity provider.



## Prerequisites

Plan for waiting time in hours between the steps of this procedure.

After you activate a new certificate, wait for access tokens signed by the old certificate to expire before deleting the old certificate. The default lifetime of access tokens is 60 minutes.

For more information, see [Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md).



## Context

Signing certificates exist at the tenant level and are shared by all applications by default. You can also configure application-specific signing certificates. Shared certificates are easier to consume. However, if you need to rotate certificates, you can't delete the old certificate until **all** applications sharing that certificate are configured to use the new certificate.

For more information, see [Configure OpenID Connect \(OIDC\) Application](configure-openid-connect-oidc-application-8a0aa2e.md).

SAP Cloud Identity Services sends an email notification when your signing certificate is about to expire. The system sends the email 30 days, 14 days, and 3 days before the certificate expires. Create a new certificate and configure the relying party to use it.

> ### Note:  
> It takes approximately two minutes for the new certificate to appear under the trust configuration of the given application.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Navigate to *Applications and Resources* \> *Tenant Settings* \> *Single Sign-On* \> *OpenID Connect Configuration* \> *Signing Certificates*.

3.  Check that there's space for a new signing certificate.

    You can store two signing certificates.

    Delete the inactive certificate if you already have two.

    > ### Caution:  
    > Wait for any existing tokens signed by the inactive signing certificate to expire.
    > 
    > By default, access tokens expire after 60 minutes and refresh tokens expire after 12 hours.
    > 
    > As long as the old signing certificate exists, the system accepts digital signatures signed by that certificate. After all access tokens and refresh tokens signed by the old certificate expire, you can delete the old certificate. Access tokens have a maximum lifetime of 12 hours. Refresh tokens have a maximum lifetime of 6 months.

4.  Add a new signing certificate.

    Choose the *Add* button on the right. You can choose from the following options:


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Regenerate* 
    
    </td>
    <td valign="top">
    
    1.  Regenerate the existing certificate with new validity, reusing the same private key.

    2.  Use the wizard to set the validity period and choose *Finish*.


    > ### Recommendation:  
    > Choose a validity period of 3 years.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Create new* 
    
    </td>
    <td valign="top">
    
    1.  Create a new self-signed certificate with a new private key and the same Subject Distinguished Name \(Subject DN\).

    2.  Use the wizard to set the validity period and key size. Choose *Finish*.


    > ### Recommendation:  
    > Choose a validity period of 3 years. Choose a key size of at least 3072.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Download CSR* 
    
    </td>
    <td valign="top">
    
    1.  Download your Certificate Signing Request \(CSR\).

    2.  Use the wizard to set the Subject Distinguished Name \(Subject DN\), signing algorithm, and key size.

        > ### Recommendation:  
        > Choose a key size of at least 3072.

    3.  Choose *Download CSR*.

    4.  Use the downloaded `.csr` file to generate a certificate from the trusted CA.

    5.  Copy the newly generated certificate, choose :pencil2:, and paste the certificate as text in the *Certificate Information* field.



    
    </td>
    </tr>
    </table>
    
5.  Configure your applications that use tenant-level certificates to use the new certificate.

    > ### Note:  
    > Configuring applications one at a time reduces the potential for downtime.

    1.  Navigate to *Applications and Resources* \> *Applications* and select the application for which you want to update the trust configuration.

    2.  Under *Trust* \> *Single Sign-On* \> *OpenID Connect Configuration* \> *Identity Provider Certificates*, select the new certificate in the *Active* column.


6.  Upload the new certificate to the backend of the trusted application.

    Proceed according to your use case:


    <table>
    <tr>
    <th valign="top">

    Application Backend Supports
    
    </th>
    <th valign="top">

    Procedure
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    The discovery endpoint
    
    </td>
    <td valign="top">
    
    Refresh or point your application backend to the discovery endpoint:

    <code>https://<i class="varname">&lt;Cloud Identity Services domain&gt;</i>/.well-known/openid-configuration</code>
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Certificate files
    
    </td>
    <td valign="top">
    
    1.  Navigate to *Applications and Resources* \> *Tenant Settings* \> *Single Sign-On* \> *OpenID Connect Configuration*.

    2.  Under *Signing Certificates*, choose the *Download* icon next to the new certificate.

    3.  Upload this certificate file to the backend of the application for which you updated the trust configuration in step 5.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Certificates as text
    
    </td>
    <td valign="top">
    
    1.  Navigate to *Applications and Resources* \> *Tenant Settings* \> *Single Sign-On* \> *OpenID Connect Configuration*.

    2.  Under *Signing Certificates*, choose the *Display* icon next to the new certificate.

    3.  Copy and paste the certificate to the backend of the application for which you updated the trust configuration in step 5.



    
    </td>
    </tr>
    </table>
    
7.  After you update the trust configuration for each application that uses tenant-level certificates, set the new certificate as the default.

    Under *Tenant Settings* \> *Single Sign-On* \> *OpenID Connect Configuration* \> *Signing Certificates*, select the new certificate as the default and save your configuration.

    Any new applications use the new signing certificate by default.

8.  Wait for any existing tokens signed by the old signing certificate to expire.

    By default, access tokens expire after 60 minutes and refresh tokens expire after 12 hours.

    As long as the old signing certificate exists, the system accepts digital signatures signed by that certificate. After all access tokens and refresh tokens signed by the old certificate expire, you can delete the old certificate. Access tokens have a maximum lifetime of 12 hours. Refresh tokens have a maximum lifetime of 6 months.

9.  Deactivate the old certificate.

    Under *Tenant Settings* \> *Single Sign-On* \> *OpenID Connect Configuration* \> *Signing Certificates*, choose <span class="SAP-icons-V5"></span> Deactivate Certificate.

    The system no longer accepts tokens signed by this certificate. However, the certificate is not deleted. If some applications stop working because of the deactivated certificate, you can reactivate it.

10. Delete the old signing certificate.

    Under *Tenant Settings* \> *Single Sign-On* \> *OpenID Connect Configuration* \> *Signing Certificates*, choose :wastebasket:.


