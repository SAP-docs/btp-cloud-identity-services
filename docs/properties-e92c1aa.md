<!-- loioe92c1aa0bb634ec1a35f353f0a4588ec -->

# Properties

Properties hold the configuration of a provisioning system.

Properties define the connection and authentication information needed for accessing the provisioning system. They control which entities \(users and groups\) will be provisioned - by defining filters and unique attributes, as well as how they will be provisioned - in bulk operations or one entity at a time, with put or patch requests.

There are various types of properties depending on their usability, whether they hold mandatory or optional information, standard information in plain text or credentials in encrypted strings. They can be categorized as follows:

-   Standard

-   Credential

-   Default

-   Parameterized

-   Internal


For your system provisioning goals, you can set properties in SAP BTP cockpit: *Destinations* andthe administration console of SAP Cloud Identity Services on the *Properties* tab of the provisioning system.

> ### Note:  
> If the same properties exist in both the *Destinations* editor \(in the cockpit\) and in the *Properties* tab of the system \(in the Identity Provisioning UI\), the values set in the *Properties* tab are taken with higher priority.



<a name="loioe92c1aa0bb634ec1a35f353f0a4588ec__section_wbr_gnt_lbc"/>

## Prefixes



Property names have specific prefixes, which indicate the provisioning system the property is applicable for. This helps you distinguish between properties meant for different systems.

-   Properties starting with *<ips\>* are applicable for all provisioning systems, for example `ips.failed.request.retry.attempts`.

-   Properties starting with the abbreviation of a provisioning system name, such as *<s4hana.cloud\>* or *<sf\>*, are applicable for the given system - in this case, SAP S/4HANA Cloud and SAP SuccessFactors, respectively. For example, `s4hana.cloud.support.bulk.operation` and `sf.user.filter`.

-   Properties starting with *<scim\>* are applicable for the provisioning systems that were in use before the implementation of the system-specific prefixes. These *<scim\>* properties often apply to the first version of specific connector, although there can be exceptions. For example: `scim.user.filter` is used for filtering users in Identity Authentication version and SAP Analytics Cloud version 1. With the release of version 2 for both Identity Authentication and SAP Analytics Cloud, newer, system-specific properties were introduced: `ias.user.filter` and `sac.user.filter`.


> ### Note:  
> The scim-prefixed properties and the system-specific properties can be used interchangeably. If both are configured, Identity Provisioning will prioritize and consider the system-specific properties.

**Related Information**  


[Tenants](tenants-93160eb.md "A tenant refers to your (customer-specific) instance of SAP Cloud Identity Services. It's delivered to you as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.")

[Bundles](bundles-25b65a4.md "A bundle is a group of preconfigured products and services which are sold together.")

[Applications](applications-404a11c.md "An application is associated with a consumer of Identity Authentication as an identity provider. This consumer could be for example an SAP cloud solution, a third-party application, SAP BTP subaccount, or the SAP Cloud Identity Services administration console.")

[Provisioning Systems](provisioning-systems-15da6af.md "Identity Provisioning provides connectors to various business applications for provisioning and deprovisioning of users and groups. These business applications are set up as provisioning systems in the administration console of SAP Cloud Identity Services.")

[Transformations](transformations-81f5204.md "Transformations help you transform user and group attributes from the data model of the source system to the data model of the target system.")

[Users](users-70e95d1.md "Users in SAP Cloud Identity Services fall into two categories: administrators and end users.")

[Cookies](cookies-e60fd04.md "")

[List of Properties](list-of-properties-d6f3577.md "On this page you can find all the available properties to use in the Identity Provisioning service. You can filter them by system type name, &quot;All Systems&quot;, by a word or only part of it.")

[Manage Properties](Operation-Guide/manage-properties-4e2bc9d.md "You can add, delete and modify properties for a system in Identity Provisioning.")

