<!-- loioa9234273c390469ab711c92530c2f962 -->

# Configure SAP Jam for Real-Time Provisioning

Tenant administrators can configure SAP Jam target systems for real-time provisioning via the administration console for SAP Cloud Identity Services.



## Prerequisites

You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

> ### Note:  
> Currently, Identity Authentication supports real-time provisioning to SAP Jamand SAP Cloud Identity Services - Identity Provisioning instances.

> ### Remember:  
> Use the Identity Authentication real-time provisioning feature for up to 500 users.
> 
> If you want to provision more than 500 user, use Identity Provisioning. For more information, see [Configure Identity Authentication for Real-Time Provisioning](configure-identity-authentication-for-real-time-provisioning-3349645.md). The content in this section is not relevant for China \(Shanghai\) region.



## Context

To configure an SAP Jam target system, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Real-Time Provisioning* tile.

    This operation opens a list of the target systems.

3.  Press the *\+Add* button on the left-hand panel to add a new target system to the list.

4.  Make the corresponding entries in the *Target Configurations* and *Authentication Configurations* fields for the target system you want to add.

    All fields are obligatory.

    > ### Remember:  
    > Choose *SAP Jam* from the drop-down.

5.  Save your changes.

    If the operation is successful, the system displays the message `System <name of system> configuration updated.`

6.  \(Optional\) To check the SAP Jam Target System configuration press the *Test Connection* button.

    If the operation is successful, the system displays the message `Connection to the selected target system was established successfully.`

    > ### Note:  
    > To change the configuration, select the target system, press *Edit*, fill in the fields with the new entries, and save your changes.




<a name="loioa9234273c390469ab711c92530c2f962__postreq_kfq_ywy_zbb"/>

## Next Steps

[Provision Users to Target Systems](provision-users-to-target-systems-af6f78b.md)

**Related Information**  


[Enable Real-Time Provisioning in Source Applications](enable-real-time-provisioning-in-source-applications-0767587.md "Enable the real-time provisioning configuration in the source applications that trigger immediate sync when changes occur.")

[Configure Identity Authentication for Real-Time Provisioning](configure-identity-authentication-for-real-time-provisioning-3349645.md "Enable real-time provisioning in Identity Authentication to trigger immediate synchronization of user changes to target systems configured in Identity Provisioning.")

[Provision Users to Target Systems](provision-users-to-target-systems-af6f78b.md "Tenant administrators can provision users of Identity Authentication to SAP Jam and Identity Provisioning target systemstarget system.")

[Delete Target System](delete-target-system-6372e9a.md "As a tenant administrator, you can delete one or more target systems in a tenant of Identity Authentication.")

[Configuring Real-Time Provisioning](configuring-real-time-provisioning-617dd4b.md "As a tenant administrator, you can configure real-time provisioning to immediately provision entities from source to target systems.")

