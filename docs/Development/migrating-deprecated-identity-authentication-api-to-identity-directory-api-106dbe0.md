<!-- loio106dbe0c3fa9473396eb204acedebe5f -->

# Migrating Deprecated Identity Authentication API to Identity Directory API

Migrating from the Identity Authentication API to Identity Directory API.



<a name="loio106dbe0c3fa9473396eb204acedebe5f__section_p1r_xp2_hwb"/>

## Documentation

**Documentation Links**


<table>
<tr>
<th valign="top">

Identity Authentication Service API \(Deprecated\)

</th>
<th valign="top">

Identity Directory Service API \(Successor\)

</th>
</tr>
<tr>
<td valign="top">

[Identity Authentication API](https://api.sap.com/api/IAS_SCIM/overview)

</td>
<td valign="top">

[Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview)

</td>
</tr>
</table>



<a name="loio106dbe0c3fa9473396eb204acedebe5f__section_ynj_v42_hwb"/>

## Endpoints Mapping

**User Management**


<table>
<tr>
<th valign="top">

HTTP Method

</th>
<th valign="top">

Identity Authentication Service API \(Deprecated\)

</th>
<th valign="top">

Identity Directory Service API \(Successor\)

</th>
</tr>
<tr>
<td valign="top">

*GET*

</td>
<td valign="top">

**`/service/scim/Users/`**

</td>
<td valign="top">

**`/scim/Users/`**

</td>
</tr>
<tr>
<td valign="top">

*GET*

</td>
<td valign="top">

**`/service/scim/Users/<id*>`**

</td>
<td valign="top">

**`/scim/Users/<id**>`**

</td>
</tr>
<tr>
<td valign="top">

*POST*

</td>
<td valign="top">

**`/service/scim/Users`**

</td>
<td valign="top">

**`/scim/Users`**

</td>
</tr>
<tr>
<td valign="top">

*PUT*

</td>
<td valign="top">

**`/service/scim/Users/<id*>`**

</td>
<td valign="top">

**`/scim/Users/<id**>`**

</td>
</tr>
<tr>
<td valign="top">

*DELETE*

</td>
<td valign="top">

**`/service/scim/Users/<id*>`**

</td>
<td valign="top">

**`/scim/Users/<id**>`**

</td>
</tr>
</table>

> ### Note:  
> \*The <id\*\> is legacy `User ID`. It is a number starting with a letter. For example, `P123456`.
> 
> \*\*The <id\*\*\> is in the universally unique identifier \(UUID\) format. For example, `1234fa2b-16or-4no7-87t7-26a02bf0bk69`.

**Group Management Endpoints**


<table>
<tr>
<th valign="top">

HTTP Method

</th>
<th valign="top">

Identity Authentication Service API \(Deprecated\)

</th>
<th valign="top">

Identity Directory Service API \(Successor\)

</th>
</tr>
<tr>
<td valign="top">

*GET*

</td>
<td valign="top">

**`/service/scim/Groups/`**

</td>
<td valign="top">

**`/scim/Groups/`**

</td>
</tr>
<tr>
<td valign="top">

*GET*

</td>
<td valign="top">

**`/service/scim/Groups/<id of the group*>`**

</td>
<td valign="top">

**`/scim/Groups/<id of the group**>`**

</td>
</tr>
<tr>
<td valign="top">

*POST*

</td>
<td valign="top">

**`/service/scim/Groups`**

</td>
<td valign="top">

**`/scim/Groups`**

</td>
</tr>
<tr>
<td valign="top">

*PUT*

</td>
<td valign="top">

**`/service/scim/Groups/<id of the group*>`**

</td>
<td valign="top">

**`/scim/Groups/<id of the group**>`**

</td>
</tr>
<tr>
<td valign="top">

*DELETE*

</td>
<td valign="top">

**`/service/scim/Groups/<id of the group*>`**

</td>
<td valign="top">

**`/scim/Groups/<id of the group**>`**

</td>
</tr>
</table>

> ### Note:  
> \*The <id of the group\*\> is in a legacy ID format. For example, `63c468ode3c07406970900kc`.
> 
> \*\*The <id of the group\*\*\> is in the universally unique identifier \(UUID\) format. For example, `7369fa2b-16as-4sd7-87c7-26a01of0bk78`.

> ### Remember:  
> To assign group to a user, use the groups endpoint.



## Attributes Mapping

**Manage Users Attributes Mapping**


<table>
<tr>
<th valign="top">

Identity Authentication Service API \(Deprecated\)

</th>
<th valign="top">

Identity Directory Service API \(Successor\)

</th>
</tr>
<tr>
<td valign="top">

`id`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.userId`

</td>
</tr>
<tr>
<td valign="top">

`emails.value`

</td>
<td valign="top">

`emails.value`

</td>
</tr>
<tr>
<td valign="top">

`name.honorificPrefix`

</td>
<td valign="top">

`name.honorificPrefix`

</td>
</tr>
<tr>
<td valign="top">

`name.givenName`

</td>
<td valign="top">

`name.givenName`

</td>
</tr>
<tr>
<td valign="top">

`name.familyName`

</td>
<td valign="top">

`name.familyName`

</td>
</tr>
<tr>
<td valign="top">

`name.middleName`

</td>
<td valign="top">

`name.middleName`

</td>
</tr>
<tr>
<td valign="top">

`userName`

</td>
<td valign="top">

`userName`

</td>
</tr>
<tr>
<td valign="top">

`addresses.streetAddress``addresses.locality``addresses.region``addresses.postalCode``addresses.country```

</td>
<td valign="top">

`addresses.streetAddress``addresses.locality``addresses.region``addresses.postalCode``addresses.country``urn:ietf:params:scim:schemas:extension:sap:2.0:User.addresses.streetAddress2`

</td>
</tr>
<tr>
<td valign="top">

`addresses.streetAddress``addresses.locality``addresses.region``addresses.postalCode``addresses.country```

</td>
<td valign="top">

`addresses.streetAddress``addresses.locality``addresses.region``addresses.postalCode``addresses.country``urn:ietf:params:scim:schemas:extension:sap:2.0:User.addresses.streetAddress2`

</td>
</tr>
<tr>
<td valign="top">

`locale`

</td>
<td valign="top">

`locale`

</td>
</tr>
<tr>
<td valign="top">

`phoneNumbers[work].value`

</td>
<td valign="top">

`phoneNumbers[work].value`

</td>
</tr>
<tr>
<td valign="top">

`phoneNumbers[mobile].value`

</td>
<td valign="top">

`phoneNumbers[mobile].value`

</td>
</tr>
<tr>
<td valign="top">

`phoneNumbers[fax].value`

</td>
<td valign="top">

`phoneNumbers[fax].value`

</td>
</tr>
<tr>
<td valign="top">

`timeZone`

</td>
<td valign="top">

`timezone`

</td>
</tr>
<tr>
<td valign="top">

`password`

</td>
<td valign="top">

`password`

</td>
</tr>
<tr>
<td valign="top">

`passwordStatus`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.passwordDetails.status`

</td>
</tr>
<tr>
<td valign="top">

`active`

</td>
<td valign="top">

`active`

</td>
</tr>
<tr>
<td valign="top">

`displayName`

</td>
<td valign="top">

`displayName`

</td>
</tr>
<tr>
<td valign="top">

`contactPreferenceEmail`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.contactPreferences.email`

</td>
</tr>
<tr>
<td valign="top">

`contactPreferenceTelephone`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.contactPreferences.telephone`

</td>
</tr>
<tr>
<td valign="top">

`industryCrm`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.industry`

</td>
</tr>
<tr>
<td valign="top">

`company`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.organization`

</td>
</tr>
<tr>
<td valign="top">

`companyRelationship`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User:companyRelationship`

</td>
</tr>
<tr>
<td valign="top">

`department`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.department`

</td>
</tr>
<tr>
<td valign="top">

`title`

</td>
<td valign="top">

``

</td>
</tr>
<tr>
<td valign="top">

`groups`

</td>
<td valign="top">

`groups`

</td>
</tr>
<tr>
<td valign="top">

`passwordLoginTime`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.passwordDetails.loginTime`

</td>
</tr>
<tr>
<td valign="top">

`loginTime`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.loginTime`

</td>
</tr>
<tr>
<td valign="top">

`passwordSetTime`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.passwordDetails.setTime`

</td>
</tr>
<tr>
<td valign="top">

``

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.validFrom`

</td>
</tr>
<tr>
<td valign="top">

``

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.validTo`

</td>
</tr>
<tr>
<td valign="top">

`scenarios`

</td>
<td valign="top">

``

</td>
</tr>
<tr>
<td valign="top">

`termsOfUse`

</td>
<td valign="top">

`termsOfUse`

</td>
</tr>
<tr>
<td valign="top">

`privacyPolicy`

</td>
<td valign="top">

`privacyPolicy`

</td>
</tr>
<tr>
<td valign="top">

`newsletters`

</td>
<td valign="top">

``

</td>
</tr>
<tr>
<td valign="top">

`userType`

</td>
<td valign="top">

`userType`

</td>
</tr>
<tr>
<td valign="top">

`sourceSystem`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.sourceSystem`

</td>
</tr>
<tr>
<td valign="top">

``

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.sourceSystemId`

</td>
</tr>
<tr>
<td valign="top">

`socialIdentities`

</td>
<td valign="top">

``

</td>
</tr>
<tr>
<td valign="top">

`sendMail`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.sendMail`

</td>
</tr>
<tr>
<td valign="top">

`mailVerified`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.emails.verified`

</td>
</tr>
<tr>
<td valign="top">

`telephoneVerified`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.phoneNumbers.verified`

</td>
</tr>
<tr>
<td valign="top">

`telephoneVerificationAttempts`

</td>
<td valign="top">

``

</td>
</tr>
<tr>
<td valign="top">

`passwordPolicy`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.passwordDetails.policy`

</td>
</tr>
<tr>
<td valign="top">

`passwordStatus`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.passwordDetails.status`

</td>
</tr>
<tr>
<td valign="top">

`passwordFailedLoginAttempts`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.passwordDetails.failedLoginAttempts`

</td>
</tr>
<tr>
<td valign="top">

`applicationId`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.applicationId`

</td>
</tr>
<tr>
<td valign="top">

``

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.activationUrl`

</td>
</tr>
<tr>
<td valign="top">

`targetUrl`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.targetUrl`

</td>
</tr>
<tr>
<td valign="top">

`emailTemplateSetId`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User.emailTemplateSetId`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.employeeNumber`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.employeeNumber`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.organization`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.organization`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.costCenter`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.costCenter`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.division`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.division`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.manager.value`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.manager.value`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.manager.$ref`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.manager.$ref`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.manager.displayName`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.manager.displayName`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.department`

</td>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User.department`

</td>
</tr>
<tr>
<td valign="top">

`urn:sap:cloud:scim:schemas:extension:custom:2.0:User.attributes.`

</td>
<td valign="top">

`urn:sap:cloud:scim:schemas:extension:custom:2.0:User.attributes.`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute1`

</td>
<td valign="top">

`customAttribute1`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute2`

</td>
<td valign="top">

`customAttribute2`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute3`

</td>
<td valign="top">

`customAttribute3`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute4`

</td>
<td valign="top">

`customAttribute4`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute5`

</td>
<td valign="top">

`customAttribute5`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute6`

</td>
<td valign="top">

`customAttribute6`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute7`

</td>
<td valign="top">

`customAttribute7`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute8`

</td>
<td valign="top">

`customAttribute8`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute9`

</td>
<td valign="top">

`customAttribute9`

</td>
</tr>
<tr>
<td valign="top">

`customAttribute10`

</td>
<td valign="top">

`customAttribute10`

</td>
</tr>
</table>

**Manage Groups Attributes Mapping**


<table>
<tr>
<th valign="top">

Identity Authentication Service API \(Deprecated\)

</th>
<th valign="top">

Identity Directory Service API \(Successor\)

</th>
</tr>
<tr>
<td valign="top">

`id`

</td>
<td valign="top">

`urn:sap:cloud:scim:schemas:extension:custom:2.0:Group.additionalId`

</td>
</tr>
<tr>
<td valign="top">

`displayName`

</td>
<td valign="top">

`displayName`

</td>
</tr>
<tr>
<td valign="top">

`members.value`

</td>
<td valign="top">

`members.value`

</td>
</tr>
<tr>
<td valign="top">

`members.$ref`

</td>
<td valign="top">

`members.$ref`

</td>
</tr>
<tr>
<td valign="top">

`members.display`

</td>
<td valign="top">

``

</td>
</tr>
<tr>
<td valign="top">

``

</td>
<td valign="top">

`members.type`

</td>
</tr>
<tr>
<td valign="top">

`urn:sap:cloud:scim:schemas:extension:custom:2.0:Group.name`

</td>
<td valign="top">

`urn:sap:cloud:scim:schemas:extension:custom:2.0:Group.name`

</td>
</tr>
<tr>
<td valign="top">

`urn:sap:cloud:scim:schemas:extension:custom:2.0:Group.description`

</td>
<td valign="top">

`urn:sap:cloud:scim:schemas:extension:custom:2.0:Group.description`

</td>
</tr>
<tr>
<td valign="top">

`urn:sap:cloud:scim:schemas:extension:custom:2.0:Group.groupId`

</td>
<td valign="top">

`id`

</td>
</tr>
<tr>
<td valign="top">

``

</td>
<td valign="top">

`externalId`

</td>
</tr>
</table>

**Related Information**  


[Application Configurations API](application-configurations-api-a8fc935.md "Manage application configurations.")

[Identity Directory API](identity-directory-api-5be5692.md "Manage users, groups and custom schemas in the cloud.")

[Identity Provisioning API](identity-provisioning-api-4433374.md "Manage identity lifecycle processes for cloud and on-premise systems.")

[Identity Authentication API \(Deprecated\)](identity-authentication-api-deprecated-2f21568.md "Deprecated.")

[Invitation REST API](invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Management REST API](user-management-rest-api-e6bb70d.md "This REST API allows you to implement a request for user management, such as user registration, as well as SP user retrieval, deactivation and deletion.")

[Password Service REST API](password-service-rest-api-8d1016b.md "The password service is used for operations related to user passwords, such as verification of the user name and the password combination.")

[Forgot Password REST API](forgot-password-rest-api-d024fca.md "The forgot password REST API sends a reset password email.")

[TOTP Validation Service](totp-validation-service-3e4c3cf.md "Validation of time-based one-time password (TOTP).")

[Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6 "The Change Tenant Texts REST API of Identity Authentication can be used to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.")

[Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c "The Change Master Data Texts REST API can be used to change the predefined master data for each resource in Identity Authentication.")

