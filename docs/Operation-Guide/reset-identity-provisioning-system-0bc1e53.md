<!-- loio0bc1e53ef28247bc9a20faffaddf1f30 -->

# Reset Identity Provisioning System

Resetting an Identity Provisioning system \(source or target\) deletes all Identity Provisioning operational data.



## Context

There might be times when you would like to delete the current Identity Provisioning operational data for a particular system. For example, clearing entities that were read from the source system and were then mapped to SCIM specific attributes via the intermediate transformation logic.

This operation is called *system reset*. If you choose it, you only clear the Identity Provisioning operational data. The system configurations and all existing read and provisioned entities, along with their authorizations, will be preserved in the back-end source and target systems. To learn more, see: [Transformations](../transformations-81f5204.md) 

Cases that require reset of the provisioning system are:

-   Updating the version of the provisioning source or target system; For more information, see [Update Connector Version](update-connector-version-8558733.md).
-   Changing the attribute mapped to the variable *entityIdSourceSystem* \(for a source system\) or *entityIdTargetSystem* \(for a target system\); For more information, see [Transformation Variables](../transformation-variables-8376adb.md).
-   Resetting Identity Authentication target system might be needed after an SAP SuccessFactors instance refresh. For more information, see SAP Note [2954491](https://me.sap.com/notes/2954491).
-   Database restore of the back-end target system \(for example, Identity Authentication\). After restoring a previously saved state of the database, some data or configurations might be out of sync. It’s recommended that you reset the system before running a provisioning job.

In all other cases, reset is not required, nor recommended. If you have any concerns, report an incident on [SAP Support Portal Home](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fsupport.sap.com%2Fen%2Findex.html) for the *BC-IAM-IPS* component.

If you want to reset your system, proceed as follows:



## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems* or *Target Systems*

3.  Select the relevant source or target system.

    > ### Restriction:  
    > This *reset* operation is not applicable to proxy systems.

4.  At the top right corner of your screen, choose the *Reset* button and confirm the action.




<a name="loio0bc1e53ef28247bc9a20faffaddf1f30__postreq_ybs_jpw_4lb"/>

## Next Steps

Regardless of the type of system you have reset - source or target ones, continue with the following steps:

1.  Start a provisioning job. See: [Start and Stop Provisioning Jobs](start-and-stop-provisioning-jobs-531a261.md)

2.  Set the `ips.delete.existedbefore.entities` to **true** on all affected target systems. This ensures that, if from now on you delete entities in the source system, those entities will be recognized as previously existed entities in the target systems and will be deleted there.

3.  Start a provisioning job again.


> ### Note:  
> Following a reset, scheduled jobs preserve their defined time period.

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

[Handle Failed Operations](handle-failed-operations-0382a0c.md "In certain cases, you can set a retry for a failed operation due to an occurred exception.")

[Reset Identity Provisioning Settings](reset-identity-provisioning-settings-8c7ba9a.md "Resetting your provisioning settings will delete all provisioning systems configured for your tenant, along with the related job execution logs.")

