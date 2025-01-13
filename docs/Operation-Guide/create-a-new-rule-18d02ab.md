<!-- loio18d02ab9cc7d4caf83d8654c8c51a175 -->

# Create a New Rule

You can create rules for authentication according to different risk factors.



## Context

Each rule contains the following information:

-   **Authentication Action**

    This action is performed if the rule conditions meet the defined criteria.

    You can choose one of the following authentication actions:

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
        >     > To use *SMS Two-Factor Authentication*, you must have configured Sinch Verification in the administration console for SAP Cloud Identity Services. For more information, see [Configure Sinch Service in Administration Console](configure-sinch-service-in-administration-console-f4a04ed.md).
        >     > 
        >     > Users must have their mobile phone numbers verified. The tenant administrator can verify phone numbers manually in the administration console or via the SCIM API. For more information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md) and [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/resource/Users).
        >     > 
        >     > If the user does not have a verified phone number, the number is verified during the first log on when SMS code is required. After the user provides user name and credentials, he or she should provide the phone number in the field and request a code. Then provide the received code in the respective field and choose *Continue*. If the submitted code is correct, the user is allowed access, and the telephone number is verified.
        > 
        > -   *Web Two-Factor Authentication*
        > 
        >     Identity Authentication asks two factors to authenticate the user.
        > 
        >     If you set web two-factor authentication, users are required to authenticate with a device such as the built in biometric scanners or USB, Bluetooth or Near-Field Communication \(NFC\) devices in addition to their primary credentials.
        > 
        > -   *Email OTP Code*
        > 
        >     Identity Authentication asks two factors to authenticate the user.
        > 
        >     If you set *Email OTP Code*, users are required to provide the code sent to their email in addition to their primary credentials.
        > 
        >     > ### Caution:  
        >     > For security reasons, the Email OTP code is not a recommended two-factor authentication method. You may consider using some of the other methods instead.
        > 
        >     > ### Note:  
        >     > In the scenario, when self-registration is enabled and email verification is disabled for the application, if you set only *Email OTP Code* in the rule, users that have registered themselves in the application are required to provide an email OTP code when they activate their account. They provide the received code in the respective field and choose *Continue*. If the submitted code is correct, the user is allowed access, and the email is verified.
        > 
        >     > ### Remember:  
        >     > An Email OTP Code template for the respective languages must exist in the tenant to apply the email OTP code method. If the template does not exist, the user will see the option but when choosing it, the following message will appear: "Sorry, but you are currently not authorized for access".
        >     > 
        >     > For more information how to add email templates, see [Edit or Add an Email Template Set](edit-or-add-an-email-template-set-3c4f397.md).
        > 
        > -   *RADIUS Server Two Factor Authentication*
        > 
        >     If you set *RADIUS Server Two Factor Authentication*, users are required to provide a RADIUS passcode in addition to their primary credentials. Users must have a RADIUS token \(hard or soft\) configured for them to generate passcodes. For more information about how to configure RADIUS server in Identity Authentication, see [Configure RADIUS Server Settings \(Beta\)](configure-radius-server-settings-beta-03043ae.md).


    > ### Remember:  
    > The *Authentication Action* filed is mandatory.

-   *IP Range*

    Define a range of IP addresses that authentication requests to Identity Authentication can be sent from. The value has to be specified in Classless Inter-Domain Routing \(CIDR\) notation.

    > ### Note:  
    > By default the field is empty, meaning that any IP is allowed.

    > ### Example:  
    > Enter 123.45.67.1/24 to allow users to log on from any IP starting with 123.45.67.

    If no IP range is defined, the rule is valid for all IP ranges.

-   *Forwarded IP Range*

    Define a range of IP addresses for the original IP addresses that authentication requests to Identity Authentication can be sent from. The value has to be specified in Classless Inter-Domain Routing \(CIDR\) notation.

    > ### Caution:  
    > This range configuration is used in scenarios where authentication requests to Identity Authentication are made by a proxy server on-behalf of the user/client.
    > 
    > Configuring the *Forwarded IP Range* for the client/user IPs requires configuring the IP Range for the proxy server IP address\(es\), that directly communicates with Identity Authentication, first.
    > 
    > Identity Authentication expects the client IP to be sent by the proxy server in the **X-Forwarded-For** header of the authentication request.

    > ### Remember:  
    > Identity Authentication does not have control over the involved proxies and their number, participating in the request between the client/user and Identity Authentication and whether these proxies behave according to the scenario. Therefore it is not guaranteed that the client IP address is sent in the above mentioned header alongside the IP addresses of the proxies \(if any\) to Identity Authentication.

-   *Authentication Method*

    Specify the authenticating method, which the authenticating user has to use. If no method is selected, the rule is valid for any of the methods.

    You can choose from the following:

    -   *Client Certificate*
    -   *SPNEGO*
    -   *User Name and Password*
    -   *Token*
    -   *Social Identity Provider*
    -   *Trusted IdP SAML Assertion*

    > ### Note:  
    > If the user has an active session with any of the methods, and that method is included in the rule, they can access the application without the need for additional authentication.

-   *User Type*

    Specify the type, which the authenticating user must have. If no user type is selected, the rule is valid for any of the types.

-   *Group Type*
    -   Cloud Group - A group that is created in the Identity Directory of Cloud Identity services. This is the default choice. For more information about the Identity Directory groups, see [Groups](../groups-d93be69.md).
    -   On-Premise Group - A corporate user store group.

-   *Group*

    > ### Restriction:  
    > The administrator must be assigned the *Manage Groups* role or be part of a policy that allows reading groups to be able to view the groups in the list. For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md) or [Configure Group Authorizations](configure-group-authorizations-7a09cad.md).

    Specify a cloud or on-premise group, which the authenticating user has to be a member of. If no group is selected, the rule is valid for all users.

    If the rule is valid for an on-premise group, type in the name of the corporate user store group, for which this rule should be valid.

    The cloud groups have to be configured in the administration console for SAP Cloud Identity Services. For more information, see [Managing Groups](managing-groups-ddd067c.md).

-   *Corporate Attribute*

    Specify an attribute from the corporate identity provider \(IdP\) assertion, based on which the rule action will be applied.

    The rule must include the attribute name and value. It is valid only when the specified name and value are found in the assertion from the corporate IdP.

    > ### Note:  
    > For this rule, the *Apply Application Configurations* option of *Identity Federation* must be enabled. For more information, see [Configure Identity Federation](configure-identity-federation-c029bbb.md).

-   *Email Domain*

    Specify a domain for the email of the authenticating user.


The fields *IP Range*, *Forwarded IP Range*, *Group*, *Authentication Method*, and *User Type* are not mandatory, but at least one of them has to be specified.



<a name="loio18d02ab9cc7d4caf83d8654c8c51a175__steps_jtp_sqg_t5"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

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


[Configure Risk-Based Authentication for an Application](configure-risk-based-authentication-for-an-application-bc52fbf.md#loiobc52fbf3d59447bbb6aa22f80d8b6056 "You can define rules for authentication according to different risk factors and apply actions like Allow, Deny, and Two-Factor Authentication.")

[Examples for Risk-Based Authentication Scenarios](examples-for-risk-based-authentication-scenarios-fedc77c.md "Example scenarios for configuring risk-based authentication for an application.")

[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

