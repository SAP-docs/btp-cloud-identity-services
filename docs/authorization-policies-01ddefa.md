<!-- loio01ddefa221b2445ba7a5e061b67976ed -->

# Authorization Policies

Authorization Management lets administrators control who can access what in business applications.

Authorizations can be functional and instance-based. Administrators refine authorization policies that give access to resources in enabled business applications. They can restrict predefined and custom authorization policies based on user and business object attributes and assign them to users with the group management capabilities of the identity directory. See [Configuring Authorization Policies](Operation-Guide/configuring-authorization-policies-982ac5f.md).



## Prerequisites

In line with SAP's identity and access management \(IAM\) strategy, an identity directory with user profiles is a prerequisite for using Authorization Management. For more information, see [CIO Guide: Identity Lifecycle in SAP Landscapes](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fwww.sap.com%2Fdocuments%2F2018%2F05%2F38ce7d25-067d-0010-87a3-c30de2ffd8ff.html).



## Overview

Authorizations are a critical component of any business domain. For cloud business applications to be enterprise-grade and ready, they must incorporate a robust and highly customizable authorization concept. This involves not only checking permissions for business actions but also ensuring these actions are performed on the correct business objects, known as resources.



## Functional Authorizations

Functional authorizations are mandatory because they define what actions a user can perform in an application, such as reading data, creating records, or administrative tasks.

Following the principle of least privilege, each user receives only the permissions required for their work, with separate authorizations for personas such as administrators, support staff, auditors, key users, and specific roles like accountants or production planners. Authorization must be enforced consistently across all access paths, including user interfaces, APIs, batch processes, and search results.



<a name="loio01ddefa221b2445ba7a5e061b67976ed__section_gqp_hmr_3fc"/>

## Instance-Based Authorizations

Instance-based authorizations control who can perform specific actions on specific resources. They restrict access to specific data objects within functional authorizations. For example, in a financial application, a user might be authorized to make journal entries, but only within certain company codes. Conversely, the same user might be allowed to execute the closing process at the end of periods for different company codes. This nuanced approach ensures that permissions are tailored to specific business needs and contexts.



<a name="loio01ddefa221b2445ba7a5e061b67976ed__section_dgy_jmr_3fc"/>

## Using Authorization Policies in Custom Applications

For developers of SAP BTP based business applications, handling authorizations should be straightforward. The authorization framework enables developers to easily declare and enforce their business-specific authorization models.

There are libraries for developers of SAP BTP based business applications to declare and enforce functional and instance-based authorization. Authorizations are declared as code-based "authorization policies" of the business application and enforced with client libraries for Node.js, Java, and Go, and they provide value help for authorization administration. Authorization Management is fully integrated in the Cloud Application Programming model \([Authorization and Access Control](https://cap.cloud.sap/docs/guides/authorization)\) and supports typical SAP BTP developments \([Developing Authorizations](Development/developing-authorizations-22928a2.md)\), such a Cloud Foundry and Kyma.

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

[Cookies](cookies-e60fd04.md "")

[SAP-Managed SAP Cloud Identity](sap-managed-sap-cloud-identity-6039a38.md "SAP Cloud Identity Services support both SAP-managed and customer-managed integration models, depending on who is responsible for maintaining and operating the tenant, application and provisioning configurations.")

