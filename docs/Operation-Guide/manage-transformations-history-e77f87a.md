<!-- loioe77f87aded564ffb88fdc2c85d2b3d10 -->

# Manage Transformations History

Мanage the history of transformations, review and restore them to a previous version of your choice.

> ### Note:  
> This functionality is available for Identity Provisioning tenants running on SAP Cloud Identity infrastructure. Customers with tenants running on SAP BTP, Neo environment can only reset modified transformations to their initial state. For more information, see [Reset Transformations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/5ffde7c9bb3d4ec395fe69d518afe8bc.html "Resetting Identity Provisioning system transformations restores them to their initial state.") :arrow_upper_right: 



<a name="loioe77f87aded564ffb88fdc2c85d2b3d10__section_bzm_pct_lzb"/>

## Context

Every time you modify the transformation of a provisioning system and save your changes, a new version is created and displayed in the *Transformation History* screen. It lists all versions - from the initial to the current one, and gives you additional information about the last modification date, the person who modified it and a description. Within this screen, you can perform a number of actions: reset the transformation to its initial version, apply the current default transformation or apply a version of your choice, as well as download previous versions of the transformations for the current system. In case you need to compare two or more versions, you can do it in a text editor, once you download the respective versions.

**Transformation History**


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

*Version* 

</td>
<td valign="top">

Transformation version

> ### Note:  
> Version 1 is the initial version. The version with the highest number is the current version.

The **initial version** is the one that you get when the system is created \(manually or automatically\). If you don't make any changes to the transformation while creating the system, the initial transformation matches the default one. If you or a provisioning tool make changes to the transformation while creating the system, the initial transformation doesn't match the default one.

There is no restriction on the number of versions you can store and manage. By default, 20 versions are displayed on the screen. You need to expand the list until all your versions are displayed.

</td>
</tr>
<tr>
<td valign="top">

*Last Modified* 

</td>
<td valign="top">

Date and time the transformation was last modified

</td>
</tr>
<tr>
<td valign="top">

*Modified By* 

</td>
<td valign="top">

Who modified the transformation:

-   The userID of the person who modified the transformation

-   *SAP* - Indicates that this transformation has been migrated by SAP. This could be your initial transformation or your current one.




</td>
</tr>
<tr>
<td valign="top">

*Description* 

</td>
<td valign="top">

\(Mandatory\) Description of the changes

When modifying the transformation, saving your changes is only allowed if you provide a description.

</td>
</tr>
<tr>
<td valign="top">

*Actions* 

</td>
<td valign="top">

Actions you can perform for a selected version:

-   Apply the selected version. This restores the transformation to the selected version.

-   Download the selected version.




</td>
</tr>
<tr>
<td valign="top">

*Default Version* 

</td>
<td valign="top">

Apply the current default version.

</td>
</tr>
<tr>
<td valign="top">

*Reset to Initial* 

</td>
<td valign="top">

Reset the transformation to its initial version.

</td>
</tr>
</table>

Following the introduction of transformations history on November 27, 2023, all your systems will have initial version listed in the *Transformation History*. What this initial version means for you, however, depends on the release of the reset transformation functionality on November 1, 2021. And that is because with implementing the reset, Identity Provisioning began storing the initial version of modified transformations.

-   Systems created before November 1, 2021, will get the current transformation as initial version.

-   Systems created after November 1, 2021, will get their actual initial transformation \(the one they got at system creation\) as initial version. If this transformation has been changed, the *Transformation History* will also list the current transformation as version 2.

-   As of November 27, 2023, every newly created system is created with initial version. Disabled systems will get the initial version upon enabling them.


> ### Note:  
> Deleting a system or resetting the tenant results in deleting the transformation history. Resetting the system itself does not delete the history.



<a name="loioe77f87aded564ffb88fdc2c85d2b3d10__section_tv3_klt_lzb"/>

## Procedure

To manage your transformations history and apply the version you need, proceed as follows:

1.  Sign in to SAP Cloud Identity Services administration console and navigate to *Identity Provisioning*.

2.  Select a system under *Source Systems*, *Target Systems* or *Proxy Systems* and choose the *Transformations* tab.

    If the transformations have been modified, an info message is displayed in the message view.

3.  Select the *Edit* button and choose the clock icon.

    This opens the *Transformation History* screen.

    Without entering the edit mode, you are only allowed to view the transformation versions and download them.

4.  Choose the action that you want to execute.

5.  Choose *Close*.


