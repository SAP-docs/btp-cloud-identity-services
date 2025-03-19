<!-- loio460766b1b08d48a0b4adfb230c60a001 -->

# Get Your Tenant

Get your SAP Cloud Identity Services tenant and become productive.



<a name="loio460766b1b08d48a0b4adfb230c60a001__section_dvt_zsx_zyb"/>

## Prerequisites

Check if there is a tenant assigned to your customer ID by accessing the SAP Cloud Identity Services - Tenants application at [https://iamtenants.accounts.cloud.sap/](https://iamtenants.accounts.cloud.sap/). For more information, see [Viewing Assigned Tenants and Administrators](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/f56e6f24e373404087d6a1a9a13515a2.html).

-   If there is an existing tenant and you are among its administrators, skip this step and go to [Access Admin Console](access-admin-console-2609e81.md).

-   If there is no existing tenant, follow the steps below to get one according to your needs.




<a name="loio460766b1b08d48a0b4adfb230c60a001__section_xww_2tx_zyb"/>

## Context

An SAP Cloud Identity Services tenant is delivered to customers as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.



### Bundle with an SAP Cloud Solution

When you purchase an SAP cloud solution that bundles with SAP Cloud Identity Services, you are entitled to one productive and one test tenant. Depending on the specific cloud solution, SAP may provision only one productive tenant, only one test tenant, or both to your organization.

If you already have a tenant and you purchase additional SAP cloud solutions, you will not get additional tenants. Your existing one will be reused. However, there are some special cases and exceptions to this rule. For example:

-   Your business operates in multiple regions, and your SAP cloud solutions are delivered across these regions. You can request additional SAP Cloud Identity Services tenants in the particular region where other SAP cloud solutions have been licensed.

-   Your SAP Cloud Identity Services tenant cannot be used due to restrictions or legal requirements \(such as data residency regulations\). You can request a tenant migration to ensure that user data remains in the specified region or country.

-   You have multiple instances of SAP SuccessFactors. It is not recommended to bundle them with the same SAP Cloud Identity Services tenant. Instead, you can request a dedicated tenant for each SAP SuccessFactors instance through the SAP SuccessFactors Upgrade Center.


> ### Recommendation:  
> Using a single productive SAP Cloud Identity Services tenant for your SAP cloud solutions is important for the integration and out-of-the-box Single Sign-On \(SSO\) between these solutions. If your company is already using a productive SAP Cloud Identity Services tenant, we strongly recommend reusing it for any additional SAP cloud solutions you plan to purchase and adopt.

Getting a bundled tenant is generally an automatic process that requires no customer interaction. SAP takes care of creating and provisioning the tenant based on your cloud solution and regional choices. If you don't have a tenant, a new one will be created. If you have multiple tenants, the default tenant—typically the first one created for you—is selected and provisioned with the cloud solution. This automatic process is also used to create additional tenants when it is necessary to comply with specific regulations and in scenarios involving SAP SuccessFactors.

There are cases where customer interaction is required. If multiple tenants are available for selection, for example when using SAP for Me, Boosters, SAP SuccessFactors Upgrade Center, or other tools, you will need to choose the most appropriate one.

> ### Tip:  
> If you have multiple SAP Cloud Identity Services tenants and are unsure which one to select, consider the following recommendations:
> 
> -   Default Tenant: A tenant marked as `Default` is typically the first one created for the customer. Many SAP applications automatically integrate with this tenant when provisioned. Choose it if these specifics matter to you. To check which tenant is your default one, refer to [View Assigned Tenants and Admins](view-assigned-tenants-and-admins-f56e6f2.md).
> 
> -   Regional Provisioning: For customers with an `EU Access` contract, choose an SAP Cloud Identity Services tenant located in Europe if your SAP cloud solution is provisioned in an `EU Access` region. This ensures better performance and compliance with the European regulations. For more information, see [EU Access](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud#eu-access).
> 
> -   Tenant Migration: If the tenants available for selection are not in your desired region, you can request to migrate a specific tenant to your chosen region by opening an incident for the `BC-IAM-IDS` component.
> 
>     **Note**: Be aware that tenant migration requires a carefully planned downtime, which varies based on tenant data like the number of users, groups, and applications connected to the tenant.
> 
> -   Multi-Regional Requirements: If your business operates in multiple regions and needs additional tenants, you can request them by following the process described in [Get Additional Tenant](get-your-tenant-460766b.md#loio460766b1b08d48a0b4adfb230c60a001__section_r2y_lhg_hxb). Keep in mind that having a dedicated tenant per region might mean SSO isn't guaranteed out-of-the-box.
> 
> -   SAP SuccessFactors Use Case: If you have multiple instances of SAP SuccessFactors, you can request a separate SAP Cloud Identity Services tenant for each instance from the SAP SuccessFactors Upgrade Center. This ensures that each instance, representing the system of origin for employees, will have a dedicated identity provider and proper handling of users with the same login name. For more information, see [Initiating the Upgrade to SAP Cloud Identity Services - Identity Authentication Service](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/0271d9c4176e45ca9307e49230073240.html?version=Latest).

When tenants delivered as part of the bundling process are created, you get their tenant URLs in a welcome email from SAP. For more information, see [Bundles](bundles-25b65a4.md).



### Self-Service Request in SAP BTP Cockpit

Products delivered on SAP Business Technology Platform \(SAP BTP\) does not trigger automatic creation of SAP Cloud Identity Services productive and test tenant. You need to request the tenant in the SAP BTP cockpit.

This is true in most cases, but not for all SAP BTP applications, and depends on the subaccount where the application runs on. In SAP BTP, there are customer-managed and SAP-managed subaccounts.

-   If the application runs on SAP-managed subaccount, then the SAP Cloud Identity Services tenant is automatically provisioned with the application. In this case, the administrator of the customer doesn't have access to the SAP BTP subaccount.

-   If the application runs on customer-managed subaccount, then in most cases the administrator of the customer has to manually create SAP Cloud Identity Services tenant via SAP BTP cockpit. However, there are also exceptions, like SAP Cloud ALM \(application lifecycle management\), where SAP creates and provisions the Identity Authentication tenant.


Additional tenants and trial tenants are also created through self-service request.



### 

> ### Note:  
> Although bundled and self-requested tenants differ in the way you get them, from technical and functional perspective they have no differences.

> ### Note:  
> Be aware that it will take some time until the tenant becomes accessible. If you try to access the tenant right after creating it, you will receive ***Error 404 Not Found***.

For more information, see [Tenants](tenants-93160eb.md).



<a name="loio460766b1b08d48a0b4adfb230c60a001__section_brh_vfg_hxb"/>

## Get Productive and Test Tenant

Get your productive and test tenant as part of a self-service request in SAP BTP cockpit. Productive and test tenants have no difference from technical and functional perspective.



### Prerequisites

-   You have a global account in SAP BTP cockpit with a multi-environment subaccount.




### Procedure

1.  In the SAP BTP cockpit, choose your subaccount and navigate to *Entitlements* \> *Edit* \> *Add Service Plans*.

2.  In the pop-up dialog, select *Cloud Identity Services*.

3.  Select the *default \(Application\)* service plan, and then choose *Add Service Plan*.

4.  Save your changes on the *Entitlements* page.

5.  Navigate to *Services* \> *Service Marketplace* and select the *Cloud Identity Services* tile. Under *Application Plans* you should see the *default* plan.

6.  In the top-right corner, choose *Create* and follow the steps in the wizard to configure your new Cloud Identity Services tenant:

    1.  From the dropdown list, choose *Cloud Identity Services*.

    2.  Select the *default* plan and then choose *Next*.

    3.  From the *Cloud Service Type* dropdown, choose the tenant type: *Test* or *Productive* \(default value\).

    4.  Choose *Next*, review your configuration and choose *Create*.


    > ### Note:  
    > For each service plan you must have a separate subaccount.
    > 
    > The default plan allows you to consume SAP Cloud Identity Services. New tenants are created only if there aren't already existing tenants of the same type \(productive or test\) bound to your customer ID, regardless of the region.
    > 
    > The default test and productive tenants will be created in the same region.

    > ### Caution:  
    > If you unsubscribe the *default* plan, the Identity Authentication tenant is deactivated, if not used by other orders or products.

7.  If you initially create a test tenant and then you want to proceed with a productive one \(or vice versa\), repeat the steps above in a separate subaccount of the same region.




### 

> ### Note:  
> **SAP BTP, Neo subaccount**
> 
> If you have a global account with Neo subaccount, you can get a productive tenant and use it for free under the [General Terms and Conditions for SAP Cloud Services](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?sort=latest_desc&search=General%20Terms%20and%20Conditions). For this, you need to open your Neo subaccount, navigate to *Services* \> *Identity Authentication* tile and enable the service. The new tenants are created only if there aren't existing productive tenants bound to your customer ID already.



<a name="loio460766b1b08d48a0b4adfb230c60a001__section_r2y_lhg_hxb"/>

## Get Additional Tenant

Get an additional tenant as part of a self-service request in SAP BTP cockpit. SAP customers and partners can use SAP Cloud Identity Services additional tenants via CPEA \(Cloud Platform Enterprise Agreement\) and Pay-As-You-Go consumption-based commercial models. They can request one additional tenant per SAP BTP subaccount.

> ### Note:  
> The additional tenant doesn’t add additional logon requests. Licensed logon requests are distributed across all tenants.



### Prerequisites

-   You have a global account in SAP BTP cockpit with a multi-environment subaccount.




### Procedure

To get additional tenant using SAP BTP multi-environment subaccount, proceed as follows:

1.  In the SAP BTP cockpit, choose your subaccount and navigate to *Services* \> *Service Marketplace*.

2.  Select the *Cloud Identity Services* tile.

    > ### Tip:  
    > -   If you don't see the *Cloud Identity Service* tile, navigate to *Entitlements* trial, add the tile.
    > -   If you don't see the *additional-tenant* plan, navigate to *Entitlements* \> *Edit* \> *Add Service Plans* \> *Cloud Identity Services*, select the checkbox for the *additional-tenant* plan, press *Add Service Plans* and save your choice.
    > -   If you use directories entitlement management in your global account, you must assign the *additional-tenant* plan to the directory first, and after that to the subaccount. Once you assign the *additional-tenant* plan to your directory, it will appear in your subaccount entitlements too. For more information, see [Configure Entitlements and Quotas for Directories](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/37f8871865114f44aebee3db6ac64b72.html).

    > ### Note:  
    > For each service plan you must have a separate subaccount.
    > 
    > The *additional-tenant* plan allows the customer to create a new SAP Cloud Identity Services additional tenant. The type of the created tenant may be test or productive depending on the customer selection. The new instance is created only if there is an existing default instance bound to your customer ID.
    > 
    > You can delete the additional tenant by choosing the *Delete* button, which initiates the deletion of the subscription to the additional-tenant plan of Cloud Identity Services in your subaccount. The tenant will be deactivated for 30 days before being permanently deleted. After deletion, it cannot be restored.

3.  Choose *Services* \> *Instances and Subscriptions*.

4.  In the top-right corner, choose *Create* and follow the steps in the wizard to configure your new instance:

    1.  From the dropdown list, choose *Cloud Identity Services*.

    2.  Select the *additional-tenant* plan and then choose *Next*.

    3.  From the *Cloud Service Type* dropdown, choose the tenant type: *Test* or *Productive* \(default value\).

    4.  Choose *Next*, review your configuration and choose *Create*.



> ### Note:  
> **SAP BTP, Neo subaccount**
> 
> If you have a global account with an SAP BTP, Neo subaccount, you can get additional tenant, too. Open your existing CPEA Neo account or create new CPEA Neo account, navigate to *Services* \> *Identity Authentication - Additional Tenant* tile and enable the service.
> 
> Identity Authentication additional productive tenant will be created and the account member who triggered the creation will get an activation email. Note that test tenants cannot be created from a Neo subaccount.
> 
> If you decide to remove that additional tenant for the subaccount by choosing the *Delete* button, note that the tenant is deleted immediately.



<a name="loio460766b1b08d48a0b4adfb230c60a001__section_rsb_h3g_hxb"/>

## Get Trial Tenant

Create a trial tenant from an SAP BTP trial account.

A trial tenant is intended for testing purposes. It allows you to try out and explore SAP Cloud Identity Services – Identity Authentication and Identity Provisioning. It is free of charge and limited to a trial period in accordance with the [SAP BTP trial terms and conditions](https://accounts.sap.com/ui/public/viewTextResource?scenario=1b5ff22b-ac85-466f-9644-833d07e77d5e&resourceType=RESOURCE_TERMS_OF_USE&locale=en_US). A trial tenant differs from a test tenant. Trial tenants can be used for a limited period, while test tenants are provided to customers in addition to their productive tenants where they can test new features before implementing them productively.

> ### Restriction:  
> -   You can have only one trial tenant per SAP BTP global account regardless of how many subaccounts you create. If you have multiple subaccounts, and you've got trial tenants for them, the subaccounts will use one and the same trial tenant.
> 
> -   You can have up to 50 users in a trial tenant.
> 
> -   You can't connect to on-premise systems using the cloud connector. It's not possible to subscribe to the Cloud Identity Services connectivity plan in your trial subaccount.



### Prerequisites

-   You have a free account on SAP BTP Trial, as described in [Get a Free Account on SAP BTP Trial](https://developers.sap.com/tutorials/hcp-create-trial-account.html)




### Procedure

1.  Go to the [SAP BTP Trial page](https://account.hanatrial.ondemand.com/trial/#/home/trial) and click*Log On*.

2.  Choose *Go to Your Trial Account* and open your subaccount.

3.  In the navigation area, choose *Entitlements* and then *Edit* \> *Add Service Plans*.

4.  Select *Cloud Identity Services* from the list of entitlements available for this subaccount.

5.  Mark the *default \(Application\)* plan. The *0* number in the *Add 0 Service Plan* button increments to *1*.

6.  Choose the *Add 1 Service Plan* button.

7.  Choose *Save*.

8.  In the navigation area, choose *Services* \> *Instances and Subscriptions*.

9.  In the top-right corner, choose *Create* and follow the steps in the wizard to configure your new Cloud Identity Services tenant:

    1.  Choose *Cloud Identity Services*.

    2.  Select the *default* plan.

    3.  Choose *Create*.



> ### Note:  
> You can delete your trial tenant by deleting the subaccount or by deleting the Cloud Identity Services application under the Subscriptions section. For more information, see [Delete a Subaccount](https://help.sap.com/docs/btp/sap-business-technology-platform/delete-subaccount?version=Cloud).

> ### Note:  
> If you encounter any issues and you need support, send an email to `SAPCPTrialSupport@sap.com` or start a discussion in [SAP Community](https://community.sap.com/).



### Related Information

[**Blog Post**: SAP Cloud Identity Services offered as Trial Version](https://blogs.sap.com/2023/04/13/sap-cloud-identity-services-offered-as-trial-version/)



<a name="loio460766b1b08d48a0b4adfb230c60a001__section_gln_mjg_hxb"/>

## Assign Existing Tenant to SAP BTP Subaccount

Assign your existing tenant to SAP BTP subaccount.

You can assign existing tenant to an SAP BTP subaccount via the default plan. Activating the default plan does not trigger the creation of new tenants if tenant with the same type already exists.



### Prerequisites

-   You have an existing tenant delivered as part of a bundle with another SAP product.

-   You have a global account in SAP BTP cockpit with a Cloud Foundry subaccount.




### Procedure

1.  In the SAP BTP cockpit, choose your subaccount and navigate to *Services* \> *Service Marketplace*.

2.  Select the *Cloud Identity Services* tile. Under *Application Plans* you should see the default plan.

3.  In the top-right corner, choose *Create* and follow the steps in the wizard to configure your new instance:

    1.  From the dropdown list, choose *Cloud Identity Services*.

    2.  Select the *default* plan and then choose *Next*.

    3.  From the *Cloud Service Type* dropdown, choose the tenant type: *Test* or *Productive* \(default value\).

    4.  Choose *Next*, review your configuration and choose *Create*.



