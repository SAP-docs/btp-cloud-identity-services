<!-- loio982ac5f91d2346fda8dd8096e861fc36 -->

# Configuring Authorization Policies

Authorization management enables Identity Authentication administrators to use authorization policies in multiple environments, configure them, and assign them to users.

When you subscribe to an application that supports authorization policies, the system sets up an application in Identity Authentication for you and from there you can assign authorizations. An authorization management tenant is automatically created as a new tenant. Service instances and bindings are added automatically.

For more information, see [Subscribe to Multitenant Applications Using the Cockpit](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/7a3e39622be14413b2a4df7c02ca1170.html).



<a name="loio982ac5f91d2346fda8dd8096e861fc36__section_axh_vvq_swb"/>

## Prerequisites

-   Your application supports authorization policies. Refer to the documentation of your application.

-   Your user has administrative permissions in Identity Authentication with the the following authorizations:

    -   *Manage Applications*

    -   *Manage Groups*


    For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You are using SAP Cloud Identity Services - Identity Authentication. For more information, see [Tenant Model and Licensing](../tenant-model-and-licensing-93160eb.md).


> ### Note:  
> If your application doesn't have an *Authorization Policies* tab, it doesn't support authorization management.



<a name="loio982ac5f91d2346fda8dd8096e861fc36__section_fnh_dfz_l5b"/>

## Authorization Management

Authorization management allows SAP Cloud Identity Services - Identity Authentication administrators to refine authorization policies based on application policy templates with complex instance restrictions for data access. Developers define and deploy authorization policies with functional checks, instance-based authorizations, and user attributes. They're available in the Identity Authentication administration console. If necessary, developers can update existing authorization policies.

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
> To make sure that authorization management is resilient, we've introduced an upper limit of 200 custom authorization policies and 200 base authorization policies that can be defined per application.



<a name="loio982ac5f91d2346fda8dd8096e861fc36__section_g4l_lsx_l5b"/>

## Configuration Options

Authorization policy administrators can configure the following in custom authorization policies:

-   Combine authorization policies. See [Combine Authorization Policies](combine-authorization-policies-1a69414.md).

-   Add or delete rules and restrictions and their attribute values. See [Edit an Authorization Policy](edit-an-authorization-policy-c76aca6.md).


