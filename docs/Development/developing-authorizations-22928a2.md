<!-- loio22928a2d8b7e42cc887398ca72019821 -->

# Developing Authorizations

Developers define, update, and create authorizations. These are the basis for Authorization Management, which administrators can use to grant users access to resources.

Authorization Management enables SAP Cloud Identity Services administrators to use instance-based authorizations in the form of authorization policies in multiple environments. They assign authorization policies to users and thus manage user access to resources.

Developers define and deploy an application that supports authorization policies in SAP Cloud Identity Services. They include functional checks, instance-base authorizations, and user attributes. Authorization Management is automatically enabled for a new tenant and can be used as soon as an application requests it. Service instances and bindings are added automatically. The authorization policies are available in the SAP Cloud Identity Services administration console.

For more information, see [Adding Authentication and Authorization](https://help.sap.com/docs/authorization-and-trust-management-service/authorization-and-trust-management/adding-authentication-and-authorization) and [Configuring Authorization Policies](../Operation-Guide/configuring-authorization-policies-982ac5f.md) \(NO FINAL LINK\).



<a name="loio22928a2d8b7e42cc887398ca72019821__section_t2p_2wb_dzb"/>

## Developing Authorization Policies

Developers use the Cloud Application Programming model for authorization policies. We've provided a sample application, which you can use for the creation of authorization policies.

-   [Authorization and Access Control](https://cap.cloud.sap/docs/guides/authorization) with the Cloud Application Programming model

-   [Sample apps in GitHub](https://github.com/SAP-samples/cloud-cap-samples)




<a name="loio22928a2d8b7e42cc887398ca72019821__section_yvw_zjm_bgc"/>

## Defining Authorization Policies

The Data Control Language \(DCL\) enables developers to define authorization policies and rules using an SQL-like syntax in SAP Cloud Identity Services. This declarative language allows them to specify access controls for data and resources through structured authorization policy definitions.

-   Define authorization policies using SQL-like syntax.

-   Create reusable authorization policies with attributes and conditions.

-   Enable administrators to combine and refine rules into custom authorization policies.

-   Support user assignment in the administration console.


DCL provides essential elements including rules, resources, conditions, attributes, schemas, and packages for enterprise-grade access control implementation. For more information, see [SAP Cloud Identity Services Developer Guide](https://shiny-adventure-8j72g8e.pages.github.io/).



## Process

Developers define the base policies with data control language \(DCL\) and upload them to the authorization management server. the Authorization Management Service forwards the base policies to the DCL compiler, which transforms DCL policies into an internal format \(DCN\) and assembles them by forming authorization bundles in a bundle storage in SAP Cloud Identity Services. The bundle gateway \(BGW\) retrieves the authorization bundles on request from the authorization decision controller \(ADC\), which uses the authorization bundles as input to perform the authorization checks. The administration console displays the bundled applications.

Administrators use the base policies to create custom policies with modified rules and assign them to users.

Users of the business application can log on and have access to the resources, which are allowed by the custom authorization policies.

