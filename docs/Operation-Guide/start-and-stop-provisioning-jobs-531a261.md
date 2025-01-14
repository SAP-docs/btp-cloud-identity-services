<!-- loio531a2615b2d04eb8ba46a638b6d81cdc -->

# Start and Stop Provisioning Jobs

You can start and stop a provisioning job from the Identity Provisioning user interface \(UI\)or from an API client by using the Identity Provisioning tenant admin API.



<a name="loio531a2615b2d04eb8ba46a638b6d81cdc__section_khk_dcn_pkb"/>

## Prerequisites

-   Your source and target systems are configured and enabled.

-   \(Optional\) You have run a *Simulate* and/or a *Validate* job before you run the actual provisioning job to verify that Identity Provisioning configurations produce the desired result in the target systems.


> ### Note:  
> This documentation refers to Identity Provisioning in the Neo environment. To access the service documentation in the SAP Cloud Identity Services infrastructure, go to [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/landing-page?version=Cloud).



<a name="loio531a2615b2d04eb8ba46a638b6d81cdc__section_stf_2cn_pkb"/>

## Job Types

The Identity Provisioning service provides the following types of provisioning jobs:


<table>
<tr>
<th valign="top">

Run From

</th>
<th valign="top">

Job Type

</th>
<th valign="top">

Real Provisioning

</th>
</tr>
<tr>
<td valign="top" rowspan="4">

Аdmin console

</td>
<td valign="top">

*Read Job* - Reads all entities from the source system and provisions only new or updated entities to the target system. If the job is run in **delta read** mode, it reads and provisions only new or updated entities in the source system.

See [Read Provisioning Job](read-provisioning-job-6256021.md)

</td>
<td valign="top" rowspan="2">

Yes

</td>
</tr>
<tr>
<td valign="top">

*Resync Job* - Reads all entities from the source system and provisions all entities to the target system.

See [Resync Provisioning Job](resync-provisioning-job-668c991.md)

</td>
</tr>
<tr>
<td valign="top">

*Simulate Job* - Estimates the number of entities that will be created, updated, deleted or skipped in the target system. Provides the expected results of a resync job without modifying the target system.

See [Simulate Provisioning Jobs](simulate-provisioning-jobs-9d96db2.md)

</td>
<td valign="top" rowspan="2">

No

</td>
</tr>
<tr>
<td valign="top">

*Validate Job* - Verifies how entities \(users and groups\) would be mapped from source to target systems without modifying them.

See [Validate Provisioning Jobs](validate-provisioning-jobs-fcaec67.md)

</td>
</tr>
<tr>
<td valign="top">

API client

</td>
<td valign="top">

Use the Identity Provisioning tenant admin API to run a provisioning job from an API client. The API is available on the SAP Business Accelerator Hub.

See [Run Provisioning Jobs via API](run-provisioning-jobs-via-api-9574b40.md)

</td>
<td valign="top">

Yes

</td>
</tr>
</table>



### Start a Job

To run a job, select a source system and choose *Jobs* \> **<Job\_Type\>** \> *Run Now*.



### Schedule a Job

To schedule a job run, select a source system and choose *Jobs* \> *Read Job* \> *Schedule*.



### Stop a Job

To stop a running job, select a source system and choose the ![](images/IPS_Disable_Icon_3e878c7.png)*Stop Job* button in the *Action* column.

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

[Manage Full and Delta Read](manage-full-and-delta-read-b7f817c.md "When you set up your systems and start a scheduled provisioning task, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. However, it may take a long time for every job to be executed.")

[Manage Deleted Entities](manage-deleted-entities-3d6bdf1.md "Manage deletion of entities (users or groups) in the target system after they have been deleted from the source system.")

[Connect to On-Premise Systems](connect-to-on-premise-systems-3f1cac2.md "Set up the connection to on-premise systems when your Identity Provisioning bundle or standalone tenant is running on the infrastructure of SAP Cloud Identity Services.")

[Handle Rate Limits](handle-rate-limits-15f7f23.md "Identity Provisioning APIs implement rate limits to control the number of incoming requests for a given time.")

[Handle Failed Operations](handle-failed-operations-0382a0c.md "In certain cases, you can set a retry for a failed operation due to an occurred exception.")

[Reset Identity Provisioning Settings](reset-identity-provisioning-settings-8c7ba9a.md "Resetting your provisioning settings will delete all provisioning systems configured for your tenant, along with the related job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

[Monitor Provisioning Job Logs](../Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md "Job logs display information about the execution of provisioning jobs. Each row in the list of job logs shows information about one execution of a job.")

[Manage Provisioning Job Logs](../Monitoring-and-Reporting/manage-provisioning-job-logs-041b5ff.md "After you view and analyze the provisioning job logs, you can download or delete them.")

