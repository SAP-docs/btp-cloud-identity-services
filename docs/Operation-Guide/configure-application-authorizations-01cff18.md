<!-- loio01cff18e443142b195545a97115fc3fe -->

# Configure Application Authorizations

Configure access to the applications in the administration console of SAP Cloud Identity Services.



<a name="loio01cff18e443142b195545a97115fc3fe__prereq_yys_bdw_fzb"/>

## Prerequisites

You have enabled the authorizations based op policies option in the admin console for SAP Cloud Identity Services. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).



## Context

> ### Restriction:  
> This feature is relevant only for the Administration Console application.

Once it's enabled, it may take up to 60 seconds before the administrator can see the *Authorization Policies* tab when accessing the administration console application. Under the "applications" package the following base policies are visible: `CREATE_APPLICATIONS` , `DELETE_APPLICATIONS`, `MANAGE_APPLICATIONS`, `READ_APPLICATIONS`, and `UPDATE_APPLICATIONS`. You can add users to these policies so that they can have the rights these policies give.

> ### Note:  
> The Manage Applications authorization overrides all "applications" package policies, while the Manage Users authorization overrides the `READ_APPLICATIONS` policy only. If you want to configure access to the applications based on policies, you must remove the Manage Applications and Manage Users authorizations. For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

> ### Example:  
> Michael Adams is an administrator at retail company A. He has all the authorizations in the administration console for SAP Cloud Identity Services. Dona Moore the financial manager at company A. She is not an administrator, but she needs to have access to the list of all applications in the tenant. Michael Adams adds her to the `READ_APPLICATIONS` policy. As a result, now, when Dona accesses the administration console she sees only the *Applications* tile, and all the operations in it are read-only.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Under *System Applications*, choose the list item for the administration console.

4.  Under the tab *Authorization Policies*, filter the policies by the "applications" package.

    > ### Note:  
    > This limits the policies to the following: `CREATE_APPLICATIONS` , `DELETE_APPLICATIONS`, `MANAGE_APPLICATIONS`, `READ_APPLICATIONS`, and `UPDATE_APPLICATIONS`.

5.  Select a policy from the list

6.  Choose *Add* button.

7.  Select the user or users and choose *Add*.


**Related Information**  


[Configure User Authorizations](configure-user-authorizations-424b64c.md "Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.")

