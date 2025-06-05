<!-- loio24c9b5164dcb44a3b97b08a8c889550a -->

# Enable Phone Verification for an Application

Tenant administrators can enable phone verification via SMS code for an application.



<a name="loio24c9b5164dcb44a3b97b08a8c889550a__prereq_wp1_ttc_3db"/>

## Prerequisites

-   You have an account in Sinch Service.

-   You have configured Sinch Service. For more information, see [Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-f4a04ed.md).




<a name="loio24c9b5164dcb44a3b97b08a8c889550a__context_nwk_4gk_3db"/>

## Context

This option requires the user to provide his or her phone number in the registration or upgrade forms. After that the user receives a verification code which must be provided so that the registration or upgrade is completed. If the code fails to arrive, the user has up to five attempts to request a new code via SMS.

After that the user can either contact the system adminstrator or request a code via a phone call. Again the user has up to five attempts to request a new code via phone call. The user can trigger one phone call per session.

When this feature is enabled, the `Phone` attribute becomes required and is not configurable for user registration or upgrade. For more information, see [Configure Registration and Upgrade Forms](configure-registration-and-upgrade-forms-93a9e18.md).



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Branding and Layout* tab.

5.  Under *APPLICATION FORMS CUSTOMIZATION*, enable *Phone Verification via SMS*.

    If the operation is successful, you receive the following message: ***Application <Application Name\> updated***. The slider is switched to *ON*.

    > ### Note:  
    > If you do not want to use phone verification via SMS for an application, you can drag the slider next to it to *OFF*.

6.  **Optional:** Configure rules to skip phone verification for user types and save your changes. To configure the authentication rules, choose one of the following:


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Add a new rule
    
    </td>
    <td valign="top">
    
    See [Add a New Phone Verification Rule](add-a-new-phone-verification-rule-e920324.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Delete an existing rule
    
    </td>
    <td valign="top">
    
    Choose the delete ![](images/delete_icon_4801c38.png) icon next to the rule you want to delete.
    
    </td>
    </tr>
    </table>
    
    If the operation is successful, the system displays the message ***Verification rules updated***.




<a name="loio24c9b5164dcb44a3b97b08a8c889550a__result_knb_k2d_3db"/>

## Results

Newly created users are required to provide their phone numbers during the self-registration process.

Existing users are required to provide their phone numbers in the upgrade form.

Users should enter the code sent by SMS to their phones in order to finish the validation process.

After the phone number is verified, the user can change it on the profile page, after entering a code sent by SMS to their phones.

