<!-- loio01ddefa221b2445ba7a5e061b67976ed -->

# Authorization Policies

Authorization Management enables you to refine authorization policies that give access to resources in enabled SAP BTP-based business applications. Restrict policies based on the values of user or business object attributes. Assign policies to users with the group management capabilities of the identity directory.

Authorizations are a critical component of any business domain. For cloud business applications to be enterprise-grade and ready, they must incorporate a robust authorization concept. This involves not only checking permissions for business actions but also ensuring these actions are performed on the correct business objects, known as resources.



<a name="loio01ddefa221b2445ba7a5e061b67976ed__section_gqp_hmr_3fc"/>

## Instance-Based Authorizations

Instance-based authorizations refer to the process of verifying whether a user is permitted to perform a specific action on a particular resource. For example, in a financial application, a user might be authorized to make journal entries, but only within certain company codes. Conversely, the same user might be allowed to execute the closing process at the end of periods for different company codes. This nuanced approach ensures that permissions are tailored to specific business needs and contexts.



<a name="loio01ddefa221b2445ba7a5e061b67976ed__section_dgy_jmr_3fc"/>

## Authorization Management

For developers of SAP BTP-based business applications, handling these authorizations should be straightforward. The authorization framework should allow developers to easily declare, enforce, and manage their business-specific authorization models. By leveraging instance-based authorizations, businesses can ensure that their applications are secure, efficient, and tailored to their specific operational needs.

The Authorization Management Service of SAP Cloud Identity Services provides libraries and services for developers of SAP BTP-based business applications to declare, enforce, and manage instance based authorization checks. Authorizations are declared as code-based "authorization policies" in the project of the business application, assigned to users, and enforced with client libraries for Node.js, Java, and Go.

The Authorization Managmement Service has the following features:

-   Fine granular authorization checks in comparison with role collections on SAP BTP

-   Full integration into [Authorization and Access Control](https://cap.cloud.sap/docs/guides/authorization) with the Cloud Application Programming model

-   Supports Kubernetes applications

-   Value help for authorization administration

-   Simple integration of application-to-application, application-to-service, and service-to-service calls with a privileged mode and a simple configuration in the application section of the administration console




<a name="loio01ddefa221b2445ba7a5e061b67976ed__section_f2n_5wm_jfc"/>

## Using Identity Directory

The main additional value comes from the integration into the kernel service of the SAP Cloud Identity Services. A populated identity directory is a prerequisite for the Authorization Management System usage. When considering that customers usually use multiple SAP SaaS applications, and also have some custom apps, they’ll encounter the need to provide user data to some of these apps, for example, for display purposes and value help when they assign users to application objects. The strategy with the identity directory is to let them make users available only once in the SAP Cloud Identity Services and serve the applications from there.

We recommend to automatically assigning authorizations to users based on rules, for example, using the SAP Cloud Identity Services - Identity Provisioning or your corporate identity management system.



<a name="loio01ddefa221b2445ba7a5e061b67976ed__section_efw_bjn_jfc"/>

## Personas

1.  Developers of the business application, who define the authorization model using base authorization policies and enforce them by implementing authorization checks

2.  Administrators, who manage custom authorization policies from base policies, set business restrictions on policies, and assign bothe types of policies to application users

3.  Users of the business application, who are checked for specific attributes that authorize them to perform specific actions on specific resources




<a name="loio01ddefa221b2445ba7a5e061b67976ed__section_y5b_z25_jfc"/>

## Process

Developers define the base policies with data control language \(DCL\) and upload them to the authorization management server. the Authorization Management Service forwards the base policies to the DCL compiler, which transforms DCL policies into an internal format \(DCN\) and assembles them by forming authorization bundles in a bundle storage in SAP Cloud Identity Services. The bundle gateway \(BGW\) retrieves the authorization bundles on request from the authorization decision controller \(ADC\), which uses the authorization bundles as input to perform the authorization checks. The administration console displays the bundled applications.

Administrators use the base policies to create custom policies with modified rules and assign them to users.

Users of the business application can log on and have access to the resources, which are allowed by the custom authorization policies.

**Related Information**  


[Tenants](tenants-93160eb.md "A tenant refers to your (customer-specific) instance of SAP Cloud Identity Services. It's delivered to you as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.")

[Bundles](bundles-25b65a4.md "A bundle is a group of preconfigured products and services which are sold together.")

[Applications](applications-404a11c.md "An application is associated with a consumer of Identity Authentication as an identity provider. This consumer could be for example an SAP cloud solution, a third-party application, SAP BTP subaccount, or the SAP Cloud Identity Services administration console.")

[Provisioning Systems](provisioning-systems-15da6af.md "Identity Provisioning provides connectors to various business applications for provisioning and deprovisioning of users and groups. These business applications are set up as provisioning systems in the administration console of SAP Cloud Identity Services.")

[Properties](properties-e92c1aa.md "Properties hold the configuration of a provisioning system.")

[Transformations](transformations-81f5204.md "Transformations help you transform user and group attributes from the data model of the source system to the data model of the target system.")

[Users](users-70e95d1.md "Users in SAP Cloud Identity Services fall into two categories: administrators and end users.")

[Groups](groups-d93be69.md "SAP Cloud Identity Services offers groups to organize users based on common characteristics, authorization, or application. Use them to efficiently manage user access and permissions within your organization's SAP Cloud Identity Services environment.")

[Cookies](cookies-e60fd04.md "")

