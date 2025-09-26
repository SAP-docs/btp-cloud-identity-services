<!-- loio982ac5f91d2346fda8dd8096e861fc36 -->

# Configuring Authorization Policies

Authorization Management enables SAP Cloud Identity Services administrators to use authorization policies, customize them, and assign them to users.

When you subscribe to an application that supports authorization policies, you get a corresponding application in *Applications*, and from there you can assign authorizations.

For more information, see [Subscribe to Multitenant Applications Using the Cockpit](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/7a3e39622be14413b2a4df7c02ca1170.html), [Assign Authorization Policies](assign-authorization-policies-eac8e5e.md), and [Add Users to a Group](add-users-to-a-group-d2e1a01.md).



<a name="loio982ac5f91d2346fda8dd8096e861fc36__section_axh_vvq_swb"/>

## Prerequisites

-   Your application supports authorization policies. Refer to the documentation of your application.

-   Your user has administrative permissions in SAP Cloud Identity Services with the following authorizations:

    -   *Manage Applications*

    -   *Manage Groups*

    -   *Read Users*


    For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You are using SAP Cloud Identity Services - Identity Authentication. For more information, see [Tenants](../tenants-93160eb.md).


> ### Note:  
> If your application doesn't have an *Authorization Policies* tab, it doesn't support Authorization Management.



<a name="loio982ac5f91d2346fda8dd8096e861fc36__section_fnh_dfz_l5b"/>

## Authorization Management

Authorization Management allows SAP Cloud Identity Services administrators to refine authorization policies based on application policy templates with powerful instance restrictions for data access. Developers define and deploy authorization policies with functional checks, instance-based authorizations, and user attributes. They're available in the SAP Cloud Identity Services administration console. If necessary, developers can update existing authorization policies.

For more information, see [Developing Authorizations](../Development/developing-authorizations-22928a2.md).



<a name="loio982ac5f91d2346fda8dd8096e861fc36__section_r2m_vlx_l5b"/>

## Authorization Policy Types

An authorization policy is basically a collection of rules, which are applied to resources and restricted by conditions. Authorization policies are defined by developers and come with the respective application.

**Setting Up Authorization Policies**


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

User Role

</th>
<th valign="top">

Tool

</th>
</tr>
<tr>
<td valign="top">

Define authorization policies

</td>
<td valign="top">

Developer

</td>
<td valign="top">

Development environment

</td>
</tr>
<tr>
<td valign="top">

Deploy authorization policies with the application

</td>
<td valign="top">

Developer

</td>
<td valign="top">

Development environment

</td>
</tr>
<tr>
<td valign="top">

Modify authorization policies

</td>
<td valign="top">

Administrator

</td>
<td valign="top">

Administration console

</td>
</tr>
<tr>
<td valign="top">

Assign authorization policies to users

</td>
<td valign="top">

Administrator

</td>
<td valign="top">

Administration console

</td>
</tr>
<tr>
<td valign="top">

Delete authorization policies

</td>
<td valign="top">

Administrator

</td>
<td valign="top">

Administration console

</td>
</tr>
</table>

We distinguish between different types of authorization policies. You recognize the different types in the *Package* column.

-   The package name of the base policies is defined by the application.

-   Customers can deploy their own authorization policies in customer-developed packages, which have the package name *Customer Package* in the list of authorization policies.


**Authorization Policy Types**


<table>
<tr>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Base authorization policy

</td>
<td valign="top">

Authorization policy delivered by the application. Administrators can copy the authorization policy and modify the copy. The copy, modified or not, is a custom authorization policy. You can't change or delete it in the administration console.

</td>
</tr>
<tr>
<td valign="top">

Custom authorization policy

</td>
<td valign="top">

Authorization policy created by administrators. You can change and delete this authorization policy in the administration console.

</td>
</tr>
</table>

> ### Restriction:  
> To make sure that Authorization Management is resilient, we've introduced an upper limit of 200 custom authorization policies and 200 base authorization policies that can be defined per application.



<a name="loio982ac5f91d2346fda8dd8096e861fc36__section_g4l_lsx_l5b"/>

## Configuration Options

Authorization policy administrators can configure the following in custom authorization policies:

-   Combine authorization policies. See [Combine Authorization Policies](combine-authorization-policies-1a69414.md).

-   Add or delete rules and restrictions and their attribute values. See [Edit an Authorization Policy](edit-an-authorization-policy-c76aca6.md).




<a name="loio982ac5f91d2346fda8dd8096e861fc36__section_igk_hl2_ggc"/>

## Refining Authorization Policies

Administrators can edit an existing custom authorization policy. They can add restrictions and manage the values of the restrictions. The restrictions are refined by attributes with fixed values or user attributes. They can also add `USE` rules to a custom authorization policy and restrict them.

For more information, see [Data Control Language](data-control-language-38baa25.md).

**Related Information**  


[Configuring Applications](configuring-applications-61ad3b0.md "This section describes how you can configure the user authentication, access to an application, and use a branding style in accordance with your company requirements. It also explains the trust configuration between Identity Authentication and a service provider or client (relying party).")

[Configuring Tenant Settings](configuring-tenant-settings-d4d6fdc.md "Initially, the tenants are configured to use default settings. This section describes how you as a tenant administrator can make custom tenant configurations.")

[Configuring Password Policies](configuring-password-policies-12b3395.md "Passwords for the authentication of users are subject to certain rules. These rules are defined in the password policy. Identity Authentication provides you with two predefined password policies, in addition to which you can create and configure up to three custom password policies.")

[Configuring Privacy Policies](configuring-privacy-policies-ed48466.md "You can configure a custom privacy policy document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Configuring Terms of Use](configuring-terms-of-use-61d3a86.md "You can configure a custom terms of use document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Configuring Email Templates](configuring-email-templates-b2afbcd.md "Tenant administrators can use the default or a custom email template set for the application processes.")

[Managing Administrators](managing-administrators-786eea2.md "This section describes how, as a tenant administrator, you can list all administrators in the administration console for SAP Cloud Identity Services, add new administrators, and edit the administrator authorizations. You can also remove administrators.")

[Managing Users](managing-users-228428f.md "Tenant administrators can manage user accounts via the administration console for SAP Cloud Identity Services, and via APIs.")

[Managing Groups](managing-groups-ddd067c.md "Tenant administrators can create groups, and assign and unassign these groups to users via the administration console for SAP Cloud Identity Services.")

[Configuring Provisioning Systems](configuring-provisioning-systems-f149f76.md "Configure provisioning systems for synchronizing users and groups between business applications.")

[Configuring Real-Time Provisioning](configuring-real-time-provisioning-617dd4b.md "As a tenant administrator, you can configure real-time provisioning to immediately provision entities from source to target systems.")

[Configuring Social Identity Providers](configuring-social-identity-providers-17d400d.md "By configuring a social provider, users can log on to applications with their social media credentials by linking their accounts in Identity Authentication to the social media account.")

[Integrating with Existing Customer Landscape](integrating-with-existing-customer-landscape-cf29ea1.md "Identity Authentication can be integrated with already existing customer landscape and supports different types of delegated authentication.")

[Configuring External Authentication Providers](configuring-external-authentication-providers-4f02f94.md "Configure authentication providers in the administration console for SAP Cloud Identity Services to manage users from external providers.")

[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

