<!-- loio916289856f474589a5ac7fe27c96dd07 -->

# Monitor Central Store Logs

Central Store Logs provide information about the application-specific groups that have been provisioned from the Identity Directory to your target systems.



<a name="loio916289856f474589a5ac7fe27c96dd07__section_a1h_qcb_yxb"/>

## Prerequisites

-   You have configured the Local Identity Directory as a source system, linked it to a target system, and run at least one provisioning job. For more information, see [Start and Stop Provisioning Jobs](../Operation-Guide/start-and-stop-provisioning-jobs-531a261.md).

-   You have created an application under *Applications & Resources*, and set its application ID as the value of the `ips.application.id` property in the target system.

-   You have enabled the *Central Store-Based Provisioning* option under *Applications & Resources* \> *Application* \> *Provisioning*.




<a name="loio916289856f474589a5ac7fe27c96dd07__section_syl_hdb_yxb"/>

## Procedure

You can search, view and refresh central store logs.

1.  Sign in to the SAP Cloud Identity Services administration console and select *Identity Provisioning* \> *Provisioning Logs* \> *Central Store Logs*.

    > ### Note:  
    > *Central Store Logs* are enabled and will appear under *Provisioning Logs* whenever changes to application-specific groups occur in the Identity Directory, such as assigning users or modifying group attributes.

2.  In the *Central Store Provisioning Logs* screen, search for a log and select it. You can search by target system name, application ID, target entity ID, source entity ID and status.

    Each row in the log list provides information about a single execution of central store-based provisioning.


    <table>
    <tr>
    <th valign="top">

    Column
    
    </th>
    <th valign="top">

    Details
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Target System* 
    
    </td>
    <td valign="top">
    
    The name of the target system to which the central store-based provisioning is triggered.

    For example: *Fieldglass\_Target*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Application ID* 
    
    </td>
    <td valign="top">
    
    The ID of the application the application-specific group belongs to. It is configured as a value of the `ips.application.id` property in the target system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Source Entity ID* 
    
    </td>
    <td valign="top">
    
    The entity ID of the group in the source system, that is Identity Directory.

    For example: *4200a79f-228b-4fcd-ab15-46d2d78360f6*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Target Entity ID* 
    
    </td>
    <td valign="top">
    
    The entity ID of the group in the target system.

    For example: *baba3ba7-35f0-4567-b507-ce5555c11bbb*

    If the target entity ID is missing, it means that the central store-based provisioning has failed. This can occur, for example, when the group is not found or when multiple groups with the same display name are found in the target system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Entity Type* 
    
    </td>
    <td valign="top">
    
    The entity type: group.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Status* 
    
    </td>
    <td valign="top">
    
    The status of the central store-based provisioning

    For example:

    -   *Finished Successfully* - Central store-based provisioning finished successfully. A group is successfully updated.

    -   *Finished with Error* - Central store-based provisioning finished with error. A group failed to be updated.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Start Time* 
    
    </td>
    <td valign="top">
    
    Date, time, and time zone in UTC format when the central store-based provisioning is triggered

    For example: *28/Jan/2025 09:34:21 +02*
    
    </td>
    </tr>
    </table>
    
3.  In the *Central Store Provisioning Log Details* screen, view the following details under the *<Target System\>* name:

    -   *Log Type*: Central Store Provisioning Log Details

    -   *Source System*: The name of the source system

    -   *Entity Type*: group

    -   *Source Entity ID*: The group ID in the source system

    -   *Target Entity ID*: The group ID in the target system

    -   *Application ID*: The ID of the application the application-specific group belongs to.

    -   *Start Time*: Date, time, and time zone in UTC format when the central store-based provisioning is triggered

    -   *Status*: The status of the central store-based provisioning



    <table>
    <tr>
    <th valign="top">

    Column
    
    </th>
    <th valign="top">

    Details
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Target System* 
    
    </td>
    <td valign="top">
    
    The name of the target system to which the central store-based provisioning is triggered.

    For example: *Fieldglass\_Target*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Operation* 
    
    </td>
    <td valign="top">
    
    The type of the operation.

    -   *CREATE* - This operation will appear when a group is created in the target system.

        When provisioning application-specific groups from the Identity Directory to target systems, groups that do not exist in the target will only be created after an update is made to the group in the source. This update could involve assigning users or modifying group attributes. Newly created groups in the Identity Directory source system are not provisioned unless changes occur. This applies to application-specific groups of types: `userGroup`, `authorization` and `deepLinkActivationPermission`, with the supported operation `readWrite`.

        > ### Note:  
        > Application-specific groups with supported operations `readOnly`, `userOnlyMembership` and `membership` will not be created even if updates are made to the groups. When trying to provision such groups, you will get an ***Entity Failed*** status and an error message in the *Additional Information* section. Examples of these messages include: ***Application group not found or more than one groups for the given display name found on the target system***.

    -   *UPDATE* - This operation will appear when a group is updated in the target system.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *State* 
    
    </td>
    <td valign="top">
    
    The state of the entity when central store-based provisioning is triggered.

    -   *Entity Created*

    -   *Entity Updated*

    -   *Entity Failed*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Additional Information* 
    
    </td>
    <td valign="top">
    
    Additional information about the failed entity.
    
    </td>
    </tr>
    </table>
    
4.  \(Optional\) Choose *Refresh* to get the latest updates of the central store-based provisioning logs.


