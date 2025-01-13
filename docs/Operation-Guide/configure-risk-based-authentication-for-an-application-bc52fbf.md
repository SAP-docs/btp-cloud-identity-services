<!-- loiobc52fbf3d59447bbb6aa22f80d8b6056 -->

# Configure Risk-Based Authentication for an Application

You can define rules for authentication according to different risk factors and apply actions like *Allow*, *Deny*, and *Two-Factor Authentication*.

**Authentication Rules**

The created rules are displayed sorted by priority. When a user tries to access the application, the rules evaluate if the user meets the criteria of the rule. The evaluation starts with the rule with the highest priority, until the criteria of a rule are met. If the criteria of a rule are met, the rest of the rules aren’t evaluated.

**Default Authentication Rule**

If none of the authentication rules meets the criteria, the default authentication rule is applied. For the default authentication rule, you can configure a *Default Action*, which can be *Allow*, *Deny*, or *Two-Factor Authentication*.

> ### Note:  
> If *Two-Factor Authentication* is selected, additionally, you must specify the two-factor method or methods for the user.

The rule is valid for any *IP range*, *Forwarded IP Range*, *Group*, *Authentication Method*, or *User Type*.



<a name="loiobc52fbf3d59447bbb6aa22f80d8b6056__prereq_lx3_qzw_hhb"/>

## Prerequisites

-   \(For *RADIUS Server Two-Factor Authentication*\) You have requested this feature. For more information how to request and configure RADIUS server in Identity Authentication, see [Configure RADIUS Server Settings \(Beta\)](configure-radius-server-settings-beta-03043ae.md).
-   \(For *SMS Two-Factor Authentication*\) You have an account in Sinch Service. You have configured Sinch Service in the administration console for SAP Cloud Identity Services. For more information, see [Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-f4a04ed.md).

    > ### Note:  
    > Sinch Verification account is purchased separately. It isn’t part of the Identity Authentication contract.

-   \(For *Email OTP Code*\) An Email OTP Code template for the respective languages must exist in the tenant to apply the email OTP code method. If the template does not exist, the user will see the option but when choosing it, the following message will appear: "Sorry, but you are currently not authorized for access".

    For more information how to add email templates, see [Edit or Add an Email Template Set](edit-or-add-an-email-template-set-3c4f397.md).




<a name="loiobc52fbf3d59447bbb6aa22f80d8b6056__context_gvf_fds_s1c"/>

## Context

> ### Tip:  
> We recommend you to enable the back-up channels. Thus, the users can use the option as an alternative when they don't have access to the TOTP device or application.. For more information, see [Enable Back-Up Channels to Send Passcode for Deactivation of TOTP Two-Factor Authentication Devices](enable-back-up-channels-to-send-passcode-for-deactivation-of-totp-two-factor-authenticati-782935e.md).



<a name="loiobc52fbf3d59447bbb6aa22f80d8b6056__steps_yk5_2hs_25"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the list item of the application that you want to edit.

    > ### Note:  
    > If you do not have a created application in your list, you can create one. For more details, see Related Information.

    > ### Caution:  
    > The list also includes the `Administration Console` application. If you enable risk-based authentication for that application, make sure that you, as a tenant administrator, meet the authentication rules and the default authentication rule. Otherwise when you log out of the administration console you will not be able to log in it again if you don't meet the rules.
    > 
    > If `Administration Console` is not in the list of the applications you may request it. To do this, report an incident with a subject on [SAP Support Portal Home](https://support.sap.com/en/index.html) under the component `BC-IAM-IDS`.

4.  Choose the *Authentication and Access* tab.

5.  Under *AUTHENTICATION*, choose *Risk-Based Authentication*.

6.  **Optional:** Configure the authentication rules. To configure the authentication rules, choose one of the following:


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
    
    Create a new rule
    
    </td>
    <td valign="top">
    
    See [Create a New Rule](create-a-new-rule-18d02ab.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Edit an existing rule
    
    </td>
    <td valign="top">
    
    Choose the ![](images/edit_icon_d077ded.png) icon next to the rule you want to edit.
    
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
    <tr>
    <td valign="top">
    
    Reprioritize rules
    
    </td>
    <td valign="top">
    
    Use the arrows to reprioritize the rules.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > By default any user can log on from any IP.

7.  **Optional:** Configure the *Default Action*:

    -   *Allow* - Any user can log on from any IP. This is the default choice.
    -   *Deny* - Nobody can log on.
    -   *Two-Factor Authentication* - A drop-down appears when this choice is selected. You must specify the two-factor authentication method or methods for the end user.

8.  Save your changes.

    Once the application has been updated, the system displays the message ***Authentication rules updated***.


**Related Information**  


[Create a New Rule](create-a-new-rule-18d02ab.md "You can create rules for authentication according to different risk factors.")

[Examples for Risk-Based Authentication Scenarios](examples-for-risk-based-authentication-scenarios-fedc77c.md "Example scenarios for configuring risk-based authentication for an application.")

[SAP Cloud Identity Services Application Directory](https://api.sap.com/api/SCI_Application_Directory/overview)

