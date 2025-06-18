<!-- loio6a46913d96594c70a3a48829cbd088f7 -->

# User Import

Problems with the user import in the administration console for SAP Cloud Identity Services.

As a tenant administrator, you can import new users or update existing ones for a specific application with a CSV file via the administration console. You can also send activation emails to the users that haven't received activation emails for that application so far.

The scenario, requirements, and configurations are described in [Import or Update Users for a Specific Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/33838e0760f8411daf758a1c11818cc4.html).

> ### Tip:  
> You as a tenant administrator can view Identity Authentication troubleshooting logs to monitor the system, and diagnose and solve problems. For more information, see [View Troubleshooting Logs](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27323219a02a44198973091169b5a5c7.html) and [Analyze Troubleshooting Logs with Support Log Assistant 2.0](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/72ac00bfc4784d48a0207e54495ed636.html). See also **KBA 2942816** - [How to export and self-analyze Troubleshooting logs from Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2942816).

You may face one of the following problems:



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_wg5_tds_32c"/>

## Users don't receive emails from `notification@sapnetworkmail.com` or `ias@notifications.sap.com` after a CSV user import

**Symptom:**

You import users by uploading a CSV file successfully, but users don't receive email for that.

**Solution:**

See KBA 2940801 - [E-mail is not received after "Import Users"](https://launchpad.support.sap.com/#/notes/2940801)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_ry5_d2s_32c"/>

## Email sending is interrupted

**Symptom:**

There is a need to import users to an application and to send the initial emails, but the second step fails with the following message:

**"First 0 mails are sent. Mailing has been interrupted because sending e-mail to user with e-mail address <email\> is not possible. Please update the user e-mail and trigger e-mail sending again."**

**Solution:**

See KBA 2833007 - [First 0 mails are sent.](https://launchpad.support.sap.com/#/notes/2833007)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_rrq_42s_32c"/>

## Users have to be redirected to a specific URL after successful registration

**Symptom:**

There is a need to redirect users to a specific URL after a successful registration.

**Solution:**

See **KBA 2942954**- [Redirect users after successful registration in Identity Authentication](https://launchpad.support.sap.com/#/notes/2942954)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_jpj_s2s_32c"/>

## Import users to Identity Authentication with additional attributes

**Symptom:**

You have to import user data into Identity Authentication using the *Import Users* option of the administration console, but it only supports some certain attributes of a user, not all.

All supported attributes of a user for this function are mentioned in the SAP Help Document: [Import or Update Users for a Specific Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/33838e0760f8411daf758a1c11818cc4.html).

**Solution:**

SAP provides SCIM REST API which allows to set all other user attributes in a programmatic way.

See [SCIM REST API](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/2f215687fcf34170b0bbc8b36b60f2e9.html) and **KBA 2533357** -[Import users to Identity Authentication with additional attributes](https://launchpad.support.sap.com/#/notes/2533357)

Alternatively, SAP provides [SCIM REST API](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/2f215687fcf34170b0bbc8b36b60f2e9.html) which allows to set all other user attributes in a programmatic way.



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_esv_w2s_32c"/>

## You receive error: "Provided file has the wrong type"

**Symptom:**

When importing users to Identity Authentication, the import fails with the following error:

**"Provided file has the wrong type. Please specify a different file and try again."**

**Solution:**

See **KBA 2461975** - [Import users fails with error: Provided file has the wrong type](https://launchpad.support.sap.com/#/notes/2461975)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_wdj_ffs_32c"/>

## You receive error: "User with email '' contains empty values - error during user import"

**Symptom:**

You see the following error at user import in the Identity Authentication service:

**"User with email '' contains empty values."**

**Solution:**

See **KBA 2859442** - [User with email '' contains empty values - error during user import](https://launchpad.support.sap.com/#/notes/2859442)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_nxt_mfs_32c"/>

## You receive error: "User import has been interrupted for users with email address "<email\_address\>".

**Symptom:**

During user import \(update\), the following error is shown when the user already exists in the userbase:

**User import has been interrupted for users with e-mail address "<email\_address\>".**

The reason for this error is as follows: **"The import reported error".**

**Solution:**

See KBA 2958785 - [Identity Authentication Import Users throws Attribute '<attributeName\>' has wrong format error](https://launchpad.support.sap.com/#/notes/2958785)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_jj1_vfs_32c"/>

## You receive error: "Home URL or SAML 2.0 configuration of the application missing. You can only import users, but you cannot send activation emails."

**Symptom:**

You have imported users into the Identity Authentication tenant, but the activation e-mails to them can't be sent. The following message is shown:

**"Home URL or SAML 2.0 configuration of the application missing. You can only import users, but you cannot send activation emails."**

**Solution:**

See **KBA 2591826 -**[Activation e-mails cannot be sent - Home URL or SAML 2.0 configuration of the application missing](https://launchpad.support.sap.com/#/notes/2591826)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_k2l_kgs_32c"/>

## You receive error: "The CSV file failed to upload..."

**Symptom:**

You, as an administrator, imported a CSV user file in Identity Authentication and it returns the following error:

**"The CSV file failed to upload. Contact your system administrator for assistance."**

**Solution:**

See **KBA 2975595**- [Import users CSV file in IAS fails with error - The CSV file failed to upload](https://launchpad.support.sap.com/#/notes/2975595).



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_wvg_sgs_32c"/>

## You receive error: "0 emails sent when trying to send activation e-mails on Identity Authentication"

**Symptom:**

Users are imported to Identity Authentication, but when choosing "Send Emails", a message is received, stating that **"0 emails sent when trying to send activation e-mails on Identity Authentication".**

**Solution:** 

See **KBA 2471540** - [0 emails sent when trying to send activation e-mails on Identity Authentication](https://launchpad.support.sap.com/#/notes/2471540)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_tjs_xgs_32c"/>

## You receive error: "First 0 users are imported. User import has been interrupted for users with email address . The reason for this error is as follows: "The import reported error".

**Symptom**

Importing users from a CSV file in Identity Authentication Service is failing with the following error message:

First 0 users are imported. User import has been interrupted for users with e-mail address <user e-mail\>. The reason for this error is as follows: "The import reported error".

**Solution:**

See **KBA 2717186** - ["User import has been interrupted" in Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2717186)



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_pvd_qhs_32c"/>

## You receive error: "First <number\> users are imported. User import has been interrupted due to an invalid entity."

**Symptom:**

**The first users in the CSV file are already imported for the tenant. The next user was not imported because the CSV file contains an incorrect data for that user.**

**Solution:**

Delete the first <number\> users from the CSV file, correct the invalid row, and re-import the updated file.



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_jkr_5hs_32c"/>

## You receive error: "First <number\> users are imported. User import has been interrupted for user with email address ."

**Symptom:**

**The first <number\> users in the CSV file are already imported for the tenant. The next user was not imported because its data in the CSV file conflicts with the data in the database.**

**Solution:**

-   Correct the email for the logon name under the mail column, delete the first <number\> users from the CSV file, and re-import the updated file.

    > ### Caution:  
    > During CSV import, you can't change the email of an existing user.

-   Change the user logon name because the same logon name is used for another user in the database, delete the first <number\> users from the CSV file, and re-import the updated file.

    > ### Note:  
    > You can't have two users with the same logon name, but with different emails.

-   Contact a tenant administrator of Identity Authentication.



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_fs2_w3s_32c"/>

## You receive error: "First <number\> users are imported. User import has been interrupted due to multiple users in the database with the same email address <email address\>. The email address must be unique for each user."

**Symptom:**

The first <number\> users in the CSV file are already imported for the tenant. The next user was not imported because its email matches with the email of other users.

**Solution:**

-   Correct the user data, delete the first number\> users from the CSV file, and re-import the updated file.
-   Contact an operator of Identity Authentication to check if your emails exist in the database.



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_wsk_cjs_32c"/>

## You receive error: "The imported CSV file contains entries with a duplicate email <email address\>. The values under mail column must be unique."

**Symptom:**

You have provided a CSV file with a `mail` column that has the same email entries.

**Solution:**

Correct the file so that the mail column contains unique values.



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_rwm_3js_32c"/>

## You receive error: "The imported CSV file contains entries with a duplicate login name <login name\>. The values under loginName column must be unique."

**Reason:**

You have provided a CSV file with a `loginName` column that has the same entries.

**Solution:**

Correct the file so that the `loginName` column contains unique values.



<a name="loio6a46913d96594c70a3a48829cbd088f7__section_xny_njs_32c"/>

## You receive error: "The imported CSV file does not contain one of the mandatory columns: status, mail and lastName. Make sure that the columns status, mail, lastName are in the CSV file."

**Symptom**

An administrator imports the CSV user file in Identity Authentication and it returns the following error:

**The imported CSV file does not contain one of the mandatory columns: status, mail and lastName.**

Make sure that the columns `status`, `mail`, `lastName` are in the CSV file.

**Solution:**

Follow the ["Import or Update Users for a Specific Application" documentation](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/33838e0760f8411daf758a1c11818cc4.html) document which explains the pre-requisites, possible columns with the attributes, mandatory columns, possible values for columns.

Follow the example in the documentation which shows you how your CSV file should look like.

See also KBA 2607696 - [Import users CSV file in Cloud Identity Authentication Service and it fails with error](https://launchpad.support.sap.com/#/notes/2607696) 

**Related Information**  


[Accessing the Administration Console](accessing-the-administration-console-6187940.md "Problems with the signing into the administration console for SAP Cloud Identity Services.")

[Emails](emails-7bde0d5.md "Problems with emails sent for the different application processes.")

[Authentication](authentication-84f28fb.md "Problems with the authentication of the user and administrator.")

[Application Integration](application-integration-8acf508.md "Problems that different applications integrated with Cloud Identity Services may face.")

[Request, Create, and Delete Identity Authentication Tenant](request-create-and-delete-identity-authentication-tenant-b442658.md "Problems related to requesting, creating, or deleting a tenant.")

[End user screens](end-user-screens-a3864b5.md "Problems that you may face when working with the end user screens.")

[REST APIs](rest-apis-29ffc6b.md "Problems that you may face when using the REST APIs of Cloud Identity Services.")

[Corporate Identity Providers](corporate-identity-providers-16ab7db.md "Problems that you may face with corporate identity providers (IdPs) when using Cloud Identity services as a proxy.")

[Corporate User Store](corporate-user-store-3ade241.md "Problems with corporate user store scenarios.")

[Kerberos Authentication](kerberos-authentication-4bb4b24.md "Problems with Kerberos authentication scenarios.")

[Risk-Based Authentication](risk-based-authentication-bc7de4d.md "Problems that you may face when configuring or using with risk-based authentication.")

[Custom Domains](custom-domains-7cb2ea5.md "Problems that you may face when using custom domains in Identity Authentication.")

