<!-- loioe59ae54bc2074f699be8768403eee46a -->

# System Types

Identity Provisioning differentiates systems based on how they are created and what they are used for.

Based on how they are created, provisioning systems are classified as:

-   *Customer Managed* - These are the provisioning systems that you as a customer create and configure in the Identity Provisioning UI. There is a limit to the number of systems you can create. It is 20 for source systems and 50 or target systems. However, if your scenarios require more provisioning systems, open an incident for component **BC-IAM-IPS** to request them.

-   *SAP Initiated* - These are the provisioning systems that are automatically created and preconfigured in the Identity Provisioning UI. There is no limit to the number of systems created for you by SAP. Furthermore, you can modify their initial configuration to make them suitable for your scenario.


Based on their usage, provisioning systems are classified as: *Source*, *Target*, and *Proxy*. All three of them can be created as Customer Managed and SAP Initiated systems.



## Source Systems

A source system is the connector used for reading entities \(users, groups, roles\). Source systems can be on-premise or cloud-based, SAP or non-SAP, and usually represent the corporate user store where identities are currently maintained. Identity Provisioning reads the entities from the source system and creates or updates them in the relevant target ones. The provisioning is triggered from the *Jobs* tab of a source system.

You can connect one source system to one or multiple target systems.

> ### Remember:  
> In the case of multiple \(enabled\) target systems, when you start a *Read* or a *Resync* job, this operation will trigger provisioning of entities from this source system to all relevant target ones.

To check the list of all supported source systems, see: [Source Systems](source-systems-58033be.md)



## Target Systems

A target system is the connector used for writing \(provisioning\) entities. Target systems are usually clouds, where Identity Provisioning creates or updates the entities taken from the source system.

A target system can be connected to a single or multiple source systems.

> ### Remember:  
> In the case of multiple source systems, we recommend that you run the provisioning jobs **successively** for each system, not simultaneously. This way, you'll avoid incorrect overwriting or merging of entity data, hence failed provisioning jobs.

To check the list of all supported target systems, see: [Target Systems](target-systems-ab3f641.md)



## Proxy Systems

A proxy system is a special connector used for "hybrid" scenarios. It exposes any Identity Provisioning supported backend system as a SCIM 2.0 service provider, which can be consumed by any [SCIM 2.0](https://tools.ietf.org/html/rfc7644) compatible client application, without making a direct connection between them.

To achieve this, the Identity Provisioning service uses this special proxy system to execute provisioning operations \(create, update, delete, etc.\) requested by the client application.

The examples in this section cover using of SAP Identity Management as a consuming client application but you can use any other SCIM-based identity management solution. For more information, see: [Hybrid Scenario: SAP Identity Management](https://help.sap.com/docs/identity-provisioning/identity-provisioning/hybrid-scenario-sap-identity-management?version=Cloud)

To provide communication between SAP Identity Management and the back-end system, the proxy application uses a SCIM 2.0 protocol. A system can act as a proxy if it supports both read and write operations.

**How a proxy system works:**

1.  The Identity Provisioning service exposes the back end of a supported system as a "proxy".
2.  An external application \(for example, SAP Identity Management\) regards the proxy system as its back-end system.
3.  The entities \(users\) exposed by the back-end system are mapped to SCIM 2.0 entities, if possible. If not possible, the SCIM standard provides a mechanism to define a new resource type with the appropriate schema. You can use the custom resource type to map the back-end entities. See: [SCIM Resources](https://tools.ietf.org/html/rfc7643#section-3)
4.  Finally, the external application can start sending REST web service requests to the proxy system in order to read identities from the back end of the SCIM 2.0 system.

To check the list of all supported proxy systems, see: [Proxy Systems](proxy-systems-b10d68a.md)

