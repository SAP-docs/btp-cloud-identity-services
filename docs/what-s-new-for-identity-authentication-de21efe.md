<!-- loiode21efe39e1442618388784891497067 -->

# What's New for Identity Authentication 



This page lists the release notes of SAP Cloud Identity Services - Identity Authentication for 2023. To see the release notes for the previous year, visit [2022 What's New for Identity Authentication \(Archive\)](2022-what-s-new-for-identity-authentication-archive-3322427.md). 

To get notifications, subscribe for the Identity Authentication selection in the [What's New Viewer for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Identity%2520Authentication&locale=en-US&version=Cloud). For more information, see [Subscribing to What's New Notifications](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Identity%20Authentication&locale=en-US&version=Cloud).





****


<table>
<tr>
<th valign="top">

Technical Component



</th>
<th valign="top">

Environment



</th>
<th valign="top">

Title



</th>
<th valign="top">

Description



</th>
<th valign="top">

Action



</th>
<th valign="top">

Lifecycle



</th>
<th valign="top">

Type



</th>
<th valign="top">

Line of Business



</th>
<th valign="top">

Modular Business Process



</th>
<th valign="top">

Product



</th>
<th valign="top">

Latest Revision



</th>
<th valign="top">

Available as of



</th>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-16



</td>
<td valign="top">

2023-08-16



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Risk-Based Authentication



</td>
<td valign="top">

New authentication method *Trusted IdP SAML Assertion* is available when you create a new rule for risk-based auhentication. See [Create a New Rule](Operation-Guide/configure-risk-based-authentication-for-an-application-bc52fbf.md#loio18d02ab9cc7d4caf83d8654c8c51a175) .



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-16



</td>
<td valign="top">

2023-08-16



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Implicit Grant Type Not Enabled by Default



</td>
<td valign="top">

Today, when you create a new OpenID Connect \(OIDC\) application in Identity Authentication, the `Implicit` grant type is enabled by default.

With the planned change, new applications have the `Implicit` grant type **disabled** by default.

Action: Check if you require the `Implicit` grant type for new applications:

-   Yes: Ensure your processes for creating new applications include explicitly enabling the `Implicit` grant type.

    -   For the administration console, see [Configure OpenID Connect Application for Implicit Flow](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/c64180e84cae4303ba80b2d4b59788b7.html).

    -   For the Identity service, see [Reference Information for the Identity Service of SAP BTP](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/9379444abf3f4e2cbaade7c4001df381.html).


-   No: Nothing to do.




</td>
<td valign="top">

Required



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

Announcement



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-16



</td>
<td valign="top">

2023-11-22



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Refresh Token Flow of OIDC Protocol Restricted to Validity of Web Session



</td>
<td valign="top">

Today, you can set the validity of refresh tokens with the token policy configuration for OpenID Connect \(OIDC\). We already recommend that you add the `offline_access` scope to authorization code requests if you want the validity of refresh tokens to exceed the session timeout. Barring no other changes, the refresh token remains valid for its configured validity.

With the planned change, the service couples the validity of refresh tokens to the session timeout. Refresh tokens expire with the user session, unless you add the `offline_access scope`.

Action: Check if you define a refresh token validity for your applications longer than 12h:

-   Yes: Ensure that you decouple the refresh token from the user session with the `offline_access` scope.

    For more information, see [Token Policy Configuration for Applications](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/c4ba52e748554863917b046bf1b7b355.html).

-   No: Nothing to do.




</td>
<td valign="top">

Required



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

Announcement



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-16



</td>
<td valign="top">

2023-11-22



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-03



</td>
<td valign="top">

2023-08-02



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Simplified Configuration of Default Attributes and Assertion Attributes



</td>
<td valign="top">

In the configuration of applications, we have combined the *Default Attributes* and *Assertion Attributes* into a single screen named *Application Attributes*. This change gives administrators a complete overview of the user attributes configured for an application.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

Changed



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-09



</td>
<td valign="top">

2023-08-30



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Terms of Use Documents



</td>
<td valign="top">

Tenant administrator can delete an entire terms of use documents set. See [\(Optional\) Delete a Terms of Use Document](Operation-Guide/optional-delete-a-terms-of-use-document-6ad5df5.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-03



</td>
<td valign="top">

2023-08-02



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Privacy Policy Documents



</td>
<td valign="top">

Tenant administrator can delete an entire privacy policy documents set. See [\(Optional\) Delete a Privacy Policy Document](Operation-Guide/optional-delete-a-privacy-policy-document-4b66ac1.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-03



</td>
<td valign="top">

2023-08-02



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Support for Prompt Parameter



</td>
<td valign="top">

The `prompt` parameter is an optional parameter of an OAuth 2.0 Authorization Request in the OpenID Connect Core 1.0 specification. The service supports the *none* and *login* values for this parameter.

See [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/94ff0b4b0baa45a893c7cd24254b72b7.html).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-08-03



</td>
<td valign="top">

2023-08-02



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-28



</td>
<td valign="top">

2023-07-28



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-19



</td>
<td valign="top">

2023-07-19



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Removal of Applications of Type Reuse



</td>
<td valign="top">

Applications of type reuse instance aren't visible in the administration console anymore. Changes to these applications didn't have any effect.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

Deleted



</td>
<td valign="top">

Changed



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-19



</td>
<td valign="top">

2023-07-19



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect



</td>
<td valign="top">

Tenant administratorcan configure Identity Authentication to execute the authorization code flow enhanced with PKCE against the corporate identity provider. See [Configure Trust with OpenID Connect Corporate Identity Provider](Operation-Guide/configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-19



</td>
<td valign="top">

2023-07-19



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect



</td>
<td valign="top">

Identity Authentication аdded the `apt_id` to the list of the supported parameters. It is required for multitenant scenarios to identify corresponding Identity Authentication application. See [Call Identity Authentication End Session Endpoint](Operation-Guide/call-identity-authentication-end-session-endpoint-ec674f4.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-19



</td>
<td valign="top">

2023-07-19



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Management



</td>
<td valign="top">

Identity Authentication added the `SCIM ID` to the list of the supported attributes for the export users option. See [Export Existing Users of a Tenant of Identity Authentication](Operation-Guide/export-existing-users-of-a-tenant-of-identity-authentication-40c29d2.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-19



</td>
<td valign="top">

2023-07-19



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regular Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-12



</td>
<td valign="top">

2023-07-05



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Nofifications



</td>
<td valign="top">

As of the Jul 5, 2023 upgrade, the first administrator in every new tenant, created after that date, and all newly created administrators are automatically subscribed for system notifications. See [Send System Notifications via Emails](Operation-Guide/send-system-notifications-via-emails-aa04a8b.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-12



</td>
<td valign="top">

2023-07-05



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

REST API



</td>
<td valign="top">

User Management REST API now supports the `applicationId` parameter. The user is created for the application with the specified ID. See [User Registration](Development/user-registration-0aa433c.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-12



</td>
<td valign="top">

2023-07-05



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Groups



</td>
<td valign="top">

Tenant administrator can search for specific member in a group via SCIM ID. See [List and Search Users in User Groups](Operation-Guide/list-and-search-users-in-user-groups-4ac340a.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-12



</td>
<td valign="top">

2023-07-05



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Authentication



</td>
<td valign="top">

Support unauthenticated requests with public tokens. See [Call Identity Authentication Introspect Token Endpoint](Operation-Guide/call-identity-authentication-introspect-token-endpoint-a05f14c.md), [Call Identity Authentication Revoke Token Endpoint](Operation-Guide/call-identity-authentication-revoke-token-endpoint-3501e42.md), and [Call Identity Authentication List Sessions Endpoint](Operation-Guide/call-identity-authentication-list-sessions-endpoint-daf7e44.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-07-12



</td>
<td valign="top">

2023-07-05



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Off-Cycle Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-06-29



</td>
<td valign="top">

2023-06-28



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Corporate IdPs



</td>
<td valign="top">

Tenant administrator can copy the settings from a corporate IdP that is already existing in the tenant to a new corporate IdP. See [Create Corporate IdP in Administration Console](Operation-Guide/create-corporate-idp-in-administration-console-ae99ba9.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-06-29



</td>
<td valign="top">

2023-06-28



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-06-09



</td>
<td valign="top">

2023-06-08



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Corporate IdP



</td>
<td valign="top">

Tenant administrator can set the interval for the automatic refresh of the OpenID Connect metadata of the corporate identity provider. See [Configure Trust with OpenID Connect Corporate Identity Provider](Operation-Guide/configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-06-09



</td>
<td valign="top">

2023-06-08



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect Configurations



</td>
<td valign="top">

Tenant administrator can set the maximum wait time for front-channel logout. See [Tenant OpenID Connect Configurations](Operation-Guide/tenant-openid-connect-configurations-3d6abcc.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-06-09



</td>
<td valign="top">

2023-06-08



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-05-25



</td>
<td valign="top">

2023-05-25



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Corporate IdPs



</td>
<td valign="top">

You can change the default attributes sent to the application to uppercase or lowercase letters depending on your needs. See [Configure the Default Attributes Sent to the Application](Operation-Guide/configure-the-default-attributes-sent-to-the-application-a2f1e46.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-05-25



</td>
<td valign="top">

2023-05-25



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-05-17



</td>
<td valign="top">

2023-05-17



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-05-11



</td>
<td valign="top">

2023-05-11



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect



</td>
<td valign="top">

Identity Authentication now supports new optional parameter `logout_uri` in the `/oauth2/authorize` endpoint. See [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow](Operation-Guide/configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md), [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow with PKCE](Operation-Guide/configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-a721157.md), and [Configure the Client to Call Identity Authentication Authorize Endpoint for Implicit Flow](Operation-Guide/configure-the-client-to-call-identity-authentication-authorize-endpoint-for-implicit-flow-1ca3dc0.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-05-11



</td>
<td valign="top">

2023-05-11



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Tenant Settings



</td>
<td valign="top">

You can now reuse your existing tenant for configurations and automated subscriptions. See [Reuse SAP Cloud Identity Services Tenants for Different Customer IDs](Operation-Guide/reuse-sap-cloud-identity-services-tenants-for-different-customer-ids-ebd0258.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-05-04



</td>
<td valign="top">

2023-05-04



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-04-27



</td>
<td valign="top">

2023-04-27



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-04-20



</td>
<td valign="top">

2023-04-20



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Rewording of Security Recommendations



</td>
<td valign="top">

We improved security recommendation [BTP-IAS-0017](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-IAS-0017) to list the specific authorizations that we feel are critical not just to the service, but to your landscape as well.

In addition, we reviewed and improved the readability of the other recommendations for the service to make clear when the recommendations apply.

See [SAP Security Recommendations for Identity Authentication](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

Changed



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-04-20



</td>
<td valign="top">

2023-04-20



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Deprecation of Security Recommendation BTP-IAS-0016



</td>
<td valign="top">

Security recommendation BTP-IAS-0016 was too broadly formulated to provide clear guidance to our customers. We removed the recommendation from the list.

For other recommendations for the service, see [SAP BTP Security Recommendations for Identity Authentication](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-service=Identity%20Authentication).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

Deprecated



</td>
<td valign="top">

Changed



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-04-20



</td>
<td valign="top">

2023-04-20



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

SMS Verification



</td>
<td valign="top">

Sinch Authentication 365 is deprecated.

Action: We recommend you to configure Sinch Verification in the administration console and start using it. See [Configure Sinch Service in Administration Console](Operation-Guide/configure-sinch-service-in-administration-console-f4a04ed.md).



</td>
<td valign="top">

Recommended



</td>
<td valign="top">

Deprecated



</td>
<td valign="top">

Announcement



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-04-13



</td>
<td valign="top">

2023-04-13



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Tenant Offering



</td>
<td valign="top">

You can now create an SAP Cloud Identity Services trial tenant from an SAP BTP trial account. A trial tenant is intended for testing purposes of SAP Cloud Identity Services – Identity Authentication and Identity Provisioning. See [Tenant Model and Licensing](tenant-model-and-licensing-93160eb.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-04-13



</td>
<td valign="top">

2023-04-13



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Authorizations Based on Policies



</td>
<td valign="top">

\(Beta\) You can configure and assign a granular access control based on policies for the administrators of SAP Cloud Identity Services. See [\(Beta\) Configure Authorizations Based on Policies](Operation-Guide/beta-configure-authorizations-based-on-policies-08fea39.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

Beta



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-04-04



</td>
<td valign="top">

2023-04-04



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-03-31



</td>
<td valign="top">

2023-03-31



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Management



</td>
<td valign="top">

You can configure which user ID attribute can be visible on the *User Management* section in the administration console. See [Search Users](Operation-Guide/search-users-06078a6.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-03-31



</td>
<td valign="top">

2023-03-31



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Global User ID



</td>
<td valign="top">

You can reuse previous versions of the *Global User ID* for one and the same user. See [Search Users](Operation-Guide/search-users-06078a6.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-03-31



</td>
<td valign="top">

2023-03-31



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect Configurations



</td>
<td valign="top">

You can extend the standard OpenID Connect metadata. See [Tenant OpenID Connect Configurations](Operation-Guide/tenant-openid-connect-configurations-3d6abcc.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-03-31



</td>
<td valign="top">

2023-03-31



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Corporate IdPs



</td>
<td valign="top">

You can check which applications have established trust with a specific corporate identity provider in the administration console. See [Configure Trust with OpenID Connect Corporate Identity Provider](Operation-Guide/configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md) and [Configure Trust with SAML 2.0 Corporate Identity Provider](Operation-Guide/configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-03-31



</td>
<td valign="top">

2023-03-31



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Configuration of Authorization Policies



</td>
<td valign="top">

Authorization management enables administrators to configure authorization policies throughout multiple environments and assign them to users. In the administration console, administrators can create custom authorization policies. They can edit an existing one by adding or deleting restrictions, changing user attribute values, or by combining rules of multiple authorization policies in a new one. See [Configuring Authorization Policies](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/982ac5f91d2346fda8dd8096e861fc36.html?version=Cloud).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-03-31



</td>
<td valign="top">

2023-03-31



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-03-16



</td>
<td valign="top">

2023-03-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Administration Console



</td>
<td valign="top">

The Horizon theme is now available for the administration console of SAP Cloud Identity Services, both the web and mobile version. See [How Far is the Horizon for SAP Cloud Identity Services?](https://blogs.sap.com/2023/03/15/how-far-is-the-horizon-for-sap-cloud-identity-services/).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

 



</td>
<td valign="top">

2023-03-16



</td>
<td valign="top">

2023-03-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Troubleshooting



</td>
<td valign="top">

You can filter and view troubleshooting logs directly in the administration console for SAP Cloud Identity Services. See [View Troubleshooting Logs](Monitoring-and-Reporting/view-troubleshooting-logs-6e7543f.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

 



</td>
<td valign="top">

2023-03-16



</td>
<td valign="top">

2023-03-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect



</td>
<td valign="top">

You can configure the access token format. See [Token Policy Configuration for Applications](Operation-Guide/token-policy-configuration-for-applications-c4ba52e.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

 



</td>
<td valign="top">

2023-03-16



</td>
<td valign="top">

2023-03-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-03-01



</td>
<td valign="top">

2023-03-01



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-15



</td>
<td valign="top">

2023-02-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Management



</td>
<td valign="top">

Application user import was enhanced with new parameters : `userType` and `urn:ietf:params:scim:schemas:extension:sap:2.0:User:mailVerified`. See [Import or Update Users for a Specific Application](Operation-Guide/import-or-update-users-for-a-specific-application-33838e0.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-15



</td>
<td valign="top">

2023-02-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Applications



</td>
<td valign="top">

You can return an application's configuration to its inherited state with the *Inherit from Parent* option via the administration console. See [Edit Applications](Operation-Guide/edit-applications-69d8cad.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-15



</td>
<td valign="top">

2023-02-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Troubleshooting



</td>
<td valign="top">

You can use the troubleshooting logs to analyze OpenID Connect issues with applications and corporate identity providers. See [Logging OpenID Connect Tokens](Monitoring-and-Reporting/logging-openid-connect-tokens-b6c42b5.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-15



</td>
<td valign="top">

2023-02-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect



</td>
<td valign="top">

Identity Authentication now supports the `groups` value of the `scope` parameter. See [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow](Operation-Guide/configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-94ff0b4.md) and [Configure the Client to Call Identity Authentication Authorize Endpoint for Authorization Code Flow with PKCE](Operation-Guide/configure-the-client-to-call-identity-authentication-authorize-endpoint-for-authorization-a721157.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-15



</td>
<td valign="top">

2023-02-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

OpenID Connect



</td>
<td valign="top">

Identity Authentication now supports new parameter - `scope` for the service endpoint that returns the tokens issued by the corporate identity provider received during the OpenID Connect \(OIDC\) authentication process. See [Exchanging Identity Authentication Tokens for Tokens from Corporate Identity Providers](Development/exchanging-identity-authentication-tokens-for-tokens-from-corporate-identity-providers-a66753a.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-15



</td>
<td valign="top">

2023-02-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Identity Service



</td>
<td valign="top">

You can use the `refresh-usage-after-renewal` parameter to define the validity of the old refresh token after requesting a new one through the refresh token grant type. See [Reference Information for the Identity Service of SAP BTP](Integrating-the-Service/reference-information-for-the-identity-service-of-sap-btp-9379444.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-15



</td>
<td valign="top">

2023-02-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Administration Console



</td>
<td valign="top">

You can now configure and work with Identity Provisioning in the administration console for SAP Cloud Identity Services.

The entire provisioning functionality, which includes adding, enabling, disabling, deleting, and resetting provisioning systems, running jobs, viewing and downloading logs, is integrated there and can be accessed in the navigation area under SAP Cloud Identity Services.

The latest step in tightening SAP Cloud Identity Services integration allows you to manage your configurations in one place without the need to switch between consoles. To benefit from it, your Identity Provisioning tenant must run on SAP Cloud Identity Services infrastructure.

See [Configure Identity Provisioning in SAP Cloud Identity Services Administration Console](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/03223babed91493c9305e40269e909d2.html?state=DRAFT&version=Cloud).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-15



</td>
<td valign="top">

2023-02-15



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-09



</td>
<td valign="top">

2023-02-07



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-03



</td>
<td valign="top">

2023-02-03



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-02-02



</td>
<td valign="top">

2023-02-01



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-01-24



</td>
<td valign="top">

2023-01-24



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Manage Applications



</td>
<td valign="top">

Tenant administrator can manage applications in Identity Authentication via API. It offers endpoints for CRUD operations \(GET, PUT, POST, PATCH, DELETE\) over the applications. See [SAP Cloud Identity Services Application Directory](https://api.sap.com/api/SCI_Application_Directory/overview).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

 



</td>
<td valign="top">

2023-01-23



</td>
<td valign="top">

2023-01-23



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-01-22



</td>
<td valign="top">

2023-01-20



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Management



</td>
<td valign="top">

Tenant administrator can search users by `SCIM ID` in the administration console. See [Search Users](Operation-Guide/search-users-06078a6.md) and [Add Users to a Group](Operation-Guide/add-users-to-a-group-d2e1a01.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-01-22



</td>
<td valign="top">

2023-01-20



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

System Upgrade



</td>
<td valign="top">

Identity Authentication has been upgraded.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-01-19



</td>
<td valign="top">

2023-01-18



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Regional Availability



</td>
<td valign="top">

Identity Authentication is now available with a single data center \(DC\) for the AWS infrastructure in India. See [Regional Availability](regional-availability-be600ca.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-01-19



</td>
<td valign="top">

2023-01-18



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Tenant Settings



</td>
<td valign="top">

The `Login Name` user identifier can be configured as required or nonrequired. See [Configure User Identifier Attributes](Operation-Guide/configure-user-identifier-attributes-8b9fa88.md).



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

New



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-01-19



</td>
<td valign="top">

2023-01-18



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

Administration Console



</td>
<td valign="top">

The administration console was renamed from `Identity Authentication` to `SAP Cloud Identity Services`.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

Changed



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-01-19



</td>
<td valign="top">

2023-01-18



</td>
</tr>
<tr>
<td valign="top">

Identity Authentication 



</td>
<td valign="top">

-   Neo
-   Kyma
-   Cloud Foundry



</td>
<td valign="top">

User Management



</td>
<td valign="top">

Identity Authentication renamed user identifier `User UUID` to `Global User ID` in the administration console. The technical name of the attribute remains unchanged `userUuid`.



</td>
<td valign="top">

Info only



</td>
<td valign="top">

General Availability



</td>
<td valign="top">

Changed



</td>
<td valign="top">

Technology



</td>
<td valign="top">

Not applicable



</td>
<td valign="top">

Identity Authentication



</td>
<td valign="top">

2023-01-19



</td>
<td valign="top">

2023-01-18



</td>
</tr>
</table>



<a name="loiode21efe39e1442618388784891497067__archived"/>

## What's New Archived

-   [2022](2022-what-s-new-for-identity-authentication-archive-3322427.md)

-   [2021](2021-what-s-new-for-identity-authentication-archive-2df26f0.md)


