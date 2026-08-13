<!-- loio6039a386942c4ff6ac382491e1cab69e -->

# SAP-Managed SAP Cloud Identity

SAP Cloud Identity Services support both SAP-managed and customer-managed integration models, depending on who is responsible for maintaining and operating the tenant, application and provisioning configurations.



## Overview

SAP-managed refers to a delivery approach in which SAP is responsible for key technical and operational aspects of the solution. This reduces complexity for customers and provides a consistent, best-practice experience. SAP manages the software lifecycle, including provisioning, technical integration, monitoring, automatic updates, backups, and off-boarding. For more information, see [3709792](https://me.sap.com/notes/3709792) and [SAP's Responsibilities](https://help.sap.com/docs/CROSS_PRODUCT_BUSINESS_SUITE/ced859289b25464c9c6a3a32c60a815a/151e949f76114fbf9b69bb33e32d4c0d.html#sap's-responsibilities).

Customer-managed refers to a delivery approach in which customers are responsible for configuring and maintaining their tenants according to their business requirements. This allows customers to adapt features and functionality to their specific needs. For more information, see [Your Responsibilities](https://help.sap.com/docs/CROSS_PRODUCT_BUSINESS_SUITE/ced859289b25464c9c6a3a32c60a815a/151e949f76114fbf9b69bb33e32d4c0d.html#your-responsibilities).

SAP-managed SAP Cloud Identity Services support the following delivery approaches: SAP can manage both the tenant and the integrated applications. Customers can also manage their own tenants, with SAP managing the integrated applications connected to those tenants.

What does SAP-managed mean for the individual services within SAP Cloud Identity Services?



## Identity Authentication

-   SAP manages the trust between SAP Cloud Identity Services and the connected SAP applications.

-   In the SAP Cloud Identity Services administration console, the *Conditional Authentication* and *Authentication and Access* settings for these applications are read-only and can't be modified.

-   The *Provisioning* tab, which is used to enable central-store based provisioning, is not available.

-   The *Authorization Policies* tab remains available and can be configured as needed.

-   Most settings under *Branding and Layout* can be modified, with the exception of *Token URL Separator* and login page behavior, which remain SAP-managed.




## Identity Provisioning

-   SAP-managed source and target systems are automatically preconfigured and maintained by SAP. As a result, these systems are not displayed in the administration console. You cannot manually schedule or run provisioning jobs for them. Also, you cannot view their job logs.

-   Data replication is automated. Provisioning jobs run automatically every 30 minutes.

-   You can still create and configure provisioning systems, as well as schedule and run provisioning jobs according to your business requirements.




## Monitoring and Support

For SAP Cloud Identity Services, you can monitor and troubleshoot the parts you manage. For more information, see [Monitoring and Troubleshooting](Monitoring-and-Reporting/monitoring-and-troubleshooting-b8382ee.md).

If you encounter issues, you can report an incident to SAP Support. For information, see [Getting Support](getting-support-06818b2.md).

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

[Authorization Policies](authorization-policies-01ddefa.md "Authorization Management enables you to refine authorization policies that give access to resources in enabled SAP BTP-based business applications. Restrict policies based on the values of user or business object attributes. Assign policies to users with the group management capabilities of the identity directory.")

[Cookies](cookies-e60fd04.md "")

