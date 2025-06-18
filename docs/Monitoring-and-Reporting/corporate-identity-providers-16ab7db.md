<!-- loio16ab7dbeceba4af1a8e09f28a49a981e -->

# Corporate Identity Providers

Problems that you may face with corporate identity providers \(IdPs\) when using Cloud Identity services as a proxy.



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_yr3_1nz_32c"/>

## SSO with Corporate Identity Provider fails in some browsers/devices

**Symptom:**

One or both of the following issues are occurring:

-   Single Sign-On \(SSO\) with corporate IdPs fails in the Cloud Identity services with the following error **"Identity provider cannot process the response due to wrong configuration. Please contact your system administrator".**
-   SAML2.0 Authentication on SAP Business Technology Platform \(SAP BTP\) fails with the following error **"HTTP 400 Bad Request."**

In addition, one or both of the following statements are true:

-   The problem occurs in some browsers/devices, but not in others
-   The problem occurs only in a normal browser window, but not in private/incognito, or the other way around.

**Solution:**

See KBA **2946518** - [SSO with Corporate Identity Provider fails in some browsers/devices](https://launchpad.support.sap.com/#/notes/2946518).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_ksy_cnz_32c"/>

## Given URL does not contain SAML2 authentication request for validation

**Symptom:**

SAML 2.0 authentication when using Cloud Identity services fails and errors similar to the following ones are recorded in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816):

**"ERROR\#com.sap.security.saml2.idp.endpoints.sso.SSOEndpoint\#\#"**

**"\#Identity Provider could not process SAML2 authentication request sent over Redirect due to SAML2 core error that prevents sending error response to the caller."**

**"Reason: \[Given url: <URL DETAILS\> does not contain SAML2 authentication request for validation.\]"**

**Solution:**

See KBA **2698094 -**[Given url does not contain SAML2 authentication request for validation](https://launchpad.support.sap.com/#/notes/2698094).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_ly3_hnz_32c"/>

## Cloud Identity services as proxy to Google fails with 403 app\_not\_configured\_for\_user

**Symptom:**

Cloud Identity services as proxy to Google Workspace fails with the following errors:

**"Error: app\_not\_configured\_for\_user"**

**"Service is not configured for this user."**

**Solution:**

See KBA **3030557** - [Identity Authentication as proxy to Google fails with 403 app\_not\_configured\_for\_user](https://launchpad.support.sap.com/#/notes/3030557).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_khz_jnz_32c"/>

## Signature validation of SAML2Assertion failed

**Symptom:**

Cloud Identity services is acting as a proxy, the authentication happens through a corporate identity provider.

When logging in, users are redirected back to the login page and get in a loop.

In the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is displayed:

**"Signature validation of SAML2Assertion failed. Signature validation of SAML2Assertion failed. Caused by: Signature not valid!"**

**Solution:**

See **KBA**- 3026204 [Signature validation of SAML2Assertion failed](https://launchpad.support.sap.com/#/notes/3026204)



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_uwp_4nz_32c"/>

## Name id attribute must match at least one valid and supported user attribute value

**Symptom:**

Cloud Identity services is acting as a proxy, the authentication happens through a corporate identity provider.

Subject Name Identifier is set to`${corporateIdP.<corporateIdP attribute>}`. Identity Federation is enabled - user does exist in the Identity Directory user store.

Authentication is failing with such user, and the [Troubleshooting Log](https://launchpad.support.sap.com/#/notes/2942816) is showing the following error message:

**SAML configuration error. `Name id` attribute `${corporateIdP.<corporateIdP attribute>}` must match at least one valid and supported user attribute value**

**Solution:**

See KBA **2976923 - [Name id attribute $\{corporateIdP.<corporateIDP attribute\>\} must match at least one valid and supported user attribute value](https://launchpad.support.sap.com/#/notes/2976923).**



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_qmm_qnz_32c"/>

## HTTP Status 400 - Identity Provider could not process the logout message received - Identity Authentication

**Symptom:**

After logging out of an application via SAML configured for the Cloud Identity services, the logout fails with the following error message:

**"HTTP Status 400 - Identity Provider could not process the logout message received"**

**Solution:**

See **KBA**- 2682874 [HTTP Status 400 - Identity Provider could not process the logout message received - Identity Authentication](https://launchpad.support.sap.com/#/notes/2682874).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_n4z_24z_32c"/>

## SAML2Assertion doesn't specify `Subject NameID`

Symptom:

SAML 2.0 authentication when using Cloud Identity services or SAP NetWeaver Application Server for Java \(SAP AS Java\) as the service provider \(SP\) fails and errors similar to those below are recorded in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816):

**Authentication error.SAML2Assertion does not specify Subject NameID.**

**authenticationMethod=saml2Assertion**

**Solution:**

See KBA **2908718** - [SAML2Assertion does not specify Subject NameID](https://launchpad.support.sap.com/#/notes/2908718).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_ort_g4z_32c"/>

## Service Provider does not match specified audience in the SAML2Assertion

**Symptom:**

SAML 2.0 authentication when using Cloud Identity services fails and errors similar to below are recorded in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816):

**ERROR\#com.sap.security.saml2.idp.endpoints.sso.ACSEndpoint\#**

**Authentication error. Reason: \[Service Provider does not match specified audience in the SAML2Assertion.\]**

**Solution:**

See KBA **2693814 -**[Service Provider does not match specified audience in the SAML2Assertion](https://launchpad.support.sap.com/#/notes/2693814).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_m5c_l4z_32c"/>

## Logout Redirect URL is not working when Cloud Identity services is acting as a proxy

**Symptom:**

Logout Redirect URL is not working when Cloud Identity services is acting as a proxy. Logout Redirect URL is configured, but the logout is ending at the Single Logout Endpoint HTTP-Redirect URL.

**Solution:**

See KBA **2976906**- [Logout Redirect URL is not working when IAS is acting as a proxy](https://launchpad.support.sap.com/#/notes/2976906).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_z5c_n4z_32c"/>

## IdP not returning attribute `InResponseTo` in the response with the ID

**Symptom:**

A corporate identity provider is configured and Cloud Identity services is used as a proxy. Cloud Identity services sends an authentication request to the corporate IdP with an ID, but the IdP is not returning the attribute `InResponseTo` in the response with the ID.

Meanwhile, Cloud Identity services is showing the following error:

**"Identity provider cannot process the response due to wrong configuration. Please contact your system administrator."**

**Solution:**

See KBA **2926867 -**[InResponseTo attribute - What does IAS expect when it is used as a proxy - How To](https://launchpad.support.sap.com/#/notes/2926867).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_nx4_44z_32c"/>

## User attribute configured for `name-id format unspecified` is not supported

**Symptom:**

Authentication to an application fails when using Cloud Identity services. In the application logs and, or in the SAML trace, the error **"User attribute configured for name-id format unspecified is not supported"** can be seen.

**Solution:**

See KBA **2594230 -**[User attribute configured for name-id format unspecified is not supported](https://launchpad.support.sap.com/#/notes/2594230).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_sr1_q4z_32c"/>

## Error "Identity Provider could not process SAML2 logout message. RedirectPayload is not signed."

**Symptom:**

SAML 2.0 authentication when using Cloud Identity services as the IdP fails and errors similar to those below are recorded in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816):

**ERROR\#com.sap.security.saml2.idp.endpoints.slo.SLOEndpoint\#\#**

**Identity Provider could not process SAML2 logout message. RedirectPayload is not signed.**

**Solution:**

See KBA **2811941 - [Identity Provider could not process SAML2 logout message.RedirectPayload is not signed.](https://launchpad.support.sap.com/#/notes/2811941)**



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_jxy_bpz_32c"/>

## Cloud Identity services as proxy to ADFS or Azure fails because of the Scoping tag

**Symptom:**

Microsoft ADFS or Azure is set as a [Corporate Identity Provider](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html) to delegate authentication from a Cloud Identity services tenant.

Authentication is not working on the ADFS/Azure side and either of the following messages is seen:

**The SAML authentication request element 'Scoping' is not supported.**

**The SAML authentication request property 'Scoping/ProxyCount' is not supported.**

**Solution:**

See KBA **2615705 -**[Identity Authentication Service as proxy to ADFS or Azure fails because of the Scoping tag](https://launchpad.support.sap.com/#/notes/2615705).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_ady_dpz_32c"/>

## How to connect Ping Identity to Cloud Identity services

**Symptom:**

There is a need to configure Ping Identity as a corporate identity provider for Cloud Identity services.

Solution:

See KBA **2968405 -**[How to connect Ping Identity to Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2968405).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_uxz_gpz_32c"/>

## How to connect Azure Active Directory to Cloud Identity services

**Symptom:**

There is a need to configure Azure as a corporate IdP to SAP Cloud Identity Services.

**Solution:**

See KBA **2945035**- [How to connect Azure Active Directory to Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2945035).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_lzr_1qz_32c"/>

## How to configure Okta as corporate identity provider with Cloud Identity services

**Symptom:**

There is a need to configure Okta as corporate IdP for an application with SAP Cloud Identity Services as proxy.

**Solution:**

See KBA **2943651** - [How to configure Okta as corporate identity provider with Identity Authentication](https://launchpad.support.sap.com/#/notes/2943651).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_br4_5qz_32c"/>

## Incorrect destination when using Okta corporate IdP with Cloud Identity services

**Symptom:**

When using theSAP Cloud Identity Services tenant as a proxy in a corporate IdP-initiated login scenario with the corporate IdP Okta, the following error appears:

Error:**Identity Provider could not process the authentication request received. Delete your browser cache and stored cookies, and restart your browser. If you still experience issues after doing this, please contact your administrator.**

**Solution:**

See KBA **2753454**- [Incorrect destination when using Okta corporate IDP with Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2753454).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_drf_wqz_32c"/>

## Error with ADFS: "SAML2Assertion does not specify Subject NameID"

Symptom:

SAP Cloud Identity Services is acting as a proxy with Active Directory Federation Services \(AD FS\). After authentication to an application, it fails with the error HTTP Status 500.

Meanwhile, in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following errors can be seen:

-   **Authentication error. The authentication process did not set an authenticated principal in the current thread.**
-   **state=failed, action=login, objectType=user, cause=authenticationStepFailure, category=audit.authentication, credentialType="\{TRUSTED\_IDP\_SAML\_ASSERTION=rejected\}**
-   **SAML2Assertion does not specify Subject NameID.com.sap.security.saml2.sp.sso.exception.BadCredentialsException: SAML2Assertion does not specify Subject NameID.**

**Solution:**

See KBA **2945414** - ['SAML2Assertion does not specify Subject NameID' error with AD FS](https://launchpad.support.sap.com/#/notes/2945414).

Note: This topic fails to consulting category. Microsoft is responsible to do this configuration. However, this KBA provides some hints to troubleshoot and solve this issue.



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_zhx_yqz_32c"/>

## Error: "Identity provider cannot process the response due to wrong configuration. Please contact your system administrator."

Symptom:

A corporate identity provider is configured and IAS is used as a proxy. The authentication is failing and IAS is showing the following error:

**"Identity provider cannot process the response due to wrong configuration. Please contact your system administrator."**

**Solution:**

See KBA **2926891 -**[RelayState attribute - What does IAS expect when it is used as a proxy - How To](https://launchpad.support.sap.com/#/notes/2926891).



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_tm5_1rz_32c"/>

## Error: "Could not find user xxx in mongo DB."

Symptom:

-   Corporate Identity Provider is configured for authentication in Identity Authentication, but authentication is failing.
-   The [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816) is showing the following error:

    **"Authentication error.User not found: xxx Caused by: Could not find user <test@mail.com\> in mongo DB."** ensure that the Identity Authentication Troubleshooting log to contains "Could not find user <test@mail.com\> in mongo DB" error, before proceeding with the resolution of this KBA.

-   You may see the response from the service provider :

    **"****StatusCode in ResponseMessage != OK; please refer to the database trace for more information"**


**Solution:**

See KBA **2908064** - [Identity Authentication: Could not find user xxx in mongo DB.](https://launchpad.support.sap.com/#/notes/2908064)



<a name="loio16ab7dbeceba4af1a8e09f28a49a981e__section_fjz_nwz_32c"/>

## HTTP 500 error from corporate identity provider - Certificate used to validate the signature cannot be null

**Symptom**

Sign-in to Corporate Identity Provider \(IdP\) does not work with the Identity Authentication Service \(IAS\) functioning as a proxy. Corporate IdP login screen shows an "HTTP 500" error.

In [Troubleshooting Logs](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27323219a02a44198973091169b5a5c7.html), the following entries can be seen:

**"POST /saml2/idp/acs/<TenantID\>.accounts.ondemand.com HTTP/1.1" 200**

**severity=INFO, location=umtrace, crtAccount=<TenantID\>, authenticatedSubject="anonymous", **state=failed**, action=authenticate, objectType=user, **authenticationMethod=saml2Assertion**, category=audit.configuration, correlationId**

**\#ERROR\#com.sap.security.saml2.idp.endpoints.sso.ACSEndpoint\#\#<TenantID\>\#anonymous\#http-bio-127.0.0.1-8080-exec-5\#na\#N/A\#N/A\#N/A\#Authentication error.SAML2Response signature verification failed. Caused by: The certificate used to validate the signature cannot be null**

However, SAML response is successful:

**<...\>**

**<samlp:Response xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol" xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"**

**<...\>**

*<dsig:X509Certificate\><...\></dsig:X509Certificate\><...\><samlp:Status\><samlp:StatusCode Value="urn:oasis:names:tc:SAML:2.0:**status:Success**"*

*<...\>*

**Solution:**

See KBA **2758293 -**[IAS proxy scenario: HTTP 500 error from corporate identity provider - Certificate used to validate the signature cannot be null](https://launchpad.support.sap.com/#/notes/2758293).

**Related Information**  


[Accessing the Administration Console](accessing-the-administration-console-6187940.md "Problems with the signing into the administration console for SAP Cloud Identity Services.")

[User Import](user-import-6a46913.md "Problems with the user import in the administration console for SAP Cloud Identity Services.")

[Emails](emails-7bde0d5.md "Problems with emails sent for the different application processes.")

[Authentication](authentication-84f28fb.md "Problems with the authentication of the user and administrator.")

[Application Integration](application-integration-8acf508.md "Problems that different applications integrated with Cloud Identity Services may face.")

[Request, Create, and Delete Identity Authentication Tenant](request-create-and-delete-identity-authentication-tenant-b442658.md "Problems related to requesting, creating, or deleting a tenant.")

[End user screens](end-user-screens-a3864b5.md "Problems that you may face when working with the end user screens.")

[REST APIs](rest-apis-29ffc6b.md "Problems that you may face when using the REST APIs of Cloud Identity Services.")

[Corporate User Store](corporate-user-store-3ade241.md "Problems with corporate user store scenarios.")

[Kerberos Authentication](kerberos-authentication-4bb4b24.md "Problems with Kerberos authentication scenarios.")

[Risk-Based Authentication](risk-based-authentication-bc7de4d.md "Problems that you may face when configuring or using with risk-based authentication.")

[Custom Domains](custom-domains-7cb2ea5.md "Problems that you may face when using custom domains in Identity Authentication.")

