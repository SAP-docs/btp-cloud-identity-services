<!-- loioa8f8e31a92dd49c4bec8b8dd46cee1e5 -->

# Configure Provisioning Authorizations

Configure granular access control over the Identity Provisioning systems and logs in the SAP Cloud Identity Services administration console.



<a name="loioa8f8e31a92dd49c4bec8b8dd46cee1e5__prereq_yys_bdw_fzb"/>

## Prerequisites

-   You have enabled the *Policy-Based Authorizations* option in the SAP Cloud Identity Services admin console. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).

-   At least one administrator user is assigned the *Manage Identity Provisioning* role.




## Context

Identity Provisioning administrators with the *Manage Identity Provisioning* role can grant specific authorizations to other administrators, enabling them to access only source systems, target systems, proxy systems, provisioning logs, or any combination of these. The distribution of responsibilities allows each administrator within your organization to focus on their designated areas of access.

The *Manage Identity Provisioning* role is the main administrator role, granting full access to all configurations and functionalities of the service. Before the implementation of granular access control on *<XXX\>*, 2024, this role was assigned to all Identity Provisioning administrators. Admin users with this role will retain their full access.

The following authorization policies related to provisioning are supported:


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

Allows admin users to manage source systems only. This includes creating systems, managing properties, transformations and certificates, as well as running and scheduling provisioning jobs.

</td>
</tr>
<tr>
<td valign="top">

MANAGE\_PROVISIONING\_TARGETS

</td>
<td valign="top">

Allows admin users to manage source systems only. This includes creating systems, managing properties, transformations and certificates.

</td>
</tr>
<tr>
<td valign="top">

MANAGE\_PROVISIONING\_PROXIES

</td>
<td valign="top">

Allows admin users to manage source systems only. This includes creating systems, managing properties, transformations and certificates.

</td>
</tr>
<tr>
<td valign="top">

MANAGE\_PROVISIONING\_LOGS

</td>
<td valign="top">

Allows admin users to manage provisioning job logs and real-time provisioning logs.

</td>
</tr>
</table>



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Under *System Applications*, choose the *Administration Console*.

4.  Under the *Authorization Policies* tab, search for the authorization policy and select it.

    You can either use the search field or filter the policies by package type.

    The names of the policies follow this convention: *<action\>*\_*<functionality\>*\_*<resource\>*. Each package on the *Authorization Policies* tab is named after the resource.

5.  Under the *Assignments* tab, choose *Add* and add a user.

    To grant more than one authorization policy to a user, repeat steps 4 and 5 as many times as needed.




<a name="loioa8f8e31a92dd49c4bec8b8dd46cee1e5__result_j4y_qdl_bdc"/>

## Results

Following the assignment of each authorization policy, a user group named after the policy is created and assigned to the respective user.

Upon logging in, a user with the MANAGE\_PROVISIONING\_SOURCES authorization policy will only have access to the source systems in the SAP Cloud Identity Services administration console.

**Related Information**  


[Configure User Authorizations](configure-user-authorizations-424b64c.md "Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.")

[Configure Application Authorizations](configure-application-authorizations-01cff18.md "Configure granular access and control over the applications in the administration console of SAP Cloud Identity Services.")

