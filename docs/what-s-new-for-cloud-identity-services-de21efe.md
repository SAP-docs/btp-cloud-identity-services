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

2503b

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

2025-04-08

</td>
<td valign="top">

2025-04-08

</td>
<td valign="top">

2503b

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

Cloud Identity Services is available with a new data \(DC\) center, United States \(Virginia\), for the AWS infrastructure in US \(North America East\) region.

The United States \(Colorado\) DC is no longer used.

Action:

We recommend you to add the following IPs to your allowed IP list:

-   LB IP - 3.92.131.87, 52.200.183.196, 35.168.205.166
-   NAT IP - 52.44.60.92/32, 54.211.101.173/32, 54.225.47.27/32

The following IPs are no longer in use:

-   LB IP - 130.214.207.198
-   NAT IP - 130.214.242.32/27

See [Regional Availability](regional-availability-be600ca.md).

</td>
<td valign="top">

Recommended

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

2503a

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

2503a

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

2503a

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

2503a

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

2503a

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

2503a

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

2503a

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

2503b

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

2502b

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

2502b

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

2502b

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

2502b

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

2502b

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

2502b

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

2502b

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

2502b

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

2502b

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

2502b

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

2502b

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

2502a

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

2502a

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

2502a

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

2502a

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

2502a

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

2503b

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

2502a

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

2502a

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

2502a

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

2502a

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

2502a

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

2502a

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

2501b

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

2501b

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

Off-Cycle Upgrade

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

2501b

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

Action: If your scenario requires this permission, you add the **READ\_APPLICATIONS** policy to the user or users that need it. See how to do this at [Configure Application Authorizations | SAP Help Portal](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/manage-applications-rights?version=Cloud).

</td>
<td valign="top">

Recommended

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

2501b

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

2501b

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

2501b

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

2501b

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

2501b

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

Off-Cycle

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

2501a

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

2501a

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

2501a

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

2501a

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

2501a

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

2501a

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

2501a

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

Off-Cycle Upgrade

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

2413b

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

2413b

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

2413b

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

Action: If your scenario requires this permission, you add the **READ\_APPLICATIONS** policy to the user or users that need it. See how to do this at [Configure Application Authorizations | SAP Help Portal](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/manage-applications-rights?version=Cloud).

</td>
<td valign="top">

Recommended

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

2501b

</td>
</tr>
</table>



<a name="loiode21efe39e1442618388784891497067__archived"/>

## What's New Archived

-   [2024](2024-what-s-new-for-cloud-identity-services-archive-a858345.md)

-   [2023](2023-what-s-new-for-cloud-identity-services-archive-1c651db.md)


