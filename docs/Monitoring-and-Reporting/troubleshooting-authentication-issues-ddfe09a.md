<!-- loioddfe09a6e441420d9efdaf9537e140f8 -->

# Troubleshooting Authentication Issues



## Identity Provider Selection

Although BASIC authentication is one of the most frequently used authentication mechanisms, we recommend that you do not use it for applications running on SAP Business Technology Platform \(SAP BTP\).

If you are already using it, we recommend that you switch to one of the following, much more secure, authentication methods:

-   FORM - HTTP FORM authentication at SAP BTP is implemented over the Secure Assertion Markup Language \(SAML\) 2.0 protocol. Authentication is handed to an identity provider that is external to SAP BTP. See [Authorization and Trust Management in the Neo Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e6b196abbb5710148c8ec6a698441b1e.html).
-   OAUTH - Authentication according to the OAuth 2.0 protocol with an OAuth access token. See [OAuth 2.0 Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e526ca3998954d62833ffd5a19ec4523.html).

For more information about the supported authentication methods and recommendations, see [Declarative Authentication](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e637f62abb571014857cb0232adc43a7.html#loioe36c712efa844e8199a9c4bd681cb4e0).

Note: Authentication in your applications works properly only if you've correctly configured the [Application Identity Provider](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/dc618538d97610148155d97dcd123c24.html) for your subaccount.

Outcomes:

-   Identity Authentication \(custom tenant\)
-   Identity Authentication \(SAP ID Service\)



## SAP ID Service

Make sure that you are using your SAP user \(S-User or P-User\).

In case you have issue with the login credentials refer to:

[2496754](https://launchpad.support.sap.com/#/notes/2496754) - Cannot login to SAP BTP due to wrong S-user password

If you try to reset the password of an S-user and the following error is received by clicking on the activation link:

*Attribute 'lastName' has wrong format '<last name of the user\>', allowed format is '^\[^<\>:/\]+$*

refer to: [2509461](https://launchpad.support.sap.com/#/notes/2509461) - Attribute 'lastName' has wrong format

If it still doesn't work, open a ticket in component BC-NEO-SEC-IAM.

[2654164](https://launchpad.support.sap.com/#/notes/2654164) - What to consider before opening a Support Incident for SAP BTP



## Identity Authentication Tenant

Outcomes:

-   Frequently Asked Questions \(FAQ\)
-   Issue with an existing Identity Authentication tenant
-   Request, create new / delete existing Identity Authentication tenant
-   End user screens
-   APIs
-   Corporate Identity Providers
-   Corporate User Store
-   Kerberos Authentication
-   Risk-Based Authentication
-   Custom Domains
-   Submit Improvement Request



## I want to submit an improvement request

You want to submit your improvement request for Identity Authentication.

See how to do it at [Submitting Improvement Requests](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/988c6de2e65d4c0d85cc0c3d3c09545f.html).



## Custom Domains

Outcomes:

-   Invalid certificate Subject DN
-   Rename Identity Authentication Service tenant is not possible
-   Custom domain on IAS using wildcard certificate



## Custom domain on IAS using wildcard certificate

Symptom:

There is a need to configure a custom domain on IAS, using an existing wildcard certificate.

Solution:

See KBA 2922427 - [Custom domain on IAS using wildcard certificate](https://launchpad.support.sap.com/#/notes/2922427).



## Rename Identity Authentication tenant is not possible

Symptom:

There is a need to change the tenant ID for your Identity Authentication tenant available at URL:

tenant ID\>.accounts.ondemand.com/admin

Solution:

See KBA 2774169 - [Rename Identity Authentication tenant is not possible](https://launchpad.support.sap.com/#/notes/2774169).





## Error: "Invalid certificate Subject DN. Please make sure that the Subject DN of the uploaded certificate is the same as the configured one."

**Symptom:**

The following error is shown after the certificate - received from the CA - is uploaded:

*Invalid certificate Subject DN. Please make sure that the Subject DN of the uploaded certificate is the same as the configured one.*

Solution:

See KBA **2922845 -**[Invalid certificate Subject DN. Please make sure that the Subject DN of the uploaded certificate is the same as the configured one.](https://launchpad.support.sap.com/#/notes/2922845)



## Risk-Based Authentication

Outcomes:

-   Error: "Sorry, but you are currently not authorized for access"
-   Two-Factor Authentication is not taking effect in Identity Authentication
-   Passcode not valid forTwo-Factor Authentication



## Passcode not valid upon Two-Factor Authentication

**Symptom:**

The passcode generated for Two-Factor Authentication is invalid for a mobile device.

**Solution:**

See KBA **2968616** - [Passcode not valid upon Two-Factor Authentication](https://launchpad.support.sap.com/#/notes/2968616).



## Two-Factor Authentication is not taking effect in Identity Authentication

**Symptom:**

Enable Two-Factor Authentication for an Application via Risk-Based Authentication Rules.

There is no change in the behavior while login.

**Solution:**

See KBA **2941888 -**[Two-Factor Authentication is not taking effect in IAS](https://launchpad.support.sap.com/#/notes/2941888).



## Error: "Sorry, but you are currently not authorized for access"

**Symptom:**

SAML 2.0 authentication when using SAP Cloud Platform Identity Authentication Service \(IAS\) fails and a similar error to below is recorded:

***Sorry, but you are currently not authorized for access***

Screenshot of the error:

The [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816) is showing one the following error:

***cause=rbaRulesCheckFailure, message="Denied by RBA rules"**or**"Authentication error.User not found: xxx Caused by: Could not find user <e-mail\> in mongo DB."***

**Solution:**

See KBA **2891275**- [Sorry, but you are currently not authorized for access: IAS issue](https://launchpad.support.sap.com/#/notes/2891275).



## Kerberos Authentication

Outcomes:

-   Kerberos Authentication fails with Could not decrypt the encrypted data error
-   Kerberos Authentication fails with Unsupported encryption SPNEGO token type error
-   Supported number of realm or domain for Kerberos/SPNEGO in IAS



## Supported number of realm or domain for Kerberos/SPNEGO in Identity Authentication

Symptom:

There is a need to know how many realm or domain is supported for Kerberos/SPNEGO Authentication in SAP Cloud Platform Identity Authentication Service \(IAS\).

**Solution:**

See KBA **2726591** - [Supported number of realm or domain for Kerberos/SPNEGO in IAS](https://launchpad.support.sap.com/#/notes/2726591).



## Kerberos Authentication fails with Unsupported encryption SPNEGO token type error

Symptom:

Kerberos authentication is configured for Identity Authentication to allow users to log on without a username and password when they are in the corporate network based on '[Configure Kerberos Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/b0301657df074ab081ab7556854aca56.html#loiob0301657df074ab081ab7556854aca56)' SAP Help documentation.

However, users are still prompted to authenticate with a username and password.

The [Troubleshooting Log](https://launchpad.support.sap.com/#/notes/2942816) is showing the following error:

***Unsupported encryption SPNEGO token type***

**Solution:**

See KBA **2958806** - [Kerberos Authentication fails with Unsupported encryption SPNEGO token type error](https://launchpad.support.sap.com/#/notes/2958806).



## Kerberos Authentication fails with Could not decrypt the encrypted data error

**Symptom:**

Kerberos authentication is configured for Identity Authentication to allow users to log on without a username and password when they are in the corporate network based on '[Configure Kerberos Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/b0301657df074ab081ab7556854aca56.html#loiob0301657df074ab081ab7556854aca56)' SAP Help documentation.

However, users are still prompted to authenticate with a username and password.

The [Troubleshooting Log](https://launchpad.support.sap.com/#/notes/2942816) is showing the following error:

***Could not validate SPNEGO token: Could not decrypt the encrypted data***

**Solution:**

See KBA **2958786** - [Kerberos Authentication fails with Could not decrypt the encrypted data error](https://launchpad.support.sap.com/#/notes/2958786).



## Corporate User Store

Outcomes:

-   I have Cloud Foundry subaccount and need the corporate user store feature. What should I do?
-   I have a Neo subaccount and need the corporate user store feature. What should I do ?
-   How to connect Identity Authentication to on-premise user store
-   How to remove Forgot Password link from Identity Authentication logon page
-   How to reset password for users from Corporate User Store
-   ABAP as Corporate User Store for Identity Authentication
-   SAML 2.0 Response issue instant is not valid
-   OAuth Client subscription type "sci/proxy" not visible
-   End-user gets "Sorry, we could not authenticate you. Try again" error when attempting to log in with LDAP user store



## End-user gets a "Sorry, we could not authenticate you. Try again" error when attempting to log in with LDAP user store

**Symptom:**

An LDAP user store on Identity Authentication is configured, but the end-user is getting a "Sorry, we could not authenticate you. Try again" error when attempting to log in.

**Solution:**

See KBA **2680867**- [Check if the system user is locked when configuring and LDAP user store](https://launchpad.support.sap.com/#/notes/2680867).



## OAuth Client subscription type "sci/proxy" not visible

**Symptom:**

There is a need to set a subscription type to "sci/proxy" during the OAuth 2.0 configuration.

The "sci/proxy" option in the drop-down list is not present.

**Solution:**

See KBA **2768285**- [OAuth Client subscription type "sci/proxy" not visible](https://launchpad.support.sap.com/#/notes/2768285).



## SAML 2.0 Response issue instant is not valid

**Symptom:**

A corporate identity provider is configured for SAP Cloud Platform Identity Authentication Service \(IAS\). The authentication fails with an error, meanwhile, in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is shown:

***SAML2Response issue instant is not valid.com.sap.security.saml2.sp.sso.exception.BadCredentialsException: SAML2Response issue instant is not valid.Issue Instant is not valid anymore. IssueInstant: <Date\>Curent time: <Date\>***

The caused by can be the following as well, depending on the time setting on the AD FS: **Caused by: Issue Instant is not valid yet.**

**Solution:**

See KBA **2945159**- [SAML2Response issue instant is not valid](https://launchpad.support.sap.com/#/notes/2945159).





## ABAP as Corporate User Store for Identity Authentication Service

**Symptom:**

There is a need to use SAP NetWeaver AS ABAP on-premise user store in addition to SAP Cloud Platform Identity Authentication Service \(IAS\)'s own cloud user store.

**Solution:**

See KBA **2942094**- [SAP AS ABAP as Corporate User Store for SAP Identity Authentication Service \(IAS\)](https://launchpad.support.sap.com/#/notes/2942094).



## How to reset password for users from Corporate User Store

**Symptom:**

There is a need to reset the Identity Authentication service password for a user coming from the Corporate User Store. When the e-mail received to reset the password is followed, the login is successful. However, at the next login attempt, the newly set password does not work anymore.

**Solution:**

See KBA **2757021**- [Identity Authentication - Password reset for users from Corporate User Store](https://launchpad.support.sap.com/#/notes/2757021).



## How to remove Forgot Password link from Identity Authentication logon page

**Symptom:**

There is a need to remove the 'Forgot Password' link as per above from the Identity Authentication Login page. This can be a goal when Corporate User Store is used, and the password is managed on the Corporate User Store itself, so the IAS Forgot password functionality would not be needed in IAS.

**Solution:**

See KBA **2607588**- [How to remove Forgot Password link from Identity Authentication logon page](https://launchpad.support.sap.com/#/notes/2607588).



## How to connect Identity Authentication to on-premise user store

Symptom:

There is a need to integrate Identity Authentication to an on-premise user store so that users can use their corporate credentials to access cloud applications.

**Solution:**

See KBA **2461375** - [How to connect Identity Authentication to on-premise user store](https://launchpad.support.sap.com/#/notes/2461375).



## Corporate user store in Cloud Foundry environment

The corporate user store feature is supported in Cloud Foundry subaccount.

For more information about the configuration steps, see [Corporate User Store \(Cloud Foundry Environment\)](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/9942ede4fae84934a8eb184a0015c305.html).

See also KBA **3058176** - [Corporate User Store Feature in Cloud Foundry environment](https://launchpad.support.sap.com/#/notes/3058176).



## Corporate user store in Neo subaccount

The corporate user store feature is supported in Neo subaccount.

For more information about the configuration steps see [Corporate User Store \(Neo Environment\)](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/461d71c148594608b9c8b6d016e0a0c5.html).

See also KBA **2768285**- [OAuth Client subscription type "sci/proxy" not visible](https://launchpad.support.sap.com/#/notes/2768285).



## Corporate Identity Providers



Outcomes:

-   SSO with Corporate Identity Provider fails in some browsers/devices
-   Given URL does not contain SAML2 authentication request for validation
-   Identity Authentication as proxy to Google fails with 403 app\_not\_configured\_for\_user
-   Signature validation of SAML2Assertion failed
-   Name id attribute $\{corporateIdP.\} must match at least one valid and supported user attribute value
-   HTTP Status 400 - Identity Provider could not process the logout message received - Identity Authentication
-   SAML2Assertion does not specify Subject NameID
-   Service Provider does not match specified audience in the SAML2Assertion
-   Logout Redirect URL is not working when Identity Authentication is acting as a proxy
-   IdP not returning attribute InResponseTo in the response with the ID
-   User attribute configured for name-id format unspecified is not supported
-   Identity Provider could not process SAML2 logout message. RedirectPayload is not signed.
-   Identity Authentication Service as proxy to ADFS or Azure fails because of the Scoping tag
-   How to connect Ping Identity to Identity Authentication Service
-   How to connect Azure Active Directory to Identity Authentication Service
-   How to configure Okta as corporate identity provider with Identity Authentication
-   Incorrect destination when using Okta corporate IDP with Identity Authentication Service
-   Error with ADFS: SAML2Assertion does not specify Subject NameID
-   Error: "Identity provider cannot process the response due to wrong configuration. Please contact your system administrator."
-   Error: Could not find user xxx in mongo DB.
-   HTTP 500 error from corporate identity provider - Certificate used to validate the signature cannot be null

**HTTP 500 error from corporate identity provider - Certificate used to validate the signature cannot be null**



## Symptom

Login to Corporate Identity Provider \(IdP\) does not work with the Identity Authentication Service \(IAS\) functioning as a proxy. Corporate IdP login screen shows an "HTTP 500" error.

In [Troubleshooting Logs](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27323219a02a44198973091169b5a5c7.html), the following entries can be seen:

*"POST /saml2/idp/acs/<TenantID\>.accounts.ondemand.com HTTP/1.1" 200*

*severity=INFO, location=umtrace, crtAccount=<TenantID\>, authenticatedSubject="anonymous", **state=failed**, action=authenticate, objectType=user, **authenticationMethod=saml2Assertion**, category=audit.configuration, correlationId*

*\#ERROR\#com.sap.security.saml2.idp.endpoints.sso.ACSEndpoint\#\#<TenantID\>\#anonymous\#http-bio-127.0.0.1-8080-exec-5\#na\#N/A\#N/A\#N/A\#Authentication error.SAML2Response signature verification failed. Caused by: **Certificate used to validate the signature cannot be null***

Hovever, SAML response is successful:

*<...\>*

*<samlp:Response xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol" xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"*

*<...\>*

*<dsig:X509Certificate\><...\></dsig:X509Certificate\><...\><samlp:Status\><samlp:StatusCode Value="urn:oasis:names:tc:SAML:2.0:**status:Success**"*

*<...\>*

**Solution:**

See KBA **2758293 -**[IAS proxy scenario: HTTP 500 error from corporate identity provider - Certificate used to validate the signature cannot be null](https://launchpad.support.sap.com/#/notes/2758293).





## Error: Could not find user xxx in mongo DB.

Symptom:

-   Corporate Identity Provider is configured for authentication in Identity Authentication, but authentication is failing.
-   The [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816) is showing the error below:

    ***"Authentication error.User not found: xxx Caused by: Could not find user <test@mail.com\> in mongo DB."*** ensure that the Identity Authentication Troubleshooting log to contains "Could not find user <test@mail.com\> in mongo DB" error, before proceeding with the resolution of this KBA.



-   You may see the response from the service provider :

    ***"****StatusCode in ResponseMessage != OK; please refer to the database trace for more information"***


**Solution:**

See KBA **2908064** - [Identity Authentication: Could not find user xxx in mongo DB.](https://launchpad.support.sap.com/#/notes/2908064)



## Error: "Identity provider cannot process the response due to wrong configuration. Please contact your system administrator."

Symptom:

A corporate identity provider is configured and IAS is used as a proxy. The authentication is failing and IAS is showing the following error:

***"Identity provider cannot process the response due to wrong configuration. Please contact your system administrator."***

**Solution:**

See KBA **2926891 -**[RelayState attribute - What does IAS expect when it is used as a proxy - How To](https://launchpad.support.sap.com/#/notes/2926891).



## Error with ADFS: SAML2Assertion does not specify Subject NameID

Symptom:

SAP Cloud Platform Identity Authentication Service \(IAS\) is acting as a proxy with AD FS. After authentication to an application, it fails with the error HTTP Status 500.

Meanwhile, in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following errors can be seen:

-   **Authentication error.The authentication process did not set an authenticated principal in the current thread.**
-   **state=failed, action=login, objectType=user, cause=authenticationStepFailure, category=audit.authentication, credentialType="\{TRUSTED\_IDP\_SAML\_ASSERTION=rejected\}**
-   **SAML2Assertion does not specify Subject NameID.com.sap.security.saml2.sp.sso.exception.BadCredentialsException: SAML2Assertion does not specify Subject NameID.**

**Solution:**

See KBA **2945414** - ['SAML2Assertion does not specify Subject NameID' error with AD FS](https://launchpad.support.sap.com/#/notes/2945414).

*Note: This topic fails to consulting category. Microsoft is responsible to do this configuration. However, this KBA provides some hints to troubleshoot and solve this issue.*



## Incorrect destination when using Okta corporate IDP with Identity Authentication Service

**Symptom:**

When using the Identity Authentication Service \(IAS\) tenant as a proxy in a corporate IDP initiated login scenario with the corporate IDP Okta, the error detailed in the screenshot below is displayed:

Error:***Identity Provider could not process the authentication request received. Delete your browser cache and stored cookies, and restart your browser. If you still experience issues after doing this, please contact your administrator.***

**Solution:**

See KBA **2753454**- [Incorrect destination when using Okta corporate IDP with Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2753454).



## How to configure Okta as corporate identity provider with Identity Authentication

**Symptom:**

There is a need to configure Okta as Corporate Identity Provider for an application with Identity Authentication as proxy.

**Solution:**

See KBA **2943651** - [How to configure Okta as corporate identity provider with Identity Authentication](https://launchpad.support.sap.com/#/notes/2943651).



## How to connect Azure Active Directory to Identity Authentication Service

**Symptom:**

There is a need to configure Azure as a corporate identity provider for SAP Cloud Platform Identity Authentication Service.

**Solution:**

See KBA **2945035**- [How to connect Azure Active Directory to Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2945035).



## How to connect Ping Identity to Identity Authentication Service

**Symptom:**

There is a need to configure Ping Identity as a corporate identity provider for SAP Cloud Platform Identity Authentication Service.

Solution:

See KBA **2968405 -**[How to connect Ping Identity to Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2968405).



## Identity Authentication Service as proxy to ADFS or Azure fails because of the Scoping tag

**Symptom:**

Microsoft ADFS or Azure is set as a [Corporate Identity Provider](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html) to delegate authentication from an Identity Authentication tenant.

Authentication is not working on the ADFS/Azure side and either of the following messages is seen:

*The SAML authentication request element 'Scoping' is not supported.*

*The SAML authentication request property 'Scoping/ProxyCount' is not supported.*

**Solution:**

See KBA **2615705 -**[Identity Authentication Service as proxy to ADFS or Azure fails because of the Scoping tag](https://launchpad.support.sap.com/#/notes/2615705).



## Identity Provider could not process SAML2 logout message. RedirectPayload is not signed.

**Symptom:**

SAML 2.0 authentication when using Identity Authentication as the Identity Provider \(IdP\) fails and errors similar to below are recorded in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816):

***ERROR\#com.sap.security.saml2.idp.endpoints.slo.SLOEndpoint\#\#***

***Identity Provider could not process SAML2 logout message.RedirectPayload is not signed.***

**Solution:**

See KBA **2811941 - [Identity Provider could not process SAML2 logout message.RedirectPayload is not signed.](https://launchpad.support.sap.com/#/notes/2811941)**





## User attribute configured for name-id format unspecified is not supported

**Symptom:**

Authentication to an application fails when using SAP Cloud Platform Identity Authentication Service. In the application logs and/or in the SAML trace, the error **"****User attribute configured for name-id format unspecified is not supported"**can be seen.

**Solution:**

See KBA **2594230 -**[User attribute configured for name-id format unspecified is not supported](https://launchpad.support.sap.com/#/notes/2594230).



## IdP not returning attribute InResponseTo in the response with the ID

**Symptom:**

A corporate identity provider is configured and IAS is used as a proxy. IAS sends an auth request to the corporate IdP with an ID, but the IdP is not returning the attribute InResponseTo in the response with the ID.

Meanwhile, IAS is showing the following error:

***"Identity provider cannot process the response due to wrong configuration. Please contact your system administrator."***

**Solution:**

See KBA **2926867 -**[InResponseTo attribute - What does IAS expect when it is used as a proxy - How To](https://launchpad.support.sap.com/#/notes/2926867).



## Logout Redirect URL is not working when Identity Authentication is acting as a proxy

**Symptom:**

Logout Redirect URL is not working when SAP Cloud Platform Identity Authentication Service \(IAS\) is acting as a proxy. Logout Redirect URL is configured, but the logout is ending at the Single Logout Endpoint HTTP-Redirect URL.

**Solution:**

See KBA **2976906**- [Logout Redirect URL is not working when IAS is acting as a proxy](https://launchpad.support.sap.com/#/notes/2976906).



## Service Provider does not match specified audience in the SAML2Assertion

**Symptom:**

SAML 2.0 authentication when using SAP Cloud Platform Identity Authentication Service fails and errors similar to below are recorded in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816):

***ERROR\#com.sap.security.saml2.idp.endpoints.sso.ACSEndpoint\#***

***Authentication error. Reason: \[Service Provider does not match specified audience in the SAML2Assertion*.\]**

**Solution:**

See KBA **2693814 -**[Service Provider does not match specified audience in the SAML2Assertion](https://launchpad.support.sap.com/#/notes/2693814).







## SAML2Assertion does not specify Subject NameID

Symptom:

SAML 2.0 authentication when using SAP Cloud Platform Identity Authentication Service \(IAS\) or SAP NetWeaver Application Server for Java \(SAP AS Java\) as the Service Provider \(SP\) fails and errors similar to below are recorded in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816):

***Authentication error.SAML2Assertion does not specify Subject NameID.***

***authenticationMethod=saml2Assertion***

**Solution:**

See KBA **2908718** - [SAML2Assertion does not specify Subject NameID](https://launchpad.support.sap.com/#/notes/2908718).



## HTTP Status 400 - Identity Provider could not process the logout message received - Identity Authentication

**Symptom:**

After logging out of an application via SAML configured for the Identity Authentication, the logout fails with the following error message:

*"HTTP Status 400 - Identity Provider could not process the logout message received"*

**Solution:**

See **KBA**- 2682874 [HTTP Status 400 - Identity Provider could not process the logout message received - Identity Authentication](https://launchpad.support.sap.com/#/notes/2682874).



## Name id attribute must match at least one valid and supported user attribute value

**Symptom:**

Identity Authentication \(IAS\) is acting as a proxy, the authentication happens through a corporate identity provider.

Subject Name Identifier is set to $\{corporateIdP.<corporateIdP attribute\>\}. Identity Federation is enabled - user does exist in IAS user store.

Authentication is failing with such user, and the [Troubleshooting Log](https://launchpad.support.sap.com/#/notes/2942816) is showing the below error message:

***SAML configuration error.Name id attribute $\{corporateIdP.<corporateIdP attribute\>\} must match at least one valid and supported user attribute value***

**Solution:**

See KBA **2976923 - [Name id attribute $\{corporateIdP.<corporateIDP attribute\>\} must match at least one valid and supported user attribute value](https://launchpad.support.sap.com/#/notes/2976923).**



## Signature validation of SAML2Assertion failed

Symptom:

Identity Authentication is acting as a proxy, the authentication happens through a corporate identity provider.

When logging in, users are redirected back to the login page and get in a loop.

In the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is displayed:

"Signature validation of SAML2Assertion failed.Signature validation of SAML2Assertion failed. Caused by: Signature not valid!"

**Solution:**

See **KBA**- 3026204 [Signature validation of SAML2Assertion failed](https://launchpad.support.sap.com/#/notes/3026204)



## Identity Authentication as proxy to Google fails with 403 app\_not\_configured\_for\_user

**Symptom:**

Identity Authentication Service \(IAS\) as proxy to Google Workspace fails with the following error:

***Error: app\_not\_configured\_for\_user***

*Service is not configured for this user.*

**Solution:**

See KBA **3030557** - [Identity Authentication as proxy to Google fails with 403 app\_not\_configured\_for\_user](https://launchpad.support.sap.com/#/notes/3030557).



## Given URL does not contain SAML2 authentication request for validation

**Symptom:**

SAML 2.0 authentication when using SAP Cloud Platform Identity Authentication Service fails and errors similar to below are recorded in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816):

***ERROR\#com.sap.security.saml2.idp.endpoints.sso.SSOEndpoint\#\#***

***\#Identity Provider could not process SAML2 authentication request sent over Redirect due to SAML2 core error that prevents sending error response to the caller.***

***Reason: \[Given url: <URL DETAILS\> does not contain SAML2 authentication request for validation.\]***

**Solution:**

See KBA **2698094 -**[Given url does not contain SAML2 authentication request for validation](https://launchpad.support.sap.com/#/notes/2698094).



## SSO with Corporate Identity Provider fails in some browsers/devices

**Symptom:**

One or both of the following issues are occurring:

-   SSO with Corporate Identity Provider fails in the Identity Authentication Service with *"Identity provider cannot process the response due to wrong configuration. Please contact your system administrator"*.
-   SAML2.0 Authentication on SAP Cloud Platform fails with *HTTP 400 Bad Request*.

In addition, one or both of the following statements are true:

-   The problem occurs in some browsers/devices, but not in others
-   The problem occurs only in a normal browser window, but not in private/incognito, or the other way around.

**Solution:**

See KBA **2946518** - [SSO with Corporate Identity Provider fails in some browsers/devices](https://launchpad.support.sap.com/#/notes/2946518).



## How to mass delete users in Identity Authentication?

**Symptom:**

There is a need to remove a big group of users from an Identity Authentication tenant.

**Solution:**

See KBA 2986601 - [How to mass delete users in Identity Authentication?](https://launchpad.support.sap.com/#/notes/2986601)



## How to retrieve users who enabled TFA \(Two-Factor Authentication\) in Identity Authentication using SCIM REST API

**Symptom:**

I don't know how to retrieve/search users who enabled TFA \(Two-Factor Authentication\) in IAS by using SCIM REST API.

**Solution:**

See KBA **2942076** - [How to retrieve users who enabled TFA \(Two-Factor Authentication\) in IAS using SCIM REST API](https://launchpad.support.sap.com/#/notes/2942076)



## I don't know how to remove the "Forgot password" link from the Logon screen

Symptom:

You need to remove the "Forgot Password" link from the Identity Authentication Logon screen. This can be a goal when Corporate User Store is used, and the password is managed on the Corporate User Store itself, so the forgot password functionality would not be needed.

Solution:

See **KBA 2607588** - [How to remove Forgot Password link from Identity Authentication logon page](https://launchpad.support.sap.com/#/notes/2607588).



## Request / Create / Delete Identity Authentication Tenant

Identity Authentication provides one productive tenant per customer, regardless of the number of contracts signed in which Identity Authentication is included or bundled.

For more information about the tenant model, tenant licensing, and obtaining a tenant of Identity Authentication, see [Tenant Model and Licensing](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/93160ebd2dcb40e98aadcbb9a970f2b9.html).

If you don't find your solution in the documentation see the suggestions below.

If you still don't find a solution or you need to delete an existing tenant, create a customer ticket on component BC-IAM-IDS. In the ticket, specify the following:

-   Subaccount name
-   Identity Authentication tenant you want to use.

Please also consider:

**KBA**[2654164](https://launchpad.support.sap.com/#/notes/2654164) - What to consider before opening a Support Incident for SAP BTP



Outcomes:

-   Tenant is purchased but not provisioned yet
-   How to request additional Identity Authentication tenants
-   Can't find Identity Authentication tile in SCP Cockpit



## I purchased a tenant, but it hasn't been provisioned yet

**Symptom:**

An Identity Authentication tenant has been purchased but has not been provisioned yet.

**Solution:**

See KBA 2751968 - [Details required when requesting an Identity Authentication tenant](https://launchpad.support.sap.com/#/notes/2751968)



## Tenant Administration

Outcomes:

-   Administration Console \(Identity Authentication\)
-   User Import
-   E-Mail Communication
-   Authentication Issues
-   Application Integration



## Authentication Token's targetUrl is not part of the trusted domains

**Symptom:**

There is an Application using overlay in SAP Cloud Platform Identity Authentication Service for authentication, and the authentication fails with error: **Your domain is not trusted, please contact your system administrator**.

Meanwhile, in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error can be seen: **Authentication Token's targetUrl is not part of the trusted domains. Redirecting to error page.**

**Solution:**

See KBA **2944969** - [Authentication Token's targetUrl is not part of the trusted domains](https://launchpad.support.sap.com/#/notes/2944969)



## How to implement Partial SSO after Identity Authentication implementation on SuccessFactors

**Symptom:**

-   On SuccessFactors instances integrated with Identity Authentication, how no-SSO users can access the instance?
-   How to implement a similar feature to the Partial SSO from SuccessFactors on Identity Authentication.

**Solution:**

See KBA**2954556**- [How to implement Partial SSO after Identity Authentication implementation on SuccessFactors](https://launchpad.support.sap.com/#/notes/2954556)



## Authentication Issues

Outcomes:

-   You receive error: The digital signature of the received SAML message is invalid."
-   Reset password fails with error: "Identifier @. not unique."
-   Authentication fails with error: "Attribute with name loginName is not supported"
-   Authentication fails with error: "Not supported attribute"
-   Authentication fails with error: "Cookie name is not valid"
-   "Your user was valid until . For assistance, contact your administrator." error when logging on via Identity Authentication Service
-   See also



## Error: "Your user was valid until . For assistance, contact your administrator."

**Symptom:**

When trying to log on an application protected by an Identity Authentication Service tenant, the following error message is displayed:

**"Your user was valid until <date\>. For assistance, contact your administrator."**

**Solution:**

See KBA **2950819 -** ["Your user was valid until <date\>. For assistance, contact your administrator." error when logging on via Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2950819).



## Error: "Not supported attribute"

**Symptom**:

User is trying to login to an application through Identity Authentication, however the authentication is failing. The application login page is coming up after authentication in IAS.

In the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is displayed:

***message=Identity Provider could not process the authentication request received due to error on its own side.com.sap.security.saml2.lib.common.exceptions.SAML2ErrorResponseException: Not supported attribute.loginName***

Meanwhile [SAML trace](https://launchpad.support.sap.com/#/notes/2461862) has the following nameid-format:

*<NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-**format:emailAddress"\><email\_address\>**</NameID\>*

**Solution:**

See KBA 2954035 - [IAS error: Not supported attribute](https://launchpad.support.sap.com/#/notes/2954035).



## Check if e-mails are sent

**Symptom:**

End-users state that they don't receive e-mails from Identity Authentication for various application processes such as account activation, password reset, etc. There is a need to troubleshoot if the e-mails are actually sent from Identity Authentication to determine if the issue is with Identity authentication or the mail server.

**Solution:** 

There is a need to troubleshoot if the e-mails are actually sent from IAS to determine if the issue is with IAS or the e-mail server.

See **KBA 2978346** - [How to check if e-mails are sent and the sender from Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2978346).



## You receive error: "First users are imported. User import has been interrupted for user with email address ."

Reason:

You received this error, because the first <number\> users in the CSV file are already imported for the tenant. The next user was not imported because its data in the CSV file conflicts with the data in the database.

Solution:

-   Correct the e-mail for the logon name under the mail column, delete the first number\> users from the CSV file, and re-import the updated file.Caution

    During CSV import, you cannot change the e-mail of an existing user.

-   Change the user logon name because the same logon name is used for another user in the database, delete the first <number\> users from the CSV file, and re-import the updated file.Note

    You cannot have two users with the same logon name, but with different e-mails.

-   Contact an operator of Identity Authentication.







## Admin Console

You are using the [Administration Console](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/6a8e67cf98bf41968ea2849dfd0b6bbd.html), or attempting to login to an application using [Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/) service.

See [Administration Console](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/6a8e67cf98bf41968ea2849dfd0b6bbd.html) to learn more about this tool.



Outcomes:

-   Accessing Admin Console
-   Configuration Issues
-   Monitoring Access



## Monitor and Troubleshoot Access

Outcomes:

-   How to view my last login date and time
-   How to export Identity Authentication change logs
-   Collect SAML traces with Chrome or Firefox \(Identity Authentication\)



## Collect SAML traces with Chrome or Firefox \(Identity Authentication\)

Browsers now contain add-ons that specifically trace SAML.

For more information how to trace issues with SAML authentication, see KBA **2461862 - [Collecting SAML traces with Chrome or Firefox](https://launchpad.support.sap.com/#/notes/2461862).**



## How to export change logs

**Symptom:**

I want to download the history of the operations performed by administrators in the Administration Console for Identity Authentication.

**Solution:**

See KBA **2774210**- [How to export Identity Authentication change logs](https://launchpad.support.sap.com/#/notes/2774210).



## How to view my last login date and time

**Symptom:**

I want to view my last login date and time in Identity Authentication. The aim is to help check unauthorized IAS tenant access.

**Solution:**

See **KBA 2705392** - [How can users view their last login date and time: SAP Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2705392) and **KBA 2777148** - [How can Administrators check login date and time of users: SAP Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2777148).



## Configuration Issues

Outcomes:

-   Missing menus from the admin console



## Missing menus from administration console

**Symptom:**

After logging into the Identity Authentication Administration Console, one/more of the following Menu options are missing:

-   Users Authorizations
-   Applications Resources
-   Identity Providers
-   Monitoring Reporting

**Solution:**

See **KBA**2867292 - [Tile or Menu is missing from Identity Authentication Administration Console](https://launchpad.support.sap.com/#/notes/2867292).



## Problem with login to the Identity Authentication tenant

**You can reach the tenant administration console via the URL https://<tenant ID\>.accounts.ondemand.com/admin pattern.**

**You must be an administrator user.**



the Log On screen appears correctly:

but you face one of the following problems:

Outcomes:

-   I don't know who the tenant administrator is?
-   Cannot login to Administration Console of custom Identity Authentication tenant with S-user
-   Tenant is not accessible due to network problem
-   Activation e-mail problems
-   "Sorry, we could not authenticate you. Try again."
-   "Access denied. Sorry.. You entered a valid URL, but you are not authorized to view the content."
-   "Access denied. Identity Provider could not process the authentication request received."
-   "Sorry, we could not authenticate you. Try again."
-   HTTP Status 403 – Access to this Identity Authentication tenant is blocked, please contact your administrator
-   I receive a different error



## Open incident

Please open a ticket on BC-IAM-IDS component, and provide the following information:

-   -   Your tenant ID from https://tenant ID\>.accounts.ondemand.com/admin
-   Your email address
-   The error message you see
-   Attachments of screenshot that show the reproduced error, including the exact timestamp
-   If you solved your issue, a description of the steps you took
-   List of KBAs and SAP Notes, you have used to solve the issue
-   Attachments of SAML traces as per KBA: [2461862](https://launchpad.support.sap.com/#/notes/2461862) - Collecting SAML traces with Chrome or Firefox




Access to this Identity Authentication tenant is blocked, please contact your administrator"

**Symptom:**

Accessing the SAP Cloud Platform Identity Authentication Service \(IAS\) tenant fails with the below error:

***"HTTP Status 403 – Access to this Identity Authentication tenant is blocked, please contact your administrator."***

**Solution:**

See**KBA** - [https://launchpad.support.sap.com/\#/notes/2909142](https://launchpad.support.sap.com/#/notes/2909142)



## Logon fails with error: "Sorry, we could not authenticate you. Try again."

**Symptom**

Logon to the Identity Authentication Administration Console is failing with error: **Sorry, we could not authenticate you. Try again.** Using the forgot password link allows you to reset the password and log in. However, logging off and trying to login again the same error is shown as previously. Only a password reset allows login again for just one user session.

The [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816) is showing the following error:

**User authentication failed. Reason: Used logon identifier is not allowed; Identifier: \[ <logon\_identifier\> \]**

**Solution:**

See KBA 2895349 - [Cannot logon to Identity Authentication Administration Console with valid logon identifier and password](https://launchpad.support.sap.com/#/notes/2895349).



## The identity provider could not process the authentication request received

Identity Authentication using the Security Assertion Markup Language \(SAML\) 2.0 as identity provider \(IdP\) fails to process the authentication request.

Make sure the service provider's name is the same as configured in Identity Authentication, acting as IdP:

[2260000](https://i7p.wdf.sap.corp/sap/support/notes/2260000) - Identity provider could not process the authentication request received.

Outcomes:

-   Open Incident



## Access denied. Sorry... You entered a valid URL, but you are not authorized to view the content.

Immediately after you've logged on to admin console of Identity Authentication tenant, you see the message:

"Access Denied

Sorry... You entered a valid URL, but you are not authorized to view the content, contact your system administrator"

Ask an administrator to configure required authorization, as explained in the following KBA:

[2579343](https://i7p.wdf.sap.corp/sap/support/notes/2579343) - Accessing /admin of custom Identity Authentication tenant ends with "you are not authorized to view the content"

Outcomes:

-   I do not know who the administrator is



## Tenant Administrator

**Contact an existing administrator for the tenant.**

Identity Authentication does not use for authentication the users registered in the SAP Service Marketplace, but maintains an own user store for administrators and users.

Once you purchase a customer or partner account in SAP BTP, a user account for Identity Authentication is created for the contact person specified in the Order Form. The contact person is the first **tenant administrator** in the administration console for Identity Authentication. He or she receives an activation e-mail for the administration console account. The subject of the e-mail is: **Activate Your Account for Administration Console**. The **first**administrator activates the account and continues to the administration console for Identity Authentication via the console's URL.

The URL has the ***https://<tenant ID\>.accounts.ondemand.com/admin*** pattern. Tenant ID is an automatically generated ID by the system. The URL is in the activation e-mail received by the first administration and contains the tenant ID.

The first administrator can add new tenant administrators.

See also: **KBA 2774108**- [Identity Authentication Service tenant specific request only possible for customer owning the tenant](https://launchpad.support.sap.com/#/notes/2774108)

Outcomes:

-   Forgot Password



## Forgot Password

**From the Log On screen of the Administration Console, choose "Forgot password." Provide your e-mail address and choose "Send".**

If you have an account as administrator in Identity Authentication, an e-mail with a link to a page where you can reset your password will be sent.Note that the e-mail might take a few minutes to reach your inbox. If you don't have an account as administrator, you won't receive an e-mail. In this case [contact an existing administrator for the tenant](https://ga.support.sap.com/dtp/viewer/#/tree/2142/actions/28252?version=current)

See also KBA 2517844 - [How to get the activation e-mail of an Identity Authentication tenant](https://launchpad.support.sap.com/#/notes/2517844)



## Sorry, we could not authenticate you. Try again.

This is a general error, can be the symptom of many situations.

Outcomes:

-   after LDAP user store is configured.
-   with S-user credentials.
-   Login fails after successful activation
-   You forgot your password
-   You are not an administrator



## Add new tenant administrator

Identity Authentication does not use for authentication the users registered in the SAP Service Marketplace, but maintains an own user store for administrators and users. Only administrators can access the admin console.

Ask an existing administrator to add new tenant administrators.:

[2570572](https://i7p.wdf.sap.corp/sap/support/notes/2570572) - How to add Administrators to Identity Authentication tenants

Outcomes:

-   Who is the tenant administrator?



## Login fails after successful activation with error: "Sorry, we could not authenticate you. Try again."

**Symptom:**

The user login fails after the activation link is called and the password update was successful.

The user receives the following message:

***Sorry, we could not authenticate you. Try again.***

In the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is displayed:

***Identity Provider could not process the authentication request received due to error on its own side. The SP user \[<user\_uuid\>\] is with status inactive for Service Provider \[<service\_provider\_url\>\] Caused by: javax.security.auth.login.AccountException: The SP user \[<user\_uuid\>\] is with status inactive for Service Provider \[<service\_provider\_url\>\] Caused by: The SP user \[<user\_uuid\>\] is with status inactive for Service Provider \[<service\_provider\_url\>\]***

**Solution:**

See KBA 2770797 - [The IAS tenant user login fails after successful activation: Sorry, we could not authenticate you. Try again.](https://launchpad.support.sap.com/#/notes/2770797)



## Cannot login to admin console with S-user

You are trying, without success, to login to the admin console of Identity Authentication tenant \(Identity Authentication tenant\) as an S-user.

There are no S-users used in custom tenants. S-users can only log on to *accounts.sap.com*, which belongs to SAP.

In a custom own tenant, you can log on using your **e-mail** address and password.

See KBA, [2424064](https://i7p.wdf.sap.corp/sap/support/notes/2424064) - Cannot login to admin console of custom Identity Authentication tenant with S-user



## User is locked when configuring LDAP user store on SAP BTP

You have configured an LDAP scenario based on the [Configure SAP BTP When Connecting to an LDAP User Store documentation](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/461d71c148594608b9c8b6d016e0a0c5.html#loiof48d4ea4ec4747ac8425385ded5d1e25).

However, when you attempt to log on, you see "Sorry, we could not authenticate you. Try again."

There is an issue in the connection between the SAP Cloud Connector and the corporate user store due to an issue with the system user which is used to access the corporate user store.

See KBA: [2680867](https://i7p.wdf.sap.corp/sap/support/notes/2680867)- Check if the system user is locked when configuring and LDAP user store on SAP BTP



## E-Mail Activation

**As a tenant administrator you can reach the administrator console via the URL https://<tenant ID\>.accounts.ondemand.com/admin pattern.**

Tenant ID is an automatically generated ID by the system. The URL is in the activation e-mail received by you.

Check your inbox for an e-mail from **notification@sapnetworkmail.com**.

Outcomes:

-   I have activated my account but still face problems
-   I haven't activated my account or didn't receive e-mail.



## Activation E-Mail Issues

**Open your inbox and search for an e-mail from *notification@sapnetworkmail.com.***The e-mail contains a URL to activate your account.

-   **If the URL is expired**
    -   The system sends you a new activation e-mail. Follow the procedure to activate your account.

-   **If the link is invalid or already used or you haven't received an e-mail**
    -   Check your spam folder
    -   Contact an existing administrator for the tenant to ask the following

        -   Whether an activation e-mail was sent\(or if only an initial password was set, since this case no e-mail is sent\).
        -   To resend the activation e-mail \(Admin Console --\> "User Management" --\> Select user --\> choose "Authentication" tab --\> click "Password Details" --\> "Send E-Mail"\).



See also: **KBA 2517844** - [How to get the activation e-mail of an Identity Authentication tenant](https://launchpad.support.sap.com/#/notes/2517844)

-   Who is my administrator?



## Tenant is not accessible due to network problem

**Symptom:**

Identity Authentication tenant cannot be accessed - the browser throws ERR\_EMPTY\_RESPONSE, or similar error message \(***ERR\_TIMED\_OUT***, t***ook too long to respond***, etc\).

Timeout-related errors can also be seen on the browser.

**Solution:**

See KBA 2918278 - [IAS tenant is not accessible due to network problem](https://launchpad.support.sap.com/#/notes/2918278).

This KBA provides some hints on how to investigate further.



## Cannot login to Administration Console of custom Identity Authentication tenant with S-user

**Symptom:**

Logging into the Administration Console of an Identity Authentication tenant with an S-user is unsuccessful.

**Solution:**

See KBA **2424064**- [Cannot login to Administration Console of custom Identity Authentication tenant with S-user](https://launchpad.support.sap.com/#/notes/2424064).



## How to get information about the tenant administrator?

**Symptom:**

You don't know who is the tenant administrator?

**Solution:**

See KBA 3035908 - [https://launchpad.support.sap.com/\#/notes/3035908](https://launchpad.support.sap.com/#/notes/3035908)

Outcomes:

-   Tenant Administrator



## Frequently Asked Questions \(FAQ\)

In this guided answer tree, you can find answers to some common questions you may have about the Identity Authentication service. Instructions on what to do if you need help, and links to documentation for common configurations.

Outcomes:

-   General Tenant Information
-   Entitlement Information
-   Cost Related Information
-   Corporate Users Store Information
-   X.509 Certificates Related Information

