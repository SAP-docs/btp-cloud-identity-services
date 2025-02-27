<!-- loioa9ff3e3d5c9e4062860499e05259e31a -->

# Manage Application-Specific Groups by Identity Provisioning

By running provisioning jobs, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant and provision them afterward to target systems of your choice.



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_osm_xjx_12c"/>

## Prerequisites

You have an existing application in your SAP Cloud Identity Services tenant. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_igx_b2c_b2c"/>

## Context

The application-specific groups are a special kind of groups which can be created in the Identity Directory of SAP Cloud Identity Services by running provisioning jobs, or via the administration console for SAP Cloud Identity Services. For more information, see [Create a Group](create-a-group-b1b638d.md).

Operating with application-specific groups by the Identity Provisioning service requires having a source system with set property `ips.application.id`. By running provisioning jobs from such source system you can create, update, and delete application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant, depending on the values of their attributes.

Each application-specific group contains information about the application to which it is associated through the `application ID`. That is how you can distinguish which group comes from which application \(or provisioning system in the context of Identity Provisioning\) in the Identity Directory.

Another specific attribute for these groups is `supportedOperations`. The purpose of this attribute is to specify what are the supported operations by the Identity Provisioning for each application-specific group. For more information, see [Groups](../groups-d93be69.md).

> ### Note:  
> Currently, application-specific groups are supported for SAP Advanced Financial Closing, SAP Ariba Applications, SAP Analytics Cloud, SAP Application Server ABAP, SAP Ariba Central Invoice Management, SAP Sales Cloud and SAP Service Cloud, Microsoft Entra ID, and Local Identity Directory provisioning systems.

Below is described the result from each operation with an application-specific group executed by the Identity Provisioning, depending on the value of its attribute `supportedOperations`.



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_tlt_yjx_12c"/>

## Create Application-Specific Groups

By running provisioning jobs from your source system, associated to an application, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant.

When you configure Local Identity Directory as source system and you try to create a group that already exists in the target system with matching attributes and `supportedOperations` attribute value `userOnlyMembership` or `membership`, its group members are updated. If you try to provision a group with value `readOnly` for the attribute `supportedOperations`, it is displayed as *Skipped* in the job log statistics for the source system. In case the group has value `readWrite` for the attribute `supportedOperations`, it is created in the target system.



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_nny_x3c_b2c"/>

## Update Application-Specific Groups

If you update a user group assignment or a group itself in the application to which is associated your source system and you run a read or resync job, the Identity Provisioning tries to search and resolve this group in the Identity Directory of your SAP Cloud Identity Services tenant.

In case such application-specific group is found, depending on the value of the attribute `supportedOperations` this will result in:

-   `readOnly` - The group is displayed as *Skipped* in the job log statistics for the source system.
-   `readWrite` - The attributes of the group and its members are updated.
-   `userOnlyMembership` - The group members that are users are updated.
-   `membership` - The group members, both users and groups, are updated.

If such group is not found, the job fails with an exception.



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_pv1_y3c_b2c"/>

## Delete Application-Specific Groups

The deletion of application-specific groups from the local directory after they have been deleted from your source system requires setting the property `ips.delete.existedbefore.entities` = *true* in the target system. The setting of the property must be done **before** the job to delete those groups from the target system is executed. For more information, see [List of Properties](../list-of-properties-d6f3577.md).

In case you have set the `ips.delete.existedbefore.entities` property before running the provisioning job, depending on the value of the attribute `supportedOperations`, expect the following results:

-   `readOnly` - The group is displayed as *Skipped* in the job log statistics.
-   `readWrite` - The group is deleted.
-   `userOnlyMembership` - The group members that are users are deleted. The group is displayed as *Deleted* in the job log statistics.
-   `membership` - The group members, both users and groups, are deleted. The group is displayed as *Deleted* in the job log statistics.

If the property `ips.delete.existedbefore.entities` is missing or set to *false*, the Identity Provisioning will not attempt to delete the group and no record will be displayed in the job log statistics.



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_ugw_q2h_c2c"/>

## Central Store-Based Provisioning

Central store-based provisioning enables the automatic provisioning of application-specific groups from the Identity Directory to the target systems whenever changes occur. These changes include user assignments or modifications of group attributes.

The groups can be created initially in the Identity Directory by running a provisioning job from a specified source system or by using the SAP Cloud Identity Services administration console. To ensure their immediate provisioning to the target systems, the following application configurations are required:

-   An application must be created for the relevant target system under *Applications & Resources* \> *Applications*.

-   The application ID must be set as the value for the `ips.application.id` property in the target system.

-   The *Central Store-Based Provisioning* option must be enabled under *Applications & Resources* \> *Applications* \> *Provisioning*.


When provisioning application-specific groups from the Identity Directory to the target systems, groups that do not exist in the target can be created only after they are modified in the source system. New groups in the Identity Directory will not be provisioned unless they are changed.

> ### Note:  
> Application-specific groups with supported operations `readOnly`, `userOnlyMembership` and `membership` will not be created even if updates are made to the groups. If you try to provision such groups, you will get an ***Entity Failed*** status. For more information, see [Monitor Central Store Logs](../Monitoring-and-Reporting/monitor-central-store-logs-9162898.md).

This is the required configuration for enabling the central store-based provisioning. The following example uses Local Identity Directory as source system and SAP Advanced Financial Closing as target system.

1.  Sign in to SAP Cloud Identity Services administration console and navigate to *Identity Provisioning*.

2.  Add [Local Identity Directory](../local-identity-directory-59557ae.md) as a source system.

3.  **Optional**: Configure properties that are relevant for the Local Identity Directory source system, for example `idds.user.filter` and `idds.group.filter`. For more information, see [List of Properties](../list-of-properties-d6f3577.md).

4.  **Optional**: Review and adapt the default read transformations as necessary.

5.  Add a target system of your choice, for example *SAP Advanced Financial Closing*.

6.  Select the *Local Identity Directory* as relevant source system.
7.  Set the property `ips.application.id` for the target system. For more information, see [List of Properties](../list-of-properties-d6f3577.md).
8.  Start a read job from the *Local Identity Directory* source system.

9.  Navigate to your application in the administration console for SAP Cloud Identity Services under *Applications & Resources* \> *Applications* and enable the *Central Store-Based Provisioning*. For more information, see [Enable or Disable Central Store-Based Provisioning](enable-or-disable-central-store-based-provisioning-657bbaa.md).

After the procedure is executed, each change of an attribute value or a member of an application-specific group in the *Local Identity Directory* triggers instant provisioning of the modified entity to the configured target system.

**Related Information**  


[Import Groups via CSV File](import-groups-via-csv-file-daf96bd.md "As a tenant administrator, you can create new groups or update existing ones with the assigned users, via a CSV file upload.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[List and Edit Groups](list-and-edit-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.")

[Enable or Disable Central Store-Based Provisioning](enable-or-disable-central-store-based-provisioning-657bbaa.md "You can enable or disable the Central Store-Based Provisioning option in the administration console for SAP Cloud Identity Services.")

[List and Search Users in Groups](list-and-search-users-in-groups-4ac340a.md "As a tenant administrator, you can list and view information about the users in a group in a tenant in the administration console for SAP Cloud Identity Services.")

[Add Users to a Group](add-users-to-a-group-d2e1a01.md "As a tenant administrator, you can add one or more users created for a specific tenant to a group via the administration console for SAP Cloud Identity Services.")

[Remove Users from a Group](remove-users-from-a-group-301fdb7.md "As a tenant administrator, you can remove one, more than one, or all users added to a group via the administration console for SAP Cloud Identity Services.")

[Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md "As a tenant administrator, you can assign one or more groups created for a specific tenant to a user via the administration console for SAP Cloud Identity Services.")

[Unassign Groups from a User](unassign-groups-from-a-user-4353735.md "As a tenant administrator, you can unassign one or more groups that are assigned to a user via the administration console for SAP Cloud Identity Services.")

[Delete Groups](delete-groups-9853912.md "As a tenant administrator, you can delete one or more groups in administration console for SAP Cloud Identity Services.")

