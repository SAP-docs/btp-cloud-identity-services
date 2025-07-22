<!-- loio22928a2d8b7e42cc887398ca72019821 -->

# Developing Authorizations

Developers define, update, and create authorizations. These are the basis for Authorization Management, which administrators can use to grant users access to resources.

Authorization Management enables Identity Authentication administrators to use instance-based authorizations in the form of authorization policies in multiple environments. They assign authorization policies to users and thus manage user access to resources.

Developers define and deploy an application that supports authorization policies in Identity Authentication. They include functional checks, instance-base authorizations, and user attributes. Authorization Management is automatically enabled for a new tenant and can be used as soon as an application requests it. Service instances and bindings are added automatically. The authorization policies are available in the Identity Authentication administration console.

For more information, see [Adding Authentication and Authorization](https://help.sap.com/docs/authorization-and-trust-management-service/authorization-and-trust-management/adding-authentication-and-authorization) and [Configuring Authorization Policies](../Operation-Guide/configuring-authorization-policies-982ac5f.md).



<a name="loio22928a2d8b7e42cc887398ca72019821__section_t2p_2wb_dzb"/>

## Developing Authorization Policies

Developers use the Cloud Application Programming model for authorization policies. We've provided a sample application, which you can use for the creation of authorization policies.

-   [Authorization and Access Control](https://cap.cloud.sap/docs/guides/authorization) with the Cloud Application Programming model

-   [Sample apps in GitHub](https://github.com/SAP-samples/cloud-cap-samples)




The Data Control Language \(DCL\) enables developers to define authorization policies and rules using an SQL-like syntax in SAP Cloud Identity Services. This declarative language allows them to specify access controls for data and resources through structured authorization policy definitions.

-   Define authorization policies using SQL-like syntax.

-   Create reusable authorization policies with attributes and conditions.

-   Enable administrators to combine and refine rules into custom authorization policies.

-   Support user assignment in the administration console.


DCL provides essential elements including rules, resources, conditions, attributes, schemas, and packages for enterprise-grade access control implementation. For more information, see  <?sap-ot O2O class="- topic/xref " href="38baa251132c4b088f41261fb3158fb3.xml" text="" desc="" xtrc="xref:5" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/22928a2d8b7e42cc887398ca72019821.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

