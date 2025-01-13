<!-- loioa8deb0d43c15459f8ce05ffc0b452383 -->

# Monitor Real-Time Logs

Real-time provisioning logs display information about the execution of a real-time sync of a user or a group entity.



<a name="loioa8deb0d43c15459f8ce05ffc0b452383__section_a1h_qcb_yxb"/>

## Prerequisites

-   Your Identity Provisioning tenant is running on SAP Cloud Identity infrastructure.

-   You have configured the real-time provisioning scenario. For more information, see [Real-Time Provisioning in SAP Cloud Identity Infrastructure](https://help.sap.com/docs/identity-provisioning/identity-provisioning/real-time-provisioning-in-sap-cloud-identity-infrastructure?version=Cloud)

-   Your source and target systems are enabled. For more information, see [Enable and Disable Systems](../Operation-Guide/enable-and-disable-systems-89da372.md)




<a name="loioa8deb0d43c15459f8ce05ffc0b452383__section_syl_hdb_yxb"/>

## Procedure

You can search, view, refresh and configure a retention period of real-time provisioning logs. Proceed as follows:

1.  Sign in to the SAP Cloud Identity Services administration console and select *Identity Provisioning* \> *Provisioning Logs* \> *Real-Time Logs*.

2.  In the *Real-Time Provisioning Execution Logs* screen, search for a log and select it. You can search by source system name, entity ID, entity type and status.

    Each row in the list of logs displays the following information about one execution of a real-time sync.


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
    
    *Source System* 
    
    </td>
    <td valign="top">
    
    The name of the source system the real-time provisioning is triggered from.

    For example: *IAS\_Source*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Entity ID* 
    
    </td>
    <td valign="top">
    
    The entity ID of the user or the group in the target system.

    For example: *baba3ba7-35f0-4567-b507-ce5555c11bbb*

    If the entity ID is missing, this means that the real-time provisioning has failed. It happens when something goes wrong with the source system.

    For example, the source system is disabled or establishing the connection to the source system has failed due to incorrect URL. In this case, you get the log without the entity ID.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Entity Type* 
    
    </td>
    <td valign="top">
    
    The entity type: user or group.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Start Time* 
    
    </td>
    <td valign="top">
    
    Date, time, and time zone in UTC format when the real-time sync is triggered.

    For example: *28/Jun/2023 09:19:00 +03*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Status* 
    
    </td>
    <td valign="top">
    
    The status of the real-time provisioning.

    For example:

    -   *Finished Successfully* - Real-time provisioning finished successfully. A user or a group is successfully created, updated or deleted real time.

    -   *Finished with Error* - Real-time provisioning finished with error. A user or a group failed to be created, updated or deleted real time.



    
    </td>
    </tr>
    </table>
    
3.  In the *Real-Time Log Details* screen, view the following details under the *<Source System\>* name: log type \(*Real Time*\), entity ID \(if it is available\), start time, status, error message and *Result on Target System* table.


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
    
    The name of the target system the real-time provisioning is triggered to.

    For example: *Concur\_Target*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Operation* 
    
    </td>
    <td valign="top">
    
    The type of the operation.

    -   *CREATE*

    -   *UPDATE*

    -   *PATCH*

    -   *DELETE*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *State* 
    
    </td>
    <td valign="top">
    
    The state of the entity when real-time provisioning is triggered.

    -   *Entity Created*

    -   *Entity Updated*

    -   *Entity Skipped*

    -   *Entity Already Provisioned*

    -   *Entity Failed*

    -   *Entity Read*

    -   *Entity Deleted*

    -   *Entity Not Provisioned*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Additional Information* 
    
    </td>
    <td valign="top">
    
    Additional information about the failed entity.

    If the target system is SAP BTP XS Advanced UAA \(Cloud Foundry\), the *Additional Information* column shows the origin of the users that have been created, updated or deleted.
    
    </td>
    </tr>
    </table>
    
4.  \(Optional\) Choose *Refresh* to get the latest updates of the real-time provisioning logs.

5.  Choose *Configure* to define the retention period of real-time provisioning logs.

    Set a period \(7, 14 or 30 days\). Logs which are older than this period will be automatically deleted. By default, job logs are kept for 7 days.


> ### Restriction:  
> Note the following restrictions about the real-time provisioning logs:
> 
> -   You cannot delete them manually.
> 
> -   You cannot download them.
> 
> -   You cannot subscribe to a source system to receive notifications about their status.

