<!-- loio7bde0d5a298b44f7923dece9f0d93278 -->

# Emails

Problems with emails sent for the different application processes.

Check the following entries for issues with emails sent for the different application processes:



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_bkq_2ls_32c"/>

## Email Activation

You have received an email from **notification@sapnetworkmail.com** or:

-   If you have already activated your account - You see the following error "E-Mail Already Activated" after you’ve clicked the activation email link." E-Mail Already Activated. This message means that the Cloud Identity Services has already been activated. Use the "Forgot Password" option to gain access to your tenant.
-   If you haven't activated your account or didn't receive an email - Open your mail box and search for an e-mail from **ias@notifications.sap.com** or **notification@sapnetworkmail.com**. The email contains a link to activate your account. The following is possible:
    -   The link has expired - The system sends you a new activation email. Follow the procedure to activate your account.
    -   The link is invalid or already used, or you haven't received an email:
        -   Check your spam folder
        -   Contact an existing tenant administrator for the tenant to ask the following.

            -   Whether an activation email was sent \(or if only an initial password was set, since this case no email is sent\).
            -   To resend the activation email.

            > ### Note:  
            > [Who is my tenant administrator?](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/accessing-administration-console-61879409f6024c5cad78d5e36ce3657c?state=DRAFT&version=Dev#i-don't-know-who-the-tenant-administrator-is-)




See also: **KBA 2517844** - [How to get the activation e-mail of an Identity Authentication tenant](https://launchpad.support.sap.com/#/notes/2517844)



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_h25_bps_32c"/>

## Check if emails are sent

**Symptom:**

End-users state that they don't receive emails from Identity Authentication for various application processes such as account activation, password reset, and so on.

**Solution:** 

There is a need to troubleshoot if the e-mails are sent from Identity Authentication to determine if the issue is with Identity Authentication or the email server.

See **KBA 2978346** - [How to check if e-mails are sent and the sender from Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2978346).



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_uwv_hps_32c"/>

## Error: "Internal error; contact system administrator" in Identity Authentication

**Symptom:**

An email template in the *Default* template of an application is uploaded. During the attempt to manually send it, the following pop-up warning is shown:

**"Internal error; contact system administrator"**

In the browser logs, the following error is visible:

**"500 Internal Server Error"**

**Solution:**

See **KBA 2573314** - [E-mail template error: Internal error; contact system administrator in Identity Authentication \(IAS\)](https://launchpad.support.sap.com/#/notes/2573314) 



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_e2c_mrs_32c"/>

## Emails are in English language, which isn't the desired language

**Symptom:**

*Activate Your Account* or *Password Reset* email is in English, which isn't the desired language.

**Solution:**

See **KBA****3023020** - ["Password Reset" e-mail is in English](https://launchpad.support.sap.com/#/notes/3023020)



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_fh3_srs_32c"/>

## User receives error: "Your e-mail activation link is invalid or already used"

**Symptom:**

Account activation of the Identity Authentication service isn't possible. The following error is displayed:

**"Your e-mail activation link is invalid or already used."**

**Solution:**

See **KBA****2637748** - [Identity Authentication - Your email activation link is invalid or already used](https://launchpad.support.sap.com/#/notes/2637748)



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_mqf_yrs_32c"/>

## Identity Authentication didn't send Forgot Password email

**Symptom:**

After requesting a new password with the *Forgot Password* option, the email isn't received.

The troubleshooting log \(see **KBA 2942816** - [How to export and self-analyze Troubleshooting logs from Identity Authentication Service](https://launchpad.support.sap.com/#/notes/2942816)\) is showing the following error message:

**"No Forgot password message sent to <e-mail address\>. Limit exceeded!"**

**Solution:**

Solution KBA 2981630 - [No Forgot password message sent from Identity Authentication](https://launchpad.support.sap.com/#/notes/2981630)



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_zrf_m5s_32c"/>

## Emails sent still contain the SAP logo

**Symptom:**

After you have configured the email templates in the administration console for Identity Authentication, the emails sent still contain the SAP logo.

**Solution:**

See **KBA****2854429** - [How to Set Custom Company Logo for IAS Template E-mails](https://launchpad.support.sap.com/#/notes/2854429)



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_z4l_55s_32c"/>

## Email template set in Identity Authentication tenant isn't working

**Symptom:**

An email template set within the Identity Authentication tenant has been configured but the templates aren't applied when testing them.

**Solution:**

See **KBA****2675079** - [E-mail template set in Identity Authentication tenant not working](https://gad5158842f.us2.hana.ondemand.com/dtp/editor/services/launchpad.support.sap.com)



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_xnf_x5s_32c"/>

## Error when uploading custom email template sets in Identity Authentication

**Symptom:**

The following error message is received when uploading custom email template sets in the administration console for Identity Authentication:

![](images/Error_0_6992cc4.png)

**Solution**:

See **KBA****2716042** - [Error when uploading custom E-Mail Template Sets in Identity Authentication](https://launchpad.support.sap.com/#/notes/2716042).



<a name="loio7bde0d5a298b44f7923dece9f0d93278__section_rcz_pvs_32c"/>

## Changing the email ias@notifications.sap.com or notification@sapnetworkmail.com in Identity Authentication

**Symptom:**

When a user requests to reset their password in an Identity Authentication tenant, they receive an email from **notification@sapnetworkmail.com** \(as of Sep 29, 2021 - **ias@notifications.sap.com**\). There is a need to change this e-mail to another sender/server. Identity Authentication also provides the possibility to configure a custom mail server for the application processes e-mails.

**Solution:**

See **KBA**- [Changing the e-mail ias@notifications.sap.com \(notification@sapnetworkmail.com\) in Identity Authentication](https://launchpad.support.sap.com/#/notes/2620650).

**Related Information**  


[Accessing the Administration Console](accessing-the-administration-console-6187940.md "Problems with the signing into the administration console for SAP Cloud Identity Services.")

[User Import](user-import-6a46913.md "Problems with the user import in the administration console for SAP Cloud Identity Services.")

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

