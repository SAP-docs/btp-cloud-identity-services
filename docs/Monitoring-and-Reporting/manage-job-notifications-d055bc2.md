<!-- loiod055bc278e614713916090c532e3859f -->

# Manage Job Notifications

You can subscribe to a source system to receive notification e-mails. They provide information about the job execution and links to download job logs, in case of created, updated, failed, skipped, or deleted entities.



<a name="loiod055bc278e614713916090c532e3859f__prereq_dty_bjp_2pb"/>

## Prerequisites

Before subscribing yourself to a source system, make sure that the trust between your Identity Authentication and SAP BTP is properly set, otherwise the Identity Provisioning might not propagate your email address. To do that:

1.  Open SAP BTP cockpit and navigate to your Neo subaccount.
2.  Navigate to *Security* \> *Trust* \> *Application Identity Provider*.
3.  Check your current identity provider.
    -   If it's the default one – **SAP ID Service** \(`https://accounts.sap.com`\), you don't need to do anything.
    -   If it's a custom one, choose the link to open it for edit. Go to tab *Attributes*, and then follow steps **11–12** on page: [Setting Up Trust Between Identity Authentication and SAP BTP](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/0df6abc18397483dbb34b87dcc0622c7.html)




<a name="loiod055bc278e614713916090c532e3859f__context_snf_qlc_5z"/>

## Context

When you subscribe to a source system, you can receive notification e-mails in the following cases:

-   You start or schedule a provisioning job and it fails.

    You'll receive an e-mail with subject *Provisioning Running with Error. Source System: <name\>*. You receive one e-mail per job, after the first failed entity. If more entities fail during this job, no additional e-mails will be sent. This behavior is related to property `ips.job.notification.skip.intermediate.notifications`.

-   The failed job has finished.

    You'll receive an e-mail with subject *Provisioning Finished with Error. Source System: <name\>*. By default, if the same job runs again and keeps failing, no further notifications will be sent to your e-mail. However, you can control the notifications via properties `ips.job.notification.ignored.consecutive.failures` and `ips.job.notification.repeat.on.failure`. For more information, see: [List of Properties](../list-of-properties-d6f3577.md)

-   The job is back to normal \(the problem with the failed entities has been resolved\).

    After a new run, the job has successfully finished. You'll receive only one e-mail with subject *Provisioning Success. Source System: <name\>*.


The notification e-mail tells you which are the source and the target systems, what is the job type, its start time and status. It contains the `Navigate to details` link that opens the *Job Execution Details* screen in the Identity Provisioning UI.

In case your job finished with created, updated, failed, skipped, or deleted entities, links to `Download created entities logs`, `Download updated entities logs`, `Download error logs`, `Download skipped entities logs`, and `Download deleted entities logs` are provided, respectively. The content of the downloaded log files depends on your configuration of the `ips.trace.created.entity`, `ips.trace.created.entity.content`, `ips.trace.updated.entity`, `ips.trace.updated.entity.content`, `ips.trace.skipped.entity`, `ips.trace.skipped.entity.content`, `ips.trace.failed.entity.content`, and `ips.trace.deleted.entity` properties. For more information, see: [List of Properties](../list-of-properties-d6f3577.md)

> ### Note:  
> Sending navigation links to the download page of created, updated, failed, skipped, and deleted entities is supported for tenants running on SAP Cloud Identity Services infrastructure.

> ### Note:  
> If you subscribe to a source system, and then run a successful provisioning job, no notification e-mails will be sent.



## Procedure

1.  Access the Identity Provisioning UI and choose the *Source Systems* tile.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Select the system you need to watch and choose *Jobs*.

    > ### Note:  
    > Notifications are supported only for read and resync jobs.

4.  Choose *Subscribe*.

    -   To subscribe yourself, choose *Subscribe me*.
    -   To subscribe another user or a group \(distribution list\), choose *Subscribe others*. Fill in the required fields and choose ![](../Operation-Guide/images/IPS_Add_Icon_711b870.png)*Add*.

        > ### Note:  
        > From the *Recipients* list, you can remove existing subscribers. To do that, go to the *Action* column and choose the ![](../Operation-Guide/images/Unsubscribe_User_21262b8.png) icon.


5.  You can now run or schedule a provisioning job.

6.  If you no longer need to be subscribed to a source system, choose *Subscribe* \> *Unsubscribe me*.


**Related Information**  


[Monitor Provisioning Job Logs](monitor-provisioning-job-logs-e5b5176.md "Job logs display information about the execution of provisioning jobs. Each row in the list of job logs shows information about one execution of a job.")

