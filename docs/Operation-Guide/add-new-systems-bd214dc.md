<!-- loiobd214dcbdd824834b34045c13f1508e2 -->

# Add New Systems

You can add source, target, and proxy systems for your provisioning scenarios.

To provision entities \(users, groups, roles\) from one system to another across your enterprise, you first need to add and configure these systems as source and target connectors in Identity Provisioning.

> ### Restriction:  
> The maximum number of systems you are allowed to add is:
> 
> -   **20** sources systems
> 
> -   **50** target systems
> 
> 
> This restriction is valid for *Customer Managed* systems only. If your business requires using more systems, create an incident for component *BC-IAM-IPS* to request them. Describe your scenarios and provide a reason why you need the additional systems.

When you add a system, it is created with its default properties and transformations. If the system has different versions \(based on the APIs it provides\), you can specify which one you want to use, so that the system is created with the version specific properties and transformations.

Versioning is supported for Identity Authentication, SAP SuccessFactors, SAP Concur, SAP Analytics Cloud and SAP Sales Cloud and SAP Service Cloud. It is controlled by the `<system prefix>.api.version` property.

To add a system, proceed as follows:

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

    Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

2.  Choose the *Add* button at the top left corner of your screen.

3.  On the *Details* tab, provide the following information:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Type* 
    
    </td>
    <td valign="top">
    
    Select the system type that you want to configure.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *System Name* 
    
    </td>
    <td valign="top">
    
    Add a name for your system. Make sure it does not duplicate another system's name in the UI.

    > ### Note:  
    > System names can have a length of up to 100 characters. Only the following characters are allowed: \(a-z\), \(A-Z\), \(0-9\), \(-\), \(\_\), \(.\) and spaces.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Destination Name* 
    
    </td>
    <td valign="top">
    
    \(Optional\) Select a destination.

    If you have previously created a connectivity destination in SAP BTP cockpit on subaccount level, you can access it from the Identity Provisioning UI.

    > ### Remember:  
    > -   When you select a connectivity destination, it must be compliant to the relevant system type.
    > -   The destination should specify all the connection settings required for your identity provisioning scenario.
    > -   For *SAP Application Server ABAP* systems, creating a destination is **mandatory**.

    If you skip the *Destination Name* field, you can enter the connection and configuration properties, needed for your scenario, on the *Properties* tab.

    > ### Note:  
    > If you use both a connectivity destination and the *Properties* tab, and one and the same property exists in both places, the value set in the *Properties* tab will be considered with higher priority.
    > 
    > If you leave both the *Destination Name* field and the *Properties* tab empty and then run a job, no identity provisioning will be performed.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Description* 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a description. It will help you easily distinguish your systems in the list later on.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Source Systems*
    
    </td>
    <td valign="top">
    
    This field is displayed only for target systems.

    Select a source system whose identities you want to read and provision to the target one. You can select multiple source systems.

    > ### Tip:  
    > If you had previously added one or more source systems but some of them were later deleted in your Identity Provisioning UI, an error message will appear. To correct this inconsistency, edit the target system configuration \(select active source systems\), and save the changes.


    
    </td>
    </tr>
    </table>
    
4.  Decide on the version of the system you want to add.

    -   Choose *Save*, if the system you add has no version, or it has two or more versions and you want the default one. The new system appears in the left-side panel. The default transformations and properties are displayed under the respective tabs.

    -   Do not choose *Save*, if the system you add has two or more versions and you want to specify a particular one. In this case, proceed as follows:

        1.  From the *Details* tab \(without saving your configurations\), move to the *Properties* tab and select it.

        2.  Add the API version property for your system and a value. For example, if you add SAP SuccessFactors on the *Details* tab, add `sf.api.version` and the desired version `2`.

        3.  Now, choose *Save*.


        This creates an SAP SuccessFactors system with specific properties and transformation for version 2, which is based on SAP SuccessFactors Workforce SCIM API. Providing value 1, would result in creating a system with specific properties and transformation for version 1, which is based on SAP SuccessFactors HCM Suite OData API.

        > ### Note:  
        > Once you save your configuration, switching between versions is possible but requires manual work, mostly adding the version specific properties and transformations. For more information, see [Update Connector Version](update-connector-version-8558733.md).


5.  To add connection and configuration properties, choose *Properties* \> *Edit*. See [List of Properties](../list-of-properties-d6f3577.md)

6.  To modify your default system transformation \(if needed\), choose *Transformations* \> *Edit*.

7.  Save your changes.


At the end of the Identity Provisioning URL, a dash-separated string appears. This is the automatically generated unique ID of the newly created system.

**Related Information**  


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

[Reset Identity Provisioning Tenant](reset-identity-provisioning-tenant-8c7ba9a.md "Resetting your Identity Provisioning tenant deletes all systems you have set up for this tenant (subaccount), along with the relevant job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

[Manage Properties](manage-properties-4e2bc9d.md "You can add, delete and modify properties for a system in Identity Provisioning.")

[Manage Transformations](manage-transformations-2d0fbe5.md "You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.")

