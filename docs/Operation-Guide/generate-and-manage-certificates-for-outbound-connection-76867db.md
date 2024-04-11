<!-- loio76867db8ce534becbfc08b050695df8e -->

# Generate and Manage Certificates for Outbound Connection

Identity Provisioning handles the following tasks related to X.509 client certificates for outbound connection: generating,automatic regenerating, activating, deactivating, downloading and deleting.

Administrators can manage up to two certificates for secure outbound connection with a given provisioning system. Only one certificate can be active at a time.

Generating a second certificate might be needed in case your active certificate is about to expire. Currently, renewing or extending the validity of a certificate is handled by generating a second one. This will ensure that the communication between Identity Provisioning and the given provisioning system won't be disrupted.

Both certificates - the first and the second one, have the same distinguished name \(DN\), issued by the same certificate authority \(CA\).

Thirty days before the expiration of your active certificate you'll start receiving a warning message in the *Outbound Certificate* tab of your Identity Provisioning user interface \(UI\). If you allow the certificate to expire, it becomes invalid. It is not possible to extend its validity.

> ### Recommendation:  
> Enable *Automatic Regeneration* to ensure your certificate does not expire. This option is supported for tenants running on SAP Cloud Identity Services infrastructure.

You can subscribe to receive notification e-mails for expiration of your outbound certificate. Based on the enablement of the automatic regeneration option, the e-mail provides the following information:

-   When the automatic regeneration option is enabled, 14 days prior to the certificate expiration you will receive an e-mail with subject *Outbound Certificate Renewed. <system\_type\> System: <system\_name\>* containing details about the regenerated outbound certificate.

-   When the automatic regeneration option is not enabled, on the 30th, 14th, and 3rd day before the outbound certificate expiration, you will receive an e-mails with subject *Outbound Certificate Expiration. <system\_type\> System: <system\_name\>* containing information about the certificate.


The following table explains the key tasks available:


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*Automatic Regeneration* 

</td>
<td valign="top">

Turn automatic regeneration option on or off:

-   *ON* - enables the automatic regeneration and activation of outbound certificates.

    The certificate will be automatically regenerated and activated within 14 days prior to its expiration.

    > ### Recommendation:  
    > This option is recommended for systems validating certificates based on their subject and issuer. In such cases, no further manual steps are required.
    > 
    > This option is not recommended for systems validating certificates based on fingerprint. When you regenerate the certificate, the fingerprint is changed. This will cause the authentication to fail until the certificate is downloaded and uploaded to the connected system.

    If your active certificate has expired and you have manually generated a second one without activating it, enabling the automatic regeneration option will result in the following behavior:

    1.  A new certificate will be generated and set to active.

    2.  The expired certificate will be set to inactive.

    3.  The initially inactive certificate will be deleted.


-   *OFF* - disables the automatic regeneration.

    Certificate regeneration will not be done automatically, therefore checking certificate expiration and regeneration should be a manual process.




</td>
</tr>
<tr>
<td valign="top">

*Generate* 

</td>
<td valign="top">

You can generate a maximum of two certificates. After reaching the limit, the *Generate* button is greyed out.

The status of the first certificate you generate is set to *Active*. The status of the second certificate is set to *Inactive*.

Certificates are distinguished by their **fingerprints** \(the unique identifier of the certificate\).

</td>
</tr>
<tr>
<td valign="top">

*Subscribe* 

</td>
<td valign="top">

You can subscribe yourself or another user or a group to receive notification e-mails for expiring or automatically regenerated outbound certificates.

</td>
</tr>
<tr>
<td valign="top">

*Activate* 

</td>
<td valign="top">

Activate an inactive certificate.

> ### Recommendation:  
> We recommend that you activate your certificate after you have uploaded it in the backend provisioning system. This will ensure that the communication between Identity Provisioning and the backend system won't be disrupted.

Only one certificate can be active at a time.

</td>
</tr>
<tr>
<td valign="top">

*Download* 

</td>
<td valign="top">

You can download both active and inactive certificates.

</td>
</tr>
<tr>
<td valign="top">

*Expand* 

</td>
<td valign="top">

You can expand active and inactive certificates to view their details.

If a certificate is about to expire, you see a warning message in the details.

</td>
</tr>
<tr>
<td valign="top">

*Delete* 

</td>
<td valign="top">

You can delete only inactive certificates.

</td>
</tr>
</table>



<a name="loio76867db8ce534becbfc08b050695df8e__section_sjd_5rf_ftb"/>

## Generate Certificate

To generate a client certificate, proceed as follows:

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

    Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

2.  Select your provisioning system and choose *Outbound Certificate* \> *Generate* .

    If the certificate is generated successfully, the toast message ***Certificate generated successfully*** is displayed on the screen.

3.  View the certificate information.

    Each certificate contains fields specifying the subject, the name of the CA issuing the certificate, the algorithm used by the issuer to sign the certificate, validity period, key size and the certificate unique identifier.

4.  Download the certificate.

5.  Log on to the provisioning system you want to authenticate to \(in this case, SAP BTP ABAP Environment\) and upload the certificate to configure the certificate-based authentication there. For more information, see: [How to Create Communication Users](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/0377adea0401467f939827242c1f4014.html)

6.  Return to the Identity Provisioning UI and select the *Properties* tab of the provisioning system.

7.  Set the *Authentication* property to `ClientCertificateAuthentication`.

8.  Save your configuration.




<a name="loio76867db8ce534becbfc08b050695df8e__section_z3g_jsf_ftb"/>

## Manage Certificate Validity

To manage the certificate validity, choose your applicable approach: automatic or manual.



### Manage Validity Automatically

Enable the *Automatic Regeneration* option.

The expiring active certificate is set to inactive. A new certificate is automatically regenerated and set to active.

For systems validating certificates based on their subject and issuer, no further manual steps are required.



### Manage Validity Manually

1.  Periodically check the validity of your active certificate.

2.  When the certificate approaches its expiration date \(or it has already expired\), generate a new certificate, as described above. The status of this certificate will be *Inactive*.

3.  Continue with downloading the inactive certificate and uploading it to the backend provisioning system.

4.  Once ready, activate the second \(inactive\) certificate. As a result, your current active certificate will be set to inactive.

5.  You can safely delete the inactive certificate.




<a name="loio76867db8ce534becbfc08b050695df8e__section_y41_rxl_j1c"/>

## Subscribe for Expiring Outbound Certificate Notification

To avoid the need of checking manually the validity of your active outbound certificate, you are able to subscribe yourself or another user or a group to receive notification e-mails for its expiration. This way, you will be notified by e-mail on the 30th, 14th, and 3rd day before it expires.

To get subscribed, proceed as follows:

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

    Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

2.  Select the system you need to watch and choose *Outbound Certificates*.
3.  Choose *Subscribe*.
    -   To subscribe yourself, choose *Subsribe* \> *Subscribe me*.
    -   To subscribe another user or a group \(distribution list\), choose *Subscribe others*. Fill in the required fields *Display name* and *E-Mail* and choose ![](images/IPS_Add_Icon_711b870.png)*Add*.

        > ### Note:  
        > From the *Recipients* list, you can remove existing subscribers. To do that, go to the *Action* column and choose the ![](images/Unsubscribe_User_21262b8.png) icon.

    -   If you no longer need to be subscribed to a source system, choose *Subscribe* \> *Unsubscribe me*.



