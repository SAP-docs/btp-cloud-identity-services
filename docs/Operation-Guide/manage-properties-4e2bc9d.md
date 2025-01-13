<!-- loio4e2bc9d0c3fa4f71a75c7bdbcd49c2c4 -->

# Manage Properties

You can add, delete and modify properties for a system in Identity Provisioning.



<a name="loio4e2bc9d0c3fa4f71a75c7bdbcd49c2c4__prereq_gx1_vrb_bcb"/>

## Prerequisites

You have added a system \(source, target, or proxy\) in the Identity Provisioning user interface. To learn how, see [Add New Systems](add-new-systems-bd214dc.md).



<a name="loio4e2bc9d0c3fa4f71a75c7bdbcd49c2c4__steps_agr_hcb_gx"/>

## Procedure

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

3.  Select a system from the left panel and go to the *Properties* tab.

4.  To modify the current properties, choose ![](images/IPS_Edit_Icon_2ae4a04.png)*Edit* in the bottom right corner.

    > ### Note:  
    > When you update the URL or the host name of аn existing provisioning system, you must re-enter the values of the configured credential properties. The only exception to this are the credential properties of systems that are created with a connectivity destination.

5.  Add the properties required by your scenario to make successful connection to the selected system. You can use two types of properties:

    -   *Standard*: These are properties, whose values are displayed as numbers or plain text strings. For example: **Type**, **ProxyType**, **URL**, **Authentication**.
    -   *Credential*: These are properties whose values contain sensitive information that must not be displayed as plain text. For example: **Password** \(standard passwords, private keys, or OAuth client secrets\), **ssh.private.key** \(relevant to SSH Server\), **hana.jdbc.ssh.tunnel.private.key** \(relevant to SAP HANA Database\).

        > ### Note:  
        > Properties whose values contain sensitive information can be added only as *Credential* in the Identity Provisioning UI. The values of these properties are stored as encrypted data. They are excluded from the file during system configuration export.


6.  Save your changes.


**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

[Search and Edit Systems](search-and-edit-systems-68a02be.md "You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.")

[Enable and Disable Systems](enable-and-disable-systems-89da372.md "You can enable and disable source and target systems in Identity Provisioning.")

[Export and Import Systems](export-and-import-systems-1de7de0.md "You can export and import source, target and proxy systems in Identity Provisioning.")

[Delete Systems](delete-systems-3a37213.md "You can delete a source, target, or proxy system from Identity Provisioning.")

[Update Connector Version](update-connector-version-8558733.md "Update a connector version to allow your provisioning system to use a new API.")

[Manage Transformations](manage-transformations-2d0fbe5.md "You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.")

[Manage Certificates](manage-certificates-86d06a0.md "Identity Provisioning supports certificate-based authentication for secure communication with the provisioning systems (connectors) provided by the service.")

[Manage Full and Delta Read](manage-full-and-delta-read-b7f817c.md "When you set up your systems and start a scheduled provisioning task, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. However, it may take a long time for every job to be executed.")

[Manage Deleted Entities](manage-deleted-entities-3d6bdf1.md "Manage deletion of entities (users or groups) in the target system after they have been deleted from the source system.")

[Connect to On-Premise Systems](connect-to-on-premise-systems-3f1cac2.md "Set up the connection to on-premise systems when your Identity Provisioning bundle or standalone tenant is running on the infrastructure of SAP Cloud Identity Services.")

[Start and Stop Provisioning Jobs](start-and-stop-provisioning-jobs-531a261.md "You can start and stop a provisioning job from the Identity Provisioning user interface (UI) or from an API client by using the Identity Provisioning tenant admin API.")

[Handle Rate Limits](handle-rate-limits-15f7f23.md "Identity Provisioning APIs implement rate limits to control the number of incoming requests for a given time.")

[Handle Failed Operations](handle-failed-operations-0382a0c.md "In certain cases, you can set a retry for a failed operation due to an occurred exception.")

[Reset Identity Provisioning Tenant](reset-identity-provisioning-tenant-8c7ba9a.md "Resetting your Identity Provisioning tenant deletes all systems you have set up for this tenant (subaccount), along with the relevant job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

[List of Properties](../list-of-properties-d6f3577.md "On this page you can find all the available properties to use in the Identity Provisioning service. You can filter them by system type name, &quot;All Systems&quot;, by a word or only part of it.")

