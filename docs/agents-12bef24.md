<!-- loio12bef241b1254430a867ee8b1e6e8c43 -->

# Agents

Agent identity represents AI and automation agents in SAP Cloud Identity Services. Agents can authenticate, receive authorization, and be managed like human users while retaining agent-specific capabilities and security controls.

Agent identity combines multiple IAM artifacts to provide comprehensive identity management for agents within SAP-centric environments.



## What is an Agent Identity?

Agent identity includes these key components in SAP Cloud Identity Services:

**Application Artifact** 

-   Represents a trusted client or system, such as S/4HANA or a dedicated agent application.
-   Includes metadata: redirect URIs, keys, and trust configuration.
-   Provides the technical connection foundation for the SAP landscape.

**Agent Users \(Optional\)** 

-   Identity objects function like human users but are identified as agents.
-   Use technical authentication methods: client credentials, JWT bearer, and token exchange.
-   Support standard operations: create, read, update, and delete, similar to human users.
-   Serve as principals for policies and role assignments.

**User-Role Assignments** 

-   Provide persistent roles for unattended agents.
-   Allow transient role delegations from humans to agents. Delegations can be scoped, context-specific, or time-bound.
-   Track all delegations for audits.

Agents are typically created or deleted programmatically when you subscribe or unsubscribe to an application or use an AI tool to create an agent.



## Core Use Cases



### Agent Acting for Present Human Users

When a human user is present and delegates permissions:

-   Human-in-the-loop flow requests user approval.
-   Agent requests a user token using the authorization code grant flow.
-   Token includes user context for authorized actions.



### Agent Acting for Offline Human Users

When a human user has previously delegated permissions:

-   Agents use refresh tokens with defined validity periods.
-   Use stored delegation relationships to reduce human intervention.
-   Audit trail documents all delegated permissions.



### Unattended Agent Operations

For autonomous agent actions:

-   Agent acts on its own behalf using client credentials.
-   Enforce policy within the agent platform.
-   Configure technical access for back-end systems.

**Related Information**  


[Tenants](tenants-93160eb.md "A tenant refers to your (customer-specific) instance of SAP Cloud Identity Services. It's delivered to you as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.")

[Bundles](bundles-25b65a4.md "A bundle is a group of preconfigured products and services which are sold together.")

[Applications](applications-404a11c.md "An application is associated with a consumer of Identity Authentication as an identity provider. This consumer could be for example an SAP cloud solution, a third-party application, SAP BTP subaccount, or the SAP Cloud Identity Services administration console.")

[Provisioning Systems](provisioning-systems-15da6af.md "Identity Provisioning provides connectors to various business applications for provisioning and deprovisioning of users and groups. These business applications are set up as provisioning systems in the administration console of SAP Cloud Identity Services.")

[Properties](properties-e92c1aa.md "Properties hold the configuration of a provisioning system.")

[Transformations](transformations-81f5204.md "Transformations help you transform user and group attributes from the data model of the source system to the data model of the target system.")

[Users](users-70e95d1.md "Users in SAP Cloud Identity Services fall into three categories: administrators, end users, and technical users.")

[Groups](groups-d93be69.md "SAP Cloud Identity Services offers groups to organize users based on common characteristics, authorization, or application. Use them to efficiently manage user access and permissions within your organization's SAP Cloud Identity Services environment.")

[Authorization Policies](authorization-policies-01ddefa.md "Authorization Management enables you to refine authorization policies that give access to resources in enabled SAP BTP-based business applications. Restrict policies based on the values of user or business object attributes. Assign policies to users with the group management capabilities of the identity directory.")

[Cookies](cookies-e60fd04.md "")

[SAP-Managed SAP Cloud Identity](sap-managed-sap-cloud-identity-6039a38.md "SAP Cloud Identity Services support both SAP-managed and customer-managed integration models, depending on who is responsible for maintaining and operating the tenant, application and provisioning configurations.")

[Configuring Applications](Operation-Guide/configuring-applications-61ad3b0.md "This section describes how you can configure the user authentication, access to an application, and use a branding style in accordance with your company requirements. It also explains the trust configuration between Identity Authentication and a service provider or client (relying party).")

[Configuring Authorization Policies](Operation-Guide/configuring-authorization-policies-982ac5f.md "Authorization Management enables SAP Cloud Identity Services administrators to use authorization policies, customize them, and assign them to users.")

