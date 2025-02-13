<!-- loiod6acc19a031e403ca66f5d82b908c4c2 -->

# Entity Deletion Issues

Learn how to troubleshoot the most frequent reasons for deletion of users or groups from a target system by the Identity Provisioning.

In the scenarios described below, the entity is already provisioned by the Identity Provisioning via a provisioning job for that particuar source and target systems pair. The deletion of entities happens at the end of the provisioning job, after all users and groups are read and processed.

Since the topic is focused on occurrences of entity deletion, it does not cover cases in which this is not expected, for example, when the provisioning job:

-   has been run in a delta read mode;
-   has failed entities for the source system;
-   has an irreparable error for the source system;
-   has irreparable errors for all target systems, which the job has to provision to.

It is important to clarify that even if an entity was existing in the target system before its provisioning for the first time, it could still be deleted by the Identity Provisioning if the property `ips.delete.existedbefore.entities` is set to *true* in the target system. However, if the entity is created in the target system by provisioning in the first place, then the service is allowed to delete it \(unless `“skipOperations”:[“delete”]` is present in the transformation of the target system or there is a threshold set for deletion of entities from the target system\).

Search among the most frequent causes for entity deletion by the Identity Provisioning and learn what should be checked to make sure that this is the situation you run into:



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_k4m_xjd_zdc"/>

## The Entity is Deleted From the Source System or Re-Created with a New ID

Access the audit logs for the source system and check for the deletion of the entity and eventually its re-creation with a new ID. If there is an audit log for deletion, it should span the period before the provisioning job that deleted the entity was run.

Bellow you can find an exemplary audit log for deleted user from an Identity Authentication source system:

```
category=audit.data-change
crtAccount=<IAS tenant ID>
action=delete
objectType=user
objectId=<the SCIM ID of the deleted user in IAS>
```

For more information, see [Audit Logs](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/audit-logs?locale=en-US&version=Cloud).



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_a3f_nrd_zdc"/>

## Entity is not Returned from the API of the Source System When a Read or a Resync Job has Performed the Deletion

In the *Job Execution Details* screen, compare the *Read* statistics for the job, which deleted the entity, and the previous job for the same source-target systems pair. If you download all job logs, these statistics are displayed as value of the `numberRead` attribute. Check also if the next provisioning job for the same source-target systems re-created the entity in the target system.

In case of further investigation needed, please contact the corresponding API experts.



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_b5n_sb2_zdc"/>

## Entity Does not Meet the Filtering Criteria Defined in the Source System Anymore

Check if there is a filtering property set in the provisioning source system \(`*.user.filter` or `*.group.filter`\). Then look through the entity details in the source system itself and evaluate if it meets the defined filter.

You can also check the audit logs from the source system for entity changes that lead to not meeting the filtering criteriar. The audit logs should span the period before the provisioning job that deleted the entity was run.

It could be possible that the entity temporary did not meet the defined filter. For exmaple, a user has became inactive in the source system and then active again after the job, which deleted it from the target system has finished.

In the *Job Execution Details* screen, compare the *Read* statistics for the job, which deleted the user or the group, and the previous job for the same source-target systems pair. If you download all job logs, these statistics are displayed as value of the `numberRead` attribute. Check also if the next provisioning job for the same source-target systems has re-created the entity in the target system.

Bellow you can find an exemplary audit log for updated user that was deleted from an Identity Authentication source system:

```
category=audit.data-change
crtAccount=<IAS tenant ID>
action=update
objectType=user
objectId=<the SCIM ID of the deleted user in IAS>
payload: […]
//each changed attribute has its “oldValue” and "newValue" displayed
```



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_i1r_pmf_zdc"/>

## The Filter Set in the Source System was Changed and the Entity is no Longer Read by the Identity Provisioning

First, you can check if the filter property set in the source system has been changed. To do so, check the audit logs for any manual changes of the provisioning source system. The audit logs should span the period before the provisioning job that deleted the user.

After that, in the *Job Execution Details* screen, compare the *Read* statistics for the job, which deleted the entity, and the previous job for the same source-target systems pair. If you download all job logs, these statistics are displayed as the value of `numberRead` attribute. Check also if the next provisioning job for the same source-target systems re-created the entity in the target system.

For example, in case your SAP Cloud Identity Services tenant is running on is SAP Cloud Identity Services Infrastructure, refer to [Access Audit Logs \(Audit Log Service in SAP BTP, Cloud Foundry\)](access-audit-logs-audit-log-service-in-sap-btp-cloud-foundry-a3e793c.md) for more information. The procedure should have been applied, before Identity Provisioning sends audit logs to the Audit Log service.

For example, in case you obtain standalone or bundle tenant on SAP BTP, Neo environmen, refer to [Access Audit Logs](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/0e272c800d264d90b519574fcb1e930e.html "You can access audit logs to track changes for events and activities in your Identity Provisioning tenant.") :arrow_upper_right: for more information. The procedure should have been applied, before Identity Provisioning sends audit logs to the Audit Log service.

Bellow you can find an exemplary audit log for updated filter of an Identity Authentication source system:

```
category=audit.configuration
crtAccount=<IPS tenant ID>
action=update
objectType=System
ObjectAttribute.system-old-details
ProvisioningSystem [id=<the ID of the provisioning system>, …, name=<the name of the provisioning system>, …]
ObjectAttribute.performed-by-user
ObjectAttribute.system-new-details

```

You can see the difference between `system-old-details` and `system-new-details` for exact changes in the source system. The changes in the filter are part of the `“properties={…}”` sections of the old and the new details for the system.



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_r2m_1sf_zdc"/>

## The Entity Does not Meet an Existing Condition in the Read Transformation Anymore

Start by checking what is the condition in the read transformation of the source system. Then check the entity details in the source system itself and if it meets the condition.

You can also check on the *Job Execution Details* screen if the next provisioning job displays the entity as skipped in the statistics of the source system. You can download the job log for skipped entities and search for the entity in the downloaded file. For more information, see [Download All Skipped Entity Logs for a Single Job](manage-provisioning-job-logs-041b5ff.md#loio041b5ff608b944d19c53be780109506e__section_wvx_x4p_2tb).

It could be possible that the entity temporary did not meet the defined condition only while the job, which deleted it from the target system was running. You can see audit logs from the source system for entity changes that lead to not applying to the condition. The audit logs should span the period before the provisioning job that deleted the entity was run.

For example, if a user is skipped, in the downloaded skipped entities job log you will see a similar content:

```
user:<user ID>,

system=<system name>,
skip reason=Entity condition [($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)] is not fulfilled
//the skip reason could contain a different condition, but the sentence is “Entity condition… is not fulfilled
```

In case you need to check audit logs, because the entity did not meet the condition only while one provisioning job was running, then for Identity Authentication source system, see [Audit Logs](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/audit-logs?locale=en-US&version=Cloud). The procedure should have been applied, before Identity Provisioning sends audit logs to the Audit Log service.

Find bellow an exemplary content of an audit log for update of a user in an Identity Authentication source system that caused not meeting the defined condition:

```
category=audit.data-change
crtAccount=<IAS tenant ID>
action=update
objectType=user
objectId=<the SCIM ID of the updated user in IAS>
payload: […] 
//each changed attribute has its old and new values displayed (“oldValue” and “newValue”)

```



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_cxz_jwf_zdc"/>

## The Entity Does not Meet an Existing Condition in the Target System Anymore

Start by checking what is the condition in the write transformation of the target system. Then check the entity details in the source system itself. Consider the transformation of the source system and how the values of the attributes are mapped to each `targetPath` there. Then, evaluate if the entity meets the condition set in the target system.

For example, if the user attribute for email in the source system is `email`, and there is a similar mapping in the transformation of the source system:

```
{
“sourcePath”: “$.email”,
“targetPath”: “$.emails[0].value”
}

```

And the condition in the target system using the email is the following:

```
"condition":"$.emails[0].value =~ /.*@domain.com/”,
//this condition checks if the email is on a particular domain
```

Then you should validate that the value of the user's attribute `email`

You can also check if the next provisioning job for the same source-target systems show the user as skipped in the statistics of the target system. You can download the job log for skipped entities and search for the entity in the downloaded file. For more information, see [Download All Skipped Entity Logs for a Single Job](manage-provisioning-job-logs-041b5ff.md#loio041b5ff608b944d19c53be780109506e__section_wvx_x4p_2tb).

It could be possible that the entity temporary did not meet the defined condition only while the job, which deleted it from the target system was running. You can see audit logs from the source system for entity changes that lead to not applying to the condition. The audit logs should span the period before the provisioning job that deleted the entity was run.

For example, if a user is skipped due to this reason, the downloaded skipped entities job log will include similar content:

```
user:<user ID>,
system=<system name>,
skip reason=Entity condition [($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)] is not fulfilled
//the skip reason may contain a different condition, but the sentence is 'Entity condition… is not fulfilled'
```

In case you need to check audit logs, because the entity did not meet the condition only while one provisioning job was running, then for Identity Authentication source system, see [Audit Logs](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/audit-logs?locale=en-US&version=Cloud). The procedure should have been applied, before Identity Provisioning sends audit logs to the Audit Log service.

Find bellow an exemplary content of an audit log for update of a user in Identity Authentication source system that caused not meeting the set condition:

```
category=audit.data-change
crtAccount=<IAS tenant ID>
action=update
objectType=user
objectId=<the SCIM ID of the updated user in IAS>
payload: […]
//each changed attribute has its old and new values displayed (“oldValue” and “newValue”)

```



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_xmd_szh_12c"/>

## The Entity does not Meet a new Condition in the Source System

In that case, the entity is skipped after the Identity Provisioning reads it from the source system and it is deleted from the target.

You can check the transformation history and whether the condition in the read transformation was changed.

You can also check if the next provisioning job for the same source-target systems show the entity as skipped in the statistics of the target system. You can download the job log for skipped entities and search for the entity in the downloaded file. For more information, see [Download All Skipped Entity Logs for a Single Job](manage-provisioning-job-logs-041b5ff.md#loio041b5ff608b944d19c53be780109506e__section_wvx_x4p_2tb).

It could be possible that the entity temporary did not meet the defined condition only while the job, which deleted it from the target system was running. You can see audit logs from the source system for entity changes that lead to not applying to the condition. The audit logs should span the period before the provisioning job that deleted the entity was run.

For example, if a user is skipped due to this reason, the downloaded skipped entities job log will include similar content:

```
user:<user ID>,

system=<system name>,
skip reason=Entity condition [($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)] is not fulfilled
//the skip reason may contain a different condition, but the sentence is 'Entity condition… is not fulfilled'

```

In case you need to check audit logs, because the entity did not meet the condition only while one provisioning job was running, then for Identity Authentication source system, see [Audit Logs](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/audit-logs?locale=en-US&version=Cloud). The procedure should have been applied, before Identity Provisioning sends audit logs to the Audit Log service.

Find bellow an exemplary content of an audit log for update of a user in an Identity Authentication source system that caused not meeting the set condition:

```
category=audit.data-change
crtAccount=<IAS tenant ID>
action=update
objectType=user
objectId=<the SCIM ID of the updated user in IAS>
payload: […]
//each changed attribute has its old and new values displayed (“oldValue” and “newValue”)

```



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_aql_cm3_12c"/>

## The Entity does not Meet a new Condition set in the Target System

In that case, the entity is skipped during the provisioning to the target system and is deleted from it.

You can check the transformation history and whether the condition in the transformation of the target system was changed. After that check the entity details in the source system itself. Consider the transformation of the source system and how the values of the entity attributes are mapped to each `“targetPath”` in the target system. Then, validate if the entity does not apply to the condition in the target system based on the mappings in the transformation of the source system and the values of the entity attributes in the source system.

For example, if the user attribute for email in the source system is `email`, and there is a mapping in the transformation of the source system like the following:

```
{
“sourcePath”: “$.email”,
“targetPath”: “$.emails[0].value”
}

```

If the condition in the target system using the `email` is the following:

```
“condition”: “$.emails[0].value =~ /.*@domain.com/”,
//checks if the email ends with the specified domain
```

Then validate that the value of the user attribute `email` in the source system ends with the specified domain in the condition of the target system.

You can also check if the next provisioning job for the same source-target systems show the entity as skipped in the statistics of the target system. You can download the job log for skipped entities and search for the entity in the downloaded file. For more information, see [Download All Skipped Entity Logs for a Single Job](manage-provisioning-job-logs-041b5ff.md#loio041b5ff608b944d19c53be780109506e__section_wvx_x4p_2tb).

It could be possible that the entity temporary did not meet the defined condition only while the job, which deleted it from the target system was running. You can see audit logs from the source system for entity changes that lead to not applying to the condition. The audit logs should span the period before the provisioning job that deleted the entity was run.

If a user is skipped for not meeting the set condition in the target system, it will be seen in the downloaded skipped entities job log like:

```
user:<user ID>,

system=<system name>,
skip reason=Entity condition [($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)] is not fulfilled

//the skip reason could contain a different condition, but the sentence is 'Entity condition… is not fulfilled'

```

In case you need to check audit logs, because the entity did not meet the condition only while one provisioning job was running, then for Identity Authentication source system, see [Audit Logs](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/audit-logs?locale=en-US&version=Cloud). The procedure should have been applied, before Identity Provisioning sends audit logs to the Audit Log service.

Find bellow an exemplary content of an audit log for update of a user in an Identity Authentication source system that caused not meeting the set condition in the target system:

```
category=audit.data-change
crtAccount=<IAS tenant ID>
action=update
objectType=user
objectId=<the SCIM ID of the updated user in IAS>
payload: […] 
// each changed attribute has its old and new values displayed (“oldValue” and “newValue”)

```



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_yl1_q43_12c"/>

## Changed Mapping for `"entityIdTargetSystem"` or `"entityIdTargetSystem"` in the Transformation of the Source or Target System Without System Reset

This issue occures most frequently, but not only, while changing the version of the provisioning system, because of the different versions of the delault transformations used. The symptom is mass entity update and mass entity deletion of the same entities in the target system.

If you think that this is probably your case, check the transformation history for changes in the mapping for one of the variables `"entityIdSourceSystem"` \(part of the transformation of the source system\) or`"entityIdTargetSystem"` \(part of the transformation of the target system\). Then, check in the audit logs whether a reset was performed for the provisioning system, in which one of the above mentioned variables was changed. The audit logs should span the period before the provisioning job that deleted the entity was run.

For example, in case your SAP Cloud Identity Services tenant is running on is SAP Cloud Identity Services Infrastructure, refer to[Access Audit Logs \(Audit Log Service in SAP BTP, Cloud Foundry\)](access-audit-logs-audit-log-service-in-sap-btp-cloud-foundry-a3e793c.md) for more information. The procedure should have been applied, before Identity Provisioning sends audit logs to the Audit Log service.

For example, in case you obtain standalone or bundle tenant on SAP BTP, Neo environmen, refer to [Access Audit Logs](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/0e272c800d264d90b519574fcb1e930e.html "You can access audit logs to track changes for events and activities in your Identity Provisioning tenant.") :arrow_upper_right: for more information. The procedure should have been applied, before Identity Provisioning sends audit logs to the Audit Log service.

Bellow you can find an exemplary audit log for system reset of an Identity Authentication source system:

```
category=audit.configuration
crtAccount=<IPS tenant ID>
action=update
objectType=System
ObjectAttribute.event-type=SYSTEM_RESET
ObjectAttribute.performed-by-user
ObjectAttribute.system-id=<the ID of the provisioning system>

```

If the provisioning system was reset, this has not caused the entity deletion.

If the provisioning system was not reset but one of the above mentioned variables was changed, that caused the entities deletion.



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_irz_yr3_12c"/>

## Removed `"delete"` Operation from skipOperations Expression or the skipOperations Expression Itself from the Transformation of the Target System

All entities, which were due to be deleted from the target system while skip of `"delete"` operation was present, were reported in previous jobs as skipped. As a result from removing the `"delete"` operation or the entire skipOperations expression, they can now be deleted from the target system by the Identity Provisioning.

In that case, you can compare the skipped statistics of the job, which deleted the entities, and the previous job for the same source-target systems. If you download all job logs, these statistics are shown in the value of `“numberSkipped”` attribute. The skipped statistics should be checked for the target system, where the entity was deleted from. You can also download the job log for skipped entities of both jobs \(the one that deleted the entity from the target system and the previous one\) and find the entity in the downloaded file of the older job. For more information, see [Download All Skipped Entity Logs for a Single Job](manage-provisioning-job-logs-041b5ff.md#loio041b5ff608b944d19c53be780109506e__section_wvx_x4p_2tb).

You can also check the transformation history and whether the skipOperations expression contained `“delete”` before the provisioning job that deleted the entity from the target system was triggered.

If a user was skipped due to this reason, it will be seen in the downloaded skipped entities job log like:

```
user:<user ID>,

system=<target system name>,
skip reason=Operation [delete] is skipped in target transformation,

```



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_wlk_s53_12c"/>

## Single or Mass Entity Deletion Because the Entityes Were not Deleted Earlier

Single, or more likely mass entity deletion is possible if any of the cases described above has occured in a previous provisioning job, but that job did not delete the entities from the target system due to an error.

Some of these errors could be:

-   failed entities for the source system
-   irreparable issue during provisioning, like a connection issue, which stopped the job before it reached the point of deletion of the entities
-   delete operation failure
-   other

As a result, the entities are accumulated to be delete from the target system by a next provisioning job, which will try again to delete them \(for example, when some of the reasons listed above are no longer happening\).

You can start the investigation by checking the job logs, statistics, and job error logs of the provisioning jobs prior the one that deleted the entities. For more information, see [Manage Provisioning Job Logs](manage-provisioning-job-logs-041b5ff.md).

A proof that you have run into some of the listed sitiations can be:

-   If there were failed entities for the source system in the previous jobs, and then there were no failed entities for the source system in the job, which deleted the users from the target system.
-   If there were some irreparable errors for the source system or for the target system \(where the entities were deleted from\) in the previous jobs, and then there were no such irreparable errors in the job, which deleted the entities from the target system. Irreparable errors are connection issues, like connection reset, some timeout exception, rate limits \(response code 429 from the API of a provisioning system\), and others.
-   If there were failed entities for the target system in the previous jobs, the failures were for the entities that got deleted later from the target system, and the error job logs show failed delete operation.

    For example, if a user deletion failed, it will be displayed in the downloaded error job log as follows:

    ```
    user:<user ID>,
    system=<system name>,
    time=<time error happened>
    error=<the error details>
    content=null
    
    ```


As a last step, you can analyze the job logs of the previous jobs for some issues or patterns, which are not observed in the job, which deleted the entities from the target system.



<a name="loiod6acc19a031e403ca66f5d82b908c4c2__section_r2v_vdp_12c"/>

## How to Prevent Incorrect Entity Deletion in These Cases

By following some of the hins bellow you can avoid unintended deletion of entities from your target systems:

-   Add the standard property `ips.delete.threshold.users` \(or`ips.delete.threshold.groups` for groups\) to your target system configuration before running a provisioning. For more information, see the blog [Thresholds Prevent Unintended Deletion of Users when Provisioning with SAP Cloud Identity Services](https://community.sap.com/t5/technology-blogs-by-sap/thresholds-prevent-unintended-deletion-of-users-when-provisioning-with-sap/ba-p/13584176).
-   Migrate your Identity Provisioning tenant from SAP BTP Neo environment to SAP Cloud Identity Infrastructure, where you will be able to use more features \(like the validate job, seeing skipped entities for a job execution, and many others\). For more information, see the blog [Go for your quick win! Migrate Identity Provisioning tenants to SAP Cloud Identity infrastructure.](https://community.sap.com/t5/technology-blogs-by-sap/go-for-your-quick-win-migrate-identity-provisioning-tenants-to-sap-cloud/ba-p/13536739)
-   Always execute a validate job first, after doing a change in the transformation or properties of a provisioning system. For more information, see the blog [Simulate it until you make it! Try out the Identity Provisioning job that tests your configuration.](https://community.sap.com/t5/technology-blogs-by-sap/simulate-it-until-you-make-it-try-out-the-identity-provisioning-job-that/ba-p/13531750)
-   Follow all steps of the process for updating the connector version, decribed in [Update Connector Version](../Operation-Guide/update-connector-version-8558733.md).

**Related Information**  


[Administration Issues](administration-issues-90ce2d5.md "")

[Job and Transformation Issues](job-and-transformation-issues-dbe3c08.md "")

[Error Messages](error-messages-ad525a4.md "")

[Additional Information](additional-information-7463572.md "")

[Handling Specific Attributes](handling-specific-attributes-e957782.md "")

