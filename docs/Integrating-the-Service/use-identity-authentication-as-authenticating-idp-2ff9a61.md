<!-- loio2ff9a6103408458abdd727e639235cad -->

# Use Identity Authentication as Authenticating IdP

In this scenario, to log on to an application, users provide their credentials to Identity Authentication, and Identity Authentication asserts their identity to the application.

Every SAP S/4HANA system or SAP Analytics Cloud embedded come with an Identity Authentication as a trusted identity provider. You’ve received a provisioning email with initial access information for the Identity Authentication tenant.

For the authentication of the users, you must have them in your Identity Authentication tenant. You can import your users in Identity Authentication, or create them via the administration console or the Identity Directory API.

The tables below show the pre-configured settings for your system that you have in the Identity Authentication administration console.

> ### Note:  
> The tenant URL has the following pattern:
> 
> `https://<tenant ID>.accounts.ondemand.com/admin`
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Admins](../view-assigned-tenants-and-admins-f56e6f2.md).
> 
> If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

**ABAP tenants provisioned before SAP S/4HANA Cloud 2208**


<table>
<tr>
<th valign="top">

System

</th>
<th valign="top">

Trust-Related Setting

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top" rowspan="4">

S/4HANA Cloud or Integrated Business Planning

</td>
<td valign="top">

`Subject Name Identifier`

</td>
<td valign="top">

`Login Name`

> ### Note:  
> For successful authentication, the user name of the business user in S/4HANA Cloud or Integrated Business Planning must be identical to the login name.



</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`

</td>
<td valign="top">

`Unspecified`

</td>
</tr>
<tr>
<td valign="top">

`Apply Function to Subject Name Identifier`

</td>
<td valign="top">

`None` \(ABAP does implicit uppercase conversion\)

</td>
</tr>
<tr>
<td valign="top">

`Conditional Authentication`

</td>
<td valign="top">

Identity Authentication

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

SAP Analytics Cloud, embedded edition

</td>
<td valign="top">

`Subject Name Identifier`

</td>
<td valign="top">

`Login Name`

</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`

</td>
<td valign="top">

`Unspecified`

</td>
</tr>
<tr>
<td valign="top">

`Apply Function to Subject Name Identifier`

</td>
<td valign="top">

`Uppercase`

</td>
</tr>
<tr>
<td valign="top">

`Conditional Authentication`

</td>
<td valign="top">

Identity Authentication

</td>
</tr>
</table>

**ABAP tenants provisioned from SAP S/4HANA Cloud 2208 onwards**


<table>
<tr>
<th valign="top">

Application

</th>
<th valign="top">

Trust-related setting

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top" rowspan="4">

S/4HANA Cloud or SAP Integrated Business Planning

</td>
<td valign="top">

`Subject Name Identifier`

</td>
<td valign="top">

`Email`

> ### Note:  
> For successful authentication, the email address of the business user in S/4HANA Cloud or Integrated Business Planning must be identical to the email.



</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`

</td>
<td valign="top">

`Email`

</td>
</tr>
<tr>
<td valign="top">

`Apply Function to Subject Name Identifier`

</td>
<td valign="top">

`None` \(email addresses are compared case-insensitively\)

</td>
</tr>
<tr>
<td valign="top">

`Conditional Authentication`

</td>
<td valign="top">

`Identity Authentication`

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

SAP Analytics Cloud, embedded edition

</td>
<td valign="top">

`Subject Name Identifier`

</td>
<td valign="top">

`Email`

</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`

</td>
<td valign="top">

`Unspecified`

</td>
</tr>
<tr>
<td valign="top">

`Apply Function to Subject Name Identifier`

</td>
<td valign="top">

`Lowercase`

</td>
</tr>
<tr>
<td valign="top">

`Conditional Authentication`

</td>
<td valign="top">

`Identity Authentication`

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

SAP Datasphere

</td>
<td valign="top">

`Subject Name Identifier`

</td>
<td valign="top">

`Email`

</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`

</td>
<td valign="top">

`Email`

</td>
</tr>
<tr>
<td valign="top">

`Apply Function to Subject Name Identifier`

</td>
<td valign="top">

`None` \(email addresses are compared case-insensitively\)

</td>
</tr>
<tr>
<td valign="top">

`Conditional Authentication`

</td>
<td valign="top">

`Identity Authentication`

</td>
</tr>
</table>

> ### Note:  
> The same identifying attribute \(login name or email address\) is used for both ABAP and SAP Analytics Cloud. User records must be created in ABAP and are then automatically replicated to SAP Analytics Cloud:

-   Replication from SAP S/4HANA Cloud to SAP Analytics Cloud happens via a pre-integrated Identity Provisioning tenant \(communication scenario *SAP\_COM\_0193*\).
-   Replication from SAP Integrated Business Planning to SAP Analytics Cloud happens via the SAP-managed communication scenario *SAP\_COM\_1187*.

**Related Information**  


[Tenants](../tenants-93160eb.md "A tenant refers to your (customer-specific) instance of SAP Cloud Identity Services. It's delivered to you as part of a bundle with an SAP cloud solution or as part of a self-service request in SAP BTP cockpit.")

[Identity Directory REST API](https://api.sap.com/api/IdDS_SCIM/resource)

[Create a New User](../Operation-Guide/create-a-new-user-348deef.md "As a tenant administrator, you can create a new user in the administration console for SAP Cloud Identity Services.")

[Import CSV File with Full User Profile](../Operation-Guide/import-csv-file-with-full-user-profile-f54b900.md "As a tenant administrator, you can create new users or update existing ones with all user data, including attributes from a custom schema, via a CSV file upload.")

[Import or Update Users for a Specific Application](../Operation-Guide/import-or-update-users-for-a-specific-application-33838e0.md "As a tenant administrator, you can import new users or update existing ones for a specific application with a CSV file. You can also send activation emails to the users that have not received activation emails for that application so far.")

[Configure SAML 2.0 Service Provider](../Operation-Guide/configure-saml-2-0-service-provider-51f1f75.md "This document is intended to help you configure a SAML 2.0 service provider (SP) in the administration console for SAP Cloud Identity Services.")

[Communication Scenarios Managed by SAP](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/c15c71affb2243ec9abc071c1a62503c.html)

[Initial System Access for SAP S/4HANA Cloud in Your 3-system Landscape](https://help.sap.com/docs/SAP_S4HANA_CLOUD/b249d650b15e4b3d9fc2077ee921abd0/30415f166409468689b31571989e4b95.html?state=DRAFT&version=2202.500)

