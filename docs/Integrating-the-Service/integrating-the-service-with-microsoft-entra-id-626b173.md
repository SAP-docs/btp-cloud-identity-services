<!-- loio626b17331b4d4014b8790d3aea70b240 -->

# Integrating the Service with Microsoft Entra ID

Identity Authentication is part of the application gallery of Microsoft Entra ID \(formerly known as Microsoft Azure Active Directory or Azure AD\) under the name Identity Authentication.

This integration aims to provide single sign-on \(SSO\) between applications using Microsoft Entra ID as authenticating identity provider and applications using Identity Authentication as proxy identity provider.



## Prerequisites

-   You have a valid Microsoft Entra ID subscription.
-   You have a subscription for Identity Authentication. For more information how to get Identity Authentication, see [Initial Setup](../initial-setup-31af7da.md).



## Overview

In this scenario Identity Authentication acts as a proxy identity provider and Microsoft Entra ID as the main authentication authority for the applications. The authentication requests sent to Identity Authentication are redirected to Microsoft Entra ID. User management and authentication is done on Microsoft Entra ID side.

> ### Note:  
> Users who are in the Microsoft Entra ID user store can use the single sign-on \(SSO\) functionality.
> 
> Users who are provisioned to Identity Authentication, but not to Microsoft Entra ID, are not able to log on.

> ### Tip:  
> Identity Authentication supports the *Identity Federation* option. This option allows the application to check if the users authenticated by the corporate identity provider exist in the user store of Identity Authentication. In the default setting, the *Identity Federation* option is disabled. If *Identity Federation* is enabled, only the users that are imported in Identity Authentication are able to access the application. For more information about how to enable or disable *Identity Federation* with Identity Authentication, see **Enable Identity Federation with Identity Authentication** in [Configure Identity Federation](../Operation-Guide/configure-identity-federation-c029bbb.md).

For this scenario, the configurations are made in Microsoft Entra ID classic portal and in the administration console for SAP Cloud Identity Services.

**Related Information**  


[Integrating the Service with SAP Business Technology Platform, Neo Environment](integrating-the-service-with-sap-business-technology-platform-neo-environment-fe84459.md#loiofe84459e688c43698591d3b9e1aac828 "SAP BTP acts as a service provider, and Identity Authentication acts as an identity provider in this setup.")

[Integrating the Service with the Identity Service of SAP BTP](integrating-the-service-with-the-identity-service-of-sap-btp-d5cd80c.md "The Identity service of SAP BTP enables you to delegate authentication and authorization to Cloud Identity Services. When you register and application, the Identity service automatically creates an OpenID Connect (OIDC) application in Cloud Identity Services.")

[Integrating the Service with SAP Web IDE Full-Stack](integrating-the-service-with-sap-web-ide-full-stack-313f545.md#loio313f5456f3ab41ca925d555cda748f39 "You can use Identity Authentication as identity provider for SAP Web IDE Full-Stack.")

[Integrating the Service with SAP Document Center](integrating-the-service-with-sap-document-center-397683c.md#loio397683cff69d44c5bb2b38c76714c6ca "You can use Identity Authentication as identity provider for SAP Document Center.")

[Integrating the Service with SAP Identity Management 8.0](integrating-the-service-with-sap-identity-management-8-0-f44f931.md "")

[Integrating the Service with SAP S/4HANA Cloud, SAP Integrated Business Planning and SAP Analytics Cloud](integrating-the-service-with-sap-s-4hana-cloud-sap-integrated-business-planning-and-sap-a-dd61aea.md "This integration document aims to provide information about single sign-on (SSO) options for SAP S/4HANA Cloud or SAP Integrated Business Planning and SAP Analytics Cloud, that use Identity Authentication as an authenticating or proxy identity provider.")

[Integrating the Service with SAP Task Center](integrating-the-service-with-sap-task-center-ab5e90e.md)

[Hybrid Scenario: SAP Identity Management](hybrid-scenario-sap-identity-management-6fa419a.md "You can execute hybrid scenarios between provisioning systems from the Identity Provisioning UI and external systems that support SCIM 2.0 protocol.")

[Blogs](blogs-a89ca3e.md "Links to blogs and documents about integration scenarios with Identity Authentication.")

