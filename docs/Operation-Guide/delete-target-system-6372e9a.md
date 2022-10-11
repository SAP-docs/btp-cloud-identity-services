<!-- loio6372e9a722474faca682389d8055b469 -->

# Delete Target System

As a tenant administrator, you can delete one or more target systems in a tenant of Identity Authentication.



## Prerequisites

You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

**Related Information**  


[Configure SAP Jam Target Systems for Real-Time Provisioning](configure-sap-jam-target-systems-for-real-time-provisioning-a923427.md "Tenant administrators can configure SAP Jam target systems for real-time provisioning via the administration console for Identity Authentication.")

[Configure Identity Provisioning Target Systems for Real-Time User Provisioning](configure-identity-provisioning-target-systems-for-real-time-user-provisioning-3349645.md "You can configure Identity Provisioning target systems for real-time user provisioning via the administration console for Identity Authentication.")

[Provision Users to Target Systems](provision-users-to-target-systems-af6f78b.md "Tenant administrators can provision users of Identity Authentication to SAP Jam and Identity Provisioning target systems target system.")

 <a name="task_zcl_xlq_3v"/>

<!-- task\_zcl\_xlq\_3v -->

## Delete Multiple Target Systems



<a name="task_zcl_xlq_3v__steps_e2f_5mq_3v"/>

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

2.  Under *Users & Authorizations*, choose the *Real-Time Provisioning* tile.

    This operation opens a list of the target systems.

3.  Choose the ![](images/Edit_User_Details_e96801b.png) icon in the left-hand panel.

    This operation activates the *Delete Target Systems* mode.

4.  Select the target system or systems that you want to delete.

5.  Choose the *Delete* button.

6.  Confirm the operation in the pop-up dialog.

    Once the target system or systems have been deleted, the system displays the message ***<number\> target systems deleted***.


 <a name="task_atv_xlq_3v"/>

<!-- task\_atv\_xlq\_3v -->

## Delete Single Target System



<a name="task_atv_xlq_3v__steps_mc4_f4q_3v"/>

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

2.  Under *Users & Authorizations*, choose the *Real-Time Provisioning* tile.

    This operation opens a list of the target systems.

3.  Select the target system that you want to delete.

4.  Choose the *Delete* button in the right-hand panel to delete the selected target system.

5.  Confirm the operation in the pop-up dialog.

    Once the application has been deleted, the system displays the message ***1 target system deleted***.


**Related Information**  


[Real-Time Provisioning](real-time-provisioning-617dd4b.md "As a tenant administrator, you can configure target systems for real-time provisioning and provision users to these target systems.")

