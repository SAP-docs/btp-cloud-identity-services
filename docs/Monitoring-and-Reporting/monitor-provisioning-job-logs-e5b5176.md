<!-- loioe5b5176c17ae4ae4bd32ae07877ddd79 -->

# Monitor Provisioning Job Logs

Job logs display information about the execution of provisioning jobs. Each row in the list of job logs shows information about one execution of a job.



## Prerequisites

-   You have enabled and set up a source and a target system in the Identity Provisioning UI. Make sure all mandatory properties are configured correctly. See: [Enable and Disable Systems](../Operation-Guide/enable-and-disable-systems-89da372.md)

-   You have run a provisioning job. See: [Start and Stop Provisioning Jobs](../Operation-Guide/start-and-stop-provisioning-jobs-531a261.md)

-   Your Identity Provisioning tenant must run on SAP Cloud Identity Services infrastructure to be able to search for job logs.


> ### Note:  
> This documentation refers to Identity Provisioning in the Neo environment. To access the service documentation in the SAP Cloud Identity Services infrastructure, go to [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/landing-page?version=Cloud).



## Procedure

To search and view the job logs, proceed as follows:

1.  Access the Identity Provisioning UI and select *Provisioning Logs* \> *Job Logs*.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Provisioning Logs* \> *Job Logs*.

3.  In the *Job Execution Logs* screen, search for a job log and select it. You can search by system name, job type and status.

    Each row in the list of job logs displays the following information:


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
    
    The source system the job was triggered for.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Job Type* 
    
    </td>
    <td valign="top">
    
    The job type can be **READ**, **RESYNC** and **SIMULATE**.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Trigger Type* 
    
    </td>
    <td valign="top">
    
    The triggering type for the job. It can be:

    -   **IMMEDIATE** – for manually triggered jobs after choosing *Run Now* or for restarted jobs which were in previous status **Pending Restart**.

    -   **REPEAT** – for scheduled jobs after choosing *Schedule*.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Status* 
    
    </td>
    <td valign="top">
    
    The status of the job.

    -   **Success** – provisioning job has finished successfully.

    -   **Finished with Error** – provisioning job has finished with error. Some entities failed to be read or written, connection to the source system failed or reading from the source system encountered an issue.

    -   **Running** – provisioning job is still running and has not encountered any issues so far.

    -   **Running with Error** – provisioning job is still running, but some entities already failed.

    -   **Manually Terminated** – provisioning job is manually stopped by Identity Provisioning administrator.

    -   **Pending Restart** – provisioning job is temporary paused due to external reasons, not related to your direct interaction \(for example, when Identity Provisioning is currently down\). When the state gets back to normal, the job will automatically resume with a new job ID, continuing from the last processed entity. Its status will switch over to **Running** or **Running with Error**.

        Note that, if a provisioning job from a source system to multiple target systems stops due to an error in one of the targets, it will not resume for that specific target upon restart.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Start Time* 
    
    </td>
    <td valign="top">
    
    Date, time, and timezone in UTC format when the job is started.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *End Time* 
    
    </td>
    <td valign="top">
    
    Date, time, and timezone in UTC format when the job is finished.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Action* 
    
    </td>
    <td valign="top">
    
    Allows you to stop a running provisioning job by choosing the ![](../Operation-Guide/images/IPS_Disable_Icon_3e878c7.png)*Stop Job* button .
    
    </td>
    </tr>
    </table>
    
4.  In the *Job Execution Details* screen, view the following details about a given job:

    -   **<System\_Name\>** – Shows the source system name.

    -   **Job Type** - Shows the type of the job, as described in the table above.

    -   **Read Mode** - Shows the mode of the job. It can be:

        -   **Full Read**

        -   **Delta Read**

            The read mode considers how job-related properties, such as: `ips.delta.read` and `ips.full.read.force.count`, are configured on the source system.

            For example, if your system works in delta read mode and you set up ips.full.read.force.count=10, the *Job Execution Details* screen will display 10 consecutive jobs with *Read Mode:Delta Read* followed by one with *Read Mode:Full Read*.

            > ### Note:  
            > **Resync** and **Simulate** jobs \(the latter is available for Identity Provisioning tenants on SAP Cloud Identity Services infrastructure\) will always have Read Mode: Full Read. Migration jobs does not display read mode.


    -   **Тrigger Тype** - Shows the trigger type, as described in the table above.

    -   **Triggered by** - Shows the ID of the user who triggered the job manually. It is displayed for jobs of type read, resync and simulate with trigger type immediate.

        > ### Note:  
        > Scheduled jobs don't display the **Triggered by** information.

    -   **Start Time** and **End Time** - Shows the job start and end time, as described in the table above.

    -   **Error Message** – Shows the error message.

    -   **Job Execution Outcome** - Shows the job execution specifics that have influenced the deletion of entities from the target system\(s\) at the end of the provisioning job.

    -   **Statistics** – Shows the job statistics, that is, details about how entities are handled.

        > ### Note:  
        > Note that if an entity type is set to be ignored in the transformations, you won't get any data in the job log statistics for this entity type.


        <table>
        <tr>
        <th valign="top">

        Column
        
        </th>
        <th valign="top">

        Source System
        
        </th>
        <th valign="top">

        Target System
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        *Entity*
        
        </td>
        <td valign="top">
        
        Type of the entity \(user, group\)
        
        </td>
        <td valign="top">
        
        Type of the entity \(user, group\)
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *System*
        
        </td>
        <td valign="top">
        
        Name of the source system
        
        </td>
        <td valign="top">
        
        Name of the target system
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Action*
        
        </td>
        <td valign="top">
        
        Action executed on the system: *Read* 
        
        </td>
        <td valign="top">
        
        Action executed on the system: *Write* 
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Read*
        
        </td>
        <td valign="top">
        
        Number of read entities
        
        </td>
        <td valign="top">
        
        Not applicable
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Created*
        
        </td>
        <td valign="top">
        
        Not applicable
        
        </td>
        <td valign="top">
        
        Number of created entities
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Updated*
        
        </td>
        <td valign="top">
        
        Not applicable
        
        </td>
        <td valign="top">
        
        Number of updated entities
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Deleted*
        
        </td>
        <td valign="top">
        
        Not applicable
        
        </td>
        <td valign="top">
        
        Number of deleted entities
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Skipped*
        
        </td>
        <td valign="top">
        
        Number of skipped entities from the source system

        Entities can be skipped if they don't fulfill a condition in the read transformation.

        > ### Example:  
        > Setting this group condition in the read transformation results in skipping all read groups that do not match the specified display name.
        > 
        > > ### Code Syntax:  
        > > ```
        > > "condition": "$.displayName == 'Employee'",
        > > ```


        
        </td>
        <td valign="top">
        
        Number of skipped entities in the target system

        Entities can be skipped if they don't fulfill a condition in the write transformation.

        An application-specific group is skipped if you try to perform an operation which is not supported for it. For more information about the *supportedOperations* attribute, see [Groups](../groups-d93be69.md).

        > ### Example:  
        > Setting this group condition in the write transformation results in skipping all groups that do not match the specified display name.
        > 
        > > ### Code Syntax:  
        > > ```
        > > "condition": "$.displayName == 'Employee'",
        > > ```


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Failed*
        
        </td>
        <td valign="top">
        
        Number of entities failed during the read operation from the source system
        
        </td>
        <td valign="top">
        
        Number of entities failed to be created, updated or deleted in the target system
        
        </td>
        </tr>
        </table>
        
    -   **Failed Entities** – Shows additional information about the failed entities. A maximum number of ten entities can be displayed per job log. In case you need to view the full job log, download it from the ![](images/IPS_Export_Icon_def37e5.png)*Download All Error Logs for This Job* button. For more information see: [Manage Provisioning Job Logs](manage-provisioning-job-logs-041b5ff.md)



**Related Information**  


[Start and Stop Provisioning Jobs](../Operation-Guide/start-and-stop-provisioning-jobs-531a261.md "You can start and stop a provisioning job from the Identity Provisioning user interface (UI) or from an API client by using the Identity Provisioning tenant admin API.")

[Manage Job Notifications](manage-job-notifications-d055bc2.md "You can subscribe to a source system to receive notification e-mails. They provide information about the job execution and links to download job logs, in case of created, updated, failed, skipped, or deleted entities.")

