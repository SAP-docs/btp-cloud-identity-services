<!-- loiofe84459e688c43698591d3b9e1aac828 -->

# Integrating the Service with SAP Business Technology Platform, Neo Environment

SAP BTP acts as a service provider, and Identity Authentication acts as an identity provider in this setup.



## Context

> ### Note:  
> The content in this section is only relevant for SAP BTP, Neo environment.

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.

For the integration, you must set the trust on both SAP BTP and Identity Authentication. As a result of the trust setting, when you have deployed an application to SAP BTP that has protected resources and requires SAML authentication, the user is redirected to the logon page of Identity Authentication to provide credentials.

> ### Note:  
> Once setting Identity Authentication as a trusted identity provider for SAP BTP all the services in the SAP BTP would be authenticated via Identity Authentication. For more information about the services provided by SAP BTP, see [Services](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7613d9ce711e1014839a8273b0e91070.html).

For the integration you need to make configurations in the cockpit of SAP BTP and in the administration console for Identity Authentication. The configurations made in the administration console do not affect the authentication for the cockpit, which is carried out via the SAP-defined tenant, SAP ID service.

> ### Tip:  
> If you want to use a custom Identity Authentication tenant as an identity provider for the cockpit, see [Platform Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html) \(for the cockpit or console client\).

For more information about the access to SAP BTP and Identity Authentication, see the following sections:

-   Access to SAP BTP Cockpit
-   Access to Identity Authentication

**Related Information**  


[Integrating the Service with the Identity Service of SAP BTP](integrating-the-service-with-the-identity-service-of-sap-btp-d5cd80c.md "The Identity service of SAP BTP enables you to delegate authentication to the Identity Authentication service. The Identity service automates the creation of OpenID Connect (OIDC) applications for the Identity Authentication service for each application the Identity service registers.")

[Integrating the Service with SAP Web IDE Full-Stack](integrating-the-service-with-sap-web-ide-full-stack-313f545.md#loio313f5456f3ab41ca925d555cda748f39 "You can use Identity Authentication as identity provider for SAP Web IDE Full-Stack.")

[Integrating the Service with SAP Document Center](integrating-the-service-with-sap-document-center-397683c.md#loio397683cff69d44c5bb2b38c76714c6ca "You can use Identity Authentication as identity provider for SAP Document Center.")

[Integrating the Service with SAP Identity Management 8.0](integrating-the-service-with-sap-identity-management-8-0-f44f931.md "")

[Integrating the Service with SAP S/4HANA Cloud, SAP Integrated Business Planning and SAP Analytics Cloud](integrating-the-service-with-sap-s-4hana-cloud-sap-integrated-business-planning-and-sap-a-dd61aea.md "This integration document aims to provide information about single sign-on (SSO) options for SAP S/4HANA Cloud or SAP Integrated Business Planning and SAP Analytics Cloud, that use Identity Authentication as an authenticating or proxy identity provider.")

[Integrating the Service with Microsoft Azure AD](integrating-the-service-with-microsoft-azure-ad-626b173.md "")

[Integrating the Service with SAP Task Center](integrating-the-service-with-sap-task-center-ab5e90e.md)

[Blogs](blogs-a89ca3e.md "Links to blogs and documents about integration scenarios with Identity Authentication.")

<a name="concept_icm_hfz_gx"/>

<!-- concept\_icm\_hfz\_gx -->

## Access to SAP BTP Cockpit

Once you purchase a customer or partner account of SAP BTP, an email is sent to the contact person from your company with a link to your SAP BTP cockpit. The contact person is specified in the Order Form for SAP Cloud Services. He or she is the first subaccount member of the SAP BTP cockpit.

> ### Note:  
> For more information how to add other users for the subaccount, see [Managing Members in the Neo Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/937c3cef72bb101490cf767db0e91070.html)

The cockpit is the central point for managing all activities associated with your cloud-based business applications. For more information about the cockpit, see [Cloud Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e47748b5bb571014afedc70595804f3e.html).

To deploy applications on SAP BTP and to make configurations in the cockpit, you need a subaccount that corresponds to your role. For more information, see [Getting a Global Account](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/975c8fc61a384668a82e91c8448deb0b.html).

<a name="concept_mth_3fz_gx"/>

<!-- concept\_mth\_3fz\_gx -->

## Access to Identity Authentication

Identity Authentication does not use for authentication the users registered in the SAP Service Marketplace, but maintains an own user store for administrators and users.

Once you purchase a customer or partner account of SAP BTP, a user account for Identity Authentication is created for the same contact person, specified in the Order Form. The contact person is the first administrator in the administration console for Identity Authentication. He or she receives an activation email for the administration console account. The subject of the email is: *Activate Your Account for Administration Console*. Following the required steps, the administrator activates the account and can continue to the administration console for SAP Cloud Identity Services via the console's URL.

> ### Note:  
> The URL has the `https://<tenant ID>.accounts.ondemand.com/admin` pattern.
> 
> *Tenant ID* is an automatically generated ID by the system. The URL is in the activation email received by the first administration contains the *tenant ID*.

> ### Caution:  
> If new SAP BTP members are added into the Members page of the SAP BTP cockpit these members are not added as administrators of Identity Authentication. This is done only for the first account member. For more information about how to add new administrators in Identity Authentication, see [Add User as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loio1dc498bff0674743a1a3a0ec3f0bf298).

<a name="loio5c3a9ac58a0e475cbb988de7ef0fdf30"/>

<!-- loio5c3a9ac58a0e475cbb988de7ef0fdf30 -->

## Configure SAP BTP



## Prerequisites

-   You have a subaccount for SAP BTP.

    For more information, see [Getting a Paid Enterprise Global Account](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/82f9ff522f754e26ae89e0cd7ec7aa11.html).

-   You have a tenant of Identity Authentication.

-   You have protected your SAP BTP application.

    For more information about how to protect your resource, see [Enabling Authentication](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e637f62abb571014857cb0232adc43a7.html).

    > ### Note:  
    > If you want to use SAP BTP in a productive environment, you should purchase a customer account or join a partner account. The free tier model for SAP BTP uses the default SAP tenant.
    > 
    > By default, SAP BTP uses`SAP ID service` as a trusted identity provider. `SAP ID service` is an SAP-defined tenant that cannot be configured by external administrators. If your environment contains SAP applications such as SAP Jam, SAP Community Network or Success Map that use authentication through `SAP ID service`, you can use the default tenant.




## Context

You have two configuration options based on the following cases:

****


<table>
<tr>
<th valign="top">

You want to

</th>
<th valign="top">

Procedure

</th>
</tr>
<tr>
<td valign="top">

Add a tenant of Identity Authentication registered for your company or organization as an identity provider.

</td>
<td valign="top">

Follow the procedure in: [Identity Authentication Tenant](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d3df5b457d0c43fca117da0dc14e2f0d.html) as an Application Identity Provider.

> ### Note:  
> In this case, the trust is established automatically upon registration in both the SAP BTP and the Identity Authentication tenant. Automatically the SAP BTP Account is registered as an application in the tenant of Identity Authentication. You can find it in the administration console under the *CUSTOM APPLICATIONS* list, representing your SAP BTP account.



</td>
</tr>
<tr>
<td valign="top">

Configure manual trust

</td>
<td valign="top">

1.  Download the metadata file of Identity Authentication. For more details, see: [Tenant SAML 2.0 Configuration](../Operation-Guide/tenant-saml-2-0-configuration-e81a19b.md).

2.  Use this metadata to configure the trust on SAP BTP. For more details about this configuration, see [Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dc618538d97610148155d97dcd123c24.html).




</td>
</tr>
</table>

> ### Tip:  
> Once setting Identity Authentication as a trusted identity provider for SAP BTP all SAP BTP applications and services use the trust and configuration settings. If you need different settings for the different SAP BTP applications or services, open a new subaccount. For more information, see [Create Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d60337b3631540c6aea5908f6248bbcd.html). Once you have created the new subaccount, add the tenant of Identity Authentication in the new subaccount. Repeat the procedure from the table above to set the trust for each subaccount.

<a name="loiob48a814ed58c4299acfd4e8fd7fb5556"/>

<!-- loiob48a814ed58c4299acfd4e8fd7fb5556 -->

## Configure Identity Authentication



## Prerequisites

-   You have a tenant of Identity Authentication.
-   You have added the tenant of Identity Authentication as an identity provider in SAP BTP cockpit. For more information, see: [Identity Authentication Tenant as an Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d3df5b457d0c43fca117da0dc14e2f0d.html).
-   You have downloaded the metadata for SAP BTP as a service provider \(SP\). For more information, see [Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dc618538d97610148155d97dcd123c24.html).



## Context

You need this configuration if you have added a tenant of Identity Authentication which is not registered for the organization or company for which the SAP BTP account is created.

If you have added a tenant of Identity Authentication registered for your company or organization as an identity provider, see [Configure SAP BTP](integrating-the-service-with-sap-business-technology-platform-neo-environment-fe84459.md#loio5c3a9ac58a0e475cbb988de7ef0fdf30).



<a name="loiob48a814ed58c4299acfd4e8fd7fb5556__steps_eck_mky_gx"/>

## Procedure

1.  Set the trust with SAP BTP. For more details, see [Configure Trust](../Operation-Guide/configure-trust-f96e4c5.md)

2.  **Optional:** Customize the settings for the application. For more information, see [Configuring Applications](../Operation-Guide/configuring-applications-61ad3b0.md).


<a name="loioada5781b82a0407890b3a35e7538be76"/>

<!-- loioada5781b82a0407890b3a35e7538be76 -->

## Configure IdP-Initiated SSO with SAP BTP



## Context

You can perform IdP-initiated single sign-on \(SSO\) in SAP BTP by sending the SAML Response directly to the application URL that is protected with SAML. This requires you to change the assertion consumer service \(ACS\) endpoint on the identity provider side to point to this URL.

To configure IdP-initiated SSO with SAP BTP, follow the steps below:



## Procedure

1.  Change the ACS endpoint on the identity provider side to point to the application protected URL. For more information, see Step 6 in [Configure Trust](../Operation-Guide/configure-trust-f96e4c5.md).

2.  Configure IdP-initiated SSO. For more information, see [Configure IdP-Initiated SSO](../Operation-Guide/configure-idp-initiated-sso-5d59caa.md).


<a name="loio4310ad0c4d824ebd98b0698440719d4a"/>

<!-- loio4310ad0c4d824ebd98b0698440719d4a -->

## Configure Assertion Attributes Mapping

You have to specify how the assertion attributes are sent to SAP BTP in the assertion, and define their mapping.

<a name="task_kmc_rhg_cy"/>

<!-- task\_kmc\_rhg\_cy -->

### 1. Configure User Attributes in Identity Authentication



<a name="task_kmc_rhg_cy__steps_zdw_bnh_yv"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose your SAP BTP application from the list.

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *Assertion Attributes*.

6.  Add the assertion attributes.

7.  Save your configuration.

    ![](images/AssertAttributeMobileDocsSCI_62dd632.png)

    If the operation is successful, you receive the message ***Assertion attributes updated***.


**Related Information**  


[User Attributes Sent to the Application](../Operation-Guide/user-attributes-sent-to-the-application-d361407.md "After configuring the user attributes to be collected by the registration and upgrade forms, you have to specify how these attributes are sent to the application.")

<a name="task_ckj_rhg_cy"/>

<!-- task\_ckj\_rhg\_cy -->

### 2. Configure Mapping in SAP BTP



<a name="task_ckj_rhg_cy__steps_lfn_fyh_5v"/>

## Procedure

1.  Log on to SAP BTP cockpit with the cockpit administrator role. For more information, see [Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8d6e3a0fa4ab43e4a421d3ed08128afa).

2.  Select the subaccount and choose *Trust* in the navigation bar.

3.  Choose the *Application Identity Provider* \> *the identity provider that the platform uses for authentication*.

4.  Choose *Attributes* \> *Add Assertion-Based Attribute*.

5.  Enter the fields as follows:


    <table>
    <tr>
    <th valign="top">

    Assertion Attribute
    
    </th>
    <th valign="top">

    Principal Attribute
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    \*
    
    </td>
    <td valign="top">
    
    \*
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > This specifies that all assertion attributes will be mapped to the corresponding principal attributes without a change
    > 
    > The *Assertion Attribute* field is for the attribute that comes from the assertion.
    > 
    > The *Principal Attribute* field is the user attribute that the users will have at SAP BTP.

6.  Save your changes.


**Related Information**  


[Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dc618538d97610148155d97dcd123c24.html)

<a name="loioa58cf311103d4c3ba8c6068d7fcdfec6"/>

<!-- loioa58cf311103d4c3ba8c6068d7fcdfec6 -->

## Configure SAP BTP Custom Domains

You can make your SAP BTP applications accessible on your own domain different from hana.ondemand.com - for example www.myshop.com.



## Prerequisites

You have configured your application's custom domain using the SAP BTP console client. For more information, see [Configuring Custom Domains](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/77cf0e6cd32e496c9cc8eeac4bedde94.html#loio77cf0e6cd32e496c9cc8eeac4bedde94).



## Context

When a custom domain is used, both the domain name and the server certificate for this domain are owned by the customer.

To use a custom domain for the application that uses your Identity Authentication tenant for authentication, follow the procedure as described in the current document.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the list item of the application that will use a custom domain.

4.  Choose the *Trust* tab.

5.  Under *SAML 2.0*, choose *SAML 2.0 Configuration*.

6.  Edit the *Assertion Consumer Service Endpoint* URL field and the *Single Logout Endpoint* URLs fields by replacing `authn.hana.ondemand.com` with your custom domain name. In the example above,this would be `www.myshop.com`.

7.  Save your changes.




## Results

Once the configuration has been changed, the system displays the message ***Application <name of application\> updated***. The application can only be accessed via the custom domain.

