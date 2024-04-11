<!-- loio15da6af8e8f646828158ac854910aadc -->

# Provisioning Systems

Identity Provisioning provides connectors to various business applications for provisioning and deprovisioning of users and groups. These business applications are set up as provisioning systems in the administration console of SAP Cloud Identity Services.

Similar to applications in Identity Authentication, provisioning systems can be viewed as abstractions of the business applications, where these abstractions are used for the purposes of Identity Provisioning.

A provisioning system configured for reading users and groups is called source system. The source system is usually the user store of your organization. A provisioning system used for replicating users and groups is called target system. The target system is usually a cloud system with local user store, where entities are provisioned to from one or more source systems.

![](images/IPS_Source_and_Target_Systems_841d159.png)

The main use case of Identity Provisioning is to read users and groups from a source system and provision them to a target system. This is the standard provisioning mode illustrated in the diagram above.

Identity Provisioning can also be used in proxy mode. In this mode, the service is used for synchronizing user data to and from a central identity management solution \(for example, the on-premise SAP Identity Management\) and a provisioning system - called proxy system \(for example, SAP Analytics Cloud, embedded edition\). Here, Identity Provisioning acts as a proxy between the identity management solution and the system with proxy configuration.

For more information, see [System Types](https://help.sap.com/docs/identity-provisioning/identity-provisioning/system-types?version=Cloud) and [Supported Systems](https://help.sap.com/docs/identity-provisioning/identity-provisioning/supported-systems?version=Cloud).

**Related Information**  


[Tenants](tenants-93160eb.md "A tenant refers to your (customer-specific) instance of SAP Cloud Identity Services. It's delivered to you as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.")

[Bundles](bundles-25b65a4.md "A bundle is a group of preconfigured products and services which are sold together.")

[Applications](applications-404a11c.md "An application is associated with a consumer of Identity Authentication as an identity provider. This consumer could be for example an SAP cloud solution, a third-party application, SAP BTP subaccount, or the SAP Cloud Identity Services administration console.")

[Properties](properties-e92c1aa.md "Properties hold the configuration of a provisioning system.")

[Transformations](transformations-81f5204.md "Transformations help you transform user and group attributes from the data model of the source system to the data model of the target system.")

[Users](users-70e95d1.md "Users in SAP Cloud Identity Services fall into two categories: administrators and end users.")

[Cookies](cookies-e60fd04.md "")

