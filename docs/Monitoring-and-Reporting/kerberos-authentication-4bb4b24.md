<!-- loio4bb4b247a47e47a59b88378500ffbe82 -->

# Kerberos Authentication

Problems with Kerberos authentication scenarios.



<a name="loio4bb4b247a47e47a59b88378500ffbe82__section_nch_kjk_k2c"/>

## Error "Kerberos Authentication fails with Could not decrypt the encrypted data error"

**Symptom:**

Kerberos authentication is configured for Identity Authentication to allow users to log on without a username and password when they are in the corporate network based on [Configure Kerberos Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/b0301657df074ab081ab7556854aca56.html#loiob0301657df074ab081ab7556854aca56)' SAP Help documentation.

However, users are still prompted to authenticate with a username and password.

The [Troubleshooting Log](https://launchpad.support.sap.com/#/notes/2942816) shows the following error:

**Could not validate SPNEGO token: Could not decrypt the encrypted data**

**Solution:**

See KBA **2958786** - [Kerberos Authentication fails with Could not decrypt the encrypted data error](https://launchpad.support.sap.com/#/notes/2958786).



<a name="loio4bb4b247a47e47a59b88378500ffbe82__section_jxq_4jk_k2c"/>

## Kerberos Authentication fails with Unsupported encryption SPNEGO token type error

**Symptom:**

Kerberos authentication is configured for Identity Authentication to allow users to log on without a username and password when they are in the corporate network based on [Configure Kerberos Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/b0301657df074ab081ab7556854aca56.html#loiob0301657df074ab081ab7556854aca56) SAP Help documentation.

However, users are still prompted to authenticate with a username and password.

The [Troubleshooting Log](https://launchpad.support.sap.com/#/notes/2942816) shows the following error:

**Unsupported encryption SPNEGO token type**

**Solution:**

See KBA **2958806** - [Kerberos Authentication fails with Unsupported encryption SPNEGO token type error](https://launchpad.support.sap.com/#/notes/2958806).



<a name="loio4bb4b247a47e47a59b88378500ffbe82__section_mkb_tjk_k2c"/>

## Supported number of realms or domains for Kerberos/SPNEGO in Identity Authentication

**Symptom:**

There is a need to know how many realms or domains are supported for Kerberos/SPNEGO Authentication in Identity Authentication.

**Solution:**

See KBA **2726591** - [Supported number of realm or domain for Kerberos/SPNEGO in IAS](https://launchpad.support.sap.com/#/notes/2726591).

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

[Risk-Based Authentication](risk-based-authentication-bc7de4d.md "Problems that you may face when configuring or using with risk-based authentication.")

[Custom Domains](custom-domains-7cb2ea5.md "Problems that you may face when using custom domains in Identity Authentication.")

