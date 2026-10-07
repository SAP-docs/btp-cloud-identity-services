<!-- loio22928a2d8b7e42cc887398ca72019821 -->

# Developing Authorizations

Developers define, update, and create authorizations. These are the basis for Authorization Management, which administrators can use to grant users access to resources.

Authorization Management enables SAP Cloud Identity Services administrators to use instance-based authorizations in the form of authorization policies in multiple environments. They assign authorization policies to users and thus manage user access to resources.

Developers define and deploy an application that supports authorization policies in SAP Cloud Identity Services. They include functional checks, instance-base authorizations, and user attributes. Authorization Management is automatically enabled for a new tenant and can be used as soon as an application requests it. Service instances and bindings are added automatically. The authorization policies are available in the SAP Cloud Identity Services administration console.



<a name="loio22928a2d8b7e42cc887398ca72019821__section_t2p_2wb_dzb"/>

## Developing Authorization Policies

Developers can use the Cloud Application Programming model for authorization policies. We've provided a sample application, which you can use for the creation of authorization policies.

-   [Authorization and Access Control](https://cap.cloud.sap/docs/guides/authorization) with the Cloud Application Programming model

-   [Sample apps in GitHub](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fsap.github.io%2Fcloud-identity-developer-guide%2FSamples.html)


> ### Note:  
> Changes in the assignment of authorization policies usually take up to 15 seconds to propagate due to caching delays. The delay can also be longer. So, respect this waiting time.



<a name="loio22928a2d8b7e42cc887398ca72019821__section_yvw_zjm_bgc"/>

## Defining Authorization Policies

The Data Control Language \(DCL\) enables developers to define authorization policies and rules using an SQL-like syntax in SAP Cloud Identity Services. This declarative language allows them to specify access controls for data and resources through structured authorization policy definitions.

-   Define authorization policies using SQL-like syntax.

-   Create reusable authorization policies with attributes and conditions.

-   Enable administrators to combine and refine rules into custom authorization policies.

-   Support user assignment in the administration console.


DCL provides essential elements including rules, resources, conditions, attributes, schemas, and packages for enterprise-grade access control implementation. For more information, see [SAP Cloud Identity Services Developer Guide](https://sap.github.io/cloud-identity-developer-guide/).

