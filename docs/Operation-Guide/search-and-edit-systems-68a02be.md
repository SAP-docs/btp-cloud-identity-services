<!-- loio68a02bea560142c2a033f555eafd5509 -->

# Search and Edit Systems

You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.



<a name="loio68a02bea560142c2a033f555eafd5509__prereq_ewx_f54_55b"/>

## Prerequisites

Searching and paging of provisioning systems is supported for tenants running on SAP Cloud Identity infrastructure.



<a name="loio68a02bea560142c2a033f555eafd5509__context_mst_qtj_b1c"/>

## Context

Paging is enabled by default. The number of systems loaded per page is 20. They are sorted by type \(*Customer Managed*, *SAP Initiated* and *SAP Managed*\) and state \(*Enabled* and *Disabled*\) in the following order:

1.  Customer Managed, enabled systems are displayed alphabetically

2.  Customer Managed, disabled systems are displayed alphabetically

3.  SAP Initiated, enabled systems are displayed alphabetically

4.  SAP Initiated, disabled systems are displayed alphabetically

5.  SAP Managed, enabled systems are displayed alphabetically

6.  SAP Managed, disabled systems are displayed alphabetically


> ### Note:  
> If you can't find the system you are searching for, choose *More* to expand the list of systems as many times as needed until it is displayed.



## Procedure

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

3.  From the list on the left, either directly select a system, or search for it and select it.

4.  Select a tab and edit the configurations.

    -   *Details*
    -   *Transformations*
    -   *Properties*
    -   *Outbound Certificates*

5.  Choose the *Edit* button and make your changes.

6.  Save your changes.


**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

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

[Handle Failed Operations](handle-failed-operations-0382a0c.md "In certain cases, you can set a retry for a failed operation due to an occurred exception.")

[Reset Identity Provisioning Settings](reset-identity-provisioning-settings-8c7ba9a.md "Resetting your provisioning settings will delete all provisioning systems configured for your tenant, along with the related job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

[Manage Properties](manage-properties-4e2bc9d.md "You can add, delete and modify properties for a system in Identity Provisioning.")

[Manage Transformations](manage-transformations-2d0fbe5.md "You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.")

