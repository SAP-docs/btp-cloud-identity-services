<!-- loiof7ec8d2cccde486d83353654d6c1f18a -->

# Enable SSO with Corporate Identity Providers

Tenant administrators can enable IdP-initiated Single Sign-On \(SSO\) from one, more than one or all configured corporate identity providers \(IdPs\).



<a name="loiof7ec8d2cccde486d83353654d6c1f18a__prereq_s3p_sq3_3bb"/>

## Prerequisites

-   You are assigned the *Manage Applications* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have more than one corporate identity provider, which is configured in the administration console. For more information on how to configure a corporate identity provider, see [Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md) or [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).

-   \(For SAML 2.0 applications\) You have added the assertion consumer \(ACS\) endpoint with the URL of the application's protected page, and the index, in the metadata of that application. The ACS endpoint that you added should look like the following example:

    > ### Sample Code:  
    > ```
    > <ns3:AssertionConsumerService index="1" isDefault="false" Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST" Location="https://<application URL>/protected.jsp"
    > />
    > ```

    For more information how to configure your ACS endpoint in the administration for Identity Authentication, see [Configure SAML 2.0 Service Provider](configure-saml-2-0-service-provider-51f1f75.md).




## Context

Applications can be configured to trust one, more than one, or all corporate identity providers configured in the administration console when identity provider \(IdP\) initiated Single Sign-On \(SSO\) is used. The user accesses the application via a URL provided by the corporate identity provider.

To enable IdP-initiated SSO with corporate identity providers configured in the administration console for SAP Cloud Identity Services follow the following procedure:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under the *Conditional Authentication* section, choose the *Trust Corporate Identity Providers* list item.

6.  
<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Notes

</th>
</tr>
<tr>
<td valign="top">

**Enable the slider to allow SSO with all configured corporate identity providers.**

</td>
<td valign="top">

All corporate IdPs are allowed for sign-in.

By default this option is disabled. If enabled, all configured corporate IdPs are hidden, and you can't select a specific IdP from the list.

</td>
</tr>
<tr>
<td valign="top">

**Select a specific corporate IdP from the list.**

</td>
<td valign="top">

> ### Remember:  
> The slider on the top-right corner of the screen must be disabled. If enabled, all configured corporate IdPs are hidden



</td>
</tr>
</table>

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.




<a name="loiof7ec8d2cccde486d83353654d6c1f18a__result_fhp_jtn_jbb"/>

## Results

The application trusts the selected corporate identity providers that are configured in the administration console for SAP Cloud Identity Services.

**Related Information**  


[Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md "You choose between a local identity provider and a corporate identity provider to be the default identity provider for your application.")

[Configure Logon via Identity Authentication when a Corporate IdP is Chosen as Default](configure-logon-via-identity-authentication-when-a-corporate-idp-is-chosen-as-default-3a3bf9b.md "You can enable users to log on via Identity Authentication when a corporate identity provider (IdP) is chosen as default.")

[Configure Conditional Authentication for an Application](configure-conditional-authentication-for-an-application-0143dce.md "Tenant administrator can define rules for authenticating identity provider according to email domain, user type, user group, and IP range (specified in CIDR notation).")

[Configure Identity Federation for Applications](configure-identity-federation-for-applications-1e8e34e.md "Tenant administrator can enable identity federation for an application to override the identity federation settings on the configured corporate identity provider for the application.")

[Configure IdP-Initiated SSO with Corporate Identity Providers](configure-idp-initiated-sso-with-corporate-identity-providers-d483a52.md#loiod483a52be22946d5a05951b0fa16221f "This document shows you how to configure identity provider (IdP) initiated single sign-on (SSO) with corporate identity providers.")

