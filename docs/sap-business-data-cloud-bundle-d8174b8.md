<!-- loiod8174b83556d4dd89eb1fafbfe7a39cc -->

# SAP Business Data Cloud Bundle

SAP Business Data Cloud is bundled with SAP Cloud Identity Services – Identity Authentication only.



## Prerequisites

You must have an S-user ID with *Edit Cloud Data* authorization object in [SAP for Me](https://help.sap.com/docs/SAP_FOR_ME) in order to provision the systems for the SAP Business Data Cloud product package.

For more information, see [Provisioning and Configuring SAP Business Data Cloud in SAP for Me](https://help.sap.com/docs/business-data-cloud/onboarding-guide-business-data-cloud/provisioning-and-configuring-sap-business-data-cloud-in-sap-for-me).



## How to Obtain

The bundling of SAP Business Data Cloud with SAP Cloud Identity Services is initiated through the *Identity Provider Administration* tool. When signing in, you can choose one of the following options:

-   Provision a New SAP Cloud Identity Services Tenant

-   Use an Existing SAP Cloud Identity Services tenant


For more information, see [Create or Modify a Bundled SAP Cloud Identity Services Tenant](https://help.sap.com/docs/business-data-cloud/onboarding-guide-business-data-cloud/create-or-modify-bundled-sap-cloud-identity-services-tenant).

> ### Note:  
> Currently, the SAP Business Data Cloud tenant type is **productive only**.



## How to Use

After the tenant provisioning is completed, it appears on the *My Tenants* page in the *Identity Provider Administration* tool. Expect the following:

-   A BusinessDataCloud OIDC application is created under *Bundled Applications* in the SAP Cloud Identity Services administration console.

-   Trust is established between SAP Business Data Cloud and the SAP Cloud Identity Services tenant.

-   An initial admin user is created in the SAP Cloud Identity Services administration console if the selected tenant is newly provisioned. If the selected tenant is an existing one, a regular user is created instead.

-   Although SAP Cloud Identity Services – Identity Provisioning is currently not available for SAP Business Data Cloud, partial configurations are still created. For example, Identity Authentication is created as a source system, and SAP Business Data Cloud is partially configured as a target system.


For more information, see [Configure Authentication](https://help.sap.com/docs/business-data-cloud/onboarding-guide-business-data-cloud/create-or-modify-bundled-sap-cloud-identity-services-tenant?q=subaccount#configure-authentication).

