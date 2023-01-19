<!-- loiof7ec8d2cccde486d83353654d6c1f18a -->

# Enable IdP-Initiated SSO from All Corporate Identity Providers

\(For SAML 2.0 applications\) Tenant administrators can enable IdP-initiated single sign-on \(SSO\) from all configured corporate identity providers \(IdPs\).



<a name="loiof7ec8d2cccde486d83353654d6c1f18a__prereq_s3p_sq3_3bb"/>

## Prerequisites

-   You are assigned the *Manage Applications* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have more than one corporate identity provider, which is configured in the administration console. For more information how to configure a corporate identity provider, see [Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md).

-   \(For SAML 2.0 applications\) You have added the assertion consumer \(ACS\) endpoint with the URL of the application's protected page, and the index, in the metadata of that application. The ACS endpoint that you added should look like the following example:

    > ### Sample Code:  
    > ```
    > <ns3:AssertionConsumerService index="1" isDefault="false" Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST" Location="https://<application URL>/protected.jsp"
    > />
    > ```

    For more information how to configure your ACS endpoint in the administration for Identity Authentication, see [Configure SAML 2.0 Service Provider](configure-saml-2-0-service-provider-51f1f75.md).




## Context

Applications can be configured to trust all the corporate identity providers configured in the administration console when identity provider \(IdP\) initiated single sign-on \(SSO\) is used. The user accesses the application via URL provided by the corporate identity provider.

To enable IdP-initiated SSO with all corporate identity providers configured in the administration console for SAP Cloud Identity Services follow the procedure below:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under the *Conditional Authentication* section, enable the *Trust All Corporate Identity Providers* option.

    > ### Note:  
    > By default this option is disabled.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.




<a name="loiof7ec8d2cccde486d83353654d6c1f18a__result_fhp_jtn_jbb"/>

## Results

The application trusts all corporate identity providers that are configured in the administration console for SAP Cloud Identity Services.

**Related Information**  


[Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md "You choose between a local identity provider and a corporate identity provider to be the default identity provider for your application.")

[Configure Logon via Identity Authentication when a Corporate IdP is Chosen as Default](configure-logon-via-identity-authentication-when-a-corporate-idp-is-chosen-as-default-3a3bf9b.md "You can allow users to log on via Identity Authentication when a corporate identity provider (IdP) is chosen as default.")

[Configure Conditional Authentication for an Application](configure-conditional-authentication-for-an-application-0143dce.md "Tenant administrator can define rules for authenticating identity provider according to e-mail domain, user type, user group, and IP range (specified in CIDR notation).")

[Configure IdP-Initiated SSO with Corporate Identity Providers](configure-idp-initiated-sso-with-corporate-identity-providers-d483a52.md#loiod483a52be22946d5a05951b0fa16221f "This document shows you how to configure identity provider (IdP) initiated single sign-on (SSO) with corporate identity providers.")

