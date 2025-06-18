<!-- loio313f5456f3ab41ca925d555cda748f39 -->

# Integrating the Service with SAP Web IDE Full-Stack

You can use Identity Authentication as identity provider for SAP Web IDE Full-Stack.



## Prerequisites

-   You have a subaccount for SAP BTP.

    For more information, see [Getting a Paid Enterprise Global Account](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/82f9ff522f754e26ae89e0cd7ec7aa11.html).

-   You have an Identity Authentication tenant. For more information about how to get Identity Authentication, see [SAP BTP Pricing and Packaging Options](http://hcp.sap.com/pricing.html), or contact your SAP sales representative.

-   You have registered the Identity Authentication as a trusted identity provider for your SAP BTP account. See [Identity Authentication Tenant as an Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d3df5b457d0c43fca117da0dc14e2f0d.html).

-   You have set the trust with SAP BTP. For more details, see [Configure Trust](../Operation-Guide/configure-trust-f96e4c5.md).
-   You have switched off the *Reload Parent Page* option for SAP Web IDE Full-Stack in the administration console for SAP Cloud Identity Services. For more information, see [Enable or Disable Reload Parent Page Option](../Operation-Guide/enable-or-disable-reload-parent-page-option-0c0e9d2.md).

-   You have added your SAP Web IDE Full-Stack host to the list of the trusted domains in the administration console for SAP Cloud Identity Services. For more information, see [Configure Trusted Domains](../Operation-Guide/configure-trusted-domains-08fa1fe.md).

-   You have checked the **User ID** of the users that will be able to access SAP Web IDE Full-Stack. The **User ID** is a six-digit number preceded by the letter **P**. For more information about how to check the **User ID**, see [List and Edit User Details](../Operation-Guide/list-and-edit-user-details-045cb01.md).




## Context

> ### Note:  
> The content in this section is only relevant for SAP BTP, Neo environment.

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.

The integration between SAP Web IDE Full-Stack and Identity Authentication enables users to access SAP Web IDE Full-Stack with their Identity Authentication credentials.

SAP Web IDE Full-Stack access is protected by permissions. To grant a user the permission to access a protected resource, you can assign one of the predefined roles to such a permission. The following predefined roles are available:

-   ***DiDeveloper*** - To develop with SAP Web IDE Full-Stack, the DiDeveloper role needs to be assigned.

-   ***DiAdministrator*** - To be able to manage user data, a user has to be assigned to the DiAdministrator role.

-   ***DiScpGitAdministrator***- To be able to manage Git repositories, a user has to be assigned to the DiScpGitAdministrator role.


> ### Remember:  
> You should use the ***DiDeveloper*** or ***DiAdministrator*** role to enable users to access SAP Web IDE Full-Stack with their Identity Authentication credentials. For more information, see [Assign DiDeveloper or DiAdministrator Roles](integrating-the-service-with-sap-web-ide-full-stack-313f545.md#loioa0b0ae9fea034ff5823bc0a5b0520cd4).

**Related Information**  


[Integrating the Service with SAP Business Technology Platform, Neo Environment](integrating-the-service-with-sap-business-technology-platform-neo-environment-fe84459.md#loiofe84459e688c43698591d3b9e1aac828 "SAP BTP acts as a service provider, and Identity Authentication acts as an identity provider in this setup.")

[Integrating the Service with the Identity Service of SAP BTP](integrating-the-service-with-the-identity-service-of-sap-btp-d5cd80c.md "The Identity service of SAP BTP enables you to delegate authentication to the Identity Authentication service. The Identity service automates the creation of OpenID Connect (OIDC) applications for the Identity Authentication service for each application the Identity service registers.")

[Integrating the Service with SAP Document Center](integrating-the-service-with-sap-document-center-397683c.md#loio397683cff69d44c5bb2b38c76714c6ca "You can use Identity Authentication as identity provider for SAP Document Center.")

[Integrating the Service with SAP Identity Management 8.0](integrating-the-service-with-sap-identity-management-8-0-f44f931.md "")

[Integrating the Service with SAP S/4HANA Cloud, SAP Integrated Business Planning and SAP Analytics Cloud](integrating-the-service-with-sap-s-4hana-cloud-sap-integrated-business-planning-and-sap-a-dd61aea.md "This integration document aims to provide information about single sign-on (SSO) options for SAP S/4HANA Cloud or SAP Integrated Business Planning and SAP Analytics Cloud, that use Identity Authentication as an authenticating or proxy identity provider.")

[Integrating the Service with Microsoft Entra ID](integrating-the-service-with-microsoft-entra-id-626b173.md "")

[Integrating the Service with SAP Task Center](integrating-the-service-with-sap-task-center-ab5e90e.md)

[Hybrid Scenario: SAP Identity Management](hybrid-scenario-sap-identity-management-6fa419a.md "You can execute hybrid scenarios between provisioning systems from the Identity Provisioning UI and external systems that support SCIM 2.0 protocol.")

[Blogs](blogs-a89ca3e.md "Links to blogs and documents about integration scenarios with Identity Authentication.")

<a name="loioa0b0ae9fea034ff5823bc0a5b0520cd4"/>

<!-- loioa0b0ae9fea034ff5823bc0a5b0520cd4 -->

## Assign ***DiDeveloper*** or ***DiAdministrator*** Roles



## Context

If you want to use the ***DiDeveloper*** or ***DiAdministrator*** role together with Identity Authentication as an identity provider, complete the following steps:



## Procedure

1.  Log on to SAP BTP cockpit with the cockpit administrator role. For more information, see [Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8d6e3a0fa4ab43e4a421d3ed08128afa).

2.  In the navigation area, choose *Services* \> *SAP Web IDE Full-Stack tile*.

    > ### Note:  
    > If not enabled, choose *Enable*.

3.  Choose *Configure Service* under *Take Action*.

4.  On the *Configure Service - Roles* tab, under *New Role*, select either ***DiDeveloper*** or ***DiAdministrator*** from the list of predefined roles.

5.  Choose *Assign* from the *Individual User* section.

6.  Enter the **User ID** \(the **P number\)** of the user in question and choose *Assign*.

    > ### Note:  
    > For more information how to check the *User ID*, see [List and Edit User Details](../Operation-Guide/list-and-edit-user-details-045cb01.md). The *User ID* is a six-digit number preceded by the letter **P**.




## Results

The assigned users can log on to SAP Web IDE Full-Stack with their credentials for Identity Authentication \(email and password\).

<a name="loio45ef99026e2f48779e9510be0e47f37d"/>

<!-- loio45ef99026e2f48779e9510be0e47f37d -->

## Show User's Name on SAP Web IDE Full-Stack Home Page



## Context

When you use Identity Authentication as a trusted identity provider for SAP Web IDE Full-Stack you can configure the application to display the first name of the user that is logged on in the **menu bar** and the welcome screen.

For this scenario, you have to configure the user attribute `First Name` in Identity Authentication to be sent to SAP Web IDE Full-Stack in the assertion attribute. You also have to configure the First Name user attribute mapping for Identity Authentication in the SAP BTP cockpit.

<a name="task_wml_bfv_tv"/>

<!-- task\_wml\_bfv\_tv -->

### Configure `First Name` User Attribute in Identity Authentication



<a name="task_wml_bfv_tv__steps_cbt_3fv_tv"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose your SAP Web IDE Full-Stack application from the list.

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *Attributes*.

6.  Configure the `First Name` attribute.

7.  Save your configuration.

    If the operation is successful, you receive the message ***Attributes updated***.


<a name="task_ky3_dfv_tv"/>

<!-- task\_ky3\_dfv\_tv -->

### Configure Mapping in SAP BTP



<a name="task_ky3_dfv_tv__steps_lfn_fyh_5v"/>

## Procedure

1.  In your Web browser, open the SAP BTP cockpit using the following URLs:

    -   Europe: [https://account.hana.ondemand.com/cockpit](https://account.hana.ondemand.com/cockpit)

    -   United States: [https://account.us1.hana.ondemand.com/cockpit](https://account.us1.hana.ondemand.com/cockpit)
    -   Australia: [https://account.ap1.hana.ondemand.com/cockpit](https://account.ap1.hana.ondemand.com/cockpit)

2.  Select the customer account and choose *Trust* in the navigation bar.

3.  Choose the *Application Identity Provider* subtab, and then choose the identity provider that SAP Web IDE Full-Stack uses for authentication.

4.  Choose *Attributes* \> *Add Assertion-Based Attribute* \> **.

5.  Enter the fields as follows:


    <table>
    <tr>
    <th valign="top">

    Assertion Attribute
    
    </th>
    <th valign="top">

    Principal Attribute
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    first\_name
    
    </td>
    <td valign="top">
    
    firstname
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > The *Assertion Attribute* field is for the attribute that comes from the SAML Assertion.
    > 
    > The *Principal Attribute* field is the user attribute that the users will have at SAP BTP.

6.  Save your changes.




## Results

Once the user has been successfully authenticated to SAP Web IDE Full-Stack, his or her name will appear in *Menu bar* on the right.

![](images/WebIdeMenuBar_3ce3ec4.png)

