<!-- loiobc835e53b13c4b4d885013a79a1294f4 -->

# Monitoring with SAP Cloud ALM

SAP Cloud Identity Services are integrated with SAP Cloud ALM, which is a cloud-based application lifecycle management offering that enables you to implement, operate, and monitor your cloud solutions.



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_xxv_cg1_ybc"/>

## Initial Configuration

You can request SAP Cloud ALM on [SAP for Me](https://me.sap.com/) for yourself or for all customers for whom you have permissions.

After you've requested SAP Cloud ALM, follow the steps to set it up. For more information, see [Required Setup for SAP Cloud ALM](https://help.sap.com/docs/cloud-alm/setup-administration/required-setup).

To use the SAP Cloud ALM apps you must activate the data collection for the *Identity Authentication* and/or*Identity Provisioning* component. For more information, see [Setup for SAP Cloud Identity Services – Identity Authentication](https://support.sap.com/en/alm/sap-cloud-alm/operations/expert-portal/setup-managed-services/calm-setup-ia.html) and[Setup for SAP Cloud Identity Services – Identity Provisioning](https://support.sap.com/en/alm/sap-cloud-alm/operations/expert-portal/setup-managed-services/calm-setup-ip.html).



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_ojk_1sq_wbc"/>

## Configuration & Security Analysis

With the Configuration & Security Analysis app of SAP Cloud ALM, you can check if your Cloud Identity tenants and provisioning systems are configured in alignment with the [Security Recommendations - Identity Authentication](https://help.sap.com/docs/BTP/c8a9bb59fe624f0981efa0eff2497d7d/531f33def8074ccdb6f1f784a34dafcb.html?seclist-index=BTP-IAS) and[Security Recommendations - Identity Provisioning](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS&version=Cloud) and [Monitoring with SAP Cloud ALM](monitoring-with-sap-cloud-alm-bc835e5.md).

> ### Note:  
> Identity Provisioning reports data to SAP Cloud ALM daily. For more information, see [Monitor Security Recommendations with SAP Cloud ALM](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/monitor-security-recommendations-with-sap-cloud-alm?version=Cloud).
> 
> Identity Authentication and Identity Provisioning report data to SAP Cloud ALM daily. For more information, see [Monitor Security Recommendations with SAP Cloud ALM](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/monitor-security-recommendations-with-sap-cloud-alm?version=Cloud).

In the Configuration & Security Analysis app, the compliance of your configured tenants or systems to the applicable security recommendations is displayed with the following details:

**Configuration & Security Analysis Details**


<table>
<tr>
<th valign="top">

Service

</th>
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

Identity Provisioning

</td>
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

[BTP-IPS-0001](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS-0001&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Provisioning

</td>
<td valign="top">

***trace\_setting***

</td>
<td valign="top">

The *Data Record* displays the values set for the properties that enable logging and tracing for personal and sensitive data of the provisioned entities:

-   `ips.trace.failed.entity.content` = *<value\>*

-   `ips.trace.skipped.entity.content` = *<value\>*

-   `ips.trace.created.entity.content` = *<value\>*




</td>
<td valign="top">

*COMPLIANT* - when all three properties are set to *false*

*NONCOMPLIANT* – if one or more of these properties are set to *true*

</td>
<td valign="top">

[BTP-IPS-0002](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS-0002&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Provisioning

</td>
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

[BTP-IPS-0003](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS-0003&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Provisioning

</td>
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

[BTP-IPS-0004](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS-0004&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Provisioning

</td>
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

[BTP-IPS-0005](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS-0005&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Provisioning

</td>
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

    empty - if there are no sensitive properties configured


If there are no sensitive properties configured, the value is empty.

</td>
<td valign="top">

*COMPLIANT* in the following cases:

-   All sensitive properties are configured as type *Credential*.

-   There are no sensitive properties configured.


*NONCOMPLIANT* if one or more sensitive properties are configured as type *Standard*.

</td>
<td valign="top">

[BTP-IPS-0006](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS-0006&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Provisioning

</td>
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

[BTP-IPS-0007](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS-0007&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Provisioning

</td>
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

[BTP-IPS-0008](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IPS-0008&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***ID***

</td>
<td valign="top">

Reports the Id of the service provider or corporate identity provider \(IdP\).

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***TYPE***

</td>
<td valign="top">

Reports the type of the service provider \(`SYSTEM_APP`, `BUNDLED_APP` or `CHARGED_APP`\) or `CORPORATE_IDP` for corporate IdPs.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***NAME***

</td>
<td valign="top">

Reports the name of the service provider or corporate IdP.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***certificate\_authentication***

</td>
<td valign="top">

Checks whether the certificate generation and authentication is enabled for each of the user types. If it is, the user types are displayed in a comma separated string: `usertypes`: `employee`,`partner`. If there are no user types for which the setting is enabled, the value is empty.

</td>
<td valign="top">

*COMPLIANT* - if there is at least 1 user type for which the setting is enabled.

*NONCOMPLIANT* - if there are no user types for which the setting is enabled.

</td>
<td valign="top">

[BTP-IAS-0006](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0006&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***audit\_logs***

</td>
<td valign="top">

Checks whether there is an audit log configuration. If there is, the value is *CONFIGURED*. If there is not, the value is `empty`.

</td>
<td valign="top">

*COMPLIANT* - in case there are audit logs configurations.

*NONCOMPLIANT* - in case there are *NO* audit logs configurations.

</td>
<td valign="top">

[BTP-IAS-0011](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0011&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***custom\_domain***

</td>
<td valign="top">

Checks whether the custom domain is configured. If it is, the value is *CONFIGURED*. If it is not, the value is empty.

</td>
<td valign="top">

*COMPLIANT* - if the custom domain is configured.

*NONCOMPLIANT* - if the custom domain is *NOT* configured.

</td>
<td valign="top">

[BTP-IAS-0019](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0019&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***mail\_server\_configuration***

</td>
<td valign="top">

Checks whether there is a custom mail server configured. If the custom mail server is of type AWS, then the value is `aws`, otherwise the value is `custom`. If the there is no custom mail server configuration, the value is empty.

</td>
<td valign="top">

*COMPLIANT* - if the custom mail server is configured.

*NONCOMPLIANT* - if the custom mail server is NOT configured.

</td>
<td valign="top">

[BTP-IAS-0020](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0020&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***system\_notification***

</td>
<td valign="top">

Checks whether the admin console is configured to send emails about expiring certificates, system notifications, and new administrators to specific e-mail addresses, to the email addresses of all administrators or to none. If there are no email recipients, the value is empty. If the number of configured recipients is equal to the number of user admins or the setting to send the notifications to all admins is enabled, the value is `configured`. Otherwise it is `misconfigured`.

</td>
<td valign="top">

*COMPLIANT* - If the number of configured recipients is equal to the number of user admins or the setting to send the notifications to all admins is `enabled`.

*NONCOMPLIANT* - If there are no email recipients or if it is `misconfigured`.

</td>
<td valign="top">

[BTP-IAS-0022](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0022&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***security\_alerts***

</td>
<td valign="top">

Checks whether alerts are enabled for security critical events like email, login names, password or two-factor authentication \(TFA\) configuration changes. The value is a comma-separated string with the status for each of the categories.

> ### Example:  
> `email_change=ON,login_name_change=ON,password_change=ON,tfa_change=ON`



</td>
<td valign="top">

*COMPLIANT* - if the security alerts are enabled for the following:

-   Email change

-   Login Name change

-   Credential change

-   TFA device activation or deactivation; postpone enabling of Two-Factor Authentication


*NONCOMPLIANT* - if the security alerts are not configured or one of the above is disabled.

</td>
<td valign="top">

[BTP-IAS-0023](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0023&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***days\_without\_mfa\_prompt***

</td>
<td valign="top">

Reports the number of days for which the users will not get prompted for second-factor authentication, if they sign in from the same browser. If the property is not configured, the value is empty.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***self\_registration\_link\_lifetime\_seconds***

</td>
<td valign="top">

Reports the validity of the link sent to user for self registration in seconds.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***on\_behalf\_link\_lifetime\_seconds***

</td>
<td valign="top">

Reports the validity of the link sent to user for on-behalf registration in seconds.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***invitation\_link\_lifetime\_seconds***

</td>
<td valign="top">

Reports the validity of the link sent to user for invitation in seconds.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***forgot\_password\_lifetime\_seconds***

</td>
<td valign="top">

Reports the validity of the link sent to user for forgotten password in seconds.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***reset\_password\_lifetime\_seconds***

</td>
<td valign="top">

Reports the validity of the link sent to user for password reset in seconds.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***locked\_password\_lifetime\_seconds***

</td>
<td valign="top">

Reports the validity of the link sent to user for locked password in seconds.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***initial\_password\_token\_lifetime\_seconds***

</td>
<td valign="top">

Reports the validity of the initial password set to user in seconds.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***idp\_initiated\_sso***

</td>
<td valign="top">

Reports whether the IdP-initiated Single Sign On \(SSO\) is enabled.

If it is enabled, the value is *ON*. Otherwise the value is *OFF*.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***manage\_identity\_provisioning\_admin\_count***

</td>
<td valign="top">

Reports the count of users and systems authorized to access the [Application Configuration API](https://api.sap.com/api/SCI_Application_Directory/overview) for running Identity Provisioning jobs or downloading job logs.

> ### Example:  
> `systems=0;users=1`



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***read\_users\_admin\_count***

</td>
<td valign="top">

Reports the count of users and systems authorized to read and export users.

> ### Example:  
> `systems=0;users=1`



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***manage\_applications\_admin\_count***

</td>
<td valign="top">

Reports the count of users and systems authorized to configure applications.

> ### Example:  
> `systems=0;users=1`



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***manage\_users\_admin\_count***

</td>
<td valign="top">

Reports the count of users and systems authorized to manage, export, and import users.

> ### Example:  
> `systems=0;users=1`



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***manage\_corp\_idp\_admin\_count***

</td>
<td valign="top">

Reports the count of users and systems authorized to configure corporate identity providers.

> ### Example:  
> `systems=0;users=1`



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***manage\_groups\_admin\_count***

</td>
<td valign="top">

Reports the count of users and systems authorized to manage user groups.

> ### Example:  
> `systems=0;users=1`



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***manage\_tenant\_configuration\_admin\_count***

</td>
<td valign="top">

Reports the count of users and systems authorized to manage tenant configuration and authorization assignment to users.

> ### Example:  
> `systems=0;users=1`



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***admin\_console\_mfa***

</td>
<td valign="top">

Checks whether multi-factor authentication \(MFA\) is configured for the administration console. The possible values are:

-   `delegated_to_corp_idp` - if the administration console is set in full proxy mode and the "Apply Application Configurations" setting of the corporate IdP is disabled.
-   `configured` - if there is a TFA action configured on either service provider \(SP\) or on a tenant level.
-   `misconfigured` - if there is no TFA action configured.



</td>
<td valign="top">

*COMPLIANT* - if there is a TFA action configured.

*NONCOMPLIANT* - if there is no TFA action configured.

*UNRATED* - if it is delegated to the corporate IdP.

</td>
<td valign="top">

[BTP-IAS-0001](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0001&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***password\_policy***

</td>
<td valign="top">

Checks whether a password policy is configured. The possible values are:

-   `delegated_to_corp_idp` - if the SP is set in full proxy mode.
-   `standard` - if the password policy is set to the default standard one.
-   `enterprise` - if the password policy is set to the default enterprise one.
-   `custom` - if a custom password policy is configured.
-   `empty` - if there is no password policy set.



</td>
<td valign="top">

*COMPLIANT* - if the password policy is either custom or enterprise.

*NONCOMPLIANT* - if the password policy is either standard or none is set.

*UNRATED* - if it is delegated to the corporate IdP.

</td>
<td valign="top">

[BTP-IAS-0002](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0002&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***user\_application\_access***

</td>
<td valign="top">

Checks the access of end users to the application. The possible values are:

-   `public` - Everyone can access the application; new users can register using the self-registration process.
-   `internal` - Only existing users can access the application.
-   `private` - Only users registered by the application can log on.
-   empty - If the property is inherited from the parent application.



</td>
<td valign="top">

*COMPLIANT* - if the access is restricted only to existing users. `value=internal`.

*NONCOMPLIANT* - `value=public` or `value=private` or the value is inherited from the parent application.

</td>
<td valign="top">

[BTP-IAS-0003](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0003&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***social\_sign\_on***

</td>
<td valign="top">

Checks whether social sign-on \(SSO\) is enabled. If it is enabled, the value is *ON*. If it is disabled, the value is *OFF*. The value is empty if the property is inherited from the parent application.

</td>
<td valign="top">

*COMPLIANT* - if SSO is disabled.

*NONCOMPLIANT* - if SSO is enabled.

*UNRATED* - if it is inherited from the parent application.

</td>
<td valign="top">

[BTP-IAS-0005](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0005&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***disable\_password\_authentication***

</td>
<td valign="top">

Checks whether the default authentication method for end users to authenticate with the service is *user name* and *password*. The possible values are:

-   empty - if the configured IdP is not the default local IdP, or there is no RBA configuration, or there are no RBA rules.
-   `configured` - in case the configuration matches the described in the *COMPLIANT* status .
-   `partially configured` - the default action of the RBA configuration is either *Allow* or *TFA* and there is a RBA rule with action *Deny* which only has authentication method set to *User Name and Password* and there is a RBA rule with action different from *Deny*.



</td>
<td valign="top">

*COMPLIANT*

-   if the default action of the RBA configuration and the actions of all the RBA rules is *Deny*.
-   the default action of the RBA configuration is either *Allow* or *TFA* and there is a RBA rule with action *Deny* which only has authentication method set to *User Name and Password*.

NONCOMPLIANT

-   if the default action is *Deny* and the action of any of the RBA rules is *Allow* or *TFA* and the authentication method is either not configured or *User Name and Password*.
-   the default action of the RBA configuration is either *Allow* or *TFA* and there are no RBA rules.



</td>
<td valign="top">

[BTP-IAS-0006](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0006&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***branding***

</td>
<td valign="top">

Checks whether there is branding of the organization added to the logon screen. The possible values are:

-   empty - if there is no logo resource configured and the custom CSS is not enabled.
-   `configured` - if there is logo resource configured or the custom CSS is enabled.



</td>
<td valign="top">

*COMPLIANT* - if there is logo resource configured or the custom CSS is enabled.

*NONCOMPLIANT* - if there is no logo resource configured and the custom CSS is not enabled.

</td>
<td valign="top">

[BTP-IAS-0021](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0021&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***reCAPTCHA***

</td>
<td valign="top">

Checks whether self-registration and CAPTCHA are enabled. The possible values are: 1. empty if CAPTCHA is not enabled. 2. configured: if CAPTCHA is enabled for at least the registration form or the login page.

</td>
<td valign="top">

COMPLIANT - if the self-registration is disabled or CAPTCHA is enabled. NONCOMPLIANT - if self-registration is enabled or CAPTCHA is disabled.

</td>
<td valign="top">

[BTP-IAS-0025](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0025&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***default\_rba\_auth\_action***

</td>
<td valign="top">

Reports the default action set in the RBA configuration of the application. The possible values are:

-   *Allow*
-   *Deny*
-   *TFA*



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***default\_authenticating\_idp\_id***

</td>
<td valign="top">

Reports the `id` of the configured corporate IdP.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***default\_authenticating\_idp\_name***

</td>
<td valign="top">

Reports the name of the configured corporate IdP.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***default\_authenticating\_idp\_display\_name***

</td>
<td valign="top">

Reports the display name of the configured corporate IdP.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***default\_authenticating\_idp\_type***

</td>
<td valign="top">

Reports the type of the configured corporate IdP.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***trust\_all\_corporate\_idp***

</td>
<td valign="top">

Reports whether the *Trust All Corporate Identity Providers* setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

*****allow\_ias\_users\_log\_on*****

</td>
<td valign="top">

Reports whether the *Allow Identity Authentication Users Log On* setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***spnego\_enabled***

</td>
<td valign="top">

Reports whether the *SPNEGO Authentication* setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***biometric\_authentication\_enabled***

</td>
<td valign="top">

Reports whether the *Biometric Authentication* setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***force\_authentication***

</td>
<td valign="top">

Reports whether the *Force Authentication* setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***default\_signing\_algorithm***

</td>
<td valign="top">

Reports the *Signing Algorithm* configuration. The possible values are:

-   *SHA-1*
-   *SHA-256*
-   *SHA-512*



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***concurrent\_access***

</td>
<td valign="top">

Reports the Concurrent Access configuration. The possible values are:

-   *Allow*
-   *Warning*
-   *Error*



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***identity\_provider\_id***

</td>
<td valign="top">

Reports the `id` of the corporate IdP.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***identity\_provider\_name***

</td>
<td valign="top">

Reports the name of the corporate IdP. The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***identity\_provider\_display\_name***

</td>
<td valign="top">

Reports the display name of the corporate idP.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***identity\_provider\_type***

</td>
<td valign="top">

Reports the type of the corporate IdP. Possible values are:

-   *MS\_ADFS\_2.0 \(Microsoft ADFS / Entra ID \(SAML 2.0\)\)*
-   *SAML\_2.0 \(SAML 2.0 Compliant\)*
-   *OPENID\_CONNECT \(OpenID Connect Compliant\)**NW\_SSO \(SAP Single Sign-On \(SAML 2.0\)\)*



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***forward\_all\_sso\_requests***

</td>
<td valign="top">

Reports whether the *Forward All SSO Requests to Corporate IdP* setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***use\_identity\_auth\_user\_store***

</td>
<td valign="top">

Reports whether the *Use Identity Authentication user store* setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*COMPLIANT* - if enabled.

*NONCOMPLIANT* - if disabled.

</td>
<td valign="top">

[BTP-IAS-0015](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0015&version=Cloud)

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***allow\_identity\_auth\_users\_only***

</td>
<td valign="top">

Reports whether the *Allow Identity Authentication users only* setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***apply\_app\_auth\_configs***

</td>
<td valign="top">

Reports whether the "Apply Application Configurations" setting is enabled. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***logout\_redirect\_url***

</td>
<td valign="top">

Reports *Logout Redirect URL*. The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***default\_signing\_algorithm***

</td>
<td valign="top">

Reports the *Signing Algorithm* configuration only if the type is `NOT OPENID_CONNECT`. The possible values are:

-   *SHA-1*
-   *SHA-256*
-   *SHA-512*



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***sign\_authentication\_requests***

</td>
<td valign="top">

Reports whether the *Sign authentication requests* setting is enabled only if the type is `NOT OPENID_CONNECT`.

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***sign\_logout\_messages***

</td>
<td valign="top">

Reports whether the *Sign single logout messages* setting is enabled only if the type is `NOT OPENID_CONNECT`. The possible values are:

-   *ON*- if enabled
-   *OFF* - if disabled



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***PRIORITY***

</td>
<td valign="top">

Reports the index of the rule based on priority.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***IDENTITY\_PROVIDER\_ID***

</td>
<td valign="top">

Reports the id of the corporate IdP.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***IDENTITY\_PROVIDER\_NAME***

</td>
<td valign="top">

Reports the name of the corporate IdP. Empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***IDENTITY\_PROVIDER\_DISPLAY\_NAME***

</td>
<td valign="top">

 

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***USER\_TYPE***

</td>
<td valign="top">

Reports the user type of the rule. Possible values are: `employee`, `public`, `partner`, `customer`, `external`, `onboardee`, `alumni`. The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***USER\_GROUP***

</td>
<td valign="top">

Reports the name of the group. The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***USER\_EMAIL\_DOMAIN***

</td>
<td valign="top">

Reports the email domain of the rule. The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***IP\_NETWORK\_RANGE***

</td>
<td valign="top">

Reports the IP network range of the rule in CIDR format.

> ### Example:  
> `10.10.10.10/11`

The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***PRIORITY***

</td>
<td valign="top">

Reports the index of the rule based on priority.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***IP\_NETWORK\_RANGE***

</td>
<td valign="top">

Reports the IP network range of the rule in CIDR format.

> ### Example:  
> `10.10.10.10/11`

Empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***IP\_FORWARD\_RANGE***

</td>
<td valign="top">

Reports the IP forward range of the rule in CIDR format.

> ### Example:  
> `10.10.10.10/11`

The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***ACTION***

</td>
<td valign="top">

Reports the action of the rule. The possible values are:

-   *Allow*
-   *Deny*
-   *TFA*



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***GROUP\_TYPE***

</td>
<td valign="top">

Reports the name of the group. Possible values are:

-   *Cloud \(Cloud Group\)*
-   *Corporate\(On-Premise Group\)*
-   The value is empty if not configured.



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

******AUTH\_METHOD

</td>
<td valign="top">

Reports the authentication method for the rule. Possible values are:

-   *CERT\(Client Certificate\)**SPNEGO*
-   *UID\_PW \(User Name and Password\)*
-   *TOKEN \(Token\)*
-   *SOCIAL\_IDENTITY \(Social identity Provider\)*
-   *TRUSTED\_IDP\_SAML\_ASSERTION \(Trusted IdP SAML Assertion\)*
-   The value is empty if not configured.



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***USER\_ATTRIBUTES***

</td>
<td valign="top">

Reports the user attributes for the rule in format of `key=value`. The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***CORPORATE\_IDP\_ATTRIBUTE***

</td>
<td valign="top">

Reports the corporate IdP attribute for the rule in format of `key=value`. The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***USER\_EMAIL\_DOMAIN***

</td>
<td valign="top">

Reports the email domain of the rule. The value is empty if not configured.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***PASSWORD\_POLICY\_NAME***

</td>
<td valign="top">

Reports the name of the password policy.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***PASSWORD\_POLICY\_STRENGTH***

</td>
<td valign="top">

Reports the strength of the password policy.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***MINIMUM\_PASSWORD\_LENGTH***

</td>
<td valign="top">

Reports the minimum length of characters of the password policy.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***MINIMUM\_PASSWORD\_AGE\_HOURS***

</td>
<td valign="top">

Reports the minimum password age in hours.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***USER\_INACTIVITY\_MONTHS***

</td>
<td valign="top">

Reports the maximum user inactivity in months.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***PASSWORD\_HISTORY\_ENTRY\_COUNT***

</td>
<td valign="top">

Reports the password history entry count.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***FAILED\_SIGN\_IN\_ATTEMPTS***

</td>
<td valign="top">

Reports the failed sign in attempts.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***PASSWORD\_LOCKED\_PERIOD\_HOURS***

</td>
<td valign="top">

Reports the password locked period in hours.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***REQUIRED\_CHARACTER\_GROUPS***

</td>
<td valign="top">

Reports the number of the required character groups.

</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
<tr>
<td valign="top">

Identity Authentication

</td>
<td valign="top">

***PASSWORD\_BEHAVIOUR***

</td>
<td valign="top">

Reports the password behavior of the policy. Possible values are:

-   *reset*
-   *change*



</td>
<td valign="top">

*n/a*

</td>
<td valign="top">

*n/a*

</td>
</tr>
</table>



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_y2l_d1r_wbc"/>

## Job & Automation Monitoring

In the Job & Automation Monitoring app, you can monitor the execution of your provisioning jobs using specific metrics. The supported provisioning job types are *Read* \(immediate and scheduled\), *Resync* and *Simulate*. In the Job & Automation Monitoring app they are grouped by system name and jоb type. You have the option to drill down from a specific row to the list of executed jobs.

For more information, see [Job & Automation Monitoring](https://help.sap.com/docs/cloud-alm/applicationhelp/job-automation-monitoring?locale=en-US%20and%20https://support.sap.com/ja/alm/sap-cloud-alm/operations/expert-portal/job-monitoring.html) and the [relevant section on the SAP Support Portal](https://support.sap.com/ja/alm/sap-cloud-alm/operations/expert-portal/job-monitoring.html).



<a name="loiobc835e53b13c4b4d885013a79a1294f4__section_lpp_hzx_p2c"/>

## Getting Support

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

