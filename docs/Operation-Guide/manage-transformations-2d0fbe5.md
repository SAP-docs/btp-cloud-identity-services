<!-- loio2d0fbe58af18418cac0b8a4a2c66c386 -->

# Manage Transformations

You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.

> ### Note:  
> The graphical editor is available only for Identity Provisioning tenants running on SAP Cloud Identity infrastructure. It is the default editor.

> ### Note:  
> This documentation refers to the Identity Provisioning service on Neo environment. If you are looking for information about Identity Provisioning service in the SAP Cloud Identity infrastructure, please refer to the [SAP Cloud Identity Services](https://help.sap.com/docs/identity-authentication/identity-authentication/what-is-identity-authentication?version=Cloud) documentation.

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

    Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

2.  Select a system from the left panel and go to the *Transformations* tab.

    The graphical editor is displayed by default. You can switch to the JSON editor by choosing the code-bracket icon.

3.  Choose *Edit*. You need to work in edit mode to add, modify and delete entities and their configurations.

    -   Working with the JSON editor allows you to type changes and perform operations like select, cut, copy and paste the transformation code.

    -   Working with the graphical editor allows you to graphically model your changes.


4.  Save your changes.


**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

[Search and Edit Systems](search-and-edit-systems-68a02be.md "You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.")

[Enable and Disable Systems](enable-and-disable-systems-89da372.md "You can enable and disable source and target systems in Identity Provisioning.")

[Export and Import Systems](export-and-import-systems-1de7de0.md "You can export and import source, target and proxy systems in Identity Provisioning.")

[Delete Systems](delete-systems-3a37213.md "You can delete a source, target, or proxy system from Identity Provisioning.")

[Update Connector Version](update-connector-version-8558733.md "Update a connector version to allow your provisioning system to use a new API.")

[Manage Properties](manage-properties-4e2bc9d.md "You can add, delete and modify properties for a system in Identity Provisioning.")

[Manage Certificates](manage-certificates-86d06a0.md "Identity Provisioning supports certificate-based authentication for secure communication with the provisioning systems (connectors) provided by the service.")

[Manage Full and Delta Read](manage-full-and-delta-read-b7f817c.md "When you set up your systems and start a scheduled provisioning task, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. However, it may take a long time for every job to be executed.")

[Manage Deleted Entities](manage-deleted-entities-3d6bdf1.md "Manage deletion of entities (users or groups) in the target system after they have been deleted from the source system.")

[Connect to On-Premise Systems](connect-to-on-premise-systems-3f1cac2.md "Set up the connection to on-premise systems when your Identity Provisioning bundle or standalone tenant is running on the infrastructure of SAP Cloud Identity Services.")

[Start and Stop Provisioning Jobs](start-and-stop-provisioning-jobs-531a261.md "You can start and stop a provisioning job from the Identity Provisioning user interface (UI) or from an API client by using the Identity Provisioning tenant admin API.")

[Handle Rate Limits](handle-rate-limits-15f7f23.md "Identity Provisioning APIs implement rate limits to control the number of incoming requests for a given time.")

[Handle Failed Operations](handle-failed-operations-0382a0c.md "In certain cases, you can set a retry for a failed operation due to an occurred exception.")

[Reset Identity Provisioning Tenant](reset-identity-provisioning-tenant-8c7ba9a.md "Resetting your Identity Provisioning tenant deletes all systems you have set up for this tenant (subaccount), along with the relevant job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

[Transformation Editors](../transformation-editors-9ea770b.md "Identity Provisioning provides graphical and JSON text editor for managing provisioning system transformations.")

[Working with Graphical Editor](working-with-graphical-editor-a985398.md "You can create, update and delete entities and their attribute mappings with a handy and easy to use graphical editor. It provides typical operations for an editor, like adding new data, editing and deleting existing data and saving changes. And what's more, it brings improved user experience, requires less typing and more choosing from a list of prefilled values.")

