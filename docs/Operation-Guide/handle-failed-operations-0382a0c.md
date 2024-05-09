<!-- loio0382a0c7aafd4093aff9060b8b7e229f -->

# Handle Failed Operations

In certain cases, you can set a retry for a failed operation due to an occurred exception.

If an entity operation \(*get*, *create*, *update*, or *delete*\) fails due to an occurred exception \(rate limit, bad gateway, missing authorization, or timeout\), you can set it for retry by the Identity Provisioning. You can specify a number of retries by setting the property `ips.failed.request.retry.attempts`. You can also specify a time interval \(in seconds\) between the retries via the property `ips.failed.request.retry.attempts.interval`. For more information, see [List of Properties](../list-of-properties-d6f3577.md).

Based on the system you use, the type of failed operation, and the occurred exception, the option to retry is possible in the following cases:

**Identity Provisioning Retry Support**


<table>
<tr>
<th valign="top">

Exception

</th>
<th valign="top">

Write Operation via job or Proxy

</th>
<th valign="top">

Read Operation via job

</th>
<th valign="top">

Read Operation via Proxy

</th>
</tr>
<tr>
<td valign="top">

*Timeout exception*

</td>
<td valign="top">

All connectors

</td>
<td valign="top">

All connectors

> ### Note:  
> The retry is supported only for full read.



</td>
<td valign="top">

The retry is not supported.

</td>
</tr>
<tr>
<td valign="top">

*Too many requests \(429\)*

</td>
<td valign="top">

-   Identity Authentication

-   Microsoft Entra ID

-   SAP Analytics Cloud

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Sales Cloud and SAP Service Cloud

-   SAP SuccessFactors version 2

-   SAP Jam Collaboration

-   SCIM System

-   SAP Build Work Zone, advanced edition \([Rate and Burst Limits](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/user-and-user-list-provisioning-using-scim-api?q=SCIM%20API#rate-and-burst-limits)\)




</td>
<td valign="top">

-   Cloud Foundry UAA server

-   Identity Authentication

-   Local Identity Directory

-   Sales Cloud – Analytics & AI

-   SAP Advanced Financial Closing

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP BTP Account Members \(Neo\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Business Network

-   SAP Build Work Zone, advanced edition \([Rate and Burst Limits](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/user-and-user-list-provisioning-using-scim-api?q=SCIM%20API#rate-and-burst-limits)\)

-   SAP Build Work Zone, standard edition

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP SuccessFactors Incentive Management

-   SAP Concur version 2

-   SAP CPQ

-   SAP Data Custodian

-   SAP Enterprise Portal

-   SAP Fieldglass

-   SAP Field Service Management

-   SAP Jam Collaboration

-   SAP Sales Cloud and SAP Service Cloud

-   SAP SuccessFactors Learning

-   SAP SuccessFactors version 2

-   SAP S/4HANA for procurement planning

-   SCIM System


> ### Note:  
> The retry is supported only for full read.



</td>
<td valign="top">

-   Cloud Foundry UAA server

-   Identity Authentication

-   Local Identity Directory

-   Sales Cloud – Analytics & AI

-   SAP Advanced Financial Closing

-   SAP Analytics Cloud

-   SAP Ariba Applications

-   SAP BTP Account Members \(Neo\)

-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

-   SAP Business Network

-   SAP Build Work Zone, advanced edition \([Rate and Burst Limits](https://help.sap.com/docs/build-work-zone-advanced-edition/sap-build-work-zone-advanced-edition/user-and-user-list-provisioning-using-scim-api?q=SCIM%20API#rate-and-burst-limits)\)

-   SAP Build Work Zone, standard edition

-   SAP Central Business Configuration

-   SAP Commerce Cloud

-   SAP SuccessFactors Incentive Management

-   SAP Concur version 2

-   SAP CPQ

-   SAP Data Custodian

-   SAP Enterprise Portal

-   SAP Fieldglass

-   SAP Field Service Management

-   SAP Jam Collaboration

-   SAP Sales Cloud and SAP Service Cloud

-   SAP SuccessFactors Learning

-   SAP SuccessFactors version 2

-   SAP S/4HANA for procurement planning

-   SCIM System


> ### Note:  
> The retry is supported for single entity read by `ID` and for full read.



</td>
</tr>
<tr>
<td valign="top">

*Bad gateway \(502\)*

</td>
<td valign="top">

-   SAP Build Work Zone, standard edition
-   SAP BTP XS Advanced UAA \(Cloud Foundry\)

    > ### Note:  
    > For SAP Build Work Zone, standard edition and SAP BTP XS Advanced UAA \(Cloud Foundry\) is supported retry only for patch operation.

-   SAP Sales Cloud and SAP Service Cloud



</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud

</td>
</tr>
<tr>
<td valign="top">

*Forbidden \(403\)*

</td>
<td valign="top">

SAP Analytics Cloud

</td>
<td valign="top">

The retry is not supported.

</td>
<td valign="top">

The retry is not supported.

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

[Manage Full and Delta Read](manage-full-and-delta-read-b7f817c.md "When you set up your systems and start a scheduled provisioning task, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. However, it may take a long time for every job to be executed.")

[Manage Deleted Entities](manage-deleted-entities-3d6bdf1.md "Manage deletion of entities (users or groups) in the target system after they have been deleted from the source system.")

[Connect to On-Premise Systems](connect-to-on-premise-systems-3f1cac2.md "Set up the connection to on-premise systems when your Identity Provisioning bundle or standalone tenant is running on the infrastructure of SAP Cloud Identity Services.")

[Start and Stop Provisioning Jobs](start-and-stop-provisioning-jobs-531a261.md "You can start and stop a provisioning job from the Identity Provisioning user interface (UI) or from an API client by using the Identity Provisioning tenant admin API.")

[Handle Rate Limits](handle-rate-limits-15f7f23.md "Identity Provisioning APIs implement rate limits to control the number of incoming requests for a given time.")

[Reset Identity Provisioning Tenant](reset-identity-provisioning-tenant-8c7ba9a.md "Resetting your Identity Provisioning tenant deletes all systems you have set up for this tenant (subaccount), along with the relevant job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

[List of Properties](../list-of-properties-d6f3577.md "On this page you can find all the available properties to use in the Identity Provisioning service. You can filter them by system type name, &quot;All Systems&quot;, by a word or only part of it.")

