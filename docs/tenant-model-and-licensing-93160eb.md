<!-- loio93160ebd2dcb40e98aadcbb9a970f2b9 -->

# Tenant Model and Licensing

This document provides information about the tenant model, tenant licensing, and obtaining a tenant of Identity Authentication.



<a name="loio93160ebd2dcb40e98aadcbb9a970f2b9__section_rpy_znj_l4b"/>

## Tenant Model

Identity Authentication provides one productive and one test tenant per customer, regardless of the number of contracts signed in which Identity Authentication is included or bundled.

A tenant granted as part of a bundle isn’t limited in scope, but it allows you to use the full functionality that Identity Authentication offers. For licensing questions, see also the [Licensing and Usage](tenant-model-and-licensing-93160eb.md#loio93160ebd2dcb40e98aadcbb9a970f2b9__licensing_section) section.

Additional productive or test tenants beyond the initial ones must be purchased separately. To purchase additional tenants, go to [SAP Store](https://www.sapstore.com/solutions/80226/SAP-Cloud-Identity-Services) and place your order. If you can't place your order, submit a [Request Support ticket](https://store.sap.com/en/contact-us).

> ### Remember:  
> Beware that it will take time until the tenant becomes accessible. If you try to access the tenant right after its creation you will receive Error 404 Not Found.

> ### Note:  
> Additional productive or test tenants don’t provide additional logon requests.



<a name="loio93160ebd2dcb40e98aadcbb9a970f2b9__licensing_section"/>

## Licensing and Usage

Usage of Identity Authentication is commercially included for all SAP branded cloud solutions sold under the General Terms and Conditions for SAP Cloud Services, and all applications running on SAP BTP.

For logons for applications not sold under the General Terms and Conditions for SAP Cloud Services \(third party\), go to [SAP Store](https://www.sapstore.com/solutions/40132/SAP-Cloud-Platform-Identity-Authentication) and place an order.



<a name="loio93160ebd2dcb40e98aadcbb9a970f2b9__section_my1_b4j_l4b"/>

## Getting a Tenant

A default productive or test tenant can be obtained in one of the following cases:

-   ForSAP BTP, Cloud Foundry environment:

    **Prerequisites**

    A customer has an SAP BTP, Cloud Foundry subaccount.

    **Procedure**

    1.  In the SAP BTP, Cloud Foundry cockpit, choose your subaccount.
    2.  Navigate to *Entitlements* \> *Configure Entitlements* \> *Add Service Plans*
    3.  Locate and select *Cloud Identity Services* in the pop-up dialog.
    4.  Select the checkbox for *default* plan and add it as service plan.
    5.  Save the changes on the *Entitlements* page.
    6.  Navigate to *Services* \> *Service Marketplace*.
    7.  Select the *Cloud Identity Services* tile. Under *Application Plans* you should see the *default* plan.
    8.  Select *Create* in the top-right corner.

        A wizard opens, offering you to configure your new instance:

        1.  Enter basic info for your instance:

            1.  Choose *Cloud Identity Services* for which to create an instance from the dropdown list.

            2.  Select the *default* plan

            3.  Choose *Next*.


        2.  Define the parameters for your instance:
            1.  Choose a *Test* or *Productive* cloud service type.

                > ### Note:  
                > *Productive* is the default value.

            2.  Choose *Next*.

        3.  Review your configuration.
        4.  Choose *Create*.


    > ### Note:  
    > For each service plan you must have a separate subaccount.
    > 
    > The *default* plan allows the customer to consume Identity Authentication, Identity Provisioning, and Identity Directory services. The new instances are created only if there aren't already existing instances of the same type \(productive or test\) bound to your customer ID, regardless of the region.
    > 
    > The default test and productive tenants will be created in the same region.

    > ### Caution:  
    > If you unsubscribe the *default* plan, the Identity Authentication tenant is deactivated, if not used by other orders/products.

-   For SAP BTP, Neo environment:

    **Prerequisites**

    A customer has an SAP BTP, Neo subaccount.

     **Procedure**

    The customer can provision an Identity Authentication productive tenant and use it for free under the General Terms and Conditions for SAP Cloud Services.

    In the SAP BTP cockpit, choose your subaccount, navigate to *Services* \> *Identity Authentication tile* and enable the service.

    > ### Note:  
    > The new instances are created only if there aren't existing productive instances bound to your customer ID already.

-   Many SAP cloud products automatically trigger a tenant delivery if a default tenant isn’t yet provisioned. For example:
    -   SAP Agent Connection
    -   SAP Asset Intelligence Network
    -   SAP Launchpad Service
    -   SAP Customer Engagement Center
    -   SAP Enable Now
    -   SAP Identity Access Governance
    -   SAP Integrated Business Planning \(IBP\)
    -   SAP IoT Application Enablement
    -   SAP Jam
    -   SAP Landscape Management Cloud
    -   SAP S/4HANA Cloud
    -   SAP Rural Sourcing Management \(RSM\)
    -   SAP Sales Cloud
        -   SAP Agent Performance Management
        -   SAP Commissions
        -   SAP Territory and Quota

    -   SAP SuccessFactors



The eligible product includes instructions for provisioning of Identity Authentication tenant. The customer gets a tenant and it can be used for free under the General Terms and Conditions for SAP Cloud Services.

If a default test tenant is not created as part of other SAP cloud products delivery and the customer does not have a Cloud Foundry subaccount, then a customer can request a test tenant which will be provided upon request for no additional cost. To request a test tenant, report an incident on [SAP Support Portal Home](https://support.sap.com/) with a component BC-IAM-IDS.



<a name="loio93160ebd2dcb40e98aadcbb9a970f2b9__section_r53_ttj_l4b"/>

## Getting an Additional Tenant



<a name="loio93160ebd2dcb40e98aadcbb9a970f2b9__section_aqm_5zs_blb"/>

## CPEA

SAP customers and partners can use Identity Authentication additional tenants via CPEA as a self-service.

Customers and partners can request one additional tenant per SAP BTP subaccount.

> ### Note:  
> The Identity Authentication additional tenant doesn’t add additional logon requests. Licensed logon requests are distributed across all tenants.

For SAP BTP, Cloud Foundry environment:

**Prerequisites**

A customer has an SAP BTP, Cloud Foundry subaccount.

**Procedure**

1.  In the SAP BTP cockpit, choose your subaccount.
2.  In the navigation area, choose *Services* \> *Service Marketplace*.
3.  Select the *Cloud Identity Services* tile.

    > ### Tip:  
    > -   If you don't see the *Cloud Identity Service* tile, navigate to *Entitlements*, add the tile.
    > -   If you don't see the *additional-tenant* plan, navigate to *Entitlements* \> *Configure Entitlements* \> *Add Service Plans* \> *Cloud Identity Services*, select the checkbox for the *additional-tenant* plan, press *Add Service Plans* and save your choice.
    > -   If you use directories entitlement management in your global account, you must assign the *additional-tenant* plan to the directory first, and after that to the subaccount. Once you assign the *additional-tenant* plan to your directory, it will appear in your subaccount entitlements too. For more information, see [Configure Entitlements and Quotas for Directories \[Feature Set B\]](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/37f8871865114f44aebee3db6ac64b72.html).

    > ### Note:  
    > For each service plan you must have a separate subaccount.
    > 
    > The *additional-tenant* plan allows the customer to create a new Identity Authentication additional tenant. The type of the created tenant may be test or productive depending on the customer selection. The new instance is created only if there is an existing default instance bound to your customer ID.
    > 
    > You can disable that additional tenant for the subaccount by choosing the *Disable* button. Please note that the tenant is deleted immediately.

4.  Choose *Services* \> *Instances and Subscriptions*.
5.  Select *Create* in the top-right corner.

    A wizard opens, offering you to configure your new instance:

    1.  Enter basic info for your instance:

        1.  Choose *Cloud Identity Services* for which to create an instance from the dropdown list.

        2.  Select the *additional-tenant* plan

        3.  Choose *Next*.


    2.  Define the parameters for your instance:
        1.  Choose a *Test* or *Productive* cloud service type.

            > ### Note:  
            > *Productive* is the default value.

        2.  Choose *Next*.

    3.  Review your configuration.
    4.  Choose *Create*.


For SAP BTP, Neo environment:

**Prerequisites**

A customer has an SAP BTP, Neo subaccount.

**Procedure**

1.  In the SAP BTP cockpit, go to your existing CPEA Neo account or create new CPEA Neo account.
2.  Go to *Services*.
3.  Choose *Identity Authentication - Additional Tenant* tile.
4.  Choose *Enable*.

Identity Authentication additional productive tenant will be created and the account member who triggered the creation will get an activation e-mail.

> ### Note:  
> You can remove that additional tenant for the subaccount by choosing the *Delete* button. Please note that the tenant is deleted immediately.

**Related Information**  


[Product Details](product-details-4d404b1.md)

[Web-Based Logon Interface](web-based-logon-interface-8e40afc.md "Service providers that delegate authentication to Identity Authentication can use two types of visualization of the web-based user interfaces for the logon pages of their applications.")

[Regional Availability](regional-availability-be600ca.md "Tenants are deployed on the productive domain accounts.ondemand.com.")

[Disaster Recovery/High Availability](disaster-recovery-high-availability-2c1a055.md "Disaster recovery (DR) and high availability (HA) are based on the capabilities of the underlying infrastructure.")

[Browser Support](browser-support-0741076.md "Information on the supported browser version for the administration console, and the end user screens of Identity Authentication.")

[Supported Languages](supported-languages-0ea634d.md "Information on the supported languages for the administration console, and the end user screens of Identity Authentication.")

[Identity Provisioning: Tenant Model](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/65fa74998ef14f059806f0c5a48e5285.html?version=Cloud)

