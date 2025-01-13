<!-- loio85587335f47441f4bbe0537d90304a3b -->

# Update Connector Version

Update a connector version to allow your provisioning system to use a new API.

When an SAP cloud solution or service provides a new API for integrating with Identity Provisioning, you can update your respective connector \(provisioning system\) to use this API by configuring a version property and replacing its transformations.

For example, SAP Sales Cloud and SAP Service Cloud \(formerly known as SAP Cloud for Customer\) initially provided two SOAP-based APIs for integrating with Identity Provisioning and later introduced a SCIM-based API. Likewise, Identity Authentication service initially provided a SCIM-based API and later introduced an Identity Directory SCIM API.

Version property set to `1` means that your connector is using the initial API. You can continue using it as-is or update your connector to a new version.

> ### Note:  
> Before updating your connector to a new version, it is always a good practice to export the system for backup purposes. See: [Export and Import Systems](export-and-import-systems-1de7de0.md)

To update your connector to use a new API, proceed as follows:



<a name="loio85587335f47441f4bbe0537d90304a3b__section_hn4_2wc_lxb"/>

## Procedure

1.  Access the Identity Provisioning UI and choose a tile – *Source Systems*, *Target Systems*, or *Proxy Systems*.

    Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*, *Target Systems* or *Proxy Systems*.

2.  From the list on the left, select a system.

3.  On the *Properties* tab, configure the following:

    1.  **Version Property** - Add or update the <code><i class="varname">&lt;system_prefix&gt;</i>.api.version</code> property and set its value accordingly.


        <table>
        <tr>
        <th valign="top">

        Connector
        
        </th>
        <th valign="top">

        Property
        
        </th>
        <th valign="top">

        Value
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        Identity Authentication
        
        </td>
        <td valign="top">
        
        `ias.api.version` 
        
        </td>
        <td valign="top">
        
        -   `1` - Identity Authentication SCIM API \(in short, SCIM API version 1\)

            > ### Note:  
            > When the property is not defined - Identity Authentication SCIM API is used.

        -   `2` - Identity Directory SCIM API \(in short, SCIM API version 2\)



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SAP Concur
        
        </td>
        <td valign="top">
        
        `concur.api.version` 
        
        </td>
        <td valign="top">
        
        -   `1` - SAP Concur API \(Version 1\)

            > ### Note:  
            > When the property is not defined - SAP Concur API is used.

        -   `2` - SAP Concur SCIM API \(Version 2\)



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SAP Sales Cloud and SAP Service Cloud
        
        </td>
        <td valign="top">
        
        `c4c.api.version` 
        
        </td>
        <td valign="top">
        
        -   `1` - Version 1 \(SOAP-based API\)

            > ### Note:  
            > The SOAP-based API version 1 is depricated.

        -   `2` - Version 2 \(SOAP-based API\)

        -   `3` - Version 3 \(SCIM 2.0 based API\)



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SAP SuccessFactors
        
        </td>
        <td valign="top">
        
        `sf.api.version` 
        
        </td>
        <td valign="top">
        
        -   `1` - SAP SuccessFactors HCM Suite OData API \(Version 1\)

            > ### Note:  
            > When the property is not defined - SAP SuccessFactors HCM Suite OData API is used.

        -   `2` - SAP SuccessFactors Workforce SCIM API \(Version 2\)



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SAP Analytics Cloud
        
        </td>
        <td valign="top">
        
        `sac.api.version` 
        
        </td>
        <td valign="top">
        
        -   `1` - SAP Analytics Cloud SCIM API version 1. This is the default value.

        -   `2` - SAP Analytics Cloud SCIM API version 2



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        LDAP Server
        
        </td>
        <td valign="top">
        
        `ldap.api.version` 
        
        </td>
        <td valign="top">
        
        -   *1*- LDAP Server API version 1 is used. This is the default value.

        -   *2* - LDAP Server API version 2 is used.



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Microsoft Active Directory
        
        </td>
        <td valign="top">
        
        `ldap.api.version`
        
        </td>
        <td valign="top">
        
        -   *1*- LDAP API version 1 is used. This is the default value.

        -   *2* - LDAP API version 2 is used.



        
        </td>
        </tr>
        </table>
        
    2.  **Properties with Version-Specific Values** - Update connector properties which have version-specific values.


        <table>
        <tr>
        <th valign="top">

        Connector
        
        </th>
        <th valign="top">

        Property
        
        </th>
        <th valign="top">

        Value
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="2">
        
        SAP SuccessFactors
        
        </td>
        <td valign="top">
        
        `URL` 
        
        </td>
        <td valign="top">
        
        -   Version 1: `https://apitest.successfactors.com/odata/v2`

        -   Version 2: `https://apitest.successfactors.com`



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `sf.user.filter` 
        
        </td>
        <td valign="top">
        
        -   Version 1:

            `username eq 'cbraun'`

            `status eq 'active'`

        -   Version 2:

            `userName eq "cbraun"`

            `active eq true`



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SAP Analytics Cloud
        
        </td>
        <td valign="top">
        
        `csrf.token.path` 
        
        </td>
        <td valign="top">
        
        -   Version 1: `/api/v1/scim/Users?count=1`

        -   Version 2: `/api/v1/scim2/Users?count=1`



        
        </td>
        </tr>
        </table>
        

4.  On the *Transformations* tab, if you've customized your transformation logic, copy and save it first, and then replace it with the default transformation provided for the respective API version. Use the Identity Provisioning connector documentation as a source of information for the transformation you need.

5.  [Reset the system](reset-identity-provisioning-system-0bc1e53.md) to clear the operational data. It is assumed that you have already run provisioning jobs to target systems.

    -   If you reset a target system, set the `ips.delete.existedbefore.entities` to **true** in the target system itself. This ensures that, if from now on you delete entities in the source system that is connected to your target system, those entities will be recognized as previously existed entities in the target system and will be deleted there.

    -   If you reset a source system, set the `ips.delete.existedbefore.entities` to **true** in every target system connected to the given source system. This ensures that, if from now on you delete entities in the source system that is connected to your target system, those entities will be recognized as previously existed entities in the target system and will be deleted there.


6.  Adapt your new transformation, that is, apply the customizations from your previous transformation.

7.  Save your changes and run a provisioning job.


**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

[Search and Edit Systems](search-and-edit-systems-68a02be.md "You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.")

[Enable and Disable Systems](enable-and-disable-systems-89da372.md "You can enable and disable source and target systems in Identity Provisioning.")

[Export and Import Systems](export-and-import-systems-1de7de0.md "You can export and import source, target and proxy systems in Identity Provisioning.")

[Delete Systems](delete-systems-3a37213.md "You can delete a source, target, or proxy system from Identity Provisioning.")

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

