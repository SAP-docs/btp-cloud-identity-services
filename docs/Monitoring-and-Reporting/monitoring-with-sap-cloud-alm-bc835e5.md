<!-- loiobc835e53b13c4b4d885013a79a1294f4 -->

# Monitoring with SAP Cloud ALM

Identity ProvisioningSAP Cloud Identity Services - Identity Provisioning is integrated with [SAP Cloud ALM](https://help.sap.com/docs/CloudALM?locale=en-US&state=PRODUCTION&version=latest), which is a cloud-based application lifecycle management offering that enables you to implement, operate, and monitor your cloud solutions.



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_xxv_cg1_ybc"/>

## Initial Configuration

You can request SAP Cloud ALM on [SAP for Me](https://me.sap.com/) for yourself or for all customers for whom you have permissions.

After you've requested SAP Cloud ALM, follow the steps to set it up. For more information, see [Required Setup for SAP Cloud ALM](https://help.sap.com/docs/cloud-alm/setup-administration/required-setup).

To use the Configuration & Security Analysis app and the Job & Automation Monitoring appl, you must activate the data collection for the *Identity Provisioning* component. For more information, see [Setup for SAP Cloud Identity Services – Identity Provisioning](https://support.sap.com/en/alm/sap-cloud-alm/operations/expert-portal/setup-managed-services/calm-setup-ip.html).



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_ojk_1sq_wbc"/>

## Configuration & Security Analysis

With the Configuration & Security Analysis app of SAP Cloud ALM, you can check if your Identity ProvisioningSAP Cloud Identity Services - Identity Provisioning tenants and provisioning systems are configured in alignment with the [Security recommendations for SAP Cloud Identity Services - Identity Provisioning](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-service=Identity+Provisioning&version=Cloud).

> ### Note:  
> Identity Provisioning reports data to SAP Cloud ALM daily. For more information, see [Monitor Security Recommendations with SAP Cloud ALM](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/monitor-security-recommendations-with-sap-cloud-alm?version=Cloud).

In the Configuration & Security Analysis app, the compliance of your configured tenants or systems to the applicable security recommendations is displayed with the following details:


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Value

</th>
<th valign="top">

Security Recommendation Status

</th>
<th valign="top">

Security Recommendation Index

</th>
</tr>
<tr>
<td valign="top">

***audit\_logs***

</td>
<td valign="top">

The *Data Record* displays the number of configured OAuth clients.

> ### Caution:  
> The compliance check displays reliable data only for bundle tenants.

The *Data Record* displays the following information as displayed in the *Audit Logs* tab in the administration console for SAP Cloud Identity Services:

-   Tenant ID

-   Region

-   Subdomain


If there is no audit logs configuration, the value is empty.

</td>
<td valign="top">

*COMPLIANT* - in case there are audit logs configurations

*NONCOMPLIANT* in the following cases:

-   there is no audit log configuration

-   you have a standalone tenant




</td>
<td valign="top">

*BTP-IPS-0001*

</td>
</tr>
<tr>
<td valign="top">

***trace\_setting***

</td>
<td valign="top">

The *Data Record* displays the values set for the two properties that enable logging and tracing for personal and sensitive data of the provisioned entities:

-   `ips.trace.failed.entity.content` = *<value\>*

-   `ips.trace.skipped.entity.content` = *<value\>*




</td>
<td valign="top">

*COMPLIANT* - when both properties are set to *false*

*NONCOMPLIANT* – if one or both properties are set to *true*

</td>
<td valign="top">

*BTP-IPS-0002*

</td>
</tr>
<tr>
<td valign="top">

***outbound\_authentication\_method***

</td>
<td valign="top">

The *Data Record* displays the values set for the properties `Authentication` or `ldap.authentication`.

If there is no authentication property configured, the value is empty.

</td>
<td valign="top">

*COMPLIANT* in the following cases:

-   The system supports certificate authentication and the authentication property is set to *ClientCertificateAuthentication*.

-   The system supports **only** basic authentication and the `Authentication` property is set to *BasicAuthentication*.


*NONCOMPLIANT* in the following cases:

-   There is no authentication property configured.

-   The system supports certificate authentication, but the value of the `Authentication` property is different from *ClientCertificateAuthentication* or the certificate is not configured.




</td>
<td valign="top">

*BTP-IPS-0003*

</td>
</tr>
<tr>
<td valign="top">

***inbound\_authentication\_method***

</td>
<td valign="top">

-   *Basic Authentication*
-   *Certificate Authentication*
-   *default* - if the source system is not configured for real-time provisioning

> ### Note:  
> The compliance check is relevant on the tenant level.

> ### Note:  
> You must have an existing destination *IPS\_MANAGE\_AUTHORIZATIONS* to be able to preview reliable data and status for the recommendation.



</td>
<td valign="top">

*COMPLIANT* in the following cases:

-   The authentication type configured is certificate authentication.

-   Displayed by default for source systems that are not used for real-time provisioning.


There is a system user with configured certificate that possesses at least one of the roles: *Access Real-Time Provisioning API* or *Access Proxy System API*.

*NONCOMPLIANT* when:

There is no system user with configured certificate that possesses at least one of the roles: *Access Real-Time Provisioning API* or *Access Proxy System API*.

There is no configured destination *IPS\_MANAGE\_AUTHORIZATIONS* or its configuration is not correct.



</td>
<td valign="top">

*BTP-IPS-0004*

</td>
</tr>
<tr>
<td valign="top">

***secure\_protocols***

</td>
<td valign="top">

The *Data Record* displays the values of all configured `URL` properties.

If no URL properties are configured, the value is empty.

</td>
<td valign="top">

*COMPLIANT* in the following cases:

-   The system uses `ProxyType` *Internet* and the secure protocols used are *HTTPS* or *SSH*.

-   The system uses `ProxyType` *OnPremise*, hence insecure protocols are accepted.

-   If there are no `URL` properties configured.


*NONCOMPLIANT* when the system uses `ProxyType` *Internet* and the protocol is insecure \(for example *HTTP*\).

</td>
<td valign="top">

*BTP-IPS-0005*

</td>
</tr>
<tr>
<td valign="top">

***credential\_properties***

</td>
<td valign="top">

The check validates whether for the configuration of sensitive information are used credential properties. The information is displayed in the following format:

***`sensitive property` = <value\>***

The possible values are:

-   `true` - when the property is created as `Credential`

    For example, if you have configured `Password` as `Credential`, the result is `Password = true`

-   `false` - if the property is not created as `Credential`

    For example, if you have configured `ssh.password` as `Standard`, the result is `ssh.password = false`

    `empty` - if there are no sensitive properties configured


If there are no sensitive properties configured, the value is empty.

</td>
<td valign="top">

*COMPLIANT* in the following cases:

-   All sensitive properties are configured as type *Credential*.

-   There are no sensitive properties configured.


*NONCOMPLIANT* if one or more sensitive properties are configured as type *Standard*.

</td>
<td valign="top">

*BTP-IPS-0006*

</td>
</tr>
<tr>
<td valign="top">

***trust\_all***

</td>
<td valign="top">

The check evaluates whether the `TrustAll` property is used in productive scenarios.

The information is displayed in the following format:

`Value` = *<property value\>*

</td>
<td valign="top">

*COMPLIANT* when the property `TrustAll` is set to *false*.

*NONCOMPLIANT* - when the property `TrustAll` is set to *true*.

> ### Note:  
> The security compliance check is not supported for connectivity destinations in the SAP BTP cockpit.



</td>
<td valign="top">

*BTP-IPS-0007*

</td>
</tr>
<tr>
<td valign="top">

***ips\_admin\_user\_count***

</td>
<td valign="top">

The *Data Record* displays the number of assigned tenant administrators.

> ### Note:  
> You must have an existing destination *IPS\_MANAGE\_AUTHORIZATIONS* to be able to preview reliable data and status for the recommendation.



</td>
<td valign="top">

*COMPLIANT* when the number of tenant administrators assigned is greater than one.

*NONCOMPLIANT*:

-   In case there is only one tenant administrator assigned.

-   When there is no configured destination *IPS\_MANAGE\_AUTHORIZATIONS* or its configuration is not correct.




</td>
<td valign="top">

*BTP-IPS-0008*

</td>
</tr>
</table>



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_y2l_d1r_wbc"/>

## Job & Automation Monitoring

In the Job & Automation Monitoring app, you can monitor the execution of your jobs using specific metrics. The supported provisioning job types are *Read* \(immediate and scheduled\), *Resync* and *Simulate*. In the Job & Automation Monitoring app they are grouped by system name and jоb type. You have the option to drill down from a specific row to the list of executed jobs.

For more information, see [Job & Automation Monitoring](https://help.sap.com/docs/cloud-alm/applicationhelp/job-automation-monitoring?locale=en-US%20and%20https://support.sap.com/ja/alm/sap-cloud-alm/operations/expert-portal/job-monitoring.html) and the [relevant section on the SAP Support Portal](https://support.sap.com/ja/alm/sap-cloud-alm/operations/expert-portal/job-monitoring.html).

In case you encounter problems with setting up or using the apps, create a case under the relevant component:


<table>
<tr>
<th valign="top">

App Name

</th>
<th valign="top">

Component

</th>
</tr>
<tr>
<td valign="top">

Configuration & Security Analysis

</td>
<td valign="top">

***SV-CLM-OP-CSA***

</td>
</tr>
<tr>
<td valign="top">

Job and Automation Monitoring

</td>
<td valign="top">

***SV-CLM-OP-JM***

</td>
</tr>
</table>

**Related Information**  


[SAP Cloud ALM](https://help.sap.com/docs/CloudALM?locale=en-US&state=PRODUCTION&version=latest)

