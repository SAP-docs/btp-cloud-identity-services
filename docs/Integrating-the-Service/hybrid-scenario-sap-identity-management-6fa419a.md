<!-- loio6fa419a1901a464ea7dd214bcf476468 -->

# Hybrid Scenario: SAP Identity Management

You can execute hybrid scenarios between provisioning systems from the Identity Provisioning UI and external systems that support SCIM 2.0 protocol.



<a name="loio6fa419a1901a464ea7dd214bcf476468__section_l14_ydh_h1b"/>

## Prerequisites

-   You have an Identity Provisioning service standalone or bundle tenant.
-   You have the user credentials to connect SAP Identity Management to SAP Cloud Identity Services - Identity Provisioning. Your user has read and write permissions.

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loio6fa419a1901a464ea7dd214bcf476468__section_yl1_12h_h1b"/>

## Context

A proxy system is a special connector type you can use for *hybrid* scenarios. It exposes any Identity Provisioning supported backend system as a SCIM 2.0 service provider, which can be consumed by any [SCIM 2.0](https://tools.ietf.org/html/rfc7644) compatible client application, without making a direct connection between them.

The Identity Provisioning proxy system will initially provision entities to an external consumer system and then will start executing CRUD operations backwards, whenever the external system requests such. For more information, see [Proxy Systems](../proxy-systems-b10d68a.md).

The scenario below is exemplary. It involves a proxy connector you have added in the Identity Provisioning UI, and **SAP Identity Management** as an external leading identity management system.



<a name="loio6fa419a1901a464ea7dd214bcf476468__section_kyt_d2h_h1b"/>

## Procedure

1.  Sign in to the administration console of SAP Cloud Identity Services
2.  Open your subaccount in SAP BTP cockpit \(valid for OAuth authentication to the Identity Provisioning proxy system\).

    > ### Note:  
    > If you have a bundle tenant, then in the cockpit → *Neo* → *Overview*, you can see the Global account, which SAP provides for your bundle in the corresponding Identity Provisioning region. Then, in the global account, you can see your subaccount, where the Identity Provisioning is enabled as a service for the bundle. The display name of the subaccount starts with **SAP\_BUNDLE**.

3.  Create a technical user with the necessary authorizations. It will later be used by the external leading identity management system to connect to Identity Provisioning.

    1.  In SAP Cloud Identity Services admin console, navigate to *Users & Authorizations* \> *Administrators*.

    2.  Add an administrator user of type **System** and configure the basic authentication method for this user.

        If you already have a technical user, skip this step.

    3.  Save your changes.

    4.  Select your administrator user of type **System** and enable the *Access Proxy System API* permission.

    5.  Save your changes.


    1.  Go to *Security* \> *OAuth* \> *Clients*.
    2.  Choose *Register New Client*.
    3.  From the *Subscription* combo box, select **<provider\_subaccount\>/ipsproxy**.
    4.  From the *Authorization Grant* combo box, select **Client Credentials**.
    5.  In the *Secret* field, enter a password \(client secret\) and remember it. You will need it later, for the repository configuration in SAP Identity Management.
    6.  Copy/paste and save \(in a notepad\) the generated *Client ID*. You will need it later, too.
    7.  Assign role IPS\_PROXY\_USER to the OAuth client:
        1.  From the left-side navigation, choose *Subscriptions*.
        2.  Under the *Java Applications* section, choose *ipsproxy*.
        3.  From the left-side navigation, choose *Roles*.
        4.  Assign role **IPS\_PROXY\_USER** to the newly created OAuth client. Choose *Assign* and enter **oauth\_client\_<client\_ID\>**, where <client\_ID\> is the one from step **2.f**.


4.  Access Identity Provisioning. The access URL depends on the productive type of your Identity Provisioning. See: [Access Admin Console](../access-admin-console-2609e81.md)
    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

5.  Add a proxy system. You can choose among a list of systems available for hybrid scenarios with SAP Identity Management. To find the system you need, see [Proxy Systems](../proxy-systems-b10d68a.md) → **More Information**.
6.  Open the *Properties* tab of the selected proxy system to configure its connection settings.
7.  If necessary, modify the default *Read* and *Write* transformation mapping rules to reflect the current setup of entities in your proxy system.
8.  Save your changes.



<a name="loio6fa419a1901a464ea7dd214bcf476468__section_epk_rfc_31b"/>

## Next Steps

1.  Now, you can export the newly created proxy system. To do that, choose *Export* → *CSV format*.
2.  Then, go to SAP Identity Management to register or import a SCIM repository.

    > ### Note:  
    > If you import the *.csv* file, you will have all the fields automatically filled-in. However:
    > 
    > -   You need to manually enter your client ID and secret \(AUTH\_USER and AUTH\_PASSWORD\).
    > -   For the SCIM\_ASSIGNMENT\_METHOD constant, leave its default value: **PATCH**.
    > 
    >     However, check explicitly in the documentation of the relevant proxy system type whether you should leave the default value **PATCH**, or change it to **PUT**. Find your system under section [Proxy Systems](../proxy-systems-b10d68a.md).

3.  Then start an *Initial load* job. After the initial load is done, you can create new users or update existing ones in SAP Identity Management.



<a name="loio6fa419a1901a464ea7dd214bcf476468__section_umt_dfk_fhb"/>

## Future Identity Lifecycle

What happens when you make new changes \(create/update/delete an entity\)?

-   If a new change is made in SAP Identity Management, a new job is automatically triggered. It applies the changes in the external back-end system so that both systems become up-to-date and synchronized.
-   If a new change is made in the back-end system, you have to start a new *Initial load* job so that the changes can apply in SAP Identity Management.



<a name="loio6fa419a1901a464ea7dd214bcf476468__section_p5k_dzv_cfb"/>

## Related Information

SAP Identity Management: [Setting Up Hybrid Integration with a Cloud System](https://help.sap.com/viewer/4773a9ae1296411a9d5c24873a8d418c/8.0/en-US/9481ea8567e74be2af2ed31de458a329.html)

SAP Community Blog: [Hybrid Scenarios with Identity Provisioning Proxy](https://blogs.sap.com/2019/03/24/hybrid-scenarios-with-identity-provisioning-proxy/)

**Related Information**  


[Integrating the Service with SAP Business Technology Platform, Neo Environment](integrating-the-service-with-sap-business-technology-platform-neo-environment-fe84459.md#loiofe84459e688c43698591d3b9e1aac828 "SAP BTP acts as a service provider, and Identity Authentication acts as an identity provider in this setup.")

[Integrating the Service with the Identity Service of SAP BTP](integrating-the-service-with-the-identity-service-of-sap-btp-d5cd80c.md "The Identity service of SAP BTP enables you to delegate authentication and authorization to Cloud Identity Services. When you register and application, the Identity service automatically creates an OpenID Connect (OIDC) application in Cloud Identity Services.")

[Integrating the Service with SAP Web IDE Full-Stack](integrating-the-service-with-sap-web-ide-full-stack-313f545.md#loio313f5456f3ab41ca925d555cda748f39 "You can use Identity Authentication as identity provider for SAP Web IDE Full-Stack.")

[Integrating the Service with SAP Document Center](integrating-the-service-with-sap-document-center-397683c.md#loio397683cff69d44c5bb2b38c76714c6ca "You can use Identity Authentication as identity provider for SAP Document Center.")

[Integrating the Service with SAP Identity Management 8.0](integrating-the-service-with-sap-identity-management-8-0-f44f931.md "")

[Integrating the Service with SAP S/4HANA Cloud, SAP Integrated Business Planning and SAP Analytics Cloud](integrating-the-service-with-sap-s-4hana-cloud-sap-integrated-business-planning-and-sap-a-dd61aea.md "This integration document aims to provide information about single sign-on (SSO) options for SAP S/4HANA Cloud or SAP Integrated Business Planning and SAP Analytics Cloud, that use Identity Authentication as an authenticating or proxy identity provider.")

[Integrating the Service with Microsoft Entra ID](integrating-the-service-with-microsoft-entra-id-626b173.md "")

[Integrating the Service with SAP Task Center](integrating-the-service-with-sap-task-center-ab5e90e.md)

[Blogs](blogs-a89ca3e.md "Links to blogs and documents about integration scenarios with Identity Authentication.")

