<!-- loio89da3728e07949bdbb658b514378febd -->

# Enable and Disable Systems

You can enable and disable source and target systems in Identity Provisioning.



## Context

To use a system for provisioning purposes, its status has to be **Enabled**. When you add a new system, it is enabled by default. If one of your added systems is configured and you currently do not need it, but would like to use it later, you can disable it.



## Procedure

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

3.  From the list on the left, select a system.

4.  At the top right corner of your screen, choose one of the following options:

    -   If the system is currently disabled, choose the *Enable* button and confirm the action.
    -   If the system is currently enabled, choose the *Disable* button and confirm the action.

5.  Save your changes.


**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

[Search and Edit Systems](search-and-edit-systems-68a02be.md "You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.")

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

