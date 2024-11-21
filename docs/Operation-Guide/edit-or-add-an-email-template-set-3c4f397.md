<!-- loio3c4f39763f3c4d659a43e1c33c94b95e -->

# Edit or Add an Email Template Set

Tenant administrators can configure language versions of each template in the template set. They can also set a custom template for each language, and change the name of each template set.



<a name="loio3c4f39763f3c4d659a43e1c33c94b95e__prereq_pf3_kcb_fbb"/>

## Prerequisites

-   You are assigned the *Manage Tenant Configuration* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have prepared the plain text \(TXT\) and HTML template files that will be added in the email template set.

    For that purpose, you need to open the default template set for the respective application process in the administration console. After that, copy and paste the texts in a new file, edit the texts according to your needs, and save a copy of your versions of the documents. For more information how to open the default templates, see [View Email Template Document](view-email-template-document-148568a.md).

    > ### Remember:  
    > .Both, the TXT and HTML template files, must be saved with UTF-8 encoding.

    If you want to use a custom template set in another language, first you need to open the template set for the respective application process in the administration console. After that, copy and paste the texts in a new file, edit the texts in the respective language, and again save a copy of your versions of the documents. For more information how to open the default templates, see [View Email Template Document](view-email-template-document-148568a.md)

    > ### Caution:  
    > You should use only the placeholders used in the template documents. If you use other placeholders, even if they are in comments, emails for the respective process will not be sent. For more information, see [Allowed Placeholders per Email Template](allowed-placeholders-per-email-template-c0d4a76.md).
    > 
    > When you edit texts in languages written in Right-To-Left \(RTL\) direction check that the placeholders are situated in the right place.

    > ### Remember:  
    > If you do not specify a version for a custom template of a specific process, users will receive the email from the default template set for this process. If you do not set an email template for the self-registration process for example, users will receive the default activation email when they complete the registration.
    > 
    > If you do not specify a language version for a custom template of a specific process, users will receive the email from the default template set for this process.

    > ### Note:  
    > Both the HTML and TXT formats are included in the emails sent to a user. What the user sees, depends on the settings of his or her email client.




<a name="loio3c4f39763f3c4d659a43e1c33c94b95e__context_plz_lq1_fbb"/>

## Context

To edit or add an email template, follow the procedure below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Email Template Sets* tile.

    This operation opens a list of the template sets.

3.  Choose the list item of the template set you want to edit.

4.  **Optional:** To change the name of the template set, choose it.

5.  Select the tab signifying the process, which you want to add or change the template for.

6.  Add another language version by choosing the *\+Add Language* button or edit an existing language version by selecting the respective list item.

    1.  Choose language from the dropdown.

        > ### Note:  
        > The dropdown is grayed out when you are editing an existing language version.

    2.  Specify the subject.

        This is the subject of the email that the user receives for the respective process. You are allowed to include placeholders in the subject's text.

        > ### Note:  
        > The subject must contain at least one non-space character.

    3.  Upload the plain text template file that you have prepared.

        The text file can contain placeholders and HTML tags. For more information about the allowed placeholders, see [Allowed Placeholders per Email Template](allowed-placeholders-per-email-template-c0d4a76.md).

        > ### Remember:  
        > The *$\{other.securityAlertText\}* is mandatory for the *Send Security Alert* template. The *$\{other.securityAlertText\}* is customizable. For more information, see [Change Tenant Texts REST API](../Development/change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6). The key-value pairs that should be changed are `security.alert.<name of the flow>`.
        > 
        > The *$\{other.totpResetPasscode\}* is mandatory for the *Deactivate TOTP Device* template.

        See examples for the *Deactivate TOTP Device* and *Email OTP Code* templates below:

        *Deactivate TOTP Device*

        > ### Example:  
        > Dear $\{user.firstName\} $\{user.lastName\},
        > 
        > The passcode to deactivate your Two-Factor Authentication device is $\{other.totpResetPasscode\}.
        > 
        > Best regards,
        > 
        > Your System Administrator
        > 
        > This email may contain trade secrets or privileged, undisclosed, or otherwise confidential information. If you have received this email in error, you are hereby notified that any review, copying, or distribution of it is strictly prohibited. Please inform us immediately and destroy the original transmittal. Thank you for your cooperation.

        *Email OTP Code Template*

        > ### Example:  
        > Dear $\{user.firstName\} $\{user.lastName\},
        > 
        > The code for Email Two-Factor Authentication is $\{other.emailOtpCode\}.
        > 
        > Best regards,
        > 
        > Your System Administrator
        > 
        > This email may contain trade secrets or privileged, undisclosed, or otherwise confidential information. If you have received this email in error, you are hereby notified that any review, copying, or distribution of it is strictly prohibited. Please inform us immediately and destroy the original transmittal. Thank you for your cooperation.

    4.  Upload the HTML template file that you have prepared.

        The content of the HTML file must comply with the HTML markup requirements, and the file can contain placeholders. For more information about the allowed placeholders, see [Allowed Placeholders per Email Template](allowed-placeholders-per-email-template-c0d4a76.md).

        > ### Remember:  
        > The *$\{other.securityAlertText\}* is mandatory for the *Send Security Alert* template. The *$\{other.securityAlertText\}* is customizable. For more information, see [Change Tenant Texts REST API](../Development/change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6). The key-value pairs that should be changed are `security.alert.<name of the flow>`.
        > 
        > The *$\{other.totpResetPasscode\}* is mandatory for the *Deactivate TOTP Device* template.

        See examples for the *Deactivate TOTP Device* and *Email OTP Code* templates below:

        *Deactivate TOTP Device Template*

        > ### Example:  
        > ```
        > html>
        > 
        > <head>
        >     <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
        > <script type="text/javascript" src="/ruxitagentjs_ICA27SVfqrux_10179191120132458.js" data-dtconfig="uam=1|app=ea7c4b59f27d43eb|featureHash=ICA27SVfqrux|rdnt=1|uxrgce=1|bp=2|srms=1,1,,,|uxrgcm=100,25,300,3;100,25,300,3|dpvc=1|lastModification=1574413554517|dtVersion=10179191120132458|tp=500,50,0,1|uxdcw=1500|agentUri=/ruxitagentjs_ICA27SVfqrux_10179191120132458.js|reportUrl=/rb_c52c6336-5dbb-45f1-aa35-08a6f855165d|rid=RID_2026897975|rpid=-1322452711|domain=sap.corp"></script></head>
        > 
        > <body style="width: 600px;margin: auto;padding: 0;font-family: Arial, Helvetica, sans-serif;font-size: 14px;color: #333">
        >     <!-- gold bar -->
        >     <table cellspacing="0" cellpadding="0" width="600px" class="header" style="border-bottom-style: solid;border-bottom-color: #F0AB00;border-bottom-width: 8px;padding-top: 13px;padding-bottom: 12px">
        >         <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >             <td style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >                 <table cellspacing="0" cellpadding="0">
        >                     <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >                         <td class="logo" style="border-collapse: collapse;width: 61px;padding: 0;margin: 0">
        >                             <img src="${user.sap_mailing_logo}" style="border: 0;height: auto;line-height: 100%;outline: none;text-decoration: none" /></td>
        >                         <td class="tagline" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0;color: #888;font-weight: bold;font-size: 12px;padding-top: 2px">The Best-Run Businesses Run SAP</td>
        >                     </tr>
        >                 </table>
        >             </td>
        >             <#if user.company_logo??>
        >                 <td align="right" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >                     <div class="companylogo" style="height: 32px;overflow: hidden"><img src="${user.company_logo}" style="border: 0;height: 32px;line-height: 100%;outline: none;text-decoration: none;width: auto" /></div>
        >                 </td>
        >             </#if>
        >         </tr>
        >     </table>
        >     <table cellspacing="0" cellpadding="0" width="600px">
        >         <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >             <td class="main_first" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0;padding-top: 36px;padding-bottom: 12px">
        >                 <h1 style="font-family: Arial, Helvetica, sans-serif;font-weight: bold;font-size: 20px;color: #555;margin-bottom: 24px">Dear ${user.firstName?html} ${user.lastName?html},</h1>
        >                 <p style="font-family: Arial, Helvetica, sans-serif;font-size: 14px;line-height: 18px">The passcode to deactivate your Two-Factor Authentication device is ${other.totpResetPasscode}.</p>
        >             </td>
        >         </tr>
        >     </table>
        >     <table cellspacing="0" cellpadding="0" width="600px">
        >         <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >             <td class="main_last" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0;padding-top: 12px;padding-bottom: 36px">
        >                 <p style="font-family: Arial, Helvetica, sans-serif;font-size: 14px;line-height: 18px">Best regards,
        >                     <br/> Your System Administrator</p>
        >             </td>
        >         </tr>
        >     </table>
        >     <table cellpadding="0" cellspacing="0" width="600px">
        >         <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >             <td class="colophon" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0;font-size: 11px;color: #888;line-height: 13px">
        >                 <p style="font-family: Arial, Helvetica, sans-serif;font-size: 11px;line-height: 13px;color: #888">This email may contain trade secrets or privileged, undisclosed, or otherwise confidential information. If you have received this email in error, you are hereby notified that any review, copying, or distribution of it is strictly prohibited. Please inform us immediately and destroy the original transmittal. Thank you for your cooperation.</p>
        >             </td>
        >         </tr>
        >     </table>
        > </body>
        > 
        > </html>
        > ```

        *Email OTP Code Template*

        > ### Example:  
        > ```
        > 
        > <html>
        > 
        > <head>
        >     <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
        > </head>
        > 
        > <body style="width: 600px;margin: auto;padding: 0;font-family: Arial, Helvetica, sans-serif;font-size: 14px;color: #333">
        >     <!-- gold bar -->
        >     <table cellspacing="0" cellpadding="0" width="600px" class="header" style="border-bottom-style: solid;border-bottom-color: #F0AB00;border-bottom-width: 8px;padding-top: 13px;padding-bottom: 12px">
        >         <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >             <td style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >                 <table cellspacing="0" cellpadding="0">
        >                     <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >                         <td class="logo" style="border-collapse: collapse;width: 61px;padding: 0;margin: 0">
        >                             <img src="${user.sap_mailing_logo}" style="border: 0;height: auto;line-height: 100%;outline: none;text-decoration: none" /></td>
        >                         <td class="tagline" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0;color: #888;font-weight: bold;font-size: 12px;padding-top: 2px">The Best-Run Businesses Run SAP</td>
        >                     </tr>
        >                 </table>
        >             </td>
        >             <#if user.company_logo??>
        >                 <td align="right" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >                     <div class="companylogo" style="height: 32px;overflow: hidden"><img src="${user.company_logo}" style="border: 0;height: 32px;line-height: 100%;outline: none;text-decoration: none;width: auto" /></div>
        >                 </td>
        >             </#if>
        >         </tr>
        >     </table>
        >     <table cellspacing="0" cellpadding="0" width="600px">
        >         <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >             <td class="main_first" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0;padding-top: 36px;padding-bottom: 12px">
        >                 <h1 style="font-family: Arial, Helvetica, sans-serif;font-weight: bold;font-size: 20px;color: #555;margin-bottom: 24px">Dear ${user.firstName?html} ${user.lastName?html},</h1>
        >                 <p style="font-family: Arial, Helvetica, sans-serif;font-size: 14px;line-height: 18px">The code for Email Two-Factor Authentication is ${other.emailOtpCode}.</p>
        >             </td>
        >         </tr>
        >     </table>
        >     <table cellspacing="0" cellpadding="0" width="600px">
        >         <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >             <td class="main_last" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0;padding-top: 12px;padding-bottom: 36px">
        >                 <p style="font-family: Arial, Helvetica, sans-serif;font-size: 14px;line-height: 18px">Best regards,
        >                     <br/> Your System Administrator</p>
        >             </td>
        >         </tr>
        >     </table>
        >     <table cellpadding="0" cellspacing="0" width="600px">
        >         <tr style="border-collapse: collapse;width: 600px;padding: 0;margin: 0">
        >             <td class="colophon" style="border-collapse: collapse;width: 600px;padding: 0;margin: 0;font-size: 11px;color: #888;line-height: 13px">
        >                 <p style="font-family: Arial, Helvetica, sans-serif;font-size: 11px;line-height: 13px;color: #888">This email may contain trade secrets or privileged, undisclosed, or otherwise confidential information. If you have received this email in error, you are hereby notified that any review, copying, or distribution of it is strictly prohibited. Please inform us immediately and destroy the original transmittal. Thank you for your cooperation.</p>
        >             </td>
        >         </tr>
        >     </table>
        > </body>
        > 
        > </html>
        > ```


7.  Save your selection.

    Once the email template has been updated, the system displays the message ***Email template <name of template\> updated***.




<a name="loio3c4f39763f3c4d659a43e1c33c94b95e__result_m33_mqp_fbb"/>

## Results

When you edit a previous version of a template in the template set, the changes are applied immediately. The email that is sent contains the latest changes.

When you create a new template set, you must assign the new template set to the application. If you do not assign it, the application will use the currently assigned template.

**Related Information**  


[Create a New Email Template Set](create-a-new-email-template-set-a6fca8b.md "Tenant administrators can create a new set of email templates so that each template in the set can have a custom language version.")

[View Email Template Document](view-email-template-document-148568a.md "Tenant administrators can view language email templates in the template set uploaded in the administration console for SAP Cloud Identity Services.")

[Define an Email Template Set for an Application](define-an-email-template-set-for-an-application-fc6b54a.md "Tenant administrators can define the email template set that the application uses.")

[Delete an Email Template Set](delete-an-email-template-set-6fce69d.md "Tenant administrators can delete an email template set or a language version for a specific application process.")

[Allowed Placeholders per Email Template](allowed-placeholders-per-email-template-c0d4a76.md "This document describes which placeholders can be used in each email template.")

