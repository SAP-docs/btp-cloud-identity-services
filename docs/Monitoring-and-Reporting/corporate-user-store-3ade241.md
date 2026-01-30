<!-- loio3ade24181e164bfab0aa8c04c146b19d -->

# Corporate User Store

Problems with corporate user store scenarios.



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_ddz_kd1_j2c"/>

## Corporate user store in Cloud Foundry environment

The corporate user store feature is supported in the Cloud Foundry subaccount.

For more information about the configuration steps, see [Corporate User Store \(Cloud Foundry Environment\)](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/9942ede4fae84934a8eb184a0015c305.html).

See also KBA **3058176** - [Corporate User Store Feature in Cloud Foundry environment](https://launchpad.support.sap.com/#/notes/3058176).



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_qgf_z11_j2c"/>

## Corporate user store in Neo subaccount

The corporate user store feature is supported in the Neo subaccount.

For more information about the configuration steps, see [Corporate User Store \(Neo Environment\)](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/461d71c148594608b9c8b6d016e0a0c5.html).

See also KBA **2768285**- [OAuth Client subscription type "sci/proxy" not visible](https://launchpad.support.sap.com/#/notes/2768285).



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_w12_321_j2c"/>

## How to connect Identity Authentication to on-premise user store

**Symptom:**

There is a need to integrate Identity Authentication to an on-premise user store so that users can use their corporate credentials to access cloud applications.

**Solution:**

See KBA **2461375** - [How to connect Identity Authentication to on-premise user store](https://launchpad.support.sap.com/#/notes/2461375).



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_chk_k31_j2c"/>

## You need to remove the "Forgot password" link from the sign in screen

**Symptom:**

You need to remove the *Forgot Password* link from the Identity Authentication sign-in screen. This can be a goal when the Corporate User Store is used, and the password is managed on the Corporate User Store itself, so the forgot password functionality would not be needed.

**Solution:**

See **KBA 2607588** - [How to remove Forgot Password link from Identity Authentication logon page](https://launchpad.support.sap.com/#/notes/2607588).



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_j5g_n31_j2c"/>

## How to reset password for users from Corporate User Store

**Symptom:**

There is a need to reset the Identity Authentication service password for a user coming from the Corporate User Store. When the e-mail received to reset the password is followed, the sign-in is successful. However, at the next sign-in attempt, the newly set password does not work anymore.

**Solution:**

See KBA **2757021**- [Identity Authentication - Password reset for users from Corporate User Store](https://launchpad.support.sap.com/#/notes/2757021).



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_fbt_r31_j2c"/>

## ABAP as Corporate User Store for Identity Authentication Service

**Symptom:**

There is a need to use SAP NetWeaver AS ABAP on-premise user store in addition to Identity Authentication own cloud user store.

**Solution:**

See KBA **2942094**- [SAP AS ABAP as Corporate User Store for SAP Identity Authentication Service \(IAS\)](https://launchpad.support.sap.com/#/notes/2942094).



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_k12_t31_j2c"/>

## SAML 2.0 Response issue instant is not valid

**Symptom:**

A corporate identity provider is configured for Identity Authentication. The authentication fails with an error, meanwhile, in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is shown:

**SAML2Response issue instant is not valid.com.sap.security.saml2.sp.sso.exception.BadCredentialsException: SAML2Response issue instant is not valid.Issue Instant is not valid anymore. IssueInstant: <Date\>Curent time: <Date\>**

The caused by can be the following as well, depending on the time setting on the AD FS: **Caused by: Issue Instant is not valid yet.**

**Solution:**

See KBA **2945159**- [SAML2Response issue instant is not valid](https://launchpad.support.sap.com/#/notes/2945159).



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_fm2_w31_j2c"/>

## OAuth Client subscription type "sci/proxy" not visible

**Symptom:**

There is a need to set a subscription type to "sci/proxy" during the OAuth 2.0 configuration.

The "sci/proxy" option in the drop-down list is not present.

**Solution:**

See KBA **2768285**- [OAuth Client subscription type "sci/proxy" not visible](https://launchpad.support.sap.com/#/notes/2768285).



<a name="loio3ade24181e164bfab0aa8c04c146b19d__section_mrv_x31_j2c"/>

## Error: "End-user gets a "Sorry, we could not authenticate you. Try again" error when attempting to log in with LDAP user store"

**Symptom:**

An LDAP user store on Identity Authentication is configured, but the end-user is getting a "**Sorry, we could not authenticate you. Try again**" error when attempting to log in.

**Solution:**

See KBA **2680867**- [Check if the system user is locked when configuring and LDAP user store](https://launchpad.support.sap.com/#/notes/2680867).

**Related Information**  


[Accessing the Administration Console](accessing-the-administration-console-6187940.md "Problems with the signing into the administration console for SAP Cloud Identity Services.")

[User Import](user-import-6a46913.md "Problems with the user import in the administration console for SAP Cloud Identity Services.")

[Emails](emails-7bde0d5.md "Problems with emails sent for the different application processes.")

[Authentication](authentication-84f28fb.md "Problems with the authentication of the user and administrator.")

[Application Integration](application-integration-8acf508.md "Problems that different applications integrated with Cloud Identity Services may face.")

[Request, Create, and Delete Identity Authentication Tenant](request-create-and-delete-identity-authentication-tenant-b442658.md "Problems related to requesting, creating, or deleting a tenant.")

[End user screens](end-user-screens-a3864b5.md "Problems that you may face when working with the end user screens.")

[REST APIs](rest-apis-29ffc6b.md "Problems that you may face when using the REST APIs of Cloud Identity Services.")

[Corporate Identity Providers](corporate-identity-providers-16ab7db.md "Problems that you may face with corporate identity providers (IdPs) when using Cloud Identity services as a proxy.")

[Kerberos Authentication](kerberos-authentication-4bb4b24.md "Problems with Kerberos authentication scenarios.")

[Risk-Based Authentication](risk-based-authentication-bc7de4d.md "Problems that you may face when configuring or using with risk-based authentication.")

[Custom Domains](custom-domains-7cb2ea5.md "Problems that you may face when using custom domains in Identity Authentication.")

