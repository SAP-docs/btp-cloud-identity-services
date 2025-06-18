<!-- loioe59ae54bc2074f699be8768403eee46a -->

# System Types

Identity Provisioning categorizes systems based on the method of creation, usage and underlying protocols.



<a name="loioe59ae54bc2074f699be8768403eee46a__section_a4k_vxc_zcc"/>

## Creation

There are two types of provisioning systems based on the method of creation: customer managed and SAP initiated.



### Customer Managed

These are the provisioning systems that you as a customer create and configure in the Identity Provisioning UI. There is a limit to the number of systems you can create. It is 20 for source systems and 50 or target systems. However, if your scenarios require more provisioning systems, open an incident for component **BC-IAM-IPS** to request them.



### SAP Initiated

These are the provisioning systems that are automatically created and preconfigured in the Identity Provisioning UI. There is no limit to the number of systems created for you by SAP. Furthermore, you can modify their initial configuration to make them suitable for your scenario.



<a name="loioe59ae54bc2074f699be8768403eee46a__section_x5n_lyc_zcc"/>

## Usage

There are three types of provisioning systems based on their usage: *Source*, *Target*, and *Proxy*. All three of them can be created as customer managed and SAP-initiated systems.



### Source Systems

A source system is the connector used for reading entities \(users, groups, roles\). Source systems can be on-premise or cloud-based, SAP or non-SAP, and usually represent the corporate user store where identities are currently maintained. Identity Provisioning reads the entities from the source system and creates or updates them in the relevant target ones. The provisioning is triggered from the Jobs tab of a source system.

You can connect one source system to one or multiple target systems.

> ### Note:  
> In the case of multiple \(enabled\) target systems, when you start a *Read* or a *Resync* job, this operation will trigger provisioning of entities from this source system to all relevant target ones.

To check the list of all supported source systems, see: [Source Systems](source-systems-58033be.md)



### Target Systems

A target system is the connector used for writing \(provisioning\) entities. Target systems are usually clouds, where Identity Provisioning creates or updates the entities taken from the source system.

A target system can be connected to a single or multiple source systems.

> ### Note:  
> In the case of multiple source systems, we recommend that you run the provisioning jobs successively for each system, not simultaneously. This way, you'll avoid incorrect overwriting or merging of entity data, hence failed provisioning jobs.

To check the list of all supported target systems, see: [Target Systems](target-systems-ab3f641.md)



### Proxy Systems

A proxy system is a special connector used for "hybrid" scenarios. It exposes any Identity Provisioning supported backend system as a SCIM 2.0 service provider, which can be consumed by any [SCIM 2.0](https://tools.ietf.org/html/rfc7644) compatible client application, without making a direct connection between them.

To achieve this, the Identity Provisioning service uses this special proxy system to execute provisioning operations \(create, update, delete, etc.\) requested by the client application.

The examples in this section cover using of SAP Identity Management as a consuming client application but you can use any other SCIM-based identity management solution. For more information, see: [Hybrid Scenario: SAP Identity Management](Integrating-the-Service/hybrid-scenario-sap-identity-management-6fa419a.md). To provide communication between SAP Identity Management and the back-end system, the proxy application uses a SCIM 2.0 protocol. A system can act as a proxy if it supports both read and write operations.

How a proxy system works:

1.  The Identity Provisioning service exposes the back end of a supported system as a "proxy".
2.  An external application \(for example, SAP Identity Management\) regards the proxy system as its back-end system.
3.  The entities \(users\) exposed by the back-end system are mapped to SCIM 2.0 entities, if possible. If not possible, the SCIM standard provides a mechanism to define a new resource type with the appropriate schema. You can use the custom resource type to map the back-end entities. See: [SCIM Resources](https://tools.ietf.org/html/rfc7643#section-3)
4.  Finally, the external application can start sending REST web service requests to the proxy system in order to read identities from the back end of the SCIM 2.0 system.

To check the list of all supported proxy systems, see: [Proxy Systems](proxy-systems-b10d68a.md)



<a name="loioe59ae54bc2074f699be8768403eee46a__section_abp_myc_zcc"/>

## Protocol

There are four types of provisioning systems based on the underlying protocol:


<table>
<tr>
<th valign="top">

**SCIM-based** 

</th>
<th valign="top">

**SOAP/OData-based** 

</th>
<th valign="top">

**LDAP-based** 

</th>
<th valign="top">

RFC-based

</th>
</tr>
<tr>
<td valign="top">

SCIM-based systems use the SCIM \(System for Cross-domain Identity Management\) standard API to manage and provision user identities.

</td>
<td valign="top">

SOAP or OData-based systems are typically S/4HANA systems which use these protocols for identity and role management within the S/4HANA environment.

</td>
<td valign="top">

LDAP-based systems use the LDAP protocol to manage and retrieve directory information.

</td>
<td valign="top">

RFC-based systems use Remote Function Call \(RFC\) for communication between SAP systems and between SAP and non-SAP systems.

</td>
</tr>
<tr>
<td valign="top">

`Type`: *HTTP*

-   Identity Authentication

-   Intelligent Opportunity Analyzer

-   Local Identity Directory

-   SAP Advanced Financial Closing

-   SAP Advanced Workflow

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP Ariba Category Management

-   SAP Ariba Central Invoice Management

-   SAP BTP Account Members \(Neo\)

-   SAP BTP Java/HTML5 apps \(Neo\)

-   SAP BTP Platform Members \(Cloud Foundry\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Build Work Zone, advanced edition

-   SAP Build Work Zone, standard edition

-   SAP Business Network

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP Concur

-   SAP CPQ

-   SAP Data Custodian

-   SAP Datasphere

-   SAP Enable Now

-   SAP Enterprise Portal

-   SAP Fieldglass

-   SAP Field Service Management

-   SAP HANA Cloud, SAP HANA Database

-   SAP Intelligent Agriculture

-   SAP Jam Collaboration

-   SAP Master Data Integration

-   SAP S/4HANA for procurement planning

-   SAP Sales Cloud and SAP Service Cloud

-   SAP SuccessFactors version 2

-   SAP SuccessFactors Employee Central Payroll

-   SAP SuccessFactors Incentive Management

-   SAP SuccessFactors Learning

-   Sales Cloud – Analytics & AI

-   Cloud Foundry UAA Server

-   Procurement Data Warehouse

-   SCIM System

-   SSH Server \(Beta\)




</td>
<td valign="top">

`Type`: *HTTP*

-   SAP BTP ABAP environment

-   SAP Integrated Business Planning for Supply Chain

-   SAP Market Communication for Utilities

-   SAP Marketing Cloud

-   SAP S/4HANA Cloud

-   SAP S/4HANA On-Premise

-   SAP SuccessFactors version 1




</td>
<td valign="top">

`Type`: *LDAP*

-   LDAP Server

-   Microsoft Active Directory




</td>
<td valign="top">

`Type`: *RFC*

-   SAP AS ABAP




</td>
</tr>
</table>

Both Microsoft Entra ID and Google G Suite use `Type`: *HTTP*.

