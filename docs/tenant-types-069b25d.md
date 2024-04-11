<!-- loio069b25d2c12f4608b902bd618e9089f3 -->

# Tenant Types

Identity Authentication provides three types of tenants - productive, test, and trial

> ### Note:  
> For more information about obtaining a tenant of Identity Authentication, see [Tenants](tenants-93160eb.md).



<a name="loio069b25d2c12f4608b902bd618e9089f3__section_gys_qkj_3xb"/>

## Productive and Test Tenants

Identity Authentication provides one productive and one test tenant per customer, regardless of the number of contracts signed in which Identity Authentication is included or bundled. The productive and test tenants are identical from technical and functional perspective, they only differ in the naming. Test tenants are provided to customers in addition to their productive tenants where they can test new features before implementing them productively. The test tenant is also the default identity provider for the test landscape.

> ### Note:  
> In some cases, SAP order fulfillment considers the tenant type. For example, for some test instances the trust can only be configured to Identity Authentication test tenants.

> ### Restriction:  
> A customer can't change the type of the tenant.



<a name="loio069b25d2c12f4608b902bd618e9089f3__section_pbf_dy3_3xb"/>

## Trial Tenants

The trial tenant is intended for testing purposes only. It allows you to try out and explore SAP Cloud Identity Services – Identity Authentication and Identity Provisioning. It's free of charge and limited to a trial period in accordance with the SAP BTP trial terms and conditions.

> ### Restriction:  
> -   You can have only one SAP Cloud Identity Services trial tenant per SAP BTP global account regardless of how many subaccounts you create. If you have multiple subaccounts, and you have trial tenants for them, they use one and the same trial tenant.
> -   You can have up to 50 users in a trial tenant.
> -   You can't connect to on-premise systems using the cloud connector. It's not possible to subscribe to the Cloud Identity Services connectivity plan in your trial subaccount.

