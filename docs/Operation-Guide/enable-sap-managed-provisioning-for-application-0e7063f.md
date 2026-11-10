<!-- loio0e7063ffaabd42acad04138a03510c6b -->

# Enable SAP-Managed Provisioning for Application

Enable SAP-managed provisioning for a connected application to support integration scenarios with Joule, SAP Ariba Nexus, and other SAP-managed solutions. If group conflicts exist, resolve them as part of the activation process.



## Prerequisites

-   Your organization uses the SAP-managed delivery model, where SAP is responsible for the key technical and operational aspects of the solution.

-   The required provisioning configuration is automatically set up and maintained by SAP.

-   The application exists in SAP Cloud Identity Services and is displayed with the *Action Required* warning, indicating that SAP-managed provisioning has not yet been enabled.

-   You have existing users and application-specific groups in the Identity Directory.




## Context

To enable SAP-managed provisioning, you must resolve any group conflicts between the Identity Directory and the backend application. These conflicts occur when SAP-managed provisioning imports groups from the backend application that overlap with existing groups in the Identity Directory. You can resolve them by mapping the affected group to its backend counterpart or by permanently deleting it from the Identity Directory. SAP-managed provisioning can only be enabled after all conflicts have been resolved.

To enable SAP-managed provisioning, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose the *Applications* tile and select the application with the *Action Required* warning.

3.  Select the *Provisioning* tab and switch on the *SAP-Managed Provisioning* option.

    If conflicting groups exist, a three-step wizard opens. The first step displays all conflicting groups in a two-column table. If the conflicting groups have been deleted in the meantime, the wizard is skipped and SAP-managed provisioning is triggered automatically:


    <table>
    <tr>
    <th valign="top">

    Column
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Groups in Identity Directory
    
    </td>
    <td valign="top">
    
    The existing conflicting group in the directory.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Groups in *<Application\>* 
    
    </td>
    <td valign="top">
    
    The application group to map it to.
    
    </td>
    </tr>
    </table>
    
4.  Review each conflicting group in Identity Directory and either map it to the corresponding group that comes from the backend or permanently delete it from the Identity Directory.

5.  Choose the preferred source for group names. This selection applies to all mapped groups during the activation process.

    Select the *Group Name Source*:

    -   *Local Identity Directory* — use the directory group's name.
    -   *Application* — use the application group's name.

6.  Review all pending changes before proceeding.

7.  Choose *Enable* to apply all changes, including group mappings, deletion of marked groups, and activation of *SAP-Managed Provisioning*.

    > ### Note:  
    > After SAP-Managed Provisioning is enabled, it cannot be disabled.

    > ### Note:  
    > If any of the deleted groups are used in *Risk-Based Authentication* or *Conditional Authentication* rules, those rules may not work as expected after deletion.




## Results

Once SAP-managed provisioning is enabled, two provisioning flows run for each SAP application integrated with Joule. These flows integrate both the SAP application and the Identity Directory acting as source and target systems:

-   Flow 1: Read flow \(*SAP application* \> *Identity Directory*\)

    Users, groups, roles, and their assignments are replicated from the SAP application to the Identity Directory. Users without a Global User ID are assigned one, which Joule uses to correlate identities across applications.

-   Flow 2: Write-back flow \(*Identity Directory* \> *SAP application*\)

    The Global User IDs are written back to the SAP application, ensuring consistent user identification across all connected applications.




## Next Steps

Start user consolidation. This process matches user records from the connected SAP applications with identities in the Identity Directory, merging them into a single, globally linked identity that Joule uses to recognize each user across all applications.

For more information, see [Start User Consolidation](start-user-consolidation-d379a30.md).

