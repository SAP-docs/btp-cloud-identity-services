<!-- loioa9ff3e3d5c9e4062860499e05259e31a -->

# Manage Application-Specific Groups by Identity Provisioning

By running provisioning jobs, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant or Identity Authentication \(SCIM API version 2\) target system and provision them afterward to target systems of your choice.



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_osm_xjx_12c"/>

## Prerequisites

You have an existing application in your SAP Cloud Identity Services tenant. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_igx_b2c_b2c"/>

## Context

The application-specific groups are a special kind of groups which can be created in the Identity Directory of SAP Cloud Identity Services or Identity Authentication \(SCIM API version 2\) target system by running provisioning jobs, or via the administration console for SAP Cloud Identity Services. For more information, see [Create a Group](create-a-group-b1b638d.md).

Operating with application-specific groups by the Identity Provisioning service requires having a source system with set property `ips.application.id`. By running provisioning jobs from such source system you can create, update, and delete application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant or Identity Authentication \(SCIM API version 2\) target system, depending on the values of their attributes.

Each application-specific group contains information about the application to which it is associated through the `application ID`. That is how you can distinguish which group comes from which application \(or provisioning system in the context of Identity Provisioning\) in the Identity Directory or Identity Authentication \(SCIM API version 2\) target system.

Another specific attribute for these groups is `supportedOperations`. The purpose of this attribute is to specify what are the supported operations by the Identity Provisioning for each application-specific group. For more information, see [Groups](../groups-d93be69.md).

> ### Note:  
> To find out which connectors support application-specific groups, check the list of systems under *System Types* for the `ips.application.id` property in [List of Properties](../list-of-properties-d6f3577.md).

The result from each operation with an application-specific group executed by the Identity Provisioning, depending on the value of its attribute `supportedOperations`, is described below.



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_tlt_yjx_12c"/>

## Create Application-Specific Groups

By running provisioning jobs from your source system, associated to an application, you can create application-specific groups in the Identity Directory of your SAP Cloud Identity Services tenant or Identity Authentication \(SCIM API version 2\) target system.

When you configure Local Identity Directory or Identity Authentication \(SCIM API version 2\) as source system and you try to create a group that already exists in the target system with matching attributes and `supportedOperations` attribute value `userOnlyMembership` or `membership`, its group members are updated. If you try to provision a group with value `readOnly` for the attribute `supportedOperations`, it is displayed as *Skipped* in the job log statistics for the source system. In case the group has value `readWrite` for the attribute `supportedOperations`, it is created in the target system.



<a name="loioa9ff3e3d5c9e4062860499e05259e31a__section_nny_x3c_b2c"/>

## Update Application-Specific Groups

If you update a user group assignment or a group itself in the application to which is associated your source system and you run a read or resync job, the Identity Provisioning tries to search and resolve this group in the Identity Directory of your SAP Cloud Identity Services tenant or the Identity Authentication \(SCIM API version 2\) target system.

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

