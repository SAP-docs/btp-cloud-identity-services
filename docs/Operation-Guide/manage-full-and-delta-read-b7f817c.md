<!-- loiob7f817cbcf964819a23f0a2bcbd18c95 -->

# Manage Full and Delta Read

When you set up your systems and start a scheduled provisioning task, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. However, it may take a long time for every job to be executed.



## Context

Delta read is a concept for optimizing the amount of data retrieved from the source system. Delta read is much faster, but sometimes might have limitations. In order for a source system to support delta read mode, its API should allow the implementation of this feature.

For example, the *Microsoft Active Directory* source system uses the **uSNChanged** attribute. For more information, see [Microsoft: Polling for Changes Using USNChanged](https://msdn.microsoft.com/en-us/library/ms677627(v=vs.85).aspx).

The main difference between delta and full read is:

-   *Delta read* – only modified data is read from the source system and triggered to the target one. Modified data means: new entities and updates on existing entities. Entities deleted from the source system will not be deleted from the target. They can be deleted only during a *full read* job.
-   *Full read* – all entities \(new, updated, deleted, and existing unchanged ones\) are read and checked every time a provisioning job is triggered to the target system.

To keep source and target systems completely synchronized, you can use the *Resync* type of provisioning job.

> ### Tip:  
> We recommend that you enforce full reads from time to time if the connector is in delta read mode. To achieve this, you need to set up the following source system property: `ips.full.read.force.count`. For example, `ips.full.read.force.count` = **10** will result in alternating full reads after every 10 delta reads are performed.
> 
> This property only impacts scheduled runs; manually triggered runs are ignored. In case it is not set, only delta read jobs will be executed.

> ### Remember:  
> When the Identity Provisioning reads entities from a source system for the first time, it always triggers a **full read** job. If the job is successful, the service can then continue with delta read jobs \(if such are activated\). During a delta read job, the service reads only the entities that are new or have been modified after the last successful job.

> ### Note:  
> Note that Identity Provisioning will not delete entities in the target system if the job runs in **delta read** mode, if entities fail to be read from the source system or if both conditions apply. Deletion is only possible when the job runs in **full read** mode and the entities are successfully read from the source system.
> 
> In cases where deletion does not occur automatically, you must decide on the next steps. You can either resolve the failed entities in the source system and run a full read job, or proceed with deletion as described in [Manage Deleted Entities](manage-deleted-entities-3d6bdf1.md).

Below are listed all source systems that currently support *delta read* mode.



<a name="loiob7f817cbcf964819a23f0a2bcbd18c95__section_nnh_c5p_xkb"/>

## Supported Systems


<table>
<tr>
<th valign="top">

System Type

</th>
<th valign="top">

Details

</th>
</tr>
<tr>
<td valign="top">

*Microsoft Active Directory* 

</td>
<td valign="top">

Default mode: *Full read*

You can switch to delta read, if you set up the relevant property: `ips.delta.read` = **enabled**

Bear in mind the following specifics and limitations:

-   Make sure that the service user, which is used in the AD destination, has a **Domain Admin** role, otherwise the connector won't be able to extract any data from the recycle bin.
-   Due to the *linked attributes* concept of AD, there is a limitation in the Microsoft Active Directory read connector, when performing in delta read mode. We recommend that you enforce full reads periodically in order to avoid data loss. See: [Microsoft: Linked Attributes](https://msdn.microsoft.com/en-us/library/ms677270(v=vs.85).aspx)
-   You need to set limitations about which particular attributes to be read. For this purpose, set the properties `ldap.user.attributes` and `ldap.group.attributes` and add **uSNChanged** to the attributes list. Otherwise, the provisioning job will run in *full read* mode.
-   If an entity is moved outside the base path \(another directory context\), the connector won't recognize this change during delta read.



</td>
</tr>
<tr>
<td valign="top">

*SAP SuccessFactors* 

</td>
<td valign="top">

Default mode: *Delta read*

You can switch to full read, if you set up the relevant property: `ips.delta.read` = **disabled**

</td>
</tr>
<tr>
<td valign="top">

*SAP SuccessFactors Learning* 

</td>
<td valign="top">

Default mode: *Delta read*

You can switch to full read, if you set up the relevant property: `ips.delta.read` = **disabled**

</td>
</tr>
<tr>
<td valign="top">

*Identity Authentication* 

</td>
<td valign="top" rowspan="15">

Default mode: *Full read*

You can switch to delta read, if you set up the relevant property: `ips.delta.read` = **enabled**

> ### Note:  
> When using SAP Central Business Configuration and Identity Directory SCIM API \(in short, SCIM API version 2\), delta read mode is only supported for user resources.

For delta read of resources \(users and groups\), bear in mind the following API requirements:

-   The system API should return **lastModified**, which is a subattribute of the **meta** attribute. The **lastModified** subattribute denotes the most recent date and time when the resource details were updated at the service provider. See: [SCIM: Common Attributes](https://tools.ietf.org/html/rfc7643#section-3.1)

-   The system API has to also support filtering by the **lastModified** attribute, and the system should support the **gt** operator in filter expressions. See: [SCIM: Filtering](https://tools.ietf.org/html/rfc7644#section-3.4.2.2)




</td>
</tr>
<tr>
<td valign="top">

*Intelligent Opportunity Analyzer* 

</td>
</tr>
<tr>
<td valign="top">

*Local Identity Directory* 

</td>
</tr>
<tr>
<td valign="top">

*SAP Central Business Configuration* 

</td>
</tr>
<tr>
<td valign="top">

*SAP Data Custodian* 

</td>
</tr>
<tr>
<td valign="top">

*SAP Enterprise Portal* 

</td>
</tr>
<tr>
<td valign="top">

*SAP SuccessFactors Employee Central Payroll* 

</td>
</tr>
<tr>
<td valign="top">

*SAP Sales Cloud and SAP Service Cloud* 

</td>
</tr>
<tr>
<td valign="top">

*SAP Field Service Management* 

</td>
</tr>
<tr>
<td valign="top">

*SAP CPQ* 

</td>
</tr>
<tr>
<td valign="top">

*SAP Advanced Financial Closing* 

</td>
</tr>
<tr>
<td valign="top">

*SAP Advanced Workflow* 

</td>
</tr>
<tr>
<td valign="top">

*SAP Intelligent Agriculture* 

</td>
</tr>
<tr>
<td valign="top">

*SAP HANA Cloud, SAP HANA Database* 

</td>
</tr>
<tr>
<td valign="top">

*SCIM System*

\(General SCIM system, if fulfills the API requirements\)

</td>
</tr>
</table>

**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

[Search and Edit Systems](search-and-edit-systems-68a02be.md "You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.")

[Enable and Disable Systems](enable-and-disable-systems-89da372.md "You can enable and disable source and target systems in Identity Provisioning.")

[Export and Import Systems](export-and-import-systems-1de7de0.md "You can export and import source, target and proxy systems in Identity Provisioning.")

[Delete Systems](delete-systems-3a37213.md "You can delete a source, target, or proxy system from Identity Provisioning.")

[Update Connector Version](update-connector-version-8558733.md "Update a connector version to allow your provisioning system to use a new API.")

[Manage Properties](manage-properties-4e2bc9d.md "You can add, delete and modify properties for a system in Identity Provisioning.")

[Manage Transformations](manage-transformations-2d0fbe5.md "You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.")

[Manage Certificates](manage-certificates-86d06a0.md "Identity Provisioning supports certificate-based authentication for secure communication with the provisioning systems (connectors) provided by the service.")

[Manage Deleted Entities](manage-deleted-entities-3d6bdf1.md "Manage deletion of entities (users or groups) in the target system after they have been deleted from the source system.")

[Connect to On-Premise Systems](connect-to-on-premise-systems-3f1cac2.md "Set up the connection to on-premise systems when your Identity Provisioning bundle or standalone tenant is running on the infrastructure of SAP Cloud Identity Services.")

[Start and Stop Provisioning Jobs](start-and-stop-provisioning-jobs-531a261.md "You can start and stop a provisioning job from the Identity Provisioning user interface (UI) or from an API client by using the Identity Provisioning tenant admin API.")

[Handle Rate Limits](handle-rate-limits-15f7f23.md "Identity Provisioning APIs implement rate limits to control the number of incoming requests for a given time.")

[Handle Failed Operations](handle-failed-operations-0382a0c.md "In certain cases, you can set a retry for a failed operation due to an occurred exception.")

[Reset Identity Provisioning Settings](reset-identity-provisioning-settings-8c7ba9a.md "Resetting your provisioning settings will delete all provisioning systems configured for your tenant, along with the related job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

