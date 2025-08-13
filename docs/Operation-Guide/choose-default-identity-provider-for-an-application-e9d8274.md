<!-- loioe9d82742d42b4f769c2d0f16d8e9ee41 -->

# Choose Default Identity Provider for an Application

You choose between a local identity provider and a corporate identity provider to be the default identity provider for your application.



<a name="loioe9d82742d42b4f769c2d0f16d8e9ee41__prereq_rkb_vxh_4cb"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have a configured corporate identity provider. For more information how to configure a corporate identity provider, see Related Information.

-   You haven't added any rules for authentication. For more information, see [Configure Conditional Authentication for an Application](configure-conditional-authentication-for-an-application-0143dce.md).



<a name="loioe9d82742d42b4f769c2d0f16d8e9ee41__context_skb_vxh_4cb"/>

## Context

In this scenario you choose which is the default identity provider. It can be either the local identity provider \(Identity Authentication\) or a corporate identity provider.

Initially Identity Authentication is set as the default local identity provider.

This choice gives you access to all application settings in the administration console for SAP Cloud Identity Services.

If the choice is a corporate identity provider, Identity Authentication acts as a proxy to delegate authentication to the external corporate identity provider. For more information, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md)

When you select a corporate identity provider, and you want to apply the custom application configurations for authentication and access policies, you should enable *Apply Application Configurations* for that corporate identity provider. For more information, see [Configure Identity Federation](configure-identity-federation-c029bbb.md).

To choose a default identity provider for an application, proceed as follows:



<a name="loioe9d82742d42b4f769c2d0f16d8e9ee41__steps_tkb_vxh_4cb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under the *Conditional Authentication* section, choose the *Conditional Authentication* list item.

6.  Select from the drop down the identity provider that the application will use as the default identity provider.

7.  Save your changes.

    Once the application has been updated, the system displays the message ***Conditional Authentication updated***.

    The application will use only the chosen identity provider for authentication.

    If you select the local identity provider, you will able to access the custom configurations for the applications.

    If you select a corporate identity provider, you will access only some of the custom configurations for the applications. The configurations under the *Authentication and Access* and *Branding and Layout* tabs will be partially visible. The user will be prompted to provide credentials in a single logon page.

8.  **Optional:** \(When a corporate identity provider is chosen as default identity provider\) Enable the *Allow Identity Authentication Users Log On* option. For more information see, [Use the Allow Identity Authentication Users Log On Option](use-the-allow-identity-authentication-users-log-on-option-2ec9a7f.md).


**Related Information**  


[Configure Logon via Identity Authentication when a Corporate IdP is Chosen as Default](configure-logon-via-identity-authentication-when-a-corporate-idp-is-chosen-as-default-3a3bf9b.md "You can enable users to log on via Identity Authentication when a corporate identity provider (IdP) is chosen as default.")

[Configure Conditional Authentication for an Application](configure-conditional-authentication-for-an-application-0143dce.md "Tenant administrator can define rules for authenticating identity provider according to email domain, user type, user group, and IP range (specified in CIDR notation).")

[Configure Identity Federation for Applications](configure-identity-federation-for-applications-1e8e34e.md "Tenant administrator can enable identity federation for an application to override the identity federation settings on the configured corporate identity provider for the application.")

[Enable SSO with All Corporate Identity Providers](enable-sso-with-all-corporate-identity-providers-f7ec8d2.md "Tenant administrators can enable IdP-initiated Single Sign-On (SSO) from all configured corporate identity providers (IdPs).")

[Configure Logon via Identity Authentication when a Corporate IdP is Chosen as Default](configure-logon-via-identity-authentication-when-a-corporate-idp-is-chosen-as-default-3a3bf9b.md "You can enable users to log on via Identity Authentication when a corporate identity provider (IdP) is chosen as default.")

