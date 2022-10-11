<!-- loioeac8e5e5db394e9ba409e68c66eedb77 -->

# Assign Authorization Policies

As an administrator, you can assign authorizations to Identity Authentication applications.



<a name="loioeac8e5e5db394e9ba409e68c66eedb77__prereq_ncp_j52_m5b"/>

## Prerequisites

-   Your application supports authorization policies. Refer to the documentation of your application.

-   Your user has administrative permissions in Identity Authentication with the *Manage Groups* authorization. For more information, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have a subscription to SAP Cloud Identity Services. For more information, see [SAP Cloud Identity Services](https://help.sap.com/docs/SAP_CLOUD_IDENTITY).


> ### Note:  
> If your application doesn't have an *Authorization Policies* tab, it doesn't support authorization management.



<a name="loioeac8e5e5db394e9ba409e68c66eedb77__context_qkt_gml_45b"/>

## Context

> ### Note:  
> To see details of the authorization policy, choose `Go to Policy Management`.



<a name="loioeac8e5e5db394e9ba409e68c66eedb77__steps_l1w_zx2_m5b"/>

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

2.  Under *Applications & Resources*, choose the *Applications* tile.

3.  Choose your application that supports authorization management. For information, see the documentation of the application.

    The details page of your application has an *Authorization Policies* tab.

4.  Choose the *Authorization Policies* tab.

5.  Choose an authorization policy that you want to assign. The administration console opens the *Assignments* pane.

6.  Choose *Add*.

7.  Select the users that you want to add to the authorization policy.

    You have added the selected users to an authorization policy. These users are authorized to access and use the resources with the restrictions defined in the authorization policy.


**Related Information**  


[Configuring Authorization Policies](configuring-authorization-policies-982ac5f.md "Authorization management enables Identity Authentication administrators to use authorization policies in multiple environments and assign them to users.")

