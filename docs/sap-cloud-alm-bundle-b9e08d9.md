<!-- loiob9e08d9e580f4f6cb13dbc4bd65025cc -->

# SAP Cloud ALM Bundle

SAP Cloud ALM bundles with SAP Cloud Identity Services – Identity Authentication.



<a name="loiob9e08d9e580f4f6cb13dbc4bd65025cc__section_dth_dx3_d2c"/>

## Prerequisites

You have an S-user with the role *Edit Cloud Data* on [SAP for Me](https://me.sap.com/home) in order to request SAP Cloud ALM.



<a name="loiob9e08d9e580f4f6cb13dbc4bd65025cc__section_gcd_2hj_d2c"/>

## How to Obtain

SAP Cloud ALM helps you to implement and operate intelligent cloud and hybrid business solutions. SAP Cloud ALM is included in your **cloud** subscription containing Enterprise Support, cloud edition and in SAP Enterprise Support. You can request SAP Cloud ALM on [SAP for Me](https://me.sap.com/home) for yourself or for all entitled customers for whom you have sufficient permissions. If you don't have an existing productive SAP Cloud Identity Services tenant, this will automatically trigger its creation. If you already have a productive tenant, it will be reused, except for the cases in which it cannot be used due to some restrictions and legal requirements. For more information, see [Requesting SAP Cloud ALM](https://help.sap.com/docs/cloud-alm/setup-administration/provisioning) and [Get Your Tenant](get-your-tenant-460766b.md).

> ### Note:  
> The user who requested SAP Cloud ALM receives permissions that are required for administrative tasks in the SAP BTP cockpit and in SAP Cloud ALM. Additionally, if the SAP Cloud Identity Services tenant is newly created this user is added as administrator of this tenant. If the tenant is reused, the user is added as a regular user. In case a user with matching email address already exists in the SAP Cloud Identity Services tenant, no additional user is created. In that case no activation email is sent from SAP Cloud Identity Services.

When the provisioning of SAP Cloud ALM is complete, the requesting user receives emails containing sign in information, configuration guidance, and links to support resources.



<a name="loiob9e08d9e580f4f6cb13dbc4bd65025cc__section_ilf_nhj_d2c"/>

## How to Use

This bundle tenant is provisioned to your organization in a newly created SAP BTP customer-managed subaccount. An OIDC trust is preconfigured between your Identity Authentication tenant and your SAP BTP multi-environment subaccount with enabled Cloud Foundry environment. Identity Authentication is set as trusted identity provider. This means that the way business users are signing in to SAP Cloud ALM is based on the configuration in the Identity Authentication.

You receive also the following attributes preconfigured:

-   The home URL of SAP Cloud ALM is configured. For more information, see [Configure an Application's Home URL](Operation-Guide/configure-an-application-s-home-url-be6d6f2.md).

-   The `e-mail` is configured as `Name ID` attribute in the settings of your identity provider. For more information, see [Configure the Subject Name Identifier Sent to the Application](Operation-Guide/configure-the-subject-name-identifier-sent-to-the-application-1d020e3.md).

After the provisioning of SAP Cloud ALM is complete, a few setup steps are required so that it can be used productively. For more information, see [Required Setup for SAP Cloud ALM](https://help.sap.com/docs/cloud-alm/setup-administration/required-setup). To give further users access to SAP Cloud ALM, see [Onboard Users in the Identity Authentication Service](https://help.sap.com/docs/cloud-alm/setup-administration/user-onboarding).

**Related Information**  


[SAP Cloud ALM](https://help.sap.com/docs/CloudALM?locale=en-US&state=PRODUCTION&version=latest)

[Monitoring with SAP Cloud ALM](Monitoring-and-Reporting/monitoring-with-sap-cloud-alm-bc835e5.md "SAP Cloud Identity Services are integrated with SAP Cloud ALM, which is a cloud-based application lifecycle management offering that enables you to implement, operate, and monitor your cloud solutions.")

