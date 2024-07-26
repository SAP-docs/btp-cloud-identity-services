<!-- loiobc835e53b13c4b4d885013a79a1294f4 -->

# Monitor with SAP Cloud ALM

Identity ProvisioningSAP Cloud Identity Services - Identity Provisioning is integrated with SAP Cloud ALM, which is a cloud-based application lifecycle management offering that allows you to implement and operate your cloud solutions.



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_xxv_cg1_ybc"/>

## Initial Configuration

You can request SAP Cloud ALM on [SAP for Me](https://me.sap.com/) for yourself or for all entitled customers for whom you have sufficient permissions.

After you've requested SAP Cloud ALM, there are additional configuration steps that are required to set it up for productive use. For more information, see [Required Setup for SAP Cloud ALM](https://help.sap.com/docs/cloud-alm/setup-administration/required-setup).

To be able to use the apps, you must activate the data collection for the corresponding Managed Component:

-   in the *Configuration & Security Analysis* app. For more information, see [Configuration](https://help.sap.com/docs/cloud-alm/applicationhelp/csa-configuration).

-   in the *Job & Automation Monitoring* app. For more information, see [Job & Automation Monitoring Setup & Configuration](https://support.sap.com/en/alm/sap-cloud-alm/operations/expert-portal/job-monitoring/job-automation-monitoring-details.html).

    > ### Note:  
    > In order to send job data to SAP Cloud ALM you need a service of type *Identity Provisioning*.




<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_ojk_1sq_wbc"/>

## Configuration & Security Analysis

Via the *Configuration & Security Analysis* app of SAP Cloud ALM, you can ckeck if your Identity ProvisioningSAP Cloud Identity Services - Identity Provisioning tenant and provisioning systems are configured in alignment with the [Security recommendations for SAP Cloud Identity Services - Identity Provisioning](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?version=Cloud).

In the *Configuration & Security Analysis* app, the compliance of your configured tenant or systems to the applicable security recommendations is displayed with the following details:


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

audit\_logs

</td>
<td valign="top">

-   *empty value* - in case there is no audit logs configuration

-   number of configured OAuth clients

    > ### Caution:  
    > The compliance check displays reliable data only for bundle tenants.

-   Tenant ID, Region, Subdomain, as displayed in the *Audit Logs* tab in the SAP Cloud Identity Services Admin Console




</td>
<td valign="top">

-   *COMPLIANT* - in case there are audit configurations

-   *NONCOMPLIANT* in the following cases:

    -   there is no audit configuration

    -   you obtain a standalone tenant





</td>
<td valign="top">

*BTP\_IPS\_0001*

</td>
</tr>
<tr>
<td valign="top">

trace\_setting

</td>
<td valign="top">

-   `ips.trace.failed.entity.content` = *<value\>*

-   `ips.trace.skipped.entity.content` = *<value\>*




</td>
<td valign="top">

-   *COMPLIANT* - in case both properties are set to *false*

-   *NONCOMPLIANT* – in case one or both properties are set to *true*




</td>
<td valign="top">

*BTP\_IPS\_0002*

</td>
</tr>
<tr>
<td valign="top">

outbound\_authentication\_method

</td>
<td valign="top">

-   Authentication or `ldap.authentication` property value configured

-   Empty value if no authentication property is configured




</td>
<td valign="top">

*COMPLIANT* in the following cases:

-   If the system supports Certificate authentication and the authentication property is set to *ClientCertificateAuthentication*.

-   If the system supports **only** Basic authentication and the `Authentication` property is set to *BasicAuthentication*.


*NONCOMPLIANT* in the following cases:

-   There is no authentication property configured.

-   The system supports Certificate Authentication, but the value of the authentication property is different from *ClientCertificateAuthentication* or the certificate is not configured.




</td>
<td valign="top">

*BTP\_IPS\_0003*

</td>
</tr>
<tr>
<td valign="top">

inbound\_authentication\_method

</td>
<td valign="top">

*Basic Authentication* or*Certificate Authentication*

> ### Note:  
> The compliance check is relevant for source systems, configured for real-time provisioning, and proxy systems.

> ### Note:  
> You must have an existing destination *IPS\_MANAGE\_AUTHORIZATIONS* to be able to preview reliable data and status for the recommendation.



</td>
<td valign="top">

-   *COMPLIANT* in the following cases:

    -   The authentication type configured is Certificate Authentication.

    -   displayed by default for source systems that are not used for real-time provisioning.


-   *NONCOMPLIANT*:

    -   If the authentication type configured is Basic Authentication.

    -   If there is no configured destination *IPS\_MANAGE\_AUTHORIZATIONS* or its configuration is not correct.





</td>
<td valign="top">

*BTP\_IPS\_0004*

</td>
</tr>
<tr>
<td valign="top">

secure\_protocols

</td>
<td valign="top">

-   any `URL` property = *<value\>* 

-   Empty in case no URL properties are configured




</td>
<td valign="top">

*COMPLIANT* in the following cases:

-   If the system uses `ProxyType` *Internet* and the secure protocols used are *HTTPS* or *SSH*.

-   If the system uses `ProxyType` *OnPremise*, insecure protocols are accepted.

-   If there are no `URL` properties configured.


*NONCOMPLIANT* – In case the system uses `ProxyType` *Internet* and the protocol is insecure \(for example *HTTP*\).

</td>
<td valign="top">

*BTP\_IPS\_0005*

</td>
</tr>
<tr>
<td valign="top">

credential\_properties

</td>
<td valign="top">

-   `sensitive property` = *<value\>*

-   empty if there are no sensitive properties configured




</td>
<td valign="top">

*COMPLIANT* in the following cases:

-   If all sensitive properties are configured as type *Credential*.

-   If no sensitive properties are configured.


*NONCOMPLIANT* - In case one or more sensitive properties are configured as type *Standard*.

</td>
<td valign="top">

*BTP\_IPS\_0006*

</td>
</tr>
<tr>
<td valign="top">

trust\_all

</td>
<td valign="top">

`TrustAll` = *<value\>*

</td>
<td valign="top">

-   *COMPLIANT* - If the property `TrustAll` is set to *false*.

-   *NONCOMPLIANT* - If the property `TrustAll` is set to *true*.


> ### Note:  
> The security compliance check is not supported for connectivity destinations in the SAP BTP cockpit.



</td>
<td valign="top">

*BTP\_IPS\_0007*

</td>
</tr>
<tr>
<td valign="top">

ips\_admin\_user\_count

</td>
<td valign="top">

number of tenant administrators

> ### Note:  
> You must have an existing destination *IPS\_MANAGE\_AUTHORIZATIONS* to be able to preview reliable data and status for the recommendation.



</td>
<td valign="top">

-   *COMPLIANT* - In case the number of tenant administrators assigned is higher than one.

-   *NONCOMPLIANT*:

    -   In case there is only one tenant administrator assigned.

    -   When there is no configured destination *IPS\_MANAGE\_AUTHORIZATIONS* or its configuration is not correct.





</td>
<td valign="top">

*BTP\_IPS\_0008*

</td>
</tr>
</table>

The information is updated on a daily basis. For more information, see [Monitor Security Recommendations with SAP Cloud ALM](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/monitor-security-recommendations-with-sap-cloud-alm?version=Cloud).



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_y2l_d1r_wbc"/>

## Job & Automation Monitoring

In the *Job & Automation Monitoring* app, you can experience a central job monitoring solution. You can monitor your jobs with metrics for their execution. The supported provisioning job types are *Read* \(immediate and scheduled\), *Resync* and *Simulate*. In the *Job & Automation Monitoring* app they are grouped by system name and jоb type. You have the option to drill down from a specific row to the list of executed jobs.

For more information, see [Job & Automation Monitoring](https://help.sap.com/docs/cloud-alm/applicationhelp/job-automation-monitoring?locale=en-US%20and%20https://support.sap.com/ja/alm/sap-cloud-alm/operations/expert-portal/job-monitoring.html) and the [relevant section on the SAP Support Portal](https://support.sap.com/ja/alm/sap-cloud-alm/operations/expert-portal/job-monitoring.html).

In case you encounter problems with setting up or using the apps, you can create a case to the relevant component:

-   Configuration & Security Analysis app: SV-CLM-OP-CSA

-   Job and Automation Monitoring app: SV-CLM-OP-JM


