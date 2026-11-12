<!-- loioe25de8a5eae44b2aa9dbe778b8c3f52f -->

# Configure Certificate Authentication Method

Choose how SAP Cloud Identity Services handles certificate authentication for an application — locally, by forwarding to the corporate identity provider \(IdP\), or based on conditional authentication rules.



## Prerequisites

-   You are assigned the *Manage Applications* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have configured certificate authentication for the application. For more information, see [Enable Users to Generate and Authenticate with Certificates](enable-users-to-generate-and-authenticate-with-certificates-1268ff5.md)
-   For *Corporate Identity Provider Certificate Authentication* and *Conditional Certificate Authentication*: a corporate identity provider is configured for the application. For more information, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md)
-   For *Conditional Certificate Authentication*: conditional authentication rules are defined for the application. For more information, see [Configure Conditional Authentication for an Application](configure-conditional-authentication-for-an-application-0143dce.md)



## Context

By default, when a user authenticates with a certificate, SAP Cloud Identity Services validates the certificate locally and completes the authentication without involving any corporate identity provider. This works well for standalone certificate scenarios.

SAP Cloud Identity Services also lets you configure the certificate authentication method at the application level. With the two non-default methods, instead of validating the certificate locally, the system extracts the user's email address from the certificate and sends it as a `login hint` to the corporate identity provider. Authentication is then handled by the corporate IdP, which can apply its own policies before granting access.

> ### Note:  
> For the `login hint` to be resolved correctly, the certificate must contain the user's ID.
> 
> You are assigned the *Manage Applications* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).
> 
> uses the user ID to look up the user and retrieve their email address.

The following methods in the administration console are available:


<table>
<tr>
<th valign="top">

Method

</th>
<th valign="top">

Behavior

</th>
<th valign="top">

Typical Use Case

</th>
</tr>
<tr>
<td valign="top">

*Local Certificate Authentication \(Default\)*

</td>
<td valign="top">

The certificate is validated locally. The corporate IdP isn't involved.

</td>
<td valign="top">

Applications that require local certificate validation only.

</td>
</tr>
<tr>
<td valign="top">

*Corporate Identity Provider Certificate Authentication*

</td>
<td valign="top">

The system extracts the user's email address from the certificate and sends it as a `login hint` to the corporate IdP. Authentication is handled entirely by the corporate IdP. The certificate isn't used for local authentication.

</td>
<td valign="top">

Applications that rely on a corporate IdP for all authentication \(for example, to enforce device compliance or conditional access policies\).

</td>
</tr>
<tr>
<td valign="top">

*Conditional Certificate Authentication*

</td>
<td valign="top">

Conditional authentication rules are evaluated first. If a rule matches, the user's email address is extracted from the certificate and sent as a `login hint` to the corporate identity provider. If no rule matches, the certificate is used for local authentication.

</td>
<td valign="top">

Mixed scenarios where some users authenticate via the corporate identity provider and others authenticate locally using the certificate.

</td>
</tr>
</table>

> ### Caution:  
> A corporate IdP must be configured for the application before selecting *Corporate Identity Provider Certificate Authentication* or *Conditional Certificate Authentication*. Authentication requests fail if no corporate identity provider is configured.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Authentication and Access* tab.

5.  Under *AUTHENTICATION*, choose *Certificate Authentication*.

6.  Set the method for certificate authentication:

    -   *Local Certificate Authentication \(Default\)*

    -   *Corporate Identity Provider Certificate Authentication*

    -   *Conditional Certificate Authentication*

    If the application is updated, the system displays the message ***Application <name of application\> updated***.


