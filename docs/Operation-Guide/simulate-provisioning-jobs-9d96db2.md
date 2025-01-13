<!-- loio9d96db2322494790a6d8582dd4d09deb -->

# Simulate Provisioning Jobs

You can simulate a provisioning job before you actually run it.



<a name="loio9d96db2322494790a6d8582dd4d09deb__prereq_qn1_qnw_ytb"/>

## Prerequisites

> ### Note:  
> This functionality is available only for Identity Provisioning tenants running on SAP Cloud Identity infrastructure.

The source system where you run the job must be enabled.



## Context

Simulating a provisioning job allows you to test your Identity Provisioning configurations and see whether they produce the desired result in the target system. In case the result is not what you have expected, you can identify the wrong configurations and correct them before you run the actual provisioning job.

The simulate job reads the data from the source system, applies the source and target system transformation and provides the expected results of a resync job without actually modifying the target system. The simulation is based on the Identity Provisioning operational data from previously provisioned entities using the same source and target system configurations.

Run this job whenever you change filtering properties, apply conditions or modify attribute mappings in the transformation code of a source and/or target system because these changes affect the data you want to provision. As a result, in the *Job Execution Logs* screen, you will see an estimation of the numbers of users and groups that will be created, updated, deleted or skipped in the target system.

Note that, if some of the entities already exists on the target system, the simulation won’t detect them. In such cases during the real provisioning Identity Provisioning will detect them and try to update them, so they may appear as updated entities. The simulation can detect some wrong attribute mappings as missing attributes that are defined as required in the transformation. However, it cannot predict errors that may occur on the target system as duplicate identifiers or not supported values.

Proceed as follows:



## Procedure

1.  Open the source system and choose the *Jobs* tab.

2.  Choose *Run Now* for the *Simulate Job*.

3.  Open the *Job Execution Logs* and verify the provisioned entities.




<a name="loio9d96db2322494790a6d8582dd4d09deb__result_oqv_dgb_ztb"/>

## Results

If the number of created, updated, deleted or skipped entities is what you have expected, run the read or resync job.

If the number of created, updated, deleted or skipped entities is not what you have expected, correct your configurations and run the simulate job again.

**Related Information**  


[**Blog Post**: Simulate it until you make it! Try out the Identity Provisioning job that tests your configuration.](https://blogs.sap.com/2022/07/29/simulate-it-until-you-make-it-try-out-the-identity-provisioning-job-that-tests-your-configuration./comment-page-1/#comment-633289)

