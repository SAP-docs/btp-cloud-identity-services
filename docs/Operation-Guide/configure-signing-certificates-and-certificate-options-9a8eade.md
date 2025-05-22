<!-- loio9a8eade7d6414660b95e656b356e3a92 -->

# Configure Signing Certificates and Certificate Options

You can add up to two signing certificates per application in the administration console for Cloud Identity Services.



## Context

You can add up to two signing certificates. Both signing certificates are accepted according to the certificate validity.

You can choose the identity provider certificate to be used for signing for each application. For more information about the identity provider certificates, see [Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md).

The idea behind the ability to choose the IdP certificate is that when you want to change the default IdP certificate all applications will have downtime since the applications have trust with the current default application on the application side. So, when adding new IdP certificate you can change the applications one by one to trust the new certificate.

To configure signing certificates and certificate options in the administration console for SAP Cloud Identity Services, proceed as follows:



<a name="loio9a8eade7d6414660b95e656b356e3a92__steps_ksg_x2m_fp"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *SAML 2.0 Configuration* \> *Certificates*.

6.  Under *Signing Certificate*, choose *Add* to add a base64-encoded certificate used by the identity provider to verify the signatures of the SAML protocol messages created by the service provider.

    > ### Note:  
    > If you have two certificates, you can choose a default one, to mark your primary certificate.
    > 
    > The primary certificate is always validated first. If its validation isn't successful, then the secondary certificate is used. The certificate marked as primary is your main certificate. When it's time to rotate the certificates we recommend you to add a second certificate. When the first certificate expires, and you have a second one, you can safely remove the first one.

7.  **Optional:** Under *Signing Options*, choose *Edit* and after that *Save* to configure the signing options for the application. You have the following possibilities:


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
    
    *Signing Algorithm*
    
    </td>
    <td valign="top">
    
    Select the digest algorithm for signing outgoing messages from the dropdown list.

    -   *SHA-1*
    -   *SHA-256* - the default option \(for applications created after Jun 28, 2021\)
    -   *SHA-512*


    
    </td>
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
    
8.  **Optional:** Under *Encryption Certificate*, create a certificate, if there is no encryption certificates created or you want to create a new certificate.

    1.  Choose *Create*.

    2.  Provide a file with extension `.crt` or `cer`, or insert the certificate as text.

    3.  Choose *\+Add*.


9.  **Optional:** \(Visible only if there is and encryption certificate\) Under *Encryption Option*, choose *Edit* to configure the encryption of the SAML 2.0 response

    1.  Choose the elements to encrypt from the drop-down:

        -   *None* - the default option
        -   *Whole Assertion*
        -   *Subject Name ID*
        -   *Subject Name ID and Attributes*
        -   *Attributes*

        The method for encryption is `aes-128-cbc`.

    2.  Choose *Save*.


10. **Optional:** \(If you added second signing certificate in tenant settings\) Under *IdP Certificates*, choose the certificate to be used.

    > ### Tip:  
    > When the default identity provider certificate is changed with a new one, and the old one is not used anymore, we recommend you to delete the old certificate.

11. Save your selection.

    Once the application has been changed, the system displays the message ***Application <name of application\> updated***.


**Related Information**  


[Make a New Trust Configuration](make-a-new-trust-configuration-7cecbdf.md "Configure trust from the service provider metadata by uploading it or by accessing it from a URL, or by entering the information manually.")

