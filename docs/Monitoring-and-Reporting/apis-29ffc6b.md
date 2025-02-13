<!-- loio29ffc6bcb0104fc7a1fe4d798ecf8bfc -->

# APIs

Problems that you might face when using the REST APIs of Cloud Identity Services.



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_vrw_p4y_32c"/>

## SCIM REST API request fails with Status code 415 Unsupported Media Type

**Symptom:**

Your SCIM requests are failing with **Status code 415 Unsupported Media Type**when you use one of the Manage Users SCIM Rest APIs of Identity Authentication \([Manage Users SCIM REST API](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/63d146ccfc7949328ae750c9451f887f.html)\).

**Solution:**

See **KBA 2942542** - [SCIM REST API request fails with Status code 415 Unsupported Media Type](https://launchpad.support.sap.com/#/notes/2942542)



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_vhr_y4y_32c"/>

## You receive error: "500 Internal Server Error"

**Symptom:**

While creating a user with SCIM REST API, the REST client returns error: "500 Internal Server Error"

**Solution:**

"500 Internal Server Error" usually can be caused by an incorrectly created script. See: KBA **2745866** - [SAP Cloud Platform Identity Authentication Service - "500 Internal Server Error" while creating user with SCIM REST API](https://launchpad.support.sap.com/#/notes/2745866)



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_awm_32z_32c"/>

## Change Tenant Texts REST API fails with "403 Forbidden"

**Symptom:**

Logon labels cannot be customized since POST API is not reachable due to "403 Forbidden" error:

"403 Forbidden

The request a legal request, but the server is refusing to respond to it. Unlike a 401 Unauthorized response, authenticating will make no difference."

**Solution:**

See KBA **2650614** - [Identity Authentication Service - Cannot change logon screen labels - 403 Forbidden](https://launchpad.support.sap.com/#/notes/2650614)



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_mvm_1hz_32c"/>

## User Update fails with "400 Bad Request"

**Symptom:**

User update via Identity Authentication API or Administration Console fails with "400 Bad Request" or "Bad Request". The user cannot be updated.

**Solution:**

See KBA 2895736 - [400 Bad Request when updating user in Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2895736)



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_onh_4hz_32c"/>

## 403 Forbidden error

**Symptom:**

Calling the SCIM REST API of the Identity Authentication Service via a REST client returns a 403 Forbidden error.[https://launchpad.support.sap.com/Create%20User%20Resource](https://launchpad.support.sap.com/Create%20User%20Resource)

**Solution:**

See KBA [403 Forbidden when requesting URI: https://<tenant ID\>.accounts.ondemand.com/service/scim/Users](https://launchpad.support.sap.com/#/notes/2694327)



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_dhg_rhz_32c"/>

## "Value not supported for attribute department" when updating an user via the SCIM API

**Symptom:**

When updating a user in IAS using the SCIM API, the following error is displayed:

"StatusCode: BadRequest Message: Processing of the HTTP request resulted in an exception. Please see the HTTP response returned by the 'Response' property of this exception for details. Web Response: Value not supported for attribute department. For more information about supported values, see Identity Authentication Documentation. This operation was retried 0 times. It will be retried again after this date: 2020-05-26T18:22:53.1296153Z UTC"

**Solution:**

See KBA 2931057 - ["Value not supported for attribute department" when updating an user via the SCIM API](https://launchpad.support.sap.com/#/notes/2931057)



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_zs5_whz_32c"/>

## A new IAS tenant user activation link redirects to a password change screen

**Symptom**

A new IAS tenant user activation link redirects to a password change screen, however, the activation link is correct.

**Solution:**

See KBA **2770762** - [The IAS activation link redirects to password change screen](https://launchpad.support.sap.com/#/notes/2770762)



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_m1g_zhz_32c"/>

## How to retrieve users who enabled TFA \(Two-Factor Authentication\) in Identity Authentication using SCIM REST API

**Symptom:**

I don't know how to retrieve/search users who enabled TFA \(Two-Factor Authentication\) in IAS by using SCIM REST API.

**Solution:**

See KBA **2942076** - [How to retrieve users who enabled TFA \(Two-Factor Authentication\) in IAS using SCIM REST API](https://launchpad.support.sap.com/#/notes/2942076)



<a name="loio29ffc6bcb0104fc7a1fe4d798ecf8bfc__section_bdz_13z_32c"/>

## How to mass update user password in Identity Authentication

**Symptom:**

A big number of passwords need to be updated. One by one is not a solution.

**Solution:**

See KBA 3001615 - [How to mass update user password in Identity Authentication](https://launchpad.support.sap.com/#/notes/3001615)

**Related Information**  


[Accessing the Administration Console](accessing-the-administration-console-6187940.md "Problems with the signing in to the administration console for SAP Cloud Identity Services.")

[User Import](user-import-6a46913.md "Problems with the user import in the administration console for SAP Cloud Identity Services.")

[Emails](emails-7bde0d5.md "Problems with emails sent for the different application processes.")

[Authentication](authentication-84f28fb.md "Problems with the authentication of the end user and administrator.")

[Application Integration](application-integration-8acf508.md "Problems that different applications integrated with Cloud Identity Services might face.")

[Request, Create and Delete Identity Authentication Tenant](request-create-and-delete-identity-authentication-tenant-b442658.md "Problems related to requesting, creating or deleting a tenant.")

[End user screens](end-user-screens-a3864b5.md "Problems that you might face when working with the end user screen.")

[Corporate Identity Providers](corporate-identity-providers-16ab7db.md "")

[Corporate User Store](corporate-user-store-3ade241.md "")

[Kerberos Authentication](kerberos-authentication-4bb4b24.md "")

[Risk-Based Authentication](risk-based-authentication-bc7de4d.md "")

[Custom Domains](custom-domains-7cb2ea5.md "")

