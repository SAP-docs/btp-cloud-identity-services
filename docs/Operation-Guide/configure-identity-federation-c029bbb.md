<!-- loioc029bbbaefbf4350af15115396ba14e2 -->

# Configure Identity Federation

Tenant administrators can configure whether the attributes are taken from the assertion of the corporate identity provider or from the user store of Identity Authentication, and can restrict access based on the user profile.



## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have configured Identity Authentication to use a corporate identity provider as an external authenticating authority. For more information, see [Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md) or [Configure Identity Federation](configure-identity-federation-c029bbb.md).

-   You have selected the configured identity provider as the authenticating identity provider for your application. For more information, see [Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md).

-   You have imported the users, authenticated by the corporate identity provider, in Identity Authentication. For more information about how to import users, see [Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md).




## Context

The *Identity Federation* option allows you to choose whether the user attributes are taken from the corporate IdP assertion or from Identity Authentication user store. You can also restrict access based on the user profile, and additionally apply the custom application configurations for the authentication and access policies.



### User Store

By default, *Use Identity Authentication user store* is disabled.

In scenarios when the application is using for authentication a corporate identity provider, and the *Use Identity Authentication user store* option is disabled, the user attributes, the name ID attribute, and the default attributes configurations in the administration console for Identity Authentication are not relevant. In such scenarios, Identity Authentication sends to the application the same attributes it has received from the corporate identity provider. For more information about the corporate identity provider scenario, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md).

When *Use Identity Authentication user store* option is enabled, the application checks if the users authenticated by the corporate identity provider exist in the Identity Authentication user store. For users that exist in Identity Authentication, data from Identity Authentication user store is taken and the subject name identifier, assertion and default attributes according to the application configuration are sent. For users with no profile in Identity Authentication, the application receives the nameID attribute from the corporate IdP assertion, and the attributes according to the application configuration.



### User Access

When *Allow Identity Authentication users only* is enabled, only the users that exist in Identity Authentication can access the application.

By default, *Allow Identity Authentication users only* is disabled, and all users successfully authenticated to the corporate IdP are allowed.



### Restrict Logon to Members of Certain Groups from the Corporate Identity Provider

As a next step, you can assign a group or groups to the corporate identity provider. Only users from the Identity Authentication that are members of the assigned group can access the application.

> ### Remember:  
> You can assign user groups, only when *Allow Identity Authentication users only* option is enabled. If disabled, the assigned user groups option is not taken into consideration.



### Application Configuration

By default, *Apply Application Configurations* is disabled.

When enabled, the custom application configurations for authentication and access policies are applied.

When this option is enabled, the user is authenticated by the corporate IdP, then Identity Authentication checks for the configurations for authentication and access policies on application level, and applies them. They include Risk-Based-Authentication, Terms of Use, Privacy Policy, Upgrade and Registration Forms.

 <a name="task_td1_3v4_y5"/>

<!-- task\_td1\_3v4\_y5 -->

## Use Identity Authentication user store



<a name="task_td1_3v4_y5__steps_enable_idfederation"/>

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

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure for *Identity Federation*.

    -   If you do not have an identity provider in your list, click the *Add* button to create one, and proceed with the configuration.
    -   If you have an identity provider in your list, choose the one that you want to configure.

4.  Choose *Identity Federation* to configure the options.

5.  Use the slider next to *Use Identity Authentication user store* to enable it.

    If the operation is successful, the system displays the message ***Identity provider <name of identity provider\> updated***.


 <a name="task_zlr_mnw_mhb"/>

<!-- task\_zlr\_mnw\_mhb -->

## Allow Identity Authentication users only



<a name="task_zlr_mnw_mhb__prereq_o13_yw2_nhb"/>

## Prerequisites

You have enabled *Use Identity Authentication user store* option. For more information about how to enable the option, see *Use Identity Authentication user store* in this topic.



<a name="task_zlr_mnw_mhb__steps_pvp_tw2_nhb"/>

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

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure for *Identity Federation*.

    -   If you do not have an identity provider in your list, click the *Add* button to create one, and proceed with the configuration.
    -   If you have an identity provider in your list, choose the one that you want to configure.

4.  Choose *Identity Federation* to configure the options.

5.  Use the slider next to *Allow Identity Authentication users only* to enable it.

    If the operation is successful, the system displays the message ***Identity provider <name of identity provider\> updated***.


 <a name="task_cp4_kx2_nhb"/>

<!-- task\_cp4\_kx2\_nhb -->

## Apply Application Configurations



<a name="task_cp4_kx2_nhb__prereq_uhz_nx2_nhb"/>

## Prerequisites

You have enabled *Allow Identity Authentication users only* option. For more information about how to enable the option, see *Allow Identity Authentication users only* in this topic.



<a name="task_cp4_kx2_nhb__steps_lxs_4x2_nhb"/>

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

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure for *Identity Federation*.

    -   If you do not have an identity provider in your list, click the *Add* button to create one, and proceed with the configuration.
    -   If you have an identity provider in your list, choose the one that you want to configure.

4.  Choose *Identity Federation* to configure the options.

5.  Use the slider next to *Apply Application Configurations* to enable it.

    If the operation is successful, the system displays the message ***Identity provider <name of identity provider\> updated***.


 <a name="task_nvs_4v4_y5"/>

<!-- task\_nvs\_4v4\_y5 -->

## Restrict Logon to Members of Certain Groups from the Corporate Identity Provider



<a name="task_nvs_4v4_y5__prereq_jzm_2x2_nhb"/>

## Prerequisites

You have enabled *Allow Identity Authentication users only* option. For more information about how to enable the option, see *Allow Identity Authentication users only* in this topic.



<a name="task_nvs_4v4_y5__steps_t31_4v4_y5"/>

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

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md)..

4.  Choose *Identity Federation*.

    You will see a list of the user groups assigned to this corporate identity provider. If no groups are assigned, the list will be empty.

5.  Choose the *Assign Groups* button.

6.  Select the groups that you want to assign to this corporate identity provider.

    The list does not include the groups that are already assigned to the corporate identity provider.

    If you do not have any user groups in your list, you can create one. For more details about how to create user groups and assign the group to a user, see Related Information.

7.  Save your changes.

    If the operation is successful, the system displays the message ***Identity provider <name of identity provider\> updated***.

    > ### Note:  
    > To unassign user groups, select the groups you want to unassign, choose the *Unassign Groups* button, and confirm the operation in the dialog.
    > 
    > Users that belong only to the unassigned groups will not be able to access the application any more.


**Related Information**  


[Create a New User Group](create-a-new-user-group-b1b638d.md "As a tenant administrator you can create new user groups in the tenant via the administration console for Identity Authentication.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for Identity Authentication.")

