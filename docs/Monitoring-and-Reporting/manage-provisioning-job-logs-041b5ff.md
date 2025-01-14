<!-- loio041b5ff608b944d19c53be780109506e -->

# Manage Provisioning Job Logs

After you view and analyze the provisioning job logs, you can download or delete them.



<a name="loio041b5ff608b944d19c53be780109506e__section_igv_2fb_gnb"/>

## Prerequisites

-   You have enabled and set up a source and a target system in the Identity Provisioning UI. Make sure all mandatory properties are configured correctly. See: [Enable and Disable Systems](../Operation-Guide/enable-and-disable-systems-89da372.md)
-   You have run a provisioning job. See: [Start and Stop Provisioning Jobs](../Operation-Guide/start-and-stop-provisioning-jobs-531a261.md)

> ### Note:  
> This documentation refers to Identity Provisioning in the Neo environment. To access the service documentation in the SAP Cloud Identity Services infrastructure, go to [SAP Cloud Identity Services](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/landing-page?version=Cloud).



<a name="loio041b5ff608b944d19c53be780109506e__section_upy_1xc_wbb"/>

## Download Execution Logs for All Jobs

1.  Access the Identity Provisioning UI and select *Provisioning Logs* \> *Job Logs*.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Provisioning Logs* \> *Job Logs*.

3.  From the upper right corner, choose the *Download Execution Logs for All Jobs* button.

4.  Choose *Download*. If the number of logs is too large, the execution logs will be downloaded in parts. Each part \(a ZIP archive\) contains 3000 logs, by default.

5.  Save all ZIP files in your local file system.




<a name="loio041b5ff608b944d19c53be780109506e__section_nls_jn4_ypb"/>

## Download All Error Logs for a Single Job

1.  Access the Identity Provisioning UI and select *Provisioning Logs* \> *Job Logs*.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Provisioning Logs* \> *Job Logs*.

3.  Select a job that has finished with error.

4.  Above the **Failed Entities** table, choose the ![](images/IPS_Export_Icon_def37e5.png) button and select *Download All Error Logs for This Job*.

5.  Choose *Download*. The job log is downloaded as a ZIP archive. Its name pattern is: **ips\_jobErrorLogs\_<job ID\>\_<date\>\_<time\>**

    **Hint**: The job ID is at the end of the URL of the selected job in the Identity Provisioning admin console.

6.  Save the ZIP file in your local file system, and then open it to view the log records of all failed entities from this job.

    > ### Note:  
    > If your provisioning job is in *Pending Restart* status \(that is, temporary paused due to external reasons\), the logs for this job will be generated after it is resumed and completed. Be aware that logs for created, skipped, and failed entities, on the page where the job was paused, will be duplicated, assuming the page size property is configured for the given provisioning system. For more information, see [List of Properties](../list-of-properties-d6f3577.md).
    > 
    > For example, if you have set `concur.page.size`=30 and your job paused while processing the 20th entity on the second page, the logs for those 20 entities will be duplicated. The number of duplicated logs can be equal to or less than the configured page size. If page size is not configured, the default value of 100 will be used.




<a name="loio041b5ff608b944d19c53be780109506e__section_wvx_x4p_2tb"/>

## Download All Skipped Entity Logs for a Single Job

> ### Note:  
> This functionality is available only for Identity Provisioning bundle and standalone tenants running on SAP Cloud Identity infrastructure.



### Prerequisites

-   You have set the `ips.trace.skipped.entity` property to `true` in the source system.

-   You have set the `ips.trace.skipped.entity.content` property to `true` in the source system.


For more information, see [List of Properties](../list-of-properties-d6f3577.md)

Download the skipped entities for a single job to identify the entities themselves, the systems they are skipped from, the reason behind this, as well as to view the content of the entities.

1.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Provisioning Logs* \> *Job Logs*.

2.  Select a job that has at least one skipped entity.

3.  On the right-hand side of the *Statistics* section, choose the ![](images/IPS_Export_Icon_def37e5.png) button and select *Download All Skipped Entity Logs for This Job*.

    The log is downloaded as a `zip` archive. The name of the file follows the pattern: <code>ips_jobSkippedEntitiesLogs_<i class="varname">&lt;job ID&gt;</i>_<i class="varname">&lt;date&gt;</i>_<i class="varname">&lt;time&gt;</i></code>.

4.  Save the `zip` file in your local file system, and then open it to view the log records of all skipped entities for this job.

    The log displays the following information:


    <table>
    <tr>
    <th valign="top">

    Entity Details
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *User*

    *Group*
    
    </td>
    <td valign="top">
    
    The ID of the skipped entity

    For example: `12345678-1a2b-1bc2-3cd4-1234567890ef`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *System* 
    
    </td>
    <td valign="top">
    
    The system the entity is skipped from. This could be either a source system or a target system.

    For example: `IAS.target`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Skip Reason* 
    
    </td>
    <td valign="top">
    
    The reason the entity is skipped

    Normally, a user or a group is skipped because it does not fulfill a condition in the source read transformation or the target write transformation. If this is the case, you will see the exact condition the entity does not fulfill.

    For example:

    > ### Code Syntax:  
    > ```
    > The condition: ($.emails EMPTY false) && ($.userName EMPTY false), is not fulfilled.
    > ```

    A user or a group can also be skipped if you use the `skipOperations` expression in the transformations to avoid creating, deleting, or updating entities in target systems. If this is the case, you will see the following message: ***Operation \[*<create\>**<update\>**<delete\>*\] is skipped in target transformation***
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Content* 
    
    </td>
    <td valign="top">
    
    The content \(attributes of the skipped entity

    For example:

    > ### Code Syntax:  
    > ```
    > {"active":true,"displayName":"JohnSmith","emails":[{"value":"john.smith@example.com"}],
    > "name":{"familyName":"Smith","givenName":"John"},"schemas":["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:sap:2.0:User"],"urn:ietf:params:scim:schemas:extension:sap:2.0:User":{"userUuid":"0036024b-0ede-4fc3-9ed7-c55632de8246"},"urn:sap:cloud:scim:schemas:extension:custom:2.0:User":{"userId":"12345678-1a2b-1bc2-3cd4-1234567890ef"},"userName":"","userType":"public"}
    > ```


    
    </td>
    </tr>
    </table>
    
    The log is organized in sections which start with the ID of the skipped entity. If a user or a group is skipped in more than one systems, the log will display the ID of the skipped entity as many times as there are systems where the entity is skipped from, the skip reason and the entity's content.




<a name="loio041b5ff608b944d19c53be780109506e__section_cbr_ty2_jdc"/>

## Download All Created Entity Logs for a Single Job

> ### Note:  
> This functionality is available only for Identity Provisioning bundle and standalone tenants running on SAP Cloud Identity infrastructure.



### Prerequisites

-   You have set the `ips.trace.created.entity` property to `true` in the source system.

-   You have set the `ips.trace.created.entity.content` property to `true` in the source system.


For more information, see [List of Properties](../list-of-properties-d6f3577.md)

Download the created entities for a single job to identify the system in which they are created and to view the content of the entities.

1.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Provisioning Logs* \> *Job Logs*.

2.  In the *Job Execution Logs* screen, search for a job log and select it.

3.  If the job has created at least one entity, you are able to choose the ![](images/IPS_Export_Icon_def37e5.png) button on the right-hand side of the *Statistics* section and select *Download All Created Entity Logs for This Job*.

    The log is downloaded as a `zip` archive. The name of the file follows the pattern: <code>ips_jobCreatedEntitiesLogs_<i class="varname">&lt;job ID&gt;</i>_<i class="varname">&lt;date&gt;</i>_<i class="varname">&lt;time&gt;</i></code>.

4.  Save the `zip` file in your local file system, and then open it to view the log records of all created entities for this job.

    The log displays the following information:


    <table>
    <tr>
    <th valign="top">

    Entity Details
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *User*

    *Group*
    
    </td>
    <td valign="top">
    
    The ID of the created entity in the target or proxy system

    For example: `12345678-1a2b-1bc2-3cd4-1234567890ef`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *System* 
    
    </td>
    <td valign="top">
    
    The system in which the entity is created. This could be either a target system or a proxy system.

    For example: `IAS.target`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Content* 
    
    </td>
    <td valign="top">
    
    The content attributes of the created entity

    For example:

    > ### Code Syntax:  
    > ```
    > {"active":true,"displayName":"JohnSmith","emails":[{"value":"john.smith@example.com"}],
    > "name":{"familyName":"Smith","givenName":"John"},"schemas":["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:sap:2.0:User"],"urn:ietf:params:scim:schemas:extension:sap:2.0:User":{"userUuid":"0036024b-0ede-4fc3-9ed7-c55632de8246"},"urn:sap:cloud:scim:schemas:extension:custom:2.0:User":{"userId":"12345678-1a2b-1bc2-3cd4-1234567890ef"},"userName":"","userType":"public"}
    > ```


    
    </td>
    </tr>
    </table>
    
    The log is organized in sections which start with the ID of the created entity. If a user or a group is created in more than one systems, the log will display the ID of the created entity as many times as the number of systems in which it is created and the entity's content.




<a name="loio041b5ff608b944d19c53be780109506e__section_pkz_lfq_zxb"/>

## Download Job Logs via API

> ### Note:  
> This functionality is available only for Identity Provisioning bundle and standalone tenants running on SAP Cloud Identity infrastructure.

-   You need a technical user \(a user of type System in SAP Cloud Identity Services admin console\) with *Access Identity Provisioning Tenant Admin API* permission assigned. For more information, see [Managing Administrators](https://help.sap.com/docs/identity-authentication/identity-authentication/managing-administrators?version=Cloud).


Use the Identity Provisioning tenant admin API to download job logs via API calls for a single provisioning job. The API is available on the SAP Business Accelerator Hub: [SAP Cloud Identity Services](https://api.sap.com/package/SCPIdentityServices/rest) *Identity Provisioning Service* \> *API Reference* \> *JobLogs*. The URL for accessing the Tenant Admin API follows the pattern: <code>https://&lt;ias-tenant-host&gt;/ips/service/publicapi/v1/jobLogs/<i class="varname">&lt;JobId&gt;</i>?action=export&amp;logType=<i class="varname">&lt;logType&gt;</i></code>, where:


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

*<JobId\>* 

</td>
<td valign="top">

The job identifier

</td>
</tr>
<tr>
<td valign="top">

Action

</td>
<td valign="top">

The action to be executed

Only possible value: `export`

</td>
</tr>
<tr>
<td valign="top">

*<logType\>* 

</td>
<td valign="top">

The type of the job log to be downloaded

Possible values:

-   `commonLog` - Download logs containing the following details for this specific job execution \(start time, end time, statistics, type, mode\). These details are currently included in the common logs for all job executions.

-   `failedEntitiesLog` - Download logs containing details about the failed entities for this specific job execution.

-   `skippedEntitiesLog` - Download logs containing details about the skipped entities for this specific job execution.

-   `createdEntitiesLog` - Download logs containing details about the created entities for this specific job execution.




</td>
</tr>
</table>

For example: <code>https: //<i class="varname">&lt;ias-tenant-host&gt;</i>/ips/service/publicapi/v1/jobLogs/cbc1eb01686664856111?action=export&amp;logType=allErrorsLog</code> 

Save the `zip` file in your local file system, and then open it to view the log records for the log type you have defined.



<a name="loio041b5ff608b944d19c53be780109506e__section_x5x_dmb_rbb"/>

## Delete Job Logs

If you don't need your job logs anymore, you can delete them. You can do this manually or automatically \(by setting a retention period\).

1.  Access the Identity Provisioning UI and select *Provisioning Logs* \> *Job Logs*.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Provisioning Logs* \> *Job Logs*.

3.  Choose the ![](images/IPS_Delete_Icon_a6390ce.png)*Delete Logs* icon.

    > ### Caution:  
    > This deletes the logs for all finished jobs. If a job is still running though, it will stay along with its logs.

4.  You can set a time period for keeping the job logs available for monitoring.

    1.  From the upper right corner, choose ![](images/IPS_-_Configure_job_logs_13cc507.png)*Configure Job Logs Settings*.

    2.  Set a period \(**7**, **14** or **30** days\). Logs which are older than this period will be automatically deleted. By default, job logs are kept for 7 days.

    3.  If you want to keep the logs longer, you can download and save them in your local file system.



