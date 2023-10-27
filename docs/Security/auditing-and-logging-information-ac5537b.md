<!-- loioac5537b3bf9940459a6ec7354fcd1b69 -->

# Auditing and Logging Information

Here you can find a list of the security events that are logged by Identity Authentication.

**Security events written in audit logs**


<table>
<tr>
<th valign="top">

Event grouping

</th>
<th valign="top">

What events are logged

</th>
<th valign="top">

How to identify related log events

</th>
<th valign="top">

Additional information

</th>
</tr>
<tr>
<td valign="top">

Authentication

</td>
<td valign="top">

All authentication and authorization checks.

</td>
<td valign="top">

`audit.authentication`

</td>
<td valign="top" rowspan="4">

Formatting each log in key-value pairs simplifies a lot displaying logs in systems, searching by predefined key or value, downloading logging files, etc. In the Identity Authentication audit logging interface, the following log content is available:

Caller `<caller>` did action `<action>` related to objectType `<objectType>` with unique identifier `<objectId>`. The result of this action is state `<state>` which is caused by cause `<cause>` and the message is `<message>`.

Each audit log entry consists of the following key-value pairs:

-   state\* = \[successful | aborted | failed | ignored | process\]

-   action\* = \[create | update | search | delete | upsert | add | validate | validate\_sms\_code | reset | export | import | verifyPhone | testConnection | read | restore | upload | list | provision | login | authenticate | logout | sendMail\(s\) | passwordCheck | load | rbaRuleCheck | otpCodeCheck | authenticityCheck | grantPermissions | count | setOtpAttributes | getStatistics | getUsage | setAttributes | provisionAllUsers | provisionUser\(s\) | forgotPassword | setInitialPassword | process | setConsolidationStatus | mark | sendSmsCode | issueAssertion | issueAuthorizationCode | issueJwtToken | linkUser | returningConsolidationStatus | returnungResetPasswordStatus\]

-   objectType\* = \[company | tenant\(s\) | tenantAdmin | serviceProvider\(s\) | identityProvider\(s\) | socialProvider\(s\) | service | scimGroup\(s\) | passwordPolicy\(ies\) | provisioningSystem\(s\) | allProvisioningSystems | user\(s\) | spUser |group\(s\) | thing\(s\) | contact | emailTemplates | resource | tenantLogo | scimConfiguration | smsConfiguration | spnegoConfiguration | termsOfUse | privacyPolicy | tenantSettings | trustedDomain\(s\) | tenantSamlConfiguration | auditLogClients | scimUser\(s\) | otpCode | forgotPasswordMailCounter | cockpit | usageStatistics | activityAggregator | corporateUserStore | channel | token | trustedIdp | newSpSession | activeSpAndIdpSessions | rbaAction | socialIdentity | openIdClient | googleRecaptcha | companyGroup | psrMailService| entity.Policy | entity.UserPolicy\]

-   objectId\* = \[unique attribute of the objectType – either id, or name, etc… \]

-   caller = \[The identifier of the subject\]

-   cause = \[callerUnauthorized | userNotFound | validationFailure, interrupted, otpCheckFailure, passwordCheckFailure | mailNotVerified | notSupported | alreadyUsed | maximumNumberReached | invalidCode | thirdInvalidCode | alreadyInUse | missingUserPassword | missingTargetSystemConfig\]

-   message = \[Exception message or additional message which specifies the result of the action\]

-   category\* = \[audit.authentication | audit.configuration | audit.data-change\]

-   additionalAttributes – key-value formatted attributes which are specific for each objectType

-   all change log resource types


> ### Note:  
> \* Available in each log entry.



</td>
</tr>
<tr>
<td valign="top">

Configuration

</td>
<td valign="top">

All property/properties of an entity that presents kind of configuration changes that affect the system behavior.

</td>
<td valign="top">

`audit.configuration` 

</td>
</tr>
<tr>
<td valign="top">

Data Change

</td>
<td valign="top">

All attribute/attributes of an entity changes.

</td>
<td valign="top">

`audit.data-change` 

</td>
</tr>
<tr>
<td valign="top">

Change Logs

</td>
<td valign="top">

All attribute/attributes of change logs.

</td>
<td valign="top">

audit.config-changе

</td>
</tr>
</table>

**Related Information**  


[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html)

[Audit Logging in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/02c39712c1064c96b37c1ea5bc9420dc.html)

