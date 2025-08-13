<!-- loio84f28fbd02ab484688c9a5e58be2eb5a -->

# Authentication

Problems with the authentication of the user and administrator.

The following authentication issues may occur:



<a name="loio84f28fbd02ab484688c9a5e58be2eb5a__section_vmp_3wg_hgc"/>

## Error: "Sorry, we could not authenticate you. Try again"

**Symptom**

When you try to sign in to an SAP Cloud Identity Services tenant, the following error message can be seen: **"Sorry, we could not authenticate you. Try again"** 

**Solution**

See KBA **3291844** - [Sorry, we could not authenticate you. Try again" error message seen in Identity Authentication login](https://me.sap.com/notes/3291844)



<a name="loio84f28fbd02ab484688c9a5e58be2eb5a__section_a5y_gct_32c"/>

## Error: "Your domain is not trusted. Please contact your system administrator"

**Symptom:**:

When using embedded frames or overlays in an application that authenticates against the Identity Authentication, the following error is displayed when trying to log in via the domain of the overlay:

**"Your domain is not trusted. Please contact your system administrator."**

The other error can be related to trusted domains:

**"Your request failed because the page you have to be redirected to is not trusted. Please contact your system administrator."**

**Solution:**

See KBA **2739473****\-**["Your domain is not trusted. Please contact your system administrator" in Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2739473)



<a name="loio84f28fbd02ab484688c9a5e58be2eb5a__section_kvv_dxs_32c"/>

## Error: "The digital signature of the received SAML2 message is invalid"

**Symptom:**

Identity Authentication tenant returns the message in subject when an authentication request is done from a specific service provider.

This can be checked via a SAML tracer. For more information, see **KBA** 2461862 - [Collecting SAML traces with Chrome or Firefox](https://launchpad.support.sap.com/#/notes/2461862).

If the service provider is an SAP BTP subaccount, an Error 500 can be seen on the screen.

In the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is displayed:

**"message=Identity Provider could not process the authentication request received due to error on its own side. An unexpected exception occurred. See call stack for details. Caused by: Signature of the SAML2 protocol token cannot be validated because neither primary nor secondary certificates are available in the configuration"**

**Solution:**

See KBA **2645425** - [The digital signature of the received SAML2 message is invalid](https://launchpad.support.sap.com/#/notes/2645425)



<a name="loio84f28fbd02ab484688c9a5e58be2eb5a__section_qjn_lxs_32c"/>

## Reset Password isn't working

**Symptom:**

The Reset Password option isn't working for Identity Authentication and in the [Troubleshooting Logs](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27323219a02a44198973091169b5a5c7.html) you find the following error:

**"Identifier xxx@xx.xx not unique"**

**Solution:**

See KBA 3030889 - [Reset password for IAS fails: "Identifier xxx@xx.xx not unique"](https://launchpad.support.sap.com/#/notes/3030889)



<a name="loio84f28fbd02ab484688c9a5e58be2eb5a__section_v3s_4xs_32c"/>

## Attribute with name loginName isn't supported

**Symptom:**

Authentication through Identity Authentication is failing with the following error message:

"Identity provider cannot process the request because the configuration is incorrect. Please contact your system administrator."

The [Troubleshooting Log](https://launchpad.support.sap.com/#/notes/2942816) shows the following error:

"Attribute with name loginName is not supported. Reason: loginName"

The error message can show other attributes as well, depending on the scenario.

**Solution:**:

See KBA 2954081 - [Attribute with name loginName is not supported](https://launchpad.support.sap.com/#/notes/2954081).



<a name="loio84f28fbd02ab484688c9a5e58be2eb5a__section_mpl_txs_32c"/>

## Error: "Not supported attribute"

**Symptom:**:

User is trying to sign in to an application through Identity Authentication however the authentication is failing. The application sign-in page is coming up after authentication in Identity Authentication.

In the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is displayed:

"message=Identity Provider could not process the authentication request received due to error on its own side.com.sap.security.saml2.lib.common.exceptions.SAML2ErrorResponseException: Not supported attribute.loginName"

Meanwhile [SAML trace](https://launchpad.support.sap.com/#/notes/2461862) has the following `nameid` format:

`<NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress"><email_address></NameID>`

**Solution:**

See KBA 2954035 - [IAS error: Not supported attribute](https://launchpad.support.sap.com/#/notes/2954035).



<a name="loio84f28fbd02ab484688c9a5e58be2eb5a__section_jxz_yxs_32c"/>

## Error: "Cookie name is not valid"

**Symptom:**

Authentication through Identify Authentication is failing. The troubleshooting logs of Identity Authentication, shows the following error:

**"... message=""User authentication failed.**Cookie name is not valid**: ..."**

**Solution:**

See KBA 2698571 - [User authentication failed in IAS due to error "Cookie name is not valid"](https://launchpad.support.sap.com/#/notes/2698571).



<a name="loio84f28fbd02ab484688c9a5e58be2eb5a__section_wpm_cys_32c"/>

## Error: "Your user was valid until. For assistance, contact your administrator."

**Symptom:**

When trying to sign in an application protected by an Identity Authentication tenant, the following error message is displayed:

**"Your user was valid until <date\>. For assistance, contact your administrator."**

**Solution:**

See KBA **2950819 -** ["Your user was valid until <date\>. For assistance, contact your administrator." error when logging on via Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2950819).

**Related Information**  


[Accessing the Administration Console](accessing-the-administration-console-6187940.md "Problems with the signing into the administration console for SAP Cloud Identity Services.")

[User Import](user-import-6a46913.md "Problems with the user import in the administration console for SAP Cloud Identity Services.")

[Emails](emails-7bde0d5.md "Problems with emails sent for the different application processes.")

[Application Integration](application-integration-8acf508.md "Problems that different applications integrated with Cloud Identity Services may face.")

[Request, Create, and Delete Identity Authentication Tenant](request-create-and-delete-identity-authentication-tenant-b442658.md "Problems related to requesting, creating, or deleting a tenant.")

[End user screens](end-user-screens-a3864b5.md "Problems that you may face when working with the end user screens.")

[REST APIs](rest-apis-29ffc6b.md "Problems that you may face when using the REST APIs of Cloud Identity Services.")

[Corporate Identity Providers](corporate-identity-providers-16ab7db.md "Problems that you may face with corporate identity providers (IdPs) when using Cloud Identity services as a proxy.")

[Corporate User Store](corporate-user-store-3ade241.md "Problems with corporate user store scenarios.")

[Kerberos Authentication](kerberos-authentication-4bb4b24.md "Problems with Kerberos authentication scenarios.")

[Risk-Based Authentication](risk-based-authentication-bc7de4d.md "Problems that you may face when configuring or using with risk-based authentication.")

[Custom Domains](custom-domains-7cb2ea5.md "Problems that you may face when using custom domains in Identity Authentication.")

[Accessing the Administration Console](accessing-the-administration-console-6187940.md "Problems with the signing into the administration console for SAP Cloud Identity Services.")

