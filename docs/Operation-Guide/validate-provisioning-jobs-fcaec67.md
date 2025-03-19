<!-- loiofcaec6787c6745a2bd0175c3df345bb6 -->

# Validate Provisioning Jobs

You can validate a provisioning job before you actually run it.



<a name="loiofcaec6787c6745a2bd0175c3df345bb6__prereq_qn1_qnw_ytb"/>

## Prerequisites

-   You have enabled the source system where you want to run the validate job from.

-   You have created separate CSV input files for validating users and groups.


> ### Note:  
> This functionality is available only for Identity Provisioning tenants running on SAP Cloud Identity infrastructure.



<a name="loiofcaec6787c6745a2bd0175c3df345bb6__context_z4p_g2r_jvb"/>

## Context

The validate job allows you to test how entities \(users and groups\) would be mapped from source to target systems before you run the actual provisioning job. You can use it to validate both - default and modified transformations, and see what would be the expected result in the target system.

Like the simulate job, the validate job predicts results in the target system without modifying it. However, unlike the simulate job \(which estimates the number of entities that will be created, updated, deleted or skipped\), the validate job verifies the content of the entities. For example, you can use it in the following cases:

-   You want to run your first provisioning job from system A to system B and see what will be the result when the default transformations are applied.

-   You have modified the `sourcePath` or the `targetPath` attributes in the transformations and you want to see how they will be mapped in the target system. For example, instead of populating the username in SAP Analytics Cloud target system with the email, you want to provision the username itself:


    <table>
    <tr>
    <th valign="top">

    Default Mapping
    
    </th>
    <th valign="top">

    Changed Mapping
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    > "sourcePath": "$.emails[0].value",
    > "targetPath": "$.userName"
    > },
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    > "sourcePath": "$.userName",
    > "targetPath": "$.userName"
    > },
    > ```


    
    </td>
    </tr>
    </table>
    
-   You want to test if conditions are met or if all required user and group attributes are available


To run a validate job, you need to import one or two CSV files - one for users and/or one for groups. Each file must contain a maximum of 10 users or groups with attributes as defined in the source system. The attribute names must use the JSONPath dot-notation. For example: `emais[0].value` attribute indicating the value of the first email within an email array, or `name.familyName` - a complex `name` attribute containing a `familyName` sub-attribute. If the file has more than 10 users or groups, the job will validate the first 10 and will ignore the rest.

You can create a CSV file using a text editor, for example Notepad. Make sure the number of fields match the number of headers in the file. Otherwise, you will get an error when importing the file and won't be able to proceed until you correct it.

> ### Example:  
> The following example illustrates that the number of fields does not match the number of headers \(columns 1 to 5\) at row 3.
> 
> ```
> col1,col2,col3,col4,col5
> A,B,,D,E
> L,M,N,,
> P,Q,
> ```

> ### Example:  
> The following example illustrates how to validate two users with attributes defined in the MS Entra ID source system.
> 
> ```
> userPrincipalName,id,mail,givenName,surname,groups[0].value,groups[1].value
> ChrisEvans,ec2c28da-a9fe-46c9-876e-564317f9a3af,chris@example.com,Christopher,Evans,Employee,Support
> MaryWatson,b016ecad-2c30-4fdf-8fb3-117db4911256,mary@example.com,Mary,Watson,Employee,Developer
> ```

For more information on how to create the CSV files and end-to-end examples, see the blog post [After simulation, try out validation. Identity Provisioning closes the loop with a fresh new test job.](https://blogs.sap.com/2022/11/23/after-simulation-try-out-validation.-identity-provisioning-closes-the-loop-with-a-fresh-new-test-job./?url_id=text-global-profile-inbox-bp-new-in-tag-followed)

The validate job is triggered manually. There is no option to schedule it. Proceed as follows:



<a name="loiofcaec6787c6745a2bd0175c3df345bb6__steps_qnk_bsr_jvb"/>

## Procedure

1.  Open the source system and choose the *Jobs* tab.

2.  For *Validate Job*, choose *Run Now*.

3.  In the *Import Entities* dialog box, browse for and select the CSV files for testing users and groups.

    You can import and validate one of the files or both.

4.  Choose *Validate*.




<a name="loiofcaec6787c6745a2bd0175c3df345bb6__result_s1p_f5r_jvb"/>

## Results

The result of a validate job is not displayed in the Job Logs, as it is with the read, resync and simulate jobs. It is provided in a downloadable ZIP file. Each administrator who runs the validate job, can see only his or her test results.

The ZIP file contains one or more CSV files, and a trace.log file in case the validation job identified failed or skipped entities. You can expect the following zipped files: one for each of the entities \(users and groups\) you have tested, and one for each of the target systems connected to the source system where you run the job from.

For example, if you have tested users and groups from source system A, which is connected to three target systems B, C, and D, expect a ZIP file with six CSV files.

If the result of a validate job is not what you have expected or finished with errors and skipped entities, you can identify where the wrong configurations or missing values come from and correct them.

