<!-- loio1de7de0ae29444f397d22c062b7f1216 -->

# Export and Import Systems

You can export and import source, target and proxy systems in Identity Provisioning.



## Context

If you have added and configured a system, you can export it for further use. The export-import function comes in handy in the following use cases:

-   You need to back up your system before updating to a new connector version. See: [Update Connector Version](update-connector-version-8558733.md)

-   You need another system of the same type but with slightly different setup, and you don't want to manually enter all data and configuration properties all over again.

-   You need to reuse an existing system in the Identity Provisioning UI but for another subaccount.

-   You have reached the maximum number of systems you are allowed to add. You need to add one more system, which means you must delete some of the previous ones. However, you don't want to lose their configurations, thus you export these systems.


**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

[Search and Edit Systems](search-and-edit-systems-68a02be.md "You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.")

[Enable and Disable Systems](enable-and-disable-systems-89da372.md "You can enable and disable source and target systems in Identity Provisioning.")

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

<a name="concept_hkg_dxd_gz"/>

<!-- concept\_hkg\_dxd\_gz -->

## Procedure



<a name="concept_hkg_dxd_gz__section_urr_gxd_gz"/>

## Export a System

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

    Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

2.  From the list on the left, select the system you want to export.
3.  Choose the *Export* button.
4.  The exported system configuration depends on your scenario. If your system is a *source* or a *target* one, it will be exported as a JSON file. If it's a *proxy* one, you have two options:
    -   Select *JSON format* – the system configuration will be exported as a *.json* file, which you can later import back in the Identity Provisioning UI.
    -   Select *CSV format* – the system configuration will be exported as a *.csv* file, which you can later import in the SAP Identity Management UI as a SCIM repository.

5.  Save the file on your local file system.



<a name="concept_hkg_dxd_gz__section_tkd_hxd_gz"/>

## Import a System

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

    Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

2.  Choose the *Add* button.
3.  In section *Define from File*, choose the ![](images/IPS_Import_Icon_22263e9.png)*Browse* button.
4.  Browse and select the file with system configuration you need on your local file system. You can import files with extension **.json** as well as files with no extension.
5.  The system configuration is displayed in the *Details* editor. You can also see the imported transformations and properties of this system in the respective UI tabs.
6.  Change the *System Name*, otherwise an error message will appear warning you that a system with this name already exists.
7.  The *Properties* tab will prompt you to enter the credentials \(like passwords or client secrets\). When you export a system, credentials are skipped \(not displayed as plain text in the *.json* file\). Therefore, when you import it, you have to manually enter the passwords/secrets.
8.  Save your changes.

    The imported system appears in the left-side panel. Its ID is different than the one of the "original" system \(you can see it in the URL\).


> ### Caution:  
> You cannot export a target system and import it back as a source, nor the other way around.

