<!-- loiobc7de4ddc9fe4cbd9641f5f5140aecbc -->

# Risk-Based Authentication

Problems that you may face when configuring or using with risk-based authentication.



<a name="loiobc7de4ddc9fe4cbd9641f5f5140aecbc__section_qhv_hmk_k2c"/>

## Error: "Sorry, but you are currently not authorized for access"

**Symptom:**

SAML 2.0 authentication when using Identity Authentication fails and a similar error to below is shown:

**Sorry, but you are currently not authorized for access**

The [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816) is showing one the following errors:

**cause=rbaRulesCheckFailure, message="Denied by RBA rules"** or **"Authentication error. User not found: xxx Caused by: Could not find user <e-mail\> in mongo DB."**

**Solution:**

See KBA **2891275**- [Sorry, but you are currently not authorized for access: IAS issue](https://launchpad.support.sap.com/#/notes/2891275).



<a name="loiobc7de4ddc9fe4cbd9641f5f5140aecbc__section_wcl_kmk_k2c"/>

## Two-Factor Authentication is not taking effect in Identity Authentication

**Symptom:**

Enable two-factor authentication for an application via risk-based authentication rules.

There is no change in the behavior during sign-in.

**Solution:**

See KBA **2941888 -**[Two-Factor Authentication is not taking effect in IAS](https://launchpad.support.sap.com/#/notes/2941888).



<a name="loiobc7de4ddc9fe4cbd9641f5f5140aecbc__section_zj3_mmk_k2c"/>

## Passcode not valid upon Two-Factor Authentication

**Symptom:**

The passcode generated for two-factor authentication is invalid for a mobile device.

**Solution:**

See KBA **2968616** - [Passcode not valid upon Two-Factor Authentication](https://launchpad.support.sap.com/#/notes/2968616).

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

[Corporate User Store](corporate-user-store-3ade241.md "Problems with corporate user store scenarios.")

[Kerberos Authentication](kerberos-authentication-4bb4b24.md "Problems with Kerberos authentication scenarios.")

[Custom Domains](custom-domains-7cb2ea5.md "Problems that you may face when using custom domains in Identity Authentication.")

