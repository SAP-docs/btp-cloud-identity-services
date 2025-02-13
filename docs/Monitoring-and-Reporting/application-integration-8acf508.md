<!-- loio8acf508dd7e4429d81b5203248d2743f -->

# Application Integration

Problems that different applications integrated with Cloud Identity Services might face.



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_gwq_dct_32c"/>

## You receive error: "Your registration failed because the URL of the redirect page is invalid. Please contact your system administrator"

**Symptom**

User registration on the [SAP Cloud Platform Identity Authentication Service](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html)\(IAS\) tenant fails and the following error:

"Your registration failed because the URL of the redirect page is invalid. Please contact your system administrator"

**Solution:**

See KBA **2743394** - [Your registration failed because the URL of the redirect page is invalid.](https://launchpad.support.sap.com/#/notes/2743394)



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_a5y_gct_32c"/>

## You receive error: Error: "Your domain is not trusted. Please contact your system administrator"

**Symptom**:

When using embedded frames or overlays in an application, which authenticates against the Identity Authentication Service, the following error is displayed when trying to log in via the domain of the overlay:

"Your domain is not trusted. Please contact your system administrator."

The other error can be related to trusted domains:

"Your request failed because the page you have to be redirected to is not trusted. Please contact your system administrator."

**Solution:**

See KBA **2739473****\-**["Your domain is not trusted. Please contact your system administrator" in Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2739473)



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_nxr_4ct_32c"/>

## You receive error: "The digital signature of the received SAML2 message is invalid"

**Symptom:**

An Identity Authentication tenant returns the message: "The digital signature of the received SAML2 message is invalid" in subject when an authentication request is done from a specific Service Provider. This can be checked via a SAML trace \(see SAP KBA 2461862 [Collecting SAML traces with Chrome or Firefox](https://launchpad.support.sap.com/#/notes/2461862)\).

In case the Service Provider is an SAP BTP subaccount, 500 error on the screen can be seen.

In the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error is displayed:

"message=Identity Provider could not process the authentication request received due to error on its own side.An unexpected exception occurred. See call stack for details. Caused by: Signature of the SAML2 protocol token cannot be validated because neither primary nor secondary certificates are available in the configuration"

**Solution:**

See KBA 2645425 - [The digital signature of the received SAML2 message is invalid](https://launchpad.support.sap.com/#/notes/2645425)



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_b2x_tct_32c"/>

## Integration with SAP IBP. IBP logon screen is received after authentication \(SSO does not work\)

**Symptom:**

-   You need to Integrate SAP Integrated Business Planning \(IBP\) with either SAP Cloud Platform Identity Authentication Service or a Corporate Identity Provider.
-   The authentication happens to IBP via SAP Cloud Platform Identity Authentication Service or Corporate Identity Provider, but the IBP logon screen is received after authentication \(SSO does not work\).

**Solution:**

See KBA 2659221 - [User authentication prerequisites for IBP with Identity Authentication Service or Corporate IdP](https://launchpad.support.sap.com/#/notes/2659221).



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_wsy_vct_32c"/>

## Proxy scenario with S4/HANA

**Symptom**

There is a need to access the S/4HANA application with Identity Authentication that is used as a proxy.

At login attempt, an error message is shown depending on the application is used to log in.

Solution:

See KBA 2762530 - [https://launchpad.support.sap.com/\#/notes/2762530](https://launchpad.support.sap.com/#/notes/2762530).



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_k5d_zct_32c"/>

## SFSF password migration is not taking effect

**Symptom**

After provisioning users to IAS from SuccessFactors \(through IPS\), users cannot logon to SuccessFactors with a username and password. They use the forgot password link and get an error message on the IAS logon page:

"Passwords can only be changed once every %\{param0\} hours."

or

**Passwords can only be changed once every 24 hours.**

In IAS Troubleshooting logs with "WARN" Severity, you see error:

"Cannot send Forgot Password Mail to user with uid <P\_UserID\>. Reason: PASSWORD\_DISABLED. "

other factors are:

-   SuccessFactors password migration to IAS has been configured [Migrating Passwords from SAP SuccessFactors to the SAP Cloud Platform Identity Authentication Service \(IAS\)](https://help.sap.com/viewer/568fdf1f14f14fd089a3cd15194d19cc/latest/en-US/b25f3f36deed40ddb3aee14c6818df06.html).
-   Users with the issue are existing already in IAS **prior**to running the IPS sync job.
-   Users with the issue initially try to logon but their password doesn't work. They reset the password and try logon again. This is when the error is received.

**Solution:**

See KBA 2957801 - [SFSF password migration is not taking effect - "Passwords can only be changed once every %\{param0\} hours" upon forgot password](https://launchpad.support.sap.com/#/notes/2957801).



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_jsh_fdt_32c"/>

## Authentication is throwing error in incognito mode, through Identity Authentication overlay logon page

**Symptom:**

The authentication through Identity Authentication service is working fine in Google Chrome \(or any other browser\) through embedded frame, also called overlay, for the logon page of their application.

However the Incognito mode shows "HTTP Status 400 – Bad Request error." The error may occur only at the second login attempt.

**Solution:**

See KBA



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_nvs_tdt_32c"/>

## Partial SSO after Identity Authentication implementation on SuccessFactors

**Symptom:**

-   On SuccessFactors instances integrated with Identity Authentication, how no-SSO users can access the instance?
-   How to implement a similar feature to the Partial SSO from SuccessFactors on Identity Authentication.

**Solution:**

See KBA**2954556**- [How to implement Partial SSO after Identity Authentication implementation on SuccessFactors](https://launchpad.support.sap.com/#/notes/2954556)



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_ylc_xdt_32c"/>

## Browser Back button is not supported when using SAML

**Symptom:**

Using the browser's "Back" function while applying the Security Assertion Markup Language \(SAML\) authentication leads to inconsistent results.

**Solution:**

See KBA 2677653 - [Browser Back button is not supported when using SAML](https://launchpad.support.sap.com/#/notes/2677653)



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_w5m_zdt_32c"/>

## Authentication Token's targetUrl is not part of the trusted domains

**Symptom:**

There is an Application using overlay in SAP Cloud Platform Identity Authentication Service for authentication, and the authentication fails with error: **Your domain is not trusted, please contact your system administrator**.

Meanwhile, in the [Troubleshooting log](https://launchpad.support.sap.com/#/notes/2942816), the following error can be seen: **Authentication Token's targetUrl is not part of the trusted domains. Redirecting to error page.**

**Solution:**

See KBA **2944969** - [Authentication Token's targetUrl is not part of the trusted domains](https://launchpad.support.sap.com/#/notes/2944969)



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_pwl_c2t_32c"/>

## S-user provided in the Upgrade Center is not assigned Identity Authentication admin role

**Symptom:**

The integration between SuccessFactors \(SFSF\) and Identity Authentication has been initiated.

After the integration, the Administration Console of IAS tenant \(`https://<tenantID>.accounts.ondemand.com/admin/`\) with the user provided in the Upgrade Center cannot be accessed.

Error: "Sorry, we could not authenticate you. Try again." is shown in the popup.

**Solution:**

See KBA **2983379** - [S-user provided in the Upgrade Center is not assigned IAS admin role](https://launchpad.support.sap.com/#/notes/2983379)



<a name="loio8acf508dd7e4429d81b5203248d2743f__section_x1z_f2t_32c"/>

## User presence prerequisites for Hybris Cloud with Identity Authentication Service

**Symptom:**

There is a need to Integrate SAP Hybris Cloud with SAP Cloud Platform Identity Authentication Service \(IAS\) and would like to know where users will be maintained.

**Solution:**

See KBA **2665797** - [User presence prerequisites for Hybris Cloud with Cloud Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2665797)

**Related Information**  


[Accessing the Administration Console](accessing-the-administration-console-6187940.md "Problems with the signing in to the administration console for SAP Cloud Identity Services.")

[User Import](user-import-6a46913.md "Problems with the user import in the administration console for SAP Cloud Identity Services.")

[Emails](emails-7bde0d5.md "Problems with emails sent for the different application processes.")

[Authentication](authentication-84f28fb.md "Problems with the authentication of the end user and administrator.")

[Request, Create and Delete Identity Authentication Tenant](request-create-and-delete-identity-authentication-tenant-b442658.md "Problems related to requesting, creating or deleting a tenant.")

[End user screens](end-user-screens-a3864b5.md "Problems that you might face when working with the end user screen.")

[APIs](apis-29ffc6b.md "Problems that you might face when using the REST APIs of Cloud Identity Services.")

[Corporate Identity Providers](corporate-identity-providers-16ab7db.md "")

[Corporate User Store](corporate-user-store-3ade241.md "")

[Kerberos Authentication](kerberos-authentication-4bb4b24.md "")

[Risk-Based Authentication](risk-based-authentication-bc7de4d.md "")

[Custom Domains](custom-domains-7cb2ea5.md "")

