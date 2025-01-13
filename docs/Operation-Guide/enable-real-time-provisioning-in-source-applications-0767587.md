<!-- loio076758707f72491dbc8020b746845fac -->

# Enable Real-Time Provisioning in Source Applications

Enable the real-time provisioning configuration in the source applications that trigger immediate sync when changes occur.

> ### Note:  
> In the context of real-time provisioning, Identity Authentication, SAP SuccessFactors and SAP SuccessFactors Learning are considered source applications.

The way you enable real-time provisioning differs among applications. SAP SuccessFactors requires that you turn on the Enable Real Time Sync option in the Admin Center. Identity Authentication requires that you configure Identity Provisioning as a target system in the SAP Cloud Identity Services admin console.

Regardless of application-specific configurations, you are always required to provide the real-time provisioning endpoint URL, the authentication type and credentials.





### Identity Authentication

-   [Configure Identity Authentication for Real-Time Provisioning](configure-identity-authentication-for-real-time-provisioning-3349645.md)




### SAP SuccessFactors

-   [Manage Real-Time Sync of New Hires from SAP SuccessFactors to Identity Authentication with Identity Provisioning](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/4ce03614440e4c3a85b9eb4716bc97ed.html?version=Latest)

-   [Managing Identity Authentication/Identity Provisioning Real Time Sync](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/08bc4985a894495a9a92d8ec1549d43b.html?version=Latest)




### SAP SuccessFactors Learning

-   [Learning Configuration Procedure](https://help.sap.com/docs/SAP_SUCCESSFACTORS_LEARNING/82cf7c83c7db42a8aa1d3bbdbc39e93d/3f29058a9dfe4ce38a3c774fbdf5339b.html?version=Latest)

    > ### Restriction:  
    > Real-time provisioning of **groups** is not supported for this system.


**Related Information**  


[Configure SAP Jam for Real-Time Provisioning](configure-sap-jam-for-real-time-provisioning-a923427.md "Tenant administrators can configure SAP Jam target systems for real-time provisioning via the administration console for SAP Cloud Identity Services.")

[Configure Identity Authentication for Real-Time Provisioning](configure-identity-authentication-for-real-time-provisioning-3349645.md "Enable real-time provisioning in Identity Authentication to trigger immediate synchronization of user changes to target systems configured in Identity Provisioning.")

[Provision Users to Target Systems](provision-users-to-target-systems-af6f78b.md "Tenant administrators can provision users of Identity Authentication to SAP Jam and Identity Provisioning target systemstarget system.")

[Delete Target System](delete-target-system-6372e9a.md "As a tenant administrator, you can delete one or more target systems in a tenant of Identity Authentication.")

