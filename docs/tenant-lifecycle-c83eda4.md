<!-- loioc83eda4eaafd4807abe7b34b0f8ba9b6 -->

# Tenant Lifecycle

Tenants of SAP Cloud Identity Services - Identity Authentication and Identity Provisioning go through onboarding and offboarding in their lifecycle.



<a name="loioc83eda4eaafd4807abe7b34b0f8ba9b6__section_iz1_fyc_b1c"/>

## Onboarding

Onboarding involves all the processes needed to instantiate a tenant, configure and provision it to the customer for test or productive usage.


<table>
<tr>
<th valign="top">

Tenants

</th>
<th valign="top">

Onboarding Process

</th>
</tr>
<tr>
<td valign="top">

-   Tenants delivered as part of a bundle with an SAP cloud solution

-   Tenants delivered for applications running on SAP-managed subaccounts




</td>
<td valign="top">

1.  Search for existing tenant of the customer.

    -   If one or more existing tenants are found, the existing default or the oldest one is reused.

        The oldest \(non-additional\) productive and test tenants are considered default.

    -   If no existing tenant is found, a new one is created by SAP.

2.  Tenant is preconfigured for the customer.

3.  Tenant is provisioned to the customer.


For more information, see [Bundles](bundles-25b65a4.md).

</td>
</tr>
<tr>
<td valign="top">

Tenants delivered for applications running on customer-managed subaccounts

</td>
<td valign="top">

Tenant delivery is triggered by the customer in SAP BTP cockpit. The tenant is not preconfigured and must be configured by the customer.

For more information, see [Get Your Tenant](get-your-tenant-460766b.md) .

</td>
</tr>
<tr>
<td valign="top">

Tenants delivered by triggering an upgrade process in the admin tool of SAP cloud solutions

> ### Note:  
> This is valid for tenants bundled with SAP SuccessFactors, SAP SuccessFactors Learning and others. For more information, see [Bundle Tenants and Connectors](https://help.sap.com/docs/identity-provisioning/identity-provisioning/bundle-tenants-and-connectors?version=Cloud).



</td>
<td valign="top">

Tenant delivery is triggered by the customer in the administration tool of the cloud solution. In the case of SAP SuccessFactors, this is the Upgrade Center. The tenant is preconfigured for the customer.

For more information, see [Initiating the Upgrade to SAP Cloud Identity Services - Identity Authentication Service](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/0271d9c4176e45ca9307e49230073240.html?version=2305).

</td>
</tr>
<tr>
<td valign="top">

Tenants delivered by opening a ticket to the technical component of SAP cloud solutions

> ### Note:  
> This is valid for tenants bundled with SAP Concur, SAP Ariba and older versions of SAP Marketing Cloud, SAP S/4HANA Cloud. For more information, see [Bundle Tenants and Connectors](https://help.sap.com/docs/identity-provisioning/identity-provisioning/bundle-tenants-and-connectors?version=Cloud).



</td>
<td valign="top">

1.  Customer opens a ticket to the respective technical component.

2.  The support team reuses an existing tenant or creates a new one.

3.  Tenant is not preconfigured and must be configured by the customer.


For more information, see [SAP Concur Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-concur-integration-scenario?version=Cloud).

</td>
</tr>
</table>



<a name="loioc83eda4eaafd4807abe7b34b0f8ba9b6__section_i1p_fyc_b1c"/>

## Tenant Usage

Following the onboarding phase, tenants are provisioned to customers. They can use them as-is or configure them for their customer specific needs.



<a name="loioc83eda4eaafd4807abe7b34b0f8ba9b6__section_t12_gyc_b1c"/>

## Offboarding

Offboarding leads to tenant deletion when all customer contracts for bundled SAP cloud solutions are terminated. Depending on how the tenant is delivered, you can expect the following:

-   The tenant is delivered as part of a bundling with SAP cloud solutions

    Offboarding is triggered if the customer contracts for all bundled solutions are terminated or expired. The tenant will not be deleted until the very last contract for a bundled solution is terminated.

    > ### Note:  
    > If all of your SAP licenses are terminated, and you have a valid **SAP Concur** license, if you do not use your SAP Cloud Identity Services for 30 days, your tenant may be deleted.

-   The tenant is delivered as part of s self-service request in SAP BTP cockpit

    Offboarding is triggered if the subscription to the Cloud Identity Services is deleted in SAP BTP cockpit. The following takes place:

    -   If the tenant is obtained only for SAP BTP and no other SAP cloud solutions are reusing it, this tenant will be deleted immediately.

    -   If the tenant is reused for other SAP cloud solutions, this tenant will not be deleted until all SAP cloud solutions offboard it.


    In the case of trial tenants, offboarding is triggered if the subscription to the Cloud Identity Services is deleted in SAP BTP cockpit or the SAP BTP developer trial account expired.


