<!-- loiode21efe39e1442618388784891497067 -->

# What's New for Cloud Identity Services



This page lists the release notes of Cloud Identity Services for 2025. To see the release notes for the previous year, visit [2024 What's New for Cloud Identity Services \(Archive\)](2024-what-s-new-for-cloud-identity-services-archive-a858345.md). 

To get notifications, subscribe for the Cloud Identity Services selection in the [What's New Viewer for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Cloud%20Identity%20Services&locale=en-US&version=Cloud).





****


<table>
<tr>
<th valign="top">

Technical Component

</th>
<th valign="top">

Environment

</th>
<th valign="top">

Title

</th>
<th valign="top">

Description

</th>
<th valign="top">

Action

</th>
<th valign="top">

Lifecycle

</th>
<th valign="top">

Type

</th>
<th valign="top">

Line of Business

</th>
<th valign="top">

Modular Business Process

</th>
<th valign="top">

Product

</th>
<th valign="top">

Latest Revision

</th>
<th valign="top">

Valid as Of

</th>
<th valign="top">

Version

</th>
<th valign="top">

Scope

</th>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-31

</td>
<td valign="top">

2025-07-31

</td>
<td valign="top">

28127

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-29

</td>
<td valign="top">

2025-07-29

</td>
<td valign="top">

28120

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP Ariba Central Invoice Managementsupports userUUID

</td>
<td valign="top">

SAP Ariba Central Invoice Management now supports provisioning of users with the **userUUID** attribute. The default read, write and proxy read and write transformations are enhanced to handle the universally unique identifier.

For more information, see [SAP Ariba Central Invoice Management](sap-ariba-central-invoice-management-f540d52.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-29

</td>
<td valign="top">

2025-07-29

</td>
<td valign="top">

28120

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Meta attribute mapping reordered

</td>
<td valign="top">

The `meta` attribute mapping is reordered to come before the `meta.location` attribute mapping in the proxy read transformations of Cloud Foundry UAA Server and SAP BTP XS Advanced UAA \(Cloud Foundry\). This ensures that the meta.location attribute is set correctly and is not overwritten.

Additionally, the `urn:ietf:params:scim:schemas:extension:sap:2.0:Group` extension schema is added for the group entity in the proxy read transformations of SAP BTP XS Advanced UAA \(Cloud Foundry\).

For more information, see:

-   [Cloud Foundry UAA Server](cloud-foundry-uaa-server-5e4e03c.md)
-   [SAP BTP XS Advanced UAA \(Cloud Foundry\)](sap-btp-xs-advanced-uaa-cloud-foundry-fef74f6.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-29

</td>
<td valign="top">

2025-07-29

</td>
<td valign="top">

28120

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regional Availability

</td>
<td valign="top">

Cloud Identity Services has migrated the data \(DC\) center in Saudi Arabia \(Riyadh, Dammam\) to the Google Cloud infrastructure from the SAP infrastructure.

Action:

You must add the following IPs to your allowed IP list:

-   LB IP - 34.166.140.252, 34.166.98.190
-   NAT IP - 34.166.143.220/32, 34.166.36.253/32

The following IPs are no longer in use:

-   LB IP - 130.214.222.99, 130.214.248.94
-   NAT IP - 130.214.222.32/27, 130.214.248.32/27

See [Regional Availability](regional-availability-be600ca.md).

</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-22

</td>
<td valign="top">

2025-07-22

</td>
<td valign="top">

28063

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

28063

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for SAP extension schema for groups

</td>
<td valign="top">

The default transformations of the following connectors support attributes from the SAP extension schema for groups, including application ID, type, and supported operations.

For more information, see

-   [SAP SuccessFactors Employee Central Payroll](sap-successfactors-employee-central-payroll-94d8979.md)
-   [Cloud Foundry UAA Server](cloud-foundry-uaa-server-77e07a7.md)
-   [Procurement Data Warehouse](procurement-data-warehouse-13f60ee.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

28063

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Change in provisioning job behavior

</td>
<td valign="top">

Provisioning jobs that skip create and delete operations and only update entities will no longer fail if those entities - previously provisioned from the source to the target system, are deleted in the target. By design, Identity Provisioning runs update jobs only for entities that exist in the target system.

Instead of marking these entities as failed, Identity Provisioning now classifies them as skipped. Therefore, the job status is Successful rather than Finished with Error.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

28063

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regional Availability

</td>
<td valign="top">

Cloud Identity Services is available with a new data center for the Google Cloud infrastructure in Israel. The data center is located in Tel Aviv.

Action: You must add the following IPs to your allowed IP list:

-   LB IPs - `34.165.59.107, 34.165.82.240` 
-   NAT IPs - `34.165.48.136/32, 34.165.90.82/32, 34.165.0.183/32`

See [Regional Availability](regional-availability-be600ca.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

28063

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-09

</td>
<td valign="top">

2025-07-09

</td>
<td valign="top">

28039

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

CAPTCHA Protection

</td>
<td valign="top">

Tenant administrator can enable CAPTCHA protection for the phone verification pages of the application. See [Enable Google reCAPTCHA for Application Forms](Operation-Guide/enable-google-recaptcha-for-application-forms-3db7c1e.md) and [Enable MTCaptcha for Application Forms](Operation-Guide/enable-mtcaptcha-for-application-forms-6e2f44a.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-09

</td>
<td valign="top">

2025-07-09

</td>
<td valign="top">

28039

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-07-01

</td>
<td valign="top">

2025-07-01

</td>
<td valign="top">

28019

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for SAP extension schema for groups

</td>
<td valign="top">

The default transformations of the following connectors support attributes from the SAP extension schema for groups, including application ID, type, and supported operations.

For more information, see

-   [SAP Marketing Cloud](sap-marketing-cloud-53721c8.md)
-   [SAP Market Communication for Utilities](sap-market-communication-for-utilities-47c7ec5.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2025-07-01

</td>
<td valign="top">

2025-07-01

</td>
<td valign="top">

28019

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-25

</td>
<td valign="top">

2025-06-25

</td>
<td valign="top">

28001

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Override Conditional Authentication with URL Parameter

</td>
<td valign="top">

We have added an option to the `idp` parameter for application which allows logon with OpenID Connect \(OIDC\). Use the value **local** to override the conditional authentication configuration and log on with Identity Authentication instead.

For more information, see [Configure IdP-Initiated SSO](Operation-Guide/configure-idp-initiated-sso-5d59caa.md) or [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow](Operation-Guide/configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-25

</td>
<td valign="top">

2025-06-25

</td>
<td valign="top">

28001

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-23

</td>
<td valign="top">

2025-06-23

</td>
<td valign="top">

27990

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Signing Certificates

</td>
<td valign="top">

As of June 23, 2025 the version of the newly created signing certificates is v3. See [Tenant SAML 2.0 Configurations](Operation-Guide/tenant-saml-2-0-configurations-e81a19b.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-23

</td>
<td valign="top">

2025-06-23

</td>
<td valign="top">

27990

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

27972

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Identity Federation

</td>
<td valign="top">

We have extended the identity federation for an application and on tenant level. Now, you can restrict the logon to users with certain email domains. See [Configure Identity Federation for Applications](Operation-Guide/configure-identity-federation-for-applications-1e8e34e.md) and [Configure Identity Federation](Operation-Guide/configure-identity-federation-c029bbb.md).

</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

 

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

27972

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Attributes

</td>
<td valign="top">

Cloud Identity Services now supports a new local user attribute - `License Groups` to list the license groups that give access to the premium Joule scenarios. See [Configuring User Attributes from the Identity Directory](Operation-Guide/configuring-user-attributes-from-the-identity-directory-d361407.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

27972

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP Revenue Growth Management connector

</td>
<td valign="top">

Identity Provisioning supports the SAP Revenue Growth Management connector. You can configure it as source, target, and proxy system for your provisioning scenarios.

For more information, see

-   [SAP Revenue Growth Management \(Source\)](sap-revenue-growth-management-1d02d60.md)
-   [SAP Revenue Growth Management \(Target\)](sap-revenue-growth-management-85ea2ea.md)
-   [SAP Revenue Growth Management \(Proxy\)](sap-revenue-growth-management-69970c8.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

27972

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Job Execution Outcome introduced

</td>
<td valign="top">

The *Job Execution Outcome* is now displayed on the *Job Execution Details* screen and included in the job notifications. It appears when delta-read jobs and jobs that fail to read entities from the source system affect the deletion of entities in the target system.

For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md)

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

27972

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System reset confirmation message extended

</td>
<td valign="top">

The UI message prompting confirmation for system reset has been expanded to include typical cases when a reset is necessary.

For more information, see [Reset Identity Provisioning System](Operation-Guide/reset-identity-provisioning-system-0bc1e53.md)

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

27972

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for SAP extension schema for groups

</td>
<td valign="top">

The default transformations of the following connectors support attributes from the SAP extension schema for groups, including application ID, type, and supported operations.

For more information, see

-   [SAP Integrated Business Planning for Supply Chain](sap-integrated-business-planning-for-supply-chain-65a847e.md)
-   [SAP Intelligent Agriculture](sap-intelligent-agriculture-9e47e03.md)
-   [SAP Jam Collaboration](sap-jam-collaboration-eeeb246.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

27972

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for extension enterprise schema for users

</td>
<td valign="top">

The extension enterprise schema has been defined in the default write and proxy write transformations of SAP Concur.

For more information, see [SAP Concur](sap-concur-032fd80.md)

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

2025-06-18

</td>
<td valign="top">

27972

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

27915

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Change in provisioning job behavior \(Effective July 15, 2025\)

</td>
<td valign="top">

As of July 15, 2025, provisioning jobs that skip create and delete operations and only update entities will no longer fail if those entities - previously provisioned from the source to the target system - are deleted in the target. By design, Identity Provisioning runs update jobs only for entities that exist in the target system.

Instead of marking these entities as failed, Identity Provisioning will now classify them as skipped. Therefore, the job status will be Successful rather than Finished with Error.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

2025-07-15

</td>
<td valign="top">

27915

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Applications

</td>
<td valign="top">

We have extended the application search in the administration console. Now you can filter the list items in the search field by typing the name, display name, application ID, organization ID, and client ID.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

27915

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP Analytics Cloud and SCIM System - new properties

</td>
<td valign="top">

New system-specific properties are introduced for SAP Analytics Cloud and SCIM System to hold the path appended to the URL to retrieve the CSRF token.

Previously, this path could be set for these systems via the property `csrf.token.path.`

See [List of Properties](list-of-properties-d6f3577.md) → `sac.csrf.token.path` and `scim.csrf.token.path`.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

27915

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Changed behavior of logging and tracing properties

</td>
<td valign="top">

The behavior of the properties that enable logging and tracing for personal and sensitive data \(`ips.trace.*.entity.content`\) is changed.

Setting the property to *true* is valid only for the next provisioning job execution. After the job has finished, Identity Provisioning sets the property automatically to *false*.

Previously, the value set for the tracing property remained valid until it was manually changed.

See [List of Properties](list-of-properties-d6f3577.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

27915

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

REST API

</td>
<td valign="top">

The `Identity Directory API` now supports new attribute `activationUrl` located in the user extension schema `urn:ietf:params:scim:schemas:extension:sap:2.0:User`. The `activationUrl` is a read-only attribute and it returns the activation link for the user account. It is returned only at the creation of the user. See [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/path/createUser).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

2025-06-04

</td>
<td valign="top">

27915

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

27861

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAML 2.0 Configuration

</td>
<td valign="top">

The *Name* field in the SAML 2.0 configuration page on application level has been changed to *Entity ID*. See [Configure SAML 2.0 Service Provider](Operation-Guide/configure-saml-2-0-service-provider-51f1f75.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

27861

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Password Management

</td>
<td valign="top">

You can configure the system to show a password expiration reminder at the sign-in page of the user. See [Enable Password Expiration Reminder](Operation-Guide/enable-password-expiration-reminder-a8de1be.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

27861

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Cloud Identity Services Documentation

</td>
<td valign="top">

As of May 21, 2025 the **Version** column of [What's New for Cloud Identity Services](what-s-new-for-cloud-identity-services-de21efe.md) contains the number of the version instead of the sprint number. All the information in the column has been updated.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

27861

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for SAP extension schema for groups

</td>
<td valign="top">

The default transformations of the following connectors support attributes from the SAP extension schema for groups, including application ID, type, and supported operations.

See:

-   [SAP Fieldglass](sap-fieldglass-58a6921.md)
-   [SAP Field Service Management](sap-field-service-management-19e91d6.md)
-   [SAP Enable Now](sap-enable-now-cee1e14.md)
-   [SAP Data Custodian](sap-data-custodian-acd7307.md)
-   [SAP CPQ](sap-cpq-209e23a.md)
-   [SAP HANA Cloud, SAP HANA Database](sap-hana-cloud-sap-hana-database-7c6fbdb.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

2025-05-21

</td>
<td valign="top">

27861

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP ODM User Schema Support

</td>
<td valign="top">

The default read and proxy read transformations in Identity Authentication and the Local Identity Directory support the `urn:ietf:params:scim:schemas:extension:sap.odm:2.0:User` schema. This custom SCIM schema extension is defined by SAP’s Organizational Data Model \(ODM\) and is used to enrich the standard SCIM User resource with SAP-specific attributes such as `workAssignment`, `jobDetails`, `plant`, and others.

See

-   [Identity Authentication](identity-authentication-e4e25f1.md)

-   [Local Identity Directory](local-identity-directory-8c7d05e.md)




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Download all deleted entities for a provisioning job

</td>
<td valign="top">

You can now download and view the details of all deleted entities by a provisioning job. To enable this, set the property `ips.trace.deleted.entity` to **true**.

For more information, see [Manage Provisioning Job Logs](Monitoring-and-Reporting/manage-provisioning-job-logs-041b5ff.md) and [List of Properties](list-of-properties-d6f3577.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Client Certificates

</td>
<td valign="top">

You can specify a unique DN pattern for single user authentication when configuring an X.509 client certificate. See [Configure X.509 Client Certificates for User Authentication](Operation-Guide/configure-x-509-client-certificates-for-user-authentication-52c7dcb.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

REST API

</td>
<td valign="top">

The `Identity Directory API` now supports new attribute `externalName` located in the group extension schema `urn:ietf:params:scim:schemas:extension:sap:2.0:Group`. The `externalName` attribute is unique within the application. See [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Application Authorizations

</td>
<td valign="top">

Tenant administrator now can create a restriction policy using the `applications.CREATE_APPLICATIONS` and `applications.MANAGE_APPLICATIONS` parameters. See [Configure Application Authorizations](Operation-Guide/configure-application-authorizations-01cff18.md) 

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Manage Corporate Identity Providers

</td>
<td valign="top">

Tenant administrator can manage corporate identity providers in Identity Authentication via API. It offers endpoints for CRUD operations \(GET, POST, PATCH, DELETE\) over the corporate identity providers. See [SAP Cloud Identity Services Corporate Identity Providers Directory](https://api.sap.com/api/SCI_IdentityProvider_Directory/overview).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Privacy Policy and Terms of Use

</td>
<td valign="top">

The Identity Directory API of SAP Cloud Identity Services now returns the `termsOfUse` and `privacyPolicy` parameters. See [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Application Protocol Type

</td>
<td valign="top">

The protocol type of the <code>Administration Console for Cloud Identity Services is now changed to the hybrid type <b><i>SAML 2.0 &amp; OpenID Connect</i></b> from the <b><i>SAML 2.0</i></b> type</code>. See [Applications](applications-404a11c.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud - new version 

</td>
<td valign="top">

A new connector version for SAP Sales Cloud and SAP Service Cloud is introduced. It is applicable for SAP Sales Cloud Version 2 and SAP Service Cloud Version 2 and supports certificate-based authentication, patch operations, delta read of entities, cursor-based pagination and more.

See

-   [SAP Sales Cloud and SAP Service Cloud \(Source\)](sap-sales-cloud-and-sap-service-cloud-8f3edc3.md)

-   [SAP Sales Cloud and SAP Service Cloud \(Target\)](sap-sales-cloud-and-sap-service-cloud-1a974bc.md)

-   [SAP Sales Cloud and SAP Service Cloud \(Proxy\)](sap-sales-cloud-and-sap-service-cloud-2f81c3b.md)




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP Build Work Zone, standard edition - schema support

</td>
<td valign="top">

The default transformations of SAP Build Work Zone, standard edition are extended to support the `urn:ietf:params:scim:schemas:extension:sap:2.0:User` and `urn:ietf:params:scim:schemas:extension:2.0:mapping` schema.

See [SAP Build Work Zone, standard edition](sap-build-work-zone-standard-edition-8d6586f.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for SAP extension schema for groups

</td>
<td valign="top">

The default transformations of the following connectors support attributes from the SAP extension schema for groups, including application ID, type, and supported operations.

See:

-   [SAP Central Business Configuration](sap-central-business-configuration-b572223.md)

-   [SAP Build Work Zone, advanced edition](sap-build-work-zone-advanced-edition-647c5b5.md)

-   [SAP BTP ABAP environment](sap-btp-abap-environment-bbab610.md)

-   [SAP Commerce Cloud](sap-commerce-cloud-7eb21e8.md)

-   [SAP Advanced Financial Closing](sap-advanced-financial-closing-beeeebf.md)




</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

2025-05-08

</td>
<td valign="top">

27806

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regional Availability

</td>
<td valign="top">

Cloud Identity Services has migrated the data \(DC\) center in China to Beijing in the Azure infrastructure from Shanghai in the SAP infrastructure.

Action:

You must add the following IPs to your allowed IP list:

-   LB IP - 40.162.206.196, 40.162.223.103
-   NAT IP - 40.162.31.41/32, 143.64.218.112/32

The following IPs are no longer in use:

-   LB IP - 121.91.104.198, 121.91.104.204
-   NAT IP - 121.91.104.32/27, 121.91.106.0/28, 121.91.108.0/28

See [Regional Availability](regional-availability-be600ca.md).

</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-04-16

</td>
<td valign="top">

2025-04-16

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Machine Translation

</td>
<td valign="top">

On-the-fly machine translation is now available in 39 languages for the Cloud Identity Services documentation. This means that you can generate translation of content instantly by selecting the respective language from the dropdown list.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for SAP extension schema for groups

</td>
<td valign="top">

The default transformations of Identity Authentication \(using SCIM API version 2\), SAP BTP Account Members \(Neo\) and SAP BTP XS Advanced UAA \(Cloud Foundry\) support attributes from the SAP extension schema for groups, including application ID, type, and supported operations.

See

-   [Identity Authentication](identity-authentication-e4e25f1.md)
-   [SAP BTP Account Members \(Neo\)](sap-btp-account-members-neo-a8035cd.md)
-   [SAP BTP XS Advanced UAA \(Cloud Foundry\)](sap-btp-xs-advanced-uaa-cloud-foundry-c135a52.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Identity Authentication \(using SCIM API version 2\) - changed behavior

</td>
<td valign="top">

Similar to the Local Identity Directory, you can now use Identity Authentication \(SCIM API version 2\) for reading and writing application-specific groups. Depending on the configured pair of provisioning systems, to ensure successful provisioning, you might need to manually define value mappings for the attribute `applicationId` in the source or the target system transformations.

For more information, see:

-   [Identity Authentication \(Source\)](identity-authentication-e4e25f1.md)
-   [Identity Authentication \(Target\)](identity-authentication-f217bd3.md)
-   [List of Properties](list-of-properties-d6f3577.md)→`ips.application.id`



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Registration and Upgrade Forms

</td>
<td valign="top">

You can now configure the `Department` user attribute to be displayed on application's registration and upgrade forms. See [Configure Registration and Upgrade Forms](Operation-Guide/configure-registration-and-upgrade-forms-93a9e18.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Provided APIs

</td>
<td valign="top">

The provided APIs for the `Administration Console` for Cloud Identity Services is now read-only.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regional Availability

</td>
<td valign="top">

Cloud Identity Services is available with a new data center \(DC\), United States \(Virginia\), for the AWS infrastructure in US \(North America East\) region.

The United States \(Colorado\) DC is no longer used.

Action:

You must add the following IPs to your allowed IP list:

-   LB IP - 3.92.131.87, 52.200.183.196, 35.168.205.166
-   NAT IP - 52.44.60.92/32, 54.211.101.173/32, 54.225.47.27/32

The following IPs are no longer in use:

-   LB IP - 130.214.207.198
-   NAT IP - 130.214.242.32/27

See [Regional Availability](regional-availability-be600ca.md).

</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-27

</td>
<td valign="top">

2025-03-27

</td>
<td valign="top">

27643

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

27643

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OAuth Client Authentication

</td>
<td valign="top">

The *Add JSON Web Token* UI has bee changed. Now you can manually configure the issuer or choose from OpenID Connect compliant corporate identity providers. See [Configure JWT for OAuth Client Authentication](Development/configure-jwt-for-oauth-client-authentication-1bdc729.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

27643

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Download all updated entities for a provisioning job

</td>
<td valign="top">

You can now download and view the details of all updated entities by a provisioning job. To enable this, set the properties `ips.trace.updated.entity` and `ips.trace.updated.entity.content` to *true*.

For more information, see [Manage Provisioning Job Logs](Monitoring-and-Reporting/manage-provisioning-job-logs-041b5ff.md) and [List of Properties](list-of-properties-d6f3577.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

27643

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Central store logs display source entity ID

</td>
<td valign="top">

The central store logs display the source entity ID, which represents the group ID in the Identity Directory.

For more information, see [Monitor Central Store Logs](Monitoring-and-Reporting/monitor-central-store-logs-9162898.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

27643

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP Ariba Applications - default transformations changes

</td>
<td valign="top">

The default transformations of SAP Ariba Applications are enhanced with the expression `preserveArrayWithSingleElement` set to *true*. The transformation mappings for the attribute `plant` are excluded from the default write and proxy write transformations, since the attribute's value cannot be created with POST and PUT or PATCH request anymore.

For more information, see:

-   [SAP Ariba Applications \(Source\)](sap-ariba-applications-0ef1091.md)
-   [SAP Ariba Applications \(Target\)](sap-ariba-applications-47c8903.md)
-   [SAP Ariba Applications \(Proxy\)](sap-ariba-applications-f5466e6.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

27643

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Bundle options documentation

</td>
<td valign="top">

Documentation for SAP Field Service Management and SAP Cloud ALM bundle options is now available.

For more information, see [SAP Field Service Management Bundle](sap-field-service-management-bundle-11a5849.md) and [SAP Cloud ALM Bundle](sap-cloud-alm-bundle-b9e08d9.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

27643

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect

</td>
<td valign="top">

As of April 8, 2025 grant types Token Exchange \(RFC 8693\) and JWT Bearer will take into account the risk-based authentication \(RBA\) configurations of the OpenID Connect \(OIDC\) applications in Identity Authentication during OIDC authentication process.

Grant types Authorization Code and Password already take into account the RBA configurations in Identity Authentication.

See [Exchanging Identity Authentication Tokens for Tokens from Corporate Identity Providers](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/exchanging-identity-authentication-tokens-for-tokens-from-corporate-identity-providers?state=DRAFT&version=Dev).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-25

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Identity Federation for Applications

</td>
<td valign="top">

You can enable identity federation for an application to override the identity federation settings on the configured corporate identity provider for the application. See [Configure Identity Federation for Applications](Operation-Guide/configure-identity-federation-for-applications-1e8e34e.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAML 2.0 Configuration

</td>
<td valign="top">

The SAML 2.0 configuration page on application level has been refactored. Now you can separately configure the metadata and certificates setting. See [Configure SAML 2.0 Service Provider](Operation-Guide/configure-saml-2-0-service-provider-51f1f75.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   


</td>
<td valign="top">

Attributes Based on Flexible Expressions

</td>
<td valign="top">

Cloud Identity Services now supports a new attribute based on flexible expressions for the application - `Application Groups` to list the application-specific groups to which the user is assigned to. See [Configuring Attributes Based on Flexible Expressions](Operation-Guide/configuring-attributes-based-on-flexible-expressions-a2f1e46.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Attributes Based on Flexible Expressions

</td>
<td valign="top">

The display name of `Groups` attribute based on flexible expressions for the application is renamed to `All Groups`. See [Configuring Attributes Based on Flexible Expressions](Operation-Guide/configuring-attributes-based-on-flexible-expressions-a2f1e46.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Attributes

</td>
<td valign="top">

Cloud Identity Services now supports a new local user attribute - `Application Groups` to list the application-specific groups to which the user is assigned to. See [Configuring User Attributes from the Identity Directory](Operation-Guide/configuring-user-attributes-from-the-identity-directory-d361407.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Attributes

</td>
<td valign="top">

The name of the `Groups` user attribute is renamed to `All Groups`. See [Configuring User Attributes from the Identity Directory](Operation-Guide/configuring-user-attributes-from-the-identity-directory-d361407.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Warning of unsupported entity

</td>
<td valign="top">

A warning message alerts you when adding an unsupported entity - such as a user, group, or role - in the transformations. While the entity will be accepted, it will not be applied.

See [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for externalId in UUID format

</td>
<td valign="top">

When provisioning users to SAP Build Work Zone, standard edition, the `externalId` must be in UUID format.

See [SAP Build Work Zone, standard edition](sap-build-work-zone-standard-edition-8d6586f.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

No restart for failed job

</td>
<td valign="top">

If a provisioning job from a source system to multiple target systems stops due to an error in one of the targets, it will not resume for that specific target upon restart. Previously, the job would continue after a restart.

See [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Authorizations Based on Policies

</td>
<td valign="top">

You can now restrict the access to the administration console only to one user type via the new attribute that is supported for authorizations based on policies - `user.type`. See [Configure User Authorizations](Operation-Guide/configure-user-authorizations-424b64c.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

27566

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Group Provisioning

</td>
<td valign="top">

You can enable or disable provisioning of every update in an application specific group to a target system. See [Enable or Disable Central Store-Based Provisioning](Operation-Guide/enable-or-disable-central-store-based-provisioning-657bbaa.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Certificate Renewal

</td>
<td valign="top">

Identity Authentication can update automatically the expired encryption certificate, and the SAML 2.0 certificate during the first sign in attempt that fails due to the expired certificate. The metadata URL must be provided. See [Configure SAML 2.0 Service Provider](Operation-Guide/configure-saml-2-0-service-provider-51f1f75.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Management

</td>
<td valign="top">

`Cloud Identity Services` now supports a new user type - *Alumni* for users that were once employed by the company but now they are no more part of it. See [Users](users-70e95d1.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP Cloud Identity Services - Identity Authentication integration with SAP Cloud ALM

</td>
<td valign="top">

SAP Cloud Identity Services - Identity Authentication is now integrated with SAP Cloud ALM and you can use the Configuration & Security Analysis app. See [Monitoring with SAP Cloud ALM](Monitoring-and-Reporting/monitoring-with-sap-cloud-alm-bc835e5.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for OAuth 2.0 Authorization Server Issuer Identification

</td>
<td valign="top">

The service supports the authorization server issuer identification in the authorization code flow. The authorization code flow always includes the `iss` attribute in the response. The service exposes this support in the `authorization_response_iss_parameter_supported` metadata field.

A configuration option enables you to have the service reject responses from corporate identity providers which don't provide the `iss` attribute. If you want to implement OAuth 2.0 authorization server issuer identification \(RFC 9207\), make sure you validate the `iss` attribute.

For more information, see [https://datatracker.ietf.org/doc/html/rfc9207](https://datatracker.ietf.org/doc/html/rfc9207).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-03-11

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

27709

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Increased Number of API Permission Groups Allowed

</td>
<td valign="top">

API permission groups enable you to expose APIs to other Cloud Identity Services applications. With this release, we have increased the number of API permission groups you can create from 20 to 50.

For more information, see [Provide APIs for Consumption by Other Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/provide-apis-for-consumption-by-other-applications?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Central store-based provisioning

</td>
<td valign="top">

You can enable central store-based provisioning to immediately provision updates related to user assignments in application-specific groups between the Local Identity Directory and your selected target systems.

For more information, see [Enable or Disable Central Store-Based Provisioning](Operation-Guide/enable-or-disable-central-store-based-provisioning-657bbaa.md) and [Central Store-Based Provisioning](central-store-based-provisioning-33eae39.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Intelligent Opportunity Analyzer connector

</td>
<td valign="top">

Identity Provisioning supports the Intelligent Opportunity Analyzer connector. You can configure it as source, target, and proxy system for your provisioning scenarios. See:

-   [Intelligent Opportunity Analyzer \(Source\)](intelligent-opportunity-analyzer-65feb7b.md)
-   [Intelligent Opportunity Analyzer \(Target\)](intelligent-opportunity-analyzer-a61c3df.md)
-   [Intelligent Opportunity Analyzer \(Proxy\)](intelligent-opportunity-analyzer-624fff6.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Group mapping changes

</td>
<td valign="top">

The default transformations of SAP S/4 HANA Cloud are changed to support the provisioning of application-specific groups.

For more information, see:

-   [SAP S/4 HANA Cloud \(Source\)](sap-s-4hana-cloud-d3f93a7.md)
-   [SAP S/4 HANA Cloud \(Target\)](sap-s-4hana-cloud-40940b8.md)
-   [SAP S/4 HANA Cloud \(Proxy\)](sap-s-4hana-cloud-4cb0e64.md)



</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Provisioning sub-attributes of emails attribute

</td>
<td valign="top">

Changes in proxy write transformations of SAP Ariba Category Management and SAP Ariba Central Invoice Management ensure that users with multiple email addresses are provisioned with the correct primary email.

For more information, see [SAP Ariba Category Management](sap-ariba-category-management-fb97244.md) and [SAP Ariba Central Invoice Management](sap-ariba-central-invoice-management-64a167d.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Troubleshooting entity deletion

</td>
<td valign="top">

Documentation for troubleshooting the most frequent reasons for deletion of entities from a target system by the Identity Provisioning is now available. For more information, see [Entity Deletion Issues](Monitoring-and-Reporting/entity-deletion-issues-d6acc19.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

2025-02-25

</td>
<td valign="top">

27494

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-13

</td>
<td valign="top">

2025-02-13

</td>
<td valign="top">

27436

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Central store logs

</td>
<td valign="top">

Central store logs are introduced to provide information about the application-specific groups provisioned from the Identity Directory to target systems.

For more information, see [Monitor Central Store Logs](Monitoring-and-Reporting/monitor-central-store-logs-9162898.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27419

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

New conditional function implemented

</td>
<td valign="top">

The conditional function `isRegularGroup` is implemented to verify whether a given group is a regular user group. It checks consecutively the values of the group attributes `supportedOperations` and `applicationId` and returns a Boolean result.

For more information, see [Transformation Functions](transformation-functions-0cdac7c.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27419

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27419

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Authorizations Based оn Policies

</td>
<td valign="top">

As of February 11, 2025, the **MANAGE\_USERS** policy no longer contains the read applications permission.

Action: If your scenario requires this permission, you must add the **READ\_APPLICATIONS** policy to the user or users that need it. See how to do this at [Configure Application Authorizations | SAP Help Portal](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/manage-applications-rights?version=Cloud).

</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27419

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Enforce Nonces for Authentication Requests to Corporate Identity Providers

</td>
<td valign="top">

Some corporate identity providers require that applications send nonces in their authentication requests. You can enable the service to generate nonces if applications don't provide them.

For more information, [Enforce Nonces for Corporate Identity Providers](https://help.sap.com/docs/cloud-identity-services/identity-authentication-internal/enforcing-nonces-for-corporate-identity-providers).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27419

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Disabling ID Token Hints for Corporate Identity Providers During Logout

</td>
<td valign="top">

Corporate identity providers sometimes have trouble when the ID token is included as a URL parameter in logout requests. With this release, you can disable the inclusion of the URL parameter.

For more information, see [Disable ID Token Hints for Corporate Identity Providers](https://help.sap.com/docs/cloud-identity-services/identity-authentication-internal/disabling-id-token-hints-for-corporate-identity-providers).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27419

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Group mapping changes

</td>
<td valign="top">

The default transformations of SAP Ariba Central Invoice Management, SAP Sales Cloud and SAP Service Cloud, Microsoft Entra ID, and SAP Application Server ABAP are changed to support the provisioning of application-specific groups.

For more information, refer to the relevant connector documentation under [Supported Systems](supported-systems-81ca0c1.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27419

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Provisioning sub-attributes of `emails` attribute

</td>
<td valign="top">

Changes in the proxy read transformations of Identity Authentication \(version 1 and 2\) and Local Identity Directory ensure that Identity Provisioning now reads all sub-attributes of the `emails` attribute as defined in the SCIM core schema \(that is, `value`, `type`, `primary`, `display`\).

For more information, see [Identity Authentication \(Proxy\)](identity-authentication-d45c8a3.md) and [Local Identity Directory \(Proxy\)](local-identity-directory-0624f7d.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27419

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-02-05

</td>
<td valign="top">

2025-01-05

</td>
<td valign="top">

27391

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

27344

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Invalid mapping in SAP AS ABAP

</td>
<td valign="top">

An invalid mapping containing the `valueMapping` type has been removed from the SAP AS ABAP read and proxy read transformations. Systems created before January 14, 2025, will need to fix this issue by following the instructions in SAP Note [3562746](https://me.sap.com/notes/3562746).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

27344

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Group Provisioning

</td>
<td valign="top">

You can enable or disable provisioning of every update in an application specific group to a target system. See [Enable or Disable Central Store-Based Provisioning](Operation-Guide/enable-or-disable-central-store-based-provisioning-657bbaa.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

27344

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Provisioning sub-attributes of emails attribute

</td>
<td valign="top">

Changes in the read transformations of Identity Authentication \(version 1 and 2\), Local Identity Directory, and SAP Ariba Invoice Management ensure that Identity Provisioning now reads all sub-attributes of the emails attribute as defined in the SCIM core schema \(that is, `value`, `type`, `primary`, `display`\).

Changes in the write and proxy write transformations of Identity Authentication \(version 2\) ensure that users with multiple email addresses are provisioned with the correct primary email.

For more information, see [Identity Authentication \(Source\)](identity-authentication-e4e25f1.md), [Identity Authentication \(Target\)](identity-authentication-f217bd3.md), [Identity Authentication \(Proxy\)](identity-authentication-d45c8a3.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

27344

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

New conditional functions implemented

</td>
<td valign="top">

The conditional function `isApplicationSpecificGroup` is implemented to verify whether a group is associated with a particular application configured in SAP Cloud Identity Services - Identity Authentication.

The conditional functions `IsAttributeWithOptionalPrefix` and `IsAttributeWithMandatoryPrefix` can be used to verify wheter an attribute value starts with an optional or predefined mandatory prefix.

Currently, these functions are implemented for SAP Advanced Financial Closing, SAP Ariba Applications, and SAP Analytics Cloud \(SCIM API version 1 and 2\) provisioning systems.

For more information, refer to the relevant connector documentation under [Supported Systems](supported-systems-81ca0c1.md) and [Transformation Functions](transformation-functions-0cdac7c.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

27344

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Group mapping changes

</td>
<td valign="top">

The read and proxy read transformations of SAP Ariba Applications and SAP Analytics Cloud \(SCIM API version 1 and 2\) support the provisioning of application-specific groups with `type` and `supportedOperations` group attributes.

The read transformations of these systems are extended with condition that checks if the `ips.application.id` property is not null.

The read and proxy read transformations of Local Identity Directory support the `applicationId` attribute.

For more information, refer to the relevant connector documentation under [Supported Systems](supported-systems-81ca0c1.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

27344

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Reduced Set of Scopes for Credentials of Cloud Identity Services Instances

</td>
<td valign="top">

When you create a new binding or service key for a service instance of Cloud Identity Services with the *application* plan, the generated credential only has the following scopes depending on the credential type:

-   Certificates: *OpenID* and *Identity Directory for Applications*.

-   Secrets and JSON Web Key Sets: *OpenID*.


If the application needs additional scopes, such as *Application* or *Application Users*, the tenant administrator must explicitly grant them.

For more information about configuring client credentials, see [Configure Secrets for API Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/dev-configure-secrets-for-api-authentication?version=Cloud).

For more information about using SAP Cloud Identity Services with SAP BTP, see [Integrating the Service with the Identity Service of SAP BTP](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/integrating-service-with-identity-service-of-sap-btp?version=Cloud).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

2025-01-29

</td>
<td valign="top">

27344

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-21

</td>
<td valign="top">

2025-01-21

</td>
<td valign="top">

27307

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade

</td>
<td valign="top">

Cloud Identity Services have been upgraded.

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

New

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-14

</td>
<td valign="top">

2025-01-14

</td>
<td valign="top">

27268

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SAP Build Work Zone, advanced edition - `userType` provisioning

</td>
<td valign="top">

The condition for `user.groups[]` attributes in the write transformation of SAP Build Work Zone, advanced edition is enhanced to support the provisioning of users with their `userType` based on the names of the groups that are assigned to them. The change is valid for scenarios in which the `name` of the group matches its `displayName`.

For more information, see [SAP Build Work Zone, advanced edition](sap-build-work-zone-advanced-edition-787502d.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-14

</td>
<td valign="top">

2025-01-14

</td>
<td valign="top">

27268

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Tenant Reset renamed to Reset Provisioning Settings

</td>
<td valign="top">

The *Tenant Reset* option, which enables you to delete all provisioning systems configured for your tenant, along with scheduled jobs, subscriptions, and logs, has been renamed to *Reset Provisioning Settings*.

For more information, see [Reset Identity Provisioning Settings](Operation-Guide/reset-identity-provisioning-settings-8c7ba9a.md).

</td>
<td valign="top">

Info only

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Changed

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-14

</td>
<td valign="top">

2025-01-14

</td>
<td valign="top">

27268

</td>
<td valign="top">

All scenarios

</td>
</tr>
<tr>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Authorizations Based оn Policies

</td>
<td valign="top">

As of February 11, 2025, the **MANAGE\_USERS** policy will no longer contain the read applications permission.

Action: If your scenario requires this permission, you must add the **READ\_APPLICATIONS** policy to the user or users that need it. See how to do this at [Configure Application Authorizations | SAP Help Portal](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/manage-applications-rights?version=Cloud).

</td>
<td valign="top">

Required

</td>
<td valign="top">

General Availability

</td>
<td valign="top">

Announcement

</td>
<td valign="top">

Technology

</td>
<td valign="top">

Not applicable

</td>
<td valign="top">

Cloud Identity Services 

</td>
<td valign="top">

2025-01-14

</td>
<td valign="top">

2025-02-11

</td>
<td valign="top">

27268

</td>
<td valign="top">

All scenarios

</td>
</tr>
</table>



<a name="loiode21efe39e1442618388784891497067__archived"/>

## What's New Archived

-   [2024](2024-what-s-new-for-cloud-identity-services-archive-a858345.md)

-   [2023](2023-what-s-new-for-cloud-identity-services-archive-1c651db.md)


