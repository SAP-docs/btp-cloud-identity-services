<!-- loio01cff18e443142b195545a97115fc3fe -->

# Configure Application Authorizations

Configure granular access and control over the applications in the administration console of SAP Cloud Identity Services.



<a name="loio01cff18e443142b195545a97115fc3fe__prereq_yys_bdw_fzb"/>

## Prerequisites

You have enabled the authorizations based on policies option in the admin console for SAP Cloud Identity Services. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).



## Context

> ### Restriction:  
> This feature is relevant only for the Administration Console application.

Once it's enabled, it may take up to 60 seconds before the administrator can see the *Authorization Policies* tab when accessing the administration console application. Under the "applications" package the following base policies are visible: `CREATE_APPLICATIONS` , `DELETE_APPLICATIONS`, `MANAGE_APPLICATIONS`, `READ_APPLICATIONS`, and `UPDATE_APPLICATIONS`. You can add users to these policies so that they can have the rights these policies give.

> ### Note:  
> The Manage Applications authorization overrides all "applications" package policies, while the Manage Users authorization overrides the `READ_APPLICATIONS` policy only. If you want to configure access to the applications based on policies, you must remove the Manage Applications and Manage Users authorizations. For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

You can restrict access on the basis of the base policies or you can use a custom policy, restricting the applications on the basis of the `application.organization` attribute.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Under *System Applications*, choose the list item for the administration console.

4.  Under the tab *Authorization Policies*, you can choose the following options:


    <table>
    <tr>
    <th valign="top">

     
    
    </th>
    <th valign="top">

     
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Use base policy**
    
    </td>
    <td valign="top">
    
    1.  Filter the policies by the "applications" package.

        > ### Note:  
        > This limits the policies to the following: *CREATE\_APPLICATIONS* , *DELETE\_APPLICATIONS*,*MANAGE\_APPLICATIONS*, *READ\_APPLICATIONS*, and *UPDATE\_APPLICATIONS*.

    2.  Select a policy from the list.
    3.  Choose the *Add* button.
    4.  Select the user or users and choose Add.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Use custom policy**
    
    </td>
    <td valign="top">
    
    1.  Select a custom authorization policy.

        > ### Note:  
        > If you don’t have an authorization policy in your list, you can create a restriction policy using the `applications.DELETE_APPLICATIONS`, `applications.READ_APPLICATIONS`, `applications.UPDATE_APPLICATIONS` parameters. For more information about how to create a custom authorization policy, see [Create an Authorization Policy](create-an-authorization-policy-897fc30.md).

    2.  Choose the *Edit* button.
    3.  To customize the rules of the authorization policy, choose *Rules*.
    4.  To assign user to this policy, choose the *Assignments* tab and add users from the list.

        > ### Restriction:  
        > If the user is a tenant administrator you must remove the *Manage Applications* and *Manage Users* roles from that user, otherwise they won't be able to see and have control \(read, update or delete\) over the applications for this policy.

    5.  Save your changes.

        > ### Note:  
        > Now the assigned users can see and have control over applications with *Organization ID* specified in the custom policy.



    
    </td>
    </tr>
    </table>
    



<a name="loio01cff18e443142b195545a97115fc3fe__postreq_aqc_bjd_w1c"/>

## Next Steps

View or edit the *Organization ID* of the application. By default, all applications are in the *global* organization. For more information, see [Edit Applications](edit-applications-69d8cad.md)

**Related Information**  


[Configure User Authorizations](configure-user-authorizations-424b64c.md "Configure a granular access control based on policies for the administrators of SAP Cloud Identity Services.")

[Configure Group Authorizations](configure-group-authorizations-7a09cad.md "Configure granular access and control over the groups in the administration console of SAP Cloud Identity Services.")

[Configure Provisioning Authorizations](configure-provisioning-authorizations-a8f8e31.md "Configure granular access control for the Identity Provisioning systems and logs in the SAP Cloud Identity Services administration console.")

