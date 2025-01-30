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


