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

For more information about the architecture model, see [SAP-Managed IAM Integration](https://architecture.learning.sap.com/docs/ref-arch/d94f2a) on the *SAP Architecture Center*.

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
    > Do not create configurations that duplicate or overlap with SAP-managed provisioning flows. This includes configuring jobs and modifying transformations. Running both SAP-managed and customer-managed provisioning for the same back-end systems within the same SAP-managed flow, results in data inconsistencies.




## Monitoring and Support

For SAP Cloud Identity Services, you can monitor and troubleshoot the parts you manage. For more information, see [Monitoring and Troubleshooting](Monitoring-and-Reporting/monitoring-and-troubleshooting-b8382ee.md).

If you encounter issues, you can report an incident to SAP Support. For information, see [Getting Support](getting-support-06818b2.md).



## SAP-Managed IAM for Joule

For Joule, SAP handles provisioning, integration, and maintenance with reduced setup effort. For more information about the setup steps, applicable restrictions, and the transition from customer-managed provisioning, see [SAP-Managed Provisioning](https://help.sap.com/docs/joule-work/services/sap-managed-provisioning?version=CLOUD).

For more information about the identity and access management architecture required for Joule, including the provisioning model, user consolidation stages, agent authorization, and EAC restrictions, see [Identity and Access Management for Joule](identity-and-access-management-for-joule-050287e.md).

For more information about the recommended setup steps that apply across all SAP-managed solutions, see  <?sap-ot O2O class="- topic/xref " href="e415137ba4d04391b39e785c5c3e6094.xml" text="" desc="" xtrc="xref:9" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/6039a386942c4ff6ac382491e1cab69e.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

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

[Identity and Access Management for Joule](identity-and-access-management-for-joule-050287e.md "Identity and access management architecture required for Joule, including the requirement for a single SAP Cloud Identity Services tenant, a populated Identity Directory, SAP-managed provisioning, and global user ID assignment. Understand this foundation before you implement Joule to ensure consistent authentication and authorization across all connected SAP applications.")

 <?sap-ot O2O class="- topic/link " href="e415137ba4d04391b39e785c5c3e6094.xml" text="" desc="" xtrc="link:2" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/6039a386942c4ff6ac382491e1cab69e.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[SAP-Managed IAM Integration Reference Architecture](https://architecture.learning.sap.com/docs/ref-arch/d94f2a)

