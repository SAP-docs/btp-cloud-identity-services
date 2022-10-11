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

This choice gives you access to all application settings in the administration console for Identity Authentication.

If the choice is a corporate identity provider, Identity Authentication acts as a proxy to delegate authentication to the external corporate identity provider. For more information, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md)

When you select a corporate identity provider, and you want to apply the custom application configurations for authentication and access policies, you should enable *Apply Application Configurations* for that corporate identity provider. For more information, see [Configure Identity Federation](configure-identity-federation-c029bbb.md).

To choose a default identity provider for an application, proceed as follows:



<a name="loioe9d82742d42b4f769c2d0f16d8e9ee41__steps_tkb_vxh_4cb"/>

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

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under the *Conditional Authentication* section, choose the *Conditional Authentication* list item.

6.  Select from the drop down the identity provider that the application will use as the default identity provider.

7.  Save your changes.

    Once the application has been updated, the system displays the message ***Conditional Authentication updated***.

    The application will use only the chosen identity provider for authentication.

    If you select the local identity provider, you will able to access the custom configurations for the applications.

    If you select a corporate identity provider, you will not be able to access the custom configurations for the applications. The *Authentication and Access* and *Branding and Layout* tabs will not be visible. The user will be prompted to provide credentials in a single logon page.

8.  \(When a corporate identity provider is chosen as default identity provider\) Enable the *Allow Identity Authentication Users Log On* option. For more information see, [Use the Allow Identity Authentication Users Log On Option](use-the-allow-identity-authentication-users-log-on-option-2ec9a7f.md).


**Related Information**  


[Configure Logon via Identity Authentication when a Corporate IdP is Chosen as Default](configure-logon-via-identity-authentication-when-a-corporate-idp-is-chosen-as-default-3a3bf9b.md "You can allow users to log on via Identity Authentication when a corporate identity provider (IdP) is chosen as default.")

[Configure Conditional Authentication for an Application](configure-conditional-authentication-for-an-application-0143dce.md "Tenant administrator can define rules for authenticating identity provider according to e-mail domain, user type, user group, and IP range (specified in CIDR notation).")

[Enable IdP-Initiated SSO from All Corporate Identity Providers](enable-idp-initiated-sso-from-all-corporate-identity-providers-f7ec8d2.md "(For SAML 2.0 applications) Tenant administrators can enable IdP-initiated single sign-on (SSO) from all configured corporate identity providers (IdPs).")

[Configure Logon via Identity Authentication when a Corporate IdP is Chosen as Default](configure-logon-via-identity-authentication-when-a-corporate-idp-is-chosen-as-default-3a3bf9b.md "You can allow users to log on via Identity Authentication when a corporate identity provider (IdP) is chosen as default.")

