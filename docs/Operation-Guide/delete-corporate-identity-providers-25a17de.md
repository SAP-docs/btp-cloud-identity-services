<!-- loio25a17de6b1f0447ba86e0e8447474d40 -->

# Delete Corporate Identity Providers

As a tenant administrator, you can delete one or more corporate identity providers in a tenant of Identity Authentication.



## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have at least one corporate identity provider that you want to delete.

-   The identity provider you want to delete must not be used by an application. For more information about how to choose an identity provider for an application, see [Authenticating Identity Provider for an Application](authenticating-identity-provider-for-an-application-b3aae12.md).




## Context

A *Delete Identity Providers* operation removes the identity providers and all of their configurations from the tenant of Identity Authentication.

> ### Note:  
> If you want to delete an identity provider that is in use for conditional authentication, or is set as a default identity provider for an application, edit the rules, or change the default identity provider for the application. For more information see [Authenticating Identity Provider for an Application](authenticating-identity-provider-for-an-application-b3aae12.md).

To delete one or more identity providers, not used not used by applications in the tenant, choose one of the following options:

 <a name="task_bsb_lbv_dv"/>

<!-- task\_bsb\_lbv\_dv -->

## Delete Multiple Corporate Identity Providers



<a name="task_bsb_lbv_dv__steps_z5g_vbv_dv"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Choose the ![](images/Edit_User_Details_e96801b.png) icon in the left-hand panel.

    This operation activates the *Delete Identity Providers* mode.

4.  Select the identity provider or identity providers that you want to delete.

5.  Choose the *Delete* button.

6.  Confirm the operation in the pop-up dialog.

    The system deletes only the identity providers that are not used by applications.

    Once the identity provider or identity providers have been deleted, the system displays the message ***<number\> identity providers deleted***.


 <a name="task_pjj_lbv_dv"/>

<!-- task\_pjj\_lbv\_dv -->

## Delete Single Corporate Identity Provider



<a name="task_pjj_lbv_dv__steps_byx_tbv_dv"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the identity provider that you want to delete.

    > ### Tip:  
    > Type the name of the identity provider in the search field to filter the list items.

4.  Choose the *Delete* button in the right-hand panel to delete the selected corporate identity provider.

5.  Confirm the operation in the pop-up dialog.

    The system deletes only the identity provider that is not used by applications.

    Once the identity provider has been deleted, the system displays the message ***Identity provider deleted***.


**Related Information**  


[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

[Choose Default Identity Provider for an Application](choose-default-identity-provider-for-an-application-e9d8274.md "You choose between a local identity provider and a corporate identity provider to be the default identity provider for your application.")

