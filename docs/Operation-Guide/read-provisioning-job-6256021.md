<!-- loio6256021bb76747999c636160f864c1e4 -->

# Read Provisioning Job

The *Read* job reads all entities from the source system and provisions only new or updated entities to the target one. If the job is run in **delta read** mode, it reads and provisions only new or updated entities in the source system.

> ### Note:  
> A Read job checks only for changes in the source system. If there have been changes in the target system, they are not affected by the job.

Although the name of the job implies reading users, a Read job could also lead to deleting users from the target system. This could happen if any of the following changes occur after you have run a provisioning job \(Read or Resync\):

-   A user has been deleted in the source system. As a result, on the next run of the Read job, the deleted user won’t be read from the source system and will be deleted in the target system.

-   A user filter is applied in the source system. As a result, on the next run of the Read job, the users not matching the filtering criteria will be deleted in the target system.

-   A condition is applied either in the source or in the target system. As a result, on the next run of the Read job, the users not matching the condition criteria will be skipped or deleted in the target system.

-   The mapping of the targetVariable `entityIdSourceSystem` or `entityIdTargetSystem` has been changed.


> ### Example:  
> You have a source system with users A, B, C and D.
> 
> 1.  Run a Read Job.
> 
>     Users A, B, C and D are created in the target system.
> 
> 2.  In the source system, update user C, delete user D and add a new user E.
> 
> 3.  Run a second job.
> 
>     -   If the second job is a Read Job: It reads users A, B, C and E from the source system and then creates user E, updates user C, and deletes user D in the target system.
> 
>     -   If the second job is a Delta Read job: It reads users C and E from the source system and then creates user E and updates user C.
> 
>     -   If the second job is a Resync job: It reads users A, B, C and E from the source system and then creates user E, updates users A, B and C, and deletes user D.



<a name="loio6256021bb76747999c636160f864c1e4__section_iq2_jld_lvb"/>

## Run Now

To run a read job, select a source system and choose *Jobs* \> *Read Job* \> *Run Now*. This starts a read job immediately.



<a name="loio6256021bb76747999c636160f864c1e4__section_ypn_kld_lvb"/>

## Schedule

To schedule a read job, select a source system and choose *Jobs* \> *Read Job* \> *Schedule*. This runs the job at the scheduled time period.


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*ON/OFF* 

</td>
<td valign="top">

Turn the job scheduler on or off:

-   *ON* - enables the job scheduler. After that, jobs run at the scheduled time period. This option does not run the job immediately.

-   *OFF* - stops the job scheduler. After that, jobs are stopped from running at the scheduled time. This option does not stop/pause a running job.




</td>
</tr>
<tr>
<td valign="top">

*Run job every \(minutes\)* 

</td>
<td valign="top">

Schedule how often a read job to be run. The number must be larger than **30** \(minutes\). This option sets the time period but does not run the job immediately. Thus, after you set a scheduled period, turn *ON* the job scheduler.

Use cases:

-   If the scheduled job is finished **before** the next time point, it will start again on the upcoming time point as scheduled, at the precise second.

-   If the scheduled job is finished **after** the next time point, it will skip the relevant upcoming time point\(s\) and will start again on the next available one, at the precise second.

-   If **during** a running scheduled job, you click *Run Now*, this will trigger a manual job, which will start immediately after the current scheduled job has finished. The next scheduled job will start at the upcoming regular time point, at the precise second.


> ### Remember:  
> Before you schedule a job, make sure it's not been paused \(that is, the job scheduler has not been turned off\). Otherwise, the job will not be executed.



</td>
</tr>
<tr>
<td valign="top">

*Run job on a specific day of the week and time*:

</td>
<td valign="top">

Specify the day and time to run the job. You must select at least one day of the week and the exact time. Day and time fields cannot be empty.

The job is run in customer's time zone.

> ### Note:  
> This functionality is available only for Identity Provisioning bundle and standalone tenants running on SAP Cloud Identity infrastructure.



</td>
</tr>
</table>

