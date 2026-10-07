<!-- loio6039a386942c4ff6ac382491e1cab69e -->

# SAP-Managed SAP Cloud Identity

SAP Cloud Identity Services support both SAP-managed and customer-managed integration models, depending on who is responsible for maintaining and operating the tenant, application and provisioning configurations.



## Overview

SAP-managed refers to a delivery approach in which SAP is responsible for key technical and operational aspects of the solution. This approach reduces complexity for you and provides a consistent, best-practice experience. SAP manages the software lifecycle, including provisioning, technical integration, monitoring, automatic updates, backups, and offboarding. For more information, see SAP Note [3709792](https://me.sap.com/notes/3709792) and [SAP's Responsibilities](https://help.sap.com/docs/CROSS_PRODUCT_BUSINESS_SUITE/ced859289b25464c9c6a3a32c60a815a/151e949f76114fbf9b69bb33e32d4c0d.html#sap's-responsibilities).

> ### Note:  
> To use the SAP-managed delivery approach, your tenant must run on the SAP Cloud Identity Services infrastructure. If your tenant is still running on the Neo environment, you must first migrate it to the SAP Cloud Identity Services infrastructure.
> 
> For more information, see [Migrate Identity Provisioning Bundle Tenant](https://help.sap.com/docs/identity-provisioning/identity-provisioning/migrate-identity-provisioning-bundle-tenant?version=Cloud&ai=true).

Customer-managed refers to a delivery approach in which you are responsible for configuring and maintaining your tenants according to your business requirements. This approach allows you to adapt features and functionality to your specific needs. For more information, see [Your Responsibilities](https://help.sap.com/docs/CROSS_PRODUCT_BUSINESS_SUITE/ced859289b25464c9c6a3a32c60a815a/151e949f76114fbf9b69bb33e32d4c0d.html#your-responsibilities).

SAP-managed SAP Cloud Identity Services support the following delivery approaches: SAP can manage both the tenant and the integrated applications. You can also manage your own tenants, with SAP managing the integrated applications connected to those tenants.

What does SAP-managed mean for the individual services within SAP Cloud Identity Services?



## Identity Authentication

-   SAP manages the trust between SAP Cloud Identity Services and the connected SAP applications.

-   In the SAP Cloud Identity Services administration console, the *Conditional Authentication* and *Authentication and Access* settings for these applications are read-only and can't be modified.

-   The *Provisioning* tab, which is used to enable central-store based provisioning, is not available.

-   The *Authorization Policies* tab remains available and can be configured as needed.

-   Most settings under *Branding and Layout* can be modified, with the exception of *Token URL Separator* and login page behavior, which remain SAP-managed.




## Identity Provisioning

-   SAP-managed source and target systems are automatically preconfigured and maintained by SAP. As a result, these systems are not displayed in the administration console. You cannot manually schedule or run provisioning jobs for them. Also, you cannot access their job logs.

-   Data replication is automated. Provisioning jobs run automatically every 30 minutes.

-   You can still create and configure provisioning systems, as well as schedule and run provisioning jobs according to your business requirements.

    > ### Caution:  
    > Do not create configurations that duplicate or overlap with SAP-managed provisioning flows. This includes configuring jobs and modifying transformations. Running both SAP-managed and customer-managed provisioning for the same back-end systems within the same SAP-managed flow, can result in data inconsistencies.




## Monitoring and Support

For SAP Cloud Identity Services, you can monitor and troubleshoot the parts you manage. For more information, see [Monitoring and Troubleshooting](Monitoring-and-Reporting/monitoring-and-troubleshooting-b8382ee.md).

If you encounter issues, you can report an incident to SAP Support. For information, see [Getting Support](getting-support-06818b2.md).



## SAP-Managed IAM for Joule

> ### Caution:  
> This section is still work in progress. This page contains information about product features that are part of an SAP Early Adopter Care \(EAC\) program. Products or features that are part of an EAC program are not available outside this program.

SAP-managed IAM for Joule represents an initial step toward the same unified identity model used for the SAP Business Suite. In the Business Suite model, SAP Cloud Identity Services is the authoritative source for user and role data. Assignments are distributed outward to connected applications. The current Joule model adopts a pragmatic starting point: user records and group assignments originate in each line-of-business application. Identity provisioning jobs read this data from the line-of-business system into SAP Cloud Identity Services. The jobs then write the global user ID back to the line-of-business system to link the records. The line-of-business system remains the authoritative source for user and role data in the current release.

This approach enables Joule to reuse existing user and role data without requiring you to restructure your landscapes. Fully centralized assignment management in SAP Cloud Identity Services \(the same harmonized model as the Business Suite\) is planned for a future release.

For the EAC program, the following restrictions and requirements apply to identity provisioning for SAP-managed Joule, in addition to those described in the *Identity Provisioning* section above:

-   You must manually import SAP-managed provisioning job templates from SAP Note [3784171](https://me.sap.com/notes/3784171). The system doesn't yet create jobs automatically when you activate Joule for a line-of-business application. \(If you are part of the EAC program and need access to this SAP Note, open an incident under BC-IAM-IPS.\)

    > ### Caution:  
    > Do not modify the imported SAP-managed provisioning job templates. If issues occur, do not create duplicate jobs or change the template configurations. Contact SAP Support for assistance.

-   You must set up the SAP-managed provisioning jobs after the application representing the line-of-business system already exists in SAP Cloud Identity Services. This ensures that application-specific groups created by the provisioning job are associated with the correct application.

-   Before you run the provisioning jobs, every user in scope must have logged in at least once to the line-of-business application using SAP Cloud Identity Services as the identity provider. The system can't automatically consolidate users who haven't signed in yet.

-   For SAP S/4HANA Cloud, the communication arrangement for SAP-managed identity provisioning uses communication scenario `SAP_COM_1265`.

-   You don't need identity provisioning jobs for SAP LeanIX. The access token issued by LeanIX already contains the required group information.


**Related Information**  


[Tenants](tenants-93160eb.md "A tenant refers to your (customer-specific) instance of SAP Cloud Identity Services. It's delivered to you as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.")

[Bundles](bundles-25b65a4.md "A bundle is a group of preconfigured products and services which are sold together.")

[Applications](applications-404a11c.md "An application is associated with a consumer of Identity Authentication as an identity provider. This consumer could be for example an SAP cloud solution, a third-party application, SAP BTP subaccount, or the SAP Cloud Identity Services administration console.")

[Provisioning Systems](provisioning-systems-15da6af.md "Identity Provisioning provides connectors to various business applications for provisioning and deprovisioning of users and groups. These business applications are set up as provisioning systems in the administration console of SAP Cloud Identity Services.")

[Properties](properties-e92c1aa.md "Properties hold the configuration of a provisioning system.")

[Transformations](transformations-81f5204.md "Transformations help you transform user and group attributes from the data model of the source system to the data model of the target system.")

[Users](users-70e95d1.md "Users in SAP Cloud Identity Services fall into three categories: administrators, end users, and technical users.")

[Agents](agents-12bef24.md "Agent identity represents AI and automation agents in SAP Cloud Identity Services. Agents can authenticate, receive authorization, and be managed like human users while retaining agent-specific capabilities and security controls.")

[Groups](groups-d93be69.md "SAP Cloud Identity Services offers groups to organize users based on common characteristics, authorization, or application. Use them to efficiently manage user access and permissions within your organization's SAP Cloud Identity Services environment.")

[Authorization Policies](authorization-policies-01ddefa.md "Authorization Management lets administrators control who can access what in business applications.")

[Cookies](cookies-e60fd04.md "")

