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
-   \(For *SMS Two-Factor Authentication*\) You have an account in Sinch Service. You have configured Sinch Service in the administration console for Identity Authentication. For more information, see [Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-f4a04ed.md).

    > ### Note:  
    > Sinch Authentication 365 or Sinch Verification account is purchased separately. It isn’t part of the Identity Authentication contract.

-   \(For *E-Mail OTP Code*\) An E-Mail OTP Code template for the respective languages must exist in the tenant to apply the e-mail OTP code method. If the template does not exist, the user will see the option but when choosing it, the following message will appear: "Sorry, but you are currently not authorized for access".

    For more information how to add e-mail templates, see [Edit or Add an E-Mail Template Set](edit-or-add-an-e-mail-template-set-3c4f397.md).




<a name="loiobc52fbf3d59447bbb6aa22f80d8b6056__steps_yk5_2hs_25"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

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

6.  Configure the authentication rules. To configure the authentication rules, choose one of the following:


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

    See [Create a New Rule](configure-risk-based-authentication-for-an-application-bc52fbf.md#loio18d02ab9cc7d4caf83d8654c8c51a175)


    
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

7.  Configure the *Default Action*:

    -   *Allow* - Any user can log on from any IP. This is te default choice.
    -   *Deny* - Nobody can log on.
    -   *Two-Factor Authentication* - A drop-down appears when this choice is selected. You must specify the two-factor authentication method or methods for the end user.

8.  Save your changes.

    Once the application has been updated, the system displays the message ***Authentication rules updated***.


 <a name="concept_vdp_q51_r5"/>

<!-- concept\_vdp\_q51\_r5 -->

## Examples



## Example 1 \(Setting TOTP Two-Factor Authentication\)

Donna Moore is an administrator of company A. She wants to configure Identity Authentication to always ask the company employees for a password and a TOTP passcode \(two-factor authentication\) to log on to a *Leave Request* application. For this purpose, Donna sets only a *Default Action*:

**Default Authentication Rule**

Default Action: [Two-Factor Authentication\]

Two-Factor Methods: [TOTP\]

Michael Adams is an employee of company A and as such he wants to create a leave request. To log on to the *Leave Request* application he provides his password. After that he is prompted to activate a mobile device and to provide a second factor for authentication \(a passcode generated by an authenticator app on his mobile device\). Two factors are required regardless of whether Michael is in the corporate network or on a business trip. Michael's manager, Julie Armstrong, receives a notification that Michael has created a leave request. She approves it by logging on to the application with two factors \(password and passcode generated by her mobile device\).



<a name="concept_vdp_q51_r5__section_hly_5ww_hhb"/>

## Example 2 \(Setting SMS Two-Factor Authentication\)

Donna Moore is an administrator of company A. She wants to configure Identity Authentication to always ask the company employees for a password and a SMS code \(two-factor authentication\) to log on to the *Corporate Page*. For this purpose, Donna first configures Sinch Service in the administration console for Identity Authentication. Then in the *Risk-Based Authentication* section in the administration console, he sets only a *Default Action*:

**Default Authentication Rule**

Default Action: [Two-Factor Authentication\]

Two-Factor Methods: [SMS\]

John Miller is an employee of company A and as such he wants to access the corporate page of the company. He is prompted to provide two factors \(password and the SMS code sent to his mobile device\) to log on to the corporate page. John Miller has his mobile phone verified, so he can receive SMS codes. Two factors are required regardless of whether Miller is in the corporate network or at home.



## Example 3 \(SPNEGO\)

Donna Moore is an administrator of company A. She wants to configure Identity Authentication to allow employees to access the *Leave Request* application from the corporate network with SPNEGO, and from any other network with passcode. All IPs in the company start with 189.101. She would also like to create a rule for the managers to access the application with two authentication factors. In addition she wants to restrict the access to all the users with type *Customer*. For this purpose, Donna creates the following rules:

**Authentication Rules**


<table>
<tr>
<th valign="top" align="center">

Action



</th>
<th valign="top" align="center">

IP Range



</th>
<th valign="top" align="center">

Group



</th>
<th valign="top">

Authentication Method



</th>
<th valign="top">

User Type



</th>
</tr>
<tr>
<td valign="top">

Deny



</td>
<td valign="top">

Any



</td>
<td valign="top">

Any



</td>
<td valign="top">

Any



</td>
<td valign="top">

Customer



</td>
</tr>
<tr>
<td valign="top">

Allow



</td>
<td valign="top">

189.101.112.1/16



</td>
<td valign="top">

Employees



</td>
<td valign="top">

SPNEGO



</td>
<td valign="top">

Any



</td>
</tr>
<tr>
<td valign="top">

TOTP Two-Factor Authentication



</td>
<td valign="top">

Any



</td>
<td valign="top">

Employees



</td>
<td valign="top">

Any



</td>
<td valign="top">

Any



</td>
</tr>
<tr>
<td valign="top">

TOTP Two-Factor Authentication



</td>
<td valign="top">

Any



</td>
<td valign="top">

Managers



</td>
<td valign="top">

Any



</td>
<td valign="top">

Any



</td>
</tr>
</table>

**Default Authentication Rule**

Default Action: [Deny\]

Michael Adams, as an employee of company A, accesses the application in his office and logs on with SPNEGO. When he is on a business trip, he can create leave requests by providing two factors. The two factors are SPNEGO and а passcode generated by an authenticator app on his iPhone. Michael's manager, Julie Armstrong, receives a notification that Michael has created a leave request. She approves it by logging on to the application with TOTP Two-Factor Authentication \(a password and a passcode generated by her Android phone\). Donna Moore, a customer of company A, tries to access the corporate portal, and receives a message that she is not authorized for access.



<a name="concept_vdp_q51_r5__section_bp5_w5p_hnb"/>

## Example 4 \(Setting Web Two-Factor Authentication\)

Donna Moore is an administrator of company A. She wants to configure Identity Authentication to always ask the company managers for a password and a web two-factor authentication to log on to an *Leave Request Approval* application. For this purpose, Donna sets only a *Default Action*:

**Default Authentication Rule**

Default Action: [Two-Factor Authentication\]

Two-Factor Methods: [Web Authentication\]

Michael Adams is an employee of company A and he creates a leave request. Michael's manager, Julie Armstrong, receives a notification that Michael has created a leave request. To log on to the *Leave Request Approval* application she provides her password. After that Julie is prompted to activate a security key as a second factor for authentication. Two factors are required regardless of whether Julie is in the corporate network or on a business trip.

Julie he approves the leave request by logging on to the application with two factors \(password and fingerprint\).



<a name="concept_vdp_q51_r5__section_bss_sdh_znb"/>

## Example 5 \(Setting more than one Two-Factor Authentication method\)

Donna Moore is an administrator of company A. She wants to configure Identity Authentication to always ask the company managers for a second factor in addition to their password. She wants to allow the managers to choose between a TOTP and a web two-factor authentication to log on to an *Leave Request Approval* application. For this purpose, Donna sets the *Default Action* to *Two-Factor Authentication* and configures the *Two-Factor Methods*:

**Default Authentication Rule**

Default Action: [Two-Factor Authentication\]

Two-Factor Methods: [TOTP\]; [Web Authentication\]

Michael Adams is an employee of company A and he creates a leave request. Michael's manager, Julie Armstrong, receives a notification that Michael has created a leave request. To log on to the application *Leave Request Approval* she provides her password. After that she is prompted to choose the two-factor authentication method. She chooses a security key as a second factor for authentication.

Julie approves the leave request by logging on to the application with two factors \(password and fingerprint\).

In addition to Julie's approval, the leave request must also be approved by the HR Manager of the company, John Miller. To log on to the *Leave Request Approval* application John provides his password. After that he is also prompted to choose the two-factor authentication method. John chooses TOTP. Now, he is prompted to provide a TOTP code from his device. After providing it, he is granted access to the app and approves the leave request.

Two factors are required regardless of whether Julie and John are in the corporate network or on a business trip.



<a name="concept_vdp_q51_r5__section_as2_mgf_t4b"/>

## Example 6 \(Setting Fowarded IP Range\)

Donna Moore is an administrator of company A. She wants to configure Identity Authentication to apply an additional IP range in risk-based authentication rules for system-to-system calls from SAP BTP. SAP BTP makes a system-to-system calls to Identity Authentication on customer's behalf and provides their original IP address with the request. Donna can configure the IP range for customer IPs, but it's mandatory that she configures the IP range for SAP BTP IP addresses, first.

**Related Information**  


[Create a New Rule](configure-risk-based-authentication-for-an-application-bc52fbf.md#loio18d02ab9cc7d4caf83d8654c8c51a175 "You can create rules for authentication according to different risk factors.")

[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

[Unlock User TOTP Passcode](unlock-user-totp-passcode-cb6615d.md "You can unlock a user passcode when the user must log on to the application before the automatic unlock time of 60 minutes has passed.")

[Multi-Factor Authentication](../User-Guide/multi-factor-authentication-0d41cd4.md "This document provides information about the second factor for authentication or how to log on if you are asked to provide a second factor to your primary credentials.")

 <a name="loio18d02ab9cc7d4caf83d8654c8c51a175"/>

<!-- loio18d02ab9cc7d4caf83d8654c8c51a175 -->

## Create a New Rule

You can create rules for authentication according to different risk factors.



## Context

Each rule contains the following information:

-   **Action**

    This action is performed if the rule conditions meet the defined criteria.

    You can choose one of the following actions:

    -   *Allow*

        Identity Authentication allows the authentication of the user in accordance with the rule conditions.

    -   *Deny*

        Identity Authentication denies the authentication of the user in accordance with the rule conditions. You can set this action for a test application for example, or before an application goes live.

        As long as this rule is valid, when users try to log on to the application, they get the following message: *Sorry, but you are currently not authorized for access*.

    -   *Two-Factor Authentication*

        > ### Note:  
        > If *Two-Factor Authentication* is selected, additionally, you must specify the two-factor method or methods for the user:
        > 
        > -   *TOTP Two-Factor Authentication*
        > 
        >     Identity Authentication asks two factors to authenticate the user.
        > 
        >     If you set TOTP two-factor authentication, users are required to provide a time-based one-time password \(TOTP\) called a passcode in addition to their primary credentials. Users also have to install an authenticator application on their mobile devices to generate TOTP passcodes.
        > 
        >     TOTP passcodes are time-based and valid for one logon attempt only.
        > 
        > -   *SMS Two-Factor Authentication*
        > 
        >     Identity Authentication asks two factors to authenticate the user.
        > 
        >     If you set SMS two-factor authentication, users are required to provide an SMS code sent to their mobile devices in addition to their primary credentials.
        > 
        >     > ### Remember:  
        >     > To use *SMS Two-Factor Authentication*, you must have configured SAP Authentication 365 in the administration consoled for Identity Authentication. For more information, see [Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-f4a04ed.md).
        >     > 
        >     > Users must have their mobile phone numbers verified. The tenant administrator can verify phone numbers manually in the administration console or via the SCIM API. For more information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md) and [Update User Resource \(Deprecated\)](../Development/update-user-resource-deprecated-9e36479.md).
        >     > 
        >     > If the user does not have a verified phone number, the number is verified during the first log on when SMS code is required. After the user provides user name and credentials, he or she should provide the phone number in the field and request a code. Then provide the received code in the respective field and choose *Continue*. If the submitted code is correct, the user is allowed access, and the telephone number is verified.
        > 
        > -   *Web Two-Factor Authentication*
        > 
        >     Identity Authentication asks two factors to authenticate the user.
        > 
        >     If you set web two-factor authentication, users are required to authenticate with a device such as the built in biometric scanners or USB, Bluetooth or Near-Field Communication \(NFC\) devices in addition to their primary credentials.
        > 
        > -   *E-Mail OTP Code*
        > 
        >     > ### Caution:  
        >     > For security reasons, the E-mail OTP code is not a recommended two-factor authentication method. You may consider using some of the other methods instead.
        > 
        >     Identity Authentication asks two factors to authenticate the user.
        > 
        >     If you set *E-Mail OTP Code*, users are required to provide the code sent to their e-mail in addition to their primary credentials.
        > 
        >     > ### Remember:  
        >     > An E-Mail OTP Code template for the respective languages must exist in the tenant to apply the e-mail OTP code method. If the template does not exist, the user will see the option but when choosing it, the following message will appear: "Sorry, but you are currently not authorized for access".
        >     > 
        >     > For more information how to add e-mail templates, see [Edit or Add an E-Mail Template Set](edit-or-add-an-e-mail-template-set-3c4f397.md).
        > 
        > -   *RADIUS Server Two Factor Authentication*
        > 
        >     If you set *RADIUS Server Two Factor Authentication*, users are required to provide a RADIUS passcode in addition to their primary credentials. Users must have a RADIUS token \(hard or soft\) configured for them to generate passcodes. For more information about how to configure RADIUS server in Identity Authentication, see [Configure RADIUS Server Settings \(Beta\)](configure-radius-server-settings-beta-03043ae.md).


    The *Action* filed is mandatory.

-   *IP Range*

    Define the range of allowed IP addresses or proxies that the user logs on from. The value has to be specified in Classless Inter-Domain Routing \(CIDR\) notation.

    > ### Note:  
    > By default the field is empty, meaning that any IP is allowed.

    > ### Example:  
    > Enter 123.45.67.1/24 to allow users to log on from any IP starting with 123.45.67.

    If no IP range is defined, the rule is valid for all IP ranges.

-   *Forwarded IP Range*

    Define the range of allowed IP addresses or proxies for the original IP addresses that the user logs on from. The value has to be specified in Classless Inter-Domain Routing \(CIDR\) notation.

    > ### Remember:  
    > To specify the *Forwarded IP Range*, the *IP Range* must be defined first.

-   *Group*

    Specify a cloud or on-premise group, which the authenticating user has to be a member of. If no group is selected, the rule is valid for all users.

    If the rule is valid for an on-premise group, type in the name of the corporate user store group, for which this rule should be valid.

    The cloud groups have to be configured in the administration console for Identity Authentication. For more information, see [User Groups](user-groups-ddd067c.md).

-   *Authentication Method*

    Specify the authenticating method, which the authenticating user has to use. If no method is selected, the rule is valid for any of the methods.

-   *User Type*

    Specify the type, which the authenticating user must have. If no user type is selected, the rule is valid for any of the types.

-   *Corporate Attribute*

    Specify an attribute from the corporate identity provider \(IdP\) assertion, based on which the rule action will be applied.

    The rule must include the attribute name and value. It is valid only when the specified name and value are found in the assertion from the corporate IdP.

    > ### Note:  
    > For this rule, the *Apply Application Configurations* option of *Identity Federation* must be enabled. For more information, see [Configure Identity Federation](configure-identity-federation-c029bbb.md).


The fields *IP Range*, *Group*, *Authentication Method*, and *User Type* are not mandatory, but at least one of them has to be specified.



<a name="loio18d02ab9cc7d4caf83d8654c8c51a175__steps_jtp_sqg_t5"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the list item of the application that you want to edit.

    > ### Note:  
    > If you do not have a created application in your list, you can create one. For more details, see Related Information.

    > ### Caution:  
    > The list also includes the `Administration Console` application. If you enable risk-based authentication for that application, make sure that you, as a tenant administrator, meet the authentication rules and the default authentication rule. Otherwise when you log out of the administration console you will not be able to log in it again if you don't meet the rules.
    > 
    > If `Administration Console` is not in the list of the applications you may request it. To do this, you need to report an incident with a subject on [SAP Support Portal Home](https://support.sap.com/en/index.html) under the component `BC-IAM-IDS`.

4.  Choose the *Authentication and Access* tab.

5.  Under *AUTHENTICATION*, choose *Risk-Based Authentication*.

6.  Choose *Create Rule*.

7.  Fill in the fields on the *New Risk-Based Authentication Rule* window.

8.  Choose *Create*.

9.  Save your changes.


**Related Information**  


[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

