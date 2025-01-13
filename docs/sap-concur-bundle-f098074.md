<!-- loiof0980747e54149f5b5affa7db2ac3b65 -->

# SAP Concur Bundle

SAP Concur bundles with SAP Cloud Identity Services – Identity Authentication and Identity Provisioning.



Customers can integrate SAP Cloud Identity Services no matter whether the Concur instance is integrated with their own corporate identity provider or not.

> ### Note:  
> As of March 15, 2022, Identity Provisioning bundle tenants are created only on the infrastructure of SAP Cloud Identity Services. These tenants come with most of the provisioning systems \(connectors\) enabled by default. Identity Provisioning bundle tenants running on SAP BTP, Neo environment have a limited number of connectors enabled by default. These are illustrated in the diagram that follows.



### Bundle Tenant on Neo Environment

![](images/IPS_Concur_Bundle_6cc3fd8.png)



<a name="loiof0980747e54149f5b5affa7db2ac3b65__section_llr_syg_vzb"/>

## Prerequisites

-   New or existing Concur Expense, Concur Request, Concur Invoice, and/or Concur Travel & Expense customers that have at least one other SAP cloud solution.

    > ### Note:  
    > Concur Travel-only is not currently supported.

-   Identity Authentication and Identity Provisioning tenants must be created or configured by SAP:

    1.  You need to check with your SAP Concur account team to determine if you are eligible for provisioning of a tenant with Identity Authentication and Identity Provisioning services.

    2.  If eligible, create a support case to initiate the provisioning of an SAP Cloud Identity Services tenant with Identity Authentication and Identity Provisioning services. For customers with an existing Identity Authentication and Identity Provisioning tenants, the tenants will be reused.

        > ### Note:  
        > You must create a case to set up Identity Authentication and Identity Provisioning tenant provisioning for your SAP Concur entity even if you already have existing Identity Authentication and Identity Provisioning tenants from other SAP solutions.

        To create a case, you can create an SAP Concur support case \(recommended\) or an SAP for Me case.

        For more information about creating an SAP Concur support case, see the *How to Navigate the SAP Concur Support Portal* section on the [SAP Concur Support](https://assets.concur.com/tech-pubs/SAP-Concur-Training-Library/GTM.htm) page for instructions on creating a support case. Use the Case Type = Single Sign On.

        For more information about creating an SAP for Me case, see this SAP Note: [1296527](https://me.sap.com/notes/1296527) - How to create a support case \(contact SAP Product Support\) - SAP for Me. Use the Component = BNS-CON-SSO.





<a name="loiof0980747e54149f5b5affa7db2ac3b65__section_mfk_ldd_wvb"/>

## How to Use

Normally, the tenant with Identity Authentication and Identity Provisioning services is pre-configured for out-of-the-box integrations between SAP solutions. However, in the case of SAP Concur, after the tenant provisioning is complete, you need to **manually configure** it for your authentication and provisioning scenarios. For more information, see [SAP Concur Integration Scenario](https://help.sap.com/docs/SAP_CLOUD_IDENTITY/b95c3d5bab324a3a8409eee5267a5b75/ef38d9ee3f7544d882dc3f8de123ad3d.html?version=Cloud)

