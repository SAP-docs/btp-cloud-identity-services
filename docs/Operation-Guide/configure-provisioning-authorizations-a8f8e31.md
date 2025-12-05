<!-- loioa8f8e31a92dd49c4bec8b8dd46cee1e5 -->

# Configure Provisioning Authorizations

Configure granular access control for the Identity Provisioning systems and logs in the SAP Cloud Identity Services administration console.



<a name="loioa8f8e31a92dd49c4bec8b8dd46cee1e5__prereq_yys_bdw_fzb"/>

## Prerequisites

-   You have enabled the *Policy-Based Authorizations* option in the SAP Cloud Identity Services admin console. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).

-   Your tenant administrator has the following authorizations: *Manage Application*, *Manage Groups* and *Read Users*.




## Context

> ### Restriction:  
> This feature is relevant only for the Administration Console application.

> ### Remember:  
> If your tenant has been migrated to a new region, you need to configure your authorizations based on policies again.

Tenant administrators can assign specific authorizations to users, allowing them to access only source systems, target systems, proxy systems, provisioning logs, or any combination of these. The distribution of responsibilities enables authorized users \(not necessarily administrators\) within your organization to concentrate on their specific areas of access and expertise.

The following authorization policies related to provisioning are available in the Administration Console application under the package name *provisioning*. These policies are non-editable, meaning you cannot add or delete rules \(i.e., restrictions\). You can only assign users to the authorization policy.


<table>
<tr>
<th valign="top">

Authorization Policy

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

MANAGE\_PROVISIONING\_SOURCES

</td>
<td valign="top">

Allows users to manage source systems only. This includes creating systems, managing properties, transformations and certificates, as well as running and scheduling provisioning jobs and viewing notifications.

</td>
</tr>
<tr>
<td valign="top">

MANAGE\_PROVISIONING\_TARGETS

</td>
<td valign="top">

Allows users to manage target systems only. This includes creating systems, managing properties, transformations and certificates, as well as viewing notifications.

</td>
</tr>
<tr>
<td valign="top">

MANAGE\_PROVISIONING\_PROXIES

</td>
<td valign="top">

Allows users to manage proxy systems only. This includes creating systems, managing properties, transformations and certificates, as well as viewing notifications.

</td>
</tr>
<tr>
<td valign="top">

MANAGE\_PROVISIONING\_LOGS

</td>
<td valign="top">

Allows users to manage provisioning job logs and real-time provisioning logs, as well as viewing notifications.

</td>
</tr>
</table>

> ### Note:  
> The *Manage Identity Provisioning* role, provides full access to all configurations and functionalities of the service. After the implementation of the granular access control on December 3, 2024, users assigned to this role will retain their full access, regardless of any policies assigned.

To assign users to one or more authorization policies, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Under *System Applications*, choose the *Administration Console*.

4.  Under the *Authorization Policies* tab, search for the authorization policy and select it.

    You can type the policy name or package in the search field, filter the policy by package type, or choose it directly from the list.

    The policy names follow this convention: *<action\>*\_*<functionality\>*\_*<resource\>*, for example: *MANAGE\_PROVISIONING\_LOGS*

5.  Under the *Assignments* tab, choose *Add* and add a user.

    To assign a user to multiple authorization policies, repeat steps 4 and 5 as necessary. Alternatively, you can combine multiple policies by creating a new policy of type *Customer Package* and assign the user to all included policies at once. For more information, see [Combine Authorization Policies](combine-authorization-policies-1a69414.md).




<a name="loioa8f8e31a92dd49c4bec8b8dd46cee1e5__result_j4y_qdl_bdc"/>

## Results

When an authorization policy is assigned to a user, a user group named after the policy is also assigned to that user. For example, if a user is assigned the MANAGE\_PROVISIONING\_LOGS policy, they will become members of the following user group: MANAGE\_PROVISIONING\_LOGS - provisioning - Administration Console.

Upon logging in at either `https://<tenant ID>.accounts.ondemand.com/admin` or `https://<tenant ID>.accounts.cloud.sap/admin`, the user will have access specifically to the provisioning logs in the SAP Cloud Identity Services administration console and no other areas.

**Related Information**  


[Configure User Authorizations](configure-user-authorizations-424b64c.md "Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.")

[Configure Group Authorizations](configure-group-authorizations-7a09cad.md "Configure granular access and control over the groups in the administration console of SAP Cloud Identity Services.")

[Configure Application Authorizations](configure-application-authorizations-01cff18.md "Configure granular access and control over the applications in the administration console of SAP Cloud Identity Services.")

