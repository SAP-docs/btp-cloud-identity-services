<!-- loio25b65a41e44c4759b8d0b988ac560c7c -->

# Bundles

A bundle is a group of preconfigured products and services which are sold together.

SAP Cloud Identity Services refer to a bundle as a group of preconfigured SAP cloud solutions and Cloud Identity Services. You purchase the cloud solution and get the services free of charge. The reason for bundling is to offer you out-of-the-box integration between SAP solutions.

> ### Note:  
> As a customer, you need at least one licensed SAP cloud solution which triggers SAP Cloud Identity Services tenant delivery.

The bundling process results in provisioning an SAP Cloud Identity Services tenant to your organization, where Identity Authentication and Identity Provisioning are preconfigured for the relevant SAP cloud solution. In the majority of cases, this means that in the SAP Cloud Identity Services admin console, a bundled application is created and connected to the cloud solution, where your users will log on. The trust between Identity Authentication and the given solution is established.

For Identity Provisioning, this means that communication and authentication with the provisioning systems relevant for the SAP cloud solution are set up. The transformations of those systems might be different from the default ones and adapted for specific scenarios. You are ready to schedule and run jobs to synchronize your users and groups.

Note that all provisioning systems \(connectors\) are enabled for the SAP Cloud Identity Access Governance bundle tenant, and all source and proxy connectors are enabled for the SAP Jam Collaboration bundle tenant.

> ### Note:  
> Note the availability of the following connectors within the bundle tenants running in the infrastructure of SAP Cloud Identity Services:
> 
> -   SCIM, LDAP Server, Microsoft AD, Microsoft Entra ID and Google G suite are not supported as target connectors in bundle tenants.
> 
> -   Cloud Foundry UAA Server is not supported as source, target and proxy connector in bundle tenants.

For more information, see [Get Your Tenant](get-your-tenant-460766b.md).



<a name="loio25b65a41e44c4759b8d0b988ac560c7c__section_b1k_php_ryb"/>

## SAP Cloud Solutions Bundled with Cloud Identity Services

The following SAP cloud solutions bundle with SAP Cloud Identity Services which come preconfigured for the given cloud solutions:


<table>
<tr>
<th valign="top">

SAP \(A-F\)

</th>
<th valign="top">

SAP \(G-Z\)

</th>
</tr>
<tr>
<td valign="top">

-   SAP Build Work Zone, advanced edition

-   SAP Business Technology Platform

-   SAP Central Business Configuration

-   Sales Cloud – Analytics & AI

-   SAP Cloud ALM

-   SAP Cloud Identity Access Governance

-   SAP Commerce Cloud

-   SAP Concur

-   SAP Fieldglass

-   SAP Field Service Management




</td>
<td valign="top">

-   SAP Integrated Business Planning for Supply Chain

-   SAP Jam Collaboration

-   SAP Marketing Cloud

-   SAP Market Communication for Utilities

-   SAP S/4HANA Cloud

-   SAP SuccessFactors

-   SAP SuccessFactors Learning

-   SAP SuccessFactors Incentive Management




</td>
</tr>
</table>

> ### Note:  
> Some SAP cloud solutions bundle with Identity Authentication only. There could be various reasons for that. For example, the solution may not have a local user store and therefore doesn't need to bundle with Identity Provisioning for managing identity lifecycle. Or the provisioning service doesn't offer a connector to the given SAP cloud solution.

**Related Information**  


[Tenants](tenants-93160eb.md "A tenant refers to your (customer-specific) instance of SAP Cloud Identity Services. It's delivered to you as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.")

[Applications](applications-404a11c.md "An application is associated with a consumer of Identity Authentication as an identity provider. This consumer could be for example an SAP cloud solution, a third-party application, SAP BTP subaccount, or the SAP Cloud Identity Services administration console.")

[Provisioning Systems](provisioning-systems-15da6af.md "Identity Provisioning provides connectors to various business applications for provisioning and deprovisioning of users and groups. These business applications are set up as provisioning systems in the administration console of SAP Cloud Identity Services.")

[Properties](properties-e92c1aa.md "Properties hold the configuration of a provisioning system.")

[Transformations](transformations-81f5204.md "Transformations help you transform user and group attributes from the data model of the source system to the data model of the target system.")

[Users](users-70e95d1.md "Users in SAP Cloud Identity Services fall into two categories: administrators and end users.")

[Groups](groups-d93be69.md "SAP Cloud Identity Services offers groups to organize users based on common characteristics, authorization, or application. Use them to efficiently manage user access and permissions within your organization's SAP Cloud Identity Services environment.")

[Authorization Policies](authorization-policies-01ddefa.md "Authorization Management enables you to refine authorization policies that give access to resources in enabled SAP BTP-based business applications. Restrict policies based on the values of user or business object attributes. Assign policies to users with the group management capabilities of the identity directory.")

[Cookies](cookies-e60fd04.md "")

