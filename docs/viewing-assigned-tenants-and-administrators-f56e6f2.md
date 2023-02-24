<!-- loiof56e6f24e373404087d6a1a9a13515a2 -->

# Viewing Assigned Tenants and Administrators

You can view all SAP Cloud Identity Services tenants that are assigned to your customer ID.



<a name="loiof56e6f24e373404087d6a1a9a13515a2__context_lqb_bn5_mqb"/>

## Context

The SAP Cloud Identity Services - Tenants application shows which are the Identity Authentication and Identity Provisioning tenants that are assigned to a customer ID and who are the tenant administrators of these tenants. The information also includes the status of the administrator. Only administrators that have the *Manage Tenant Configuration* role are displayed.

The default tenants, one test and productive tenant per customer, are provided regardless of the number of contracts signed in which SAP Cloud Identity Services is included or bundled. Additional productive or test tenants beyond the initial ones must be purchased separately. For more information, see [Tenant Model and Licensing](tenant-model-and-licensing-93160eb.md).



<a name="loiof56e6f24e373404087d6a1a9a13515a2__steps_ztk_cn5_mqb"/>

## Procedure

1.  Access the SAP Cloud Identity Services - Tenants application from the following link: [https://iamtenants.accounts.cloud.sap/](https://iamtenants.accounts.cloud.sap/)

2.  Log on with your *S user*.

    You can view the Identity Authentication and Identity Provisioning tenants that are assigned to your customer ID.

    ![](images/Tenant_App_Main_c05420d.png)

3.  Choose details next to the tenant to view the bundles or tenant administrators for that tenant.

    ![](images/Show_View_2be1bd0.png)

    -   Bundles - shows the bundles for the tenant.

        ![](images/Bundles_9641f9d.png)

    -   Show - shows the administrators for the tenant.

        ![](images/Tennant_App_Admins_d124030.png)

        > ### Note:  
        > The users and e-mails are masked if the domain of the authenticated user is different from the domain of the tenant administrators.



**Related Information**  


[Tenant Model and Licensing](tenant-model-and-licensing-93160eb.md "This document provides information about the tenant model, tenant licensing, and obtaining a tenant of Identity Authentication.")

