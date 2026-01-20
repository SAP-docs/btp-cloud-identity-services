<!-- loio1e8e34eb391845588c5a208c6744311c -->

# Configure Identity Federation for Applications

Tenant administrator can enable identity federation for an application to override the identity federation settings on the configured corporate identity provider for the application.



<a name="loio1e8e34eb391845588c5a208c6744311c__prereq_tvw_gtk_25b"/>

## Prerequisites

-   You are assigned the *Manage Applications* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have configured Identity Authentication to use a corporate identity provider as an external authenticating authority. For more information, see [Create Corporate IdP in Administration Console](create-corporate-idp-in-administration-console-ae99ba9.md).

-   You have selected a configured identity provider as the authenticating identity provider for your application. For more information, see [Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md).




## Context

The *Identity Federation* option allows you to choose whether the user attributes are taken from the corporate IdP assertion or from Identity Authentication user store. Additionally, you can also apply the custom application configurations for the authentication and access policies, as well as allow access based on user groups and email domains.

In scenarios where the application is using a corporate identity provider with *Identity Federation* settings for authentication, the administrator can configure identity federation for the application and override this configuration. This provides a more fine-grained identity federation in situations where multiple applications use the same corporate IdP as an external authenticating authority.



### User Store

> ### Remember:  
> By default, the *Identity Federation* for an application option is disabled. Enabling the configuration will override the *Identity Federation* settings of the authenticating identity provider.

When *Use Identity Authentication user store* option is enabled, the application checks if the users authenticated by the corporate identity provider exist in the Identity Authentication user store. The existence check is done with the name identifier sent by the corporate identity provider for the identifying attributes `uid`, `loginName`, `emails` and `phoneNumber`.

For users that exist in Identity Authentication, data from Identity Authentication user store is taken and the subject name identifier, assertion and default attributes according to the application configuration are sent. For users with no profile in Identity Authentication, the application receives the nameID attribute from the corporate IdP assertion, and the attributes according to the application configuration.



### User Access

By default, *Allow Identity Authentication users only* is disabled, and all users successfully authenticated to the corporate IdP are allowed.

When *Allow Identity Authentication users only* is enabled, only the users that exist in Identity Authentication can access the application.



### Restrict Logon to Members of Certain Groups from the Corporate Identity Provider

As a next step, you can assign a group or groups to the corporate IdP. Only users from the Identity Authentication user store that are members of the assigned group can access the application.

> ### Remember:  
> You can assign groups, only when *Allow Identity Authentication users only* option is enabled. If disabled, the assigned groups option is not taken into consideration. As a next step, you can assign a group or groups to the corporate IdP or allow certain email domains.



### Restrict Logon to Members of Certain Groups

You can assign a group or groups to the corporate identity provider. Only users from the Identity Authentication user store that are members of the assigned groups can access the application.

> ### Remember:  
> You can assign groups, only when *Allow Identity Authentication users only* option is enabled. If disabled, the assigned groups option is not taken into consideration.



### Restrict Logon to Users with Certain Email Domains

You can add email domains to restrict the access to those specific email domains. Only users from the Identity Authentication user store whose email domains are allowed can access the application.

> ### Remember:  
> You can allow email domains from the allow list, only when the *Allow Identity Authentication users only* option is enabled. If disabled, the allow list option is not taken into consideration.



### Application Configuration

Additionally, the *Apply Application Configurations* option can be enabled. By default, this option is disabled.

When enabled, the user is authenticated by the corporate IdP, then *Identity Authentication* checks for the configurations for authentication and access policies on application level, and applies them. They include *Risk-Based-Authentication*, *Terms of Use*, *Privacy Policy*, *Upgrade and Registration Forms*.

> ### Remember:  
> The concurrent user access configuration is always applied for the application regardless of the *Apply Application Configurations* state.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Select the application that you want to configure for *Identity Federation*.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose *Identity Federation* to configure the options.

5.  Choose *Edit* \> *Custom*.

6.  Select the desired check boxes:


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
    
    **Use Identity Authentication user store**
    
    </td>
    <td valign="top">
    
    When you select it, the *Allow Identity Authentication users only* becomes available for selection.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Allow Identity Authentication users only**
    
    </td>
    <td valign="top">
    
    When you select it, the *Apply Application Configurations* becomes available for selection.

    Additionally, the *User Groups* and *Allowed Email Domains*sections become visible. There you can see a list of the groups assigned to this corporate IdP and the allow list for email domains. If no groups are assigned or no email domain added, the lists are empty.

    -   To restrict logon to members of certain groups, choose the *Add* button. Select the groups that you want to assign to this corporate identity provider. The list does not include the groups that are already assigned to the corporate identity provider.

        > ### Note:  
        > To remove groups, choose *Edit*, select the groups you want to remove, choose the *Remove* button, and save your changes.
        > 
        > Users that belong only to the unassigned groups will not be able to access the application any more.

    -   To restrict logon to users from certain email domains, under *Email Domains*, choose the *Add* button. Type the email domains that you want to add to the allow list.

        > ### Note:  
        > To remove email domains, choose *Edit*, select the email domains you want to remove, choose the *Remove* button, and save your changes.
        > 
        > Users whose emails contain only the removed email domains will not be able to access the application any more.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Apply Application Configuration**
    
    </td>
    <td valign="top">
    
     
    
    </td>
    </tr>
    </table>
    
7.  Save your changes.


**Related Information**  


[Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md "You choose between a local identity provider and a corporate identity provider to be the default identity provider for your application.")

[Configure Logon via Identity Authentication when a Corporate IdP is Chosen as Default](configure-logon-via-identity-authentication-when-a-corporate-idp-is-chosen-as-default-3a3bf9b.md "You can enable users to log on via Identity Authentication when a corporate identity provider (IdP) is chosen as default.")

[Configure Conditional Authentication for an Application](configure-conditional-authentication-for-an-application-0143dce.md "Tenant administrator can define rules for authenticating identity provider according to email domain, user type, user group, and IP range (specified in CIDR notation).")

[Enable SSO with Corporate Identity Providers](enable-sso-with-corporate-identity-providers-f7ec8d2.md "Tenant administrators can enable IdP-initiated Single Sign-On (SSO) from one, more than one or all configured corporate identity providers (IdPs).")

