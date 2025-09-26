<!-- loiodbe3c08ebe7c47fb98422680c6580cc0 -->

# Job and Transformation Issues

You have a struggle with a transformation, a property or a provisioning job?

Find your particular problem below:



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_zxc_5sg_qbc"/>

## Entities Are Not Updated or Deleted in the Target System

When you set up your systems and start a manual or scheduled provisioning job, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. You can also choose to optimize the amount of retrieved data and read only the updated entities \(new, updated, deleted\). For more information about these modes, see [Manage Full and Delta Read](../Operation-Guide/manage-full-and-delta-read-b7f817c.md).

To keep source and target systems completely synchronized, you can use the **Resync** type of provisioning job.

In some cases though, specific entities should be updated or deleted, but during the provisioning job they are not read at all. They are therefore not updated in the target system.



### Entities Are Not Updated

**Problem:**

1.  Run a provisioning job \(manual or scheduled\).

2.  The job finishes successfully but some entities have not been updated.


**Reason:**

You might have set special conditions or expressions in your transformations.

**Solution:**

1.  Make sure that no special conditions or expressions \(ignore or skipOperations\) are set in the JSON transformation.

2.  Run again a **Read** or **Resync** provisioning job.

3.  Check to see if the relevant entities have been updated in the target system.


**Entities are Still Not Updated in the Target System**

If your problem requires deeper analysis by SAP, please create an incident for component BC-IAM-IPS.

In the incident, specify also:

-   The IDs of your global account and subaccount, or your bundle tenant.

-   To which region your account/tenant belongs. You can find it in this list:[\(Discovery Center\) Identity Provisioning](https://discovery-center.cloud.sap/index.html#/serviceCatalog/identity-provisioning) -\> *Service Plan*


Before you create a support case, read:

[2654164 - What to consider before opening a Support Ticket for SAP Business Technology Platform](https://launchpad.support.sap.com/#/notes/2654164)

For contract-related questions, read:

[1660069 - How to contact SAP Contracts Department for questions or issues](https://launchpad.support.sap.com/#/notes/1660069) 



### Entities Are Not Deleted

**Problem**

Your business case requires you to delete some entities \(users or groups\) from both the source and the target system. You proceed as follows:

1.  Delete these entities from the source system.

2.  Run a provisioning job \(manual or scheduled\).


As a result, the job finishes either **successfully** or **with error**, and in both cases - the relevant entities are not deleted from the target system.

**Job is successful but entities are not deleted**

**Problem**

You have deleted some entities from the source system, and then run a provisioning job.

The job finishes successfully but the relevant entities have not been deleted from the target system.

**Reason**

You either have set special conditions in your transformations, or have missed to add the`ips.delete.existedbefore.entities` property in your target system configuration.

> ### Note:  
> If the property `ips.delete.existedbefore.entities` has not been added before the job attempting the deletion is run, adding it later will not resolve the problem.

**Solution**

Resolving this issue depends on whether you have added the`ips.delete.existedbefore.entities` property in your target system before or after running the job attempting the deletion.

The property is added before running the provisioning job:

1.  Make sure that no special conditions or expressions are set in the target transformation. That includes: *ignore expression*, *skipOperations* \(skipping delete\), or *deleteEntity* scope.

2.  Run a **Read** or **Resync** provisioning job.

3.  Check if the relevant entities have been deleted from the target system.


The property is added after running the provisioning job:

If the property is added after the provisioning job finished successfully, entities recognized as "previously existed ones" cannot be deleted from the target system anymore. In this case, you need to delete them from the target system \(for example, manually or via script\).

For more information on how to properly delete entities in the target system, see [Manage Deleted Entities](../Operation-Guide/manage-deleted-entities-3d6bdf1.md).

**EntitiesAre Still Available in the Target System**

If your problem requires deeper analysis by SAP, please create an incident for component **BC-IAM-IPS**.

In the incident, specify also:

-   The IDs of your global account and subaccount, or your bundle tenant.

-   To which region your account/tenant belongs. You can find it in this list:[\(Discovery Center\) Identity Provisioning](https://discovery-center.cloud.sap/index.html#/serviceCatalog/identity-provisioning) -\> *Service Plan*


Before you create a support case, read:

[2654164 - What to consider before opening a Support Ticket for SAP Business Technology Platform](https://launchpad.support.sap.com/#/notes/2654164)

For contract-related questions, read:

[1660069 - How to contact SAP Contracts Department for questions or issues](https://launchpad.support.sap.com/#/notes/1660069) 



### Job finishes with error and entities are not deleted

**Problem**

You have deleted some entities from the source system. You have not set any special conditions or expressions \(*ignore*, *skipOperations*, or *deleteEntity* scope\) in the target transformation. You have set property`ips.delete.existedbefore.entities` to *true* in the target system, and then run a provisioning job.

The job finishes with error, and the relevant entities have not been deleted from the target system.

**Reason**

In the job log, you see that there are failed entities when the job has tried to read them from the source system.

**Solution**

1.  Resolve the failed entities in the source system.

2.  Run again a **Read** or a **Resync** provisioning job.

3.  Check if the relevant entities have been deleted from the target system.


**Entities Are Still Available in the Target System**

If your problem requires deeper analysis by SAP, please create an incident for component **BC-IAM-IPS**.

In the incident, specify also:

-   The IDs of your global account and subaccount, or your bundle tenant.

-   To which region your account/tenant belongs. You can find it in this list:[\(Discovery Center\) Identity Provisioning](https://discovery-center.cloud.sap/index.html#/serviceCatalog/identity-provisioning) -\> *Service Plan*


Before you create a support case, read:

[2654164 - What to consider before opening a Support Ticket for SAP Business Technology Platform](https://launchpad.support.sap.com/#/notes/2654164)

For contract-related questions, read:

[1660069 - How to contact SAP Contracts Department for questions or issues](https://launchpad.support.sap.com/#/notes/1660069) 



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_nrt_rxx_rbc"/>

## Entities Should Not Be Deleted in the Target System

**Problem & Reason**

The default behavior of the Identity Provisioning service is:

1.  It reads entities from a source system and provisions \(writes\) them in a target system.

2.  If, on a next reading job, the service detects that some previously existed entities are now missing, it considers them as **deleted** \(or not active anymore\).

3.  Thus, the next provisioning job \(Read or Resync\) deletes such entities from the target system.


However, these entities might still be existing and active but are not read because you have set a filter or condition for some business reason.

You**do not want** the "unread" entities \(the ones that do not fulfill the filter/condition\) to be deleted from the target.

**Solution**

To prevent deletion of existing active users in your target system, proceed as follows:

1.  Select your target system in the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services .

2.  Choose the *Transformations* tab and then *Edit*.

3.  If you want to keep existing/active users, in the user section, add the following mapping:

    > ### Sample Code:  
    > ```
    > {
    > 
    >  "constant": false,
    > 
    >  "targetPath": "$.active",
    > 
    >  "scope": "deleteEntity"
    > 
    >  }
    > ```


This way, every time you use a filter or a condition, only the relevant filtered entities \(users\) will be created or updated.

The rest users will remain as is - not updated but not deleted as well.

To learn more about this scope and see specific examples for SCIM systems, see: [Transformation Expressions](../transformation-expressions-bb8537b.md) *scope* \> *deleteEntity*.



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_zxp_4yx_rbc"/>

## Exclude Users from Provisioning to Target Systems

You want to know how to set up your provisioning scenario so that some users are not replicated to the target system based on given criteria.

Let’s assume the employees of your company \(with email domain `parentCompany.com`\) are stored in SAP SuccessFactors along with other users \(for example, contractors\). You want to replicate some of them toIdentity Authentication or SAP Analytics Cloud and exclude the rest \(with email domain `contractorsCompany.com`\) because they don’t need access to those systems to do their job.

For this, you need to specify a condition in the target system that is based on something common the users share, like their email domain.

Proceed as follows:

1.  In SAP SuccessFactors, verify that the users you want to exclude have email address.

    The user email is optional and may not be unique in SAP SuccessFactors. However, it's mandatory and unique in Identity Authentication and SAP Analytics Cloud.

2.  In the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services, select your target system and open its transformation in *Edit* mode.

    Identity Provisioning is embedded in SAP Cloud Identity Services admin console \(formerly known as Identity Authentication admin console\). If your Identity Provisioning tenant is running on SAP Cloud Identity infrastructure, you can configure and work with provisioning systems there.

3.  Depending on your scenario, add one of the following conditions within the user entity:

    > ### Sample Code:  
    > ```
    > {
    >     "user": {
    > 
    >         "condition": "!($.emails[0].value =~ /.*contractorsCompany.com/)",
    > 
    >         "mappings": [
    > ```

    Based on this condition, Identity Provisioning will provision only users that do not have email domain `contractorsCompany.com`. Users with this domain will be read from the source but will be skipped in the target system.

    > ### Sample Code:  
    > ```
    > {
    >     "user": {
    > 
    >         "condition": "$.emails[0].value!= 'user123@contractorsCompany.com' ",
    > 
    >         "mappings": [
    > ```

    Based on this condition, Identity Provisioning will provision only users that do not have the specified email. Users with this email will be read from the source but will be skipped in the target system. Use this condition in case the users you want to exclude have the same dummy email.

4.  \(Optional\) Run the **Simulate** job from the connected SAP SuccessFactors source system to verify that excluded users are skipped, therefore not provisioned. This test job is available for tenants running on SAP Cloud Identity infrastructure.
5.  If the **Simulate** job displays the expected result, run a provisioning job \(**Read** or **Resync**\).

    Adding a similar condition for excluding users is also applicable to other target systems.




<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_xvg_zzx_rbc"/>

## Ensure SAP S/4HANA Cloud Users are Replicated During Their Validity Period

You want to ensure that Identity Provisioning service replicates SAP S/4HANA Cloud users to the embedded SAP Analytics Cloud during their validity period.

This is handled by the following changed condition in the default read transformation of both - the standard \(manually created\) and the preconfigured \(automatically created\) SAP S/4HANA Cloud source systems in Identity Provisioning bundle tenants.

**Changed condition:**

> ### Sample Code:  
> ```
> {
> "user": {
> "condition": "($.user.validityPeriod.startDate <= '${currentDate}') && ($.user.validityPeriod.endDate > '${currentDate}')",
> "mappings": [
> ```

For comparison, the initial condition ensured that SAP S/4HANA Cloud users are replicated to the SAP Analytics Cloud during the validity of the *Employee* role of their business partner.

**Initial condition:**

> ### Sample Code:  
> ```
> {
> "user": {
> "condition": "($.validityPeriod.startDate <= '${currentDate}') && ($.validityPeriod.endDate > '${currentDate}')",
> "mappings": [ 
> ```

How to proceed:

1.  In the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services, open the transformation of your SAP S/4HANA Cloud source system and check the condition under the user entity.

    -   If the read transformation contains the changed condition, no action is required.

    -   If the read transformation contains the initial condition, replace it with the changed one.

        Alternatively, you can create a newSAP S/4HANA Cloud source system and configure it manually. The newly created system will contain the changed condition by default.


2.  Save your configurations.



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_on4_t1y_rbc"/>

## Ensure deleted SAP S/4HANA Cloud Users are Also Deleted in SAP Analytics Cloud

You want to ensure that users who were deleted in SAP S/4HANA Cloud source system will also be deleted in the embedded SAP Analytics Cloud target system.

This is handled by the `ips.delete.existedbefore.entities` property which is now set to *true* in the preconfigured SAP Analytics Cloud target system of the Identity Provisioning bundle tenants for SAP S/4HANA Cloud release 1911 or higher.

Initially, this property was not preconfigured in the SAP Analytics Cloud target system and had to be added manually.

How to proceed:

1.  In the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services, open the *Properties* tab of the embedded SAP Analytics Cloud target system and check if `ips.delete.existedbefore.entities` is set to*true.*

    -   If the property is set, no action is required.

    -   If the property is not set, add it and set it to *true*.

2.  Save your configurations.

> ### Note:  
> After successful user provisioning from SAP S/4HANA Cloud to SAP Analytics Cloud, if you delete users in SAP S/4HANA Cloud and want to provision the change \(that is, to delete them\) in the target system, you need to set the `ips.delete.existedbefore.entities=true` before running the job to delete the users in the target system. If you set it afterwards, the users won’t be deleted in SAP Analytics Cloud as they will be recognized as "previously existed ones". In this case, to have them deleted, you need to create an incident on component **LOD-ANA-OEM**.

For more information on the required sequence of steps for deleting users, see [Manage Deleted Entities](../Operation-Guide/manage-deleted-entities-3d6bdf1.md).



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_llb_mby_rbc"/>

## Groups Are Not Provisioned to the Target System

**Problem:**

1.  You have added a source and a target system in the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services. Both systems support provisioning of groups.

2.  You have correctly set up these systems. For the source one, you use the default group transformation.

3.  Start a provisioning job.

4.  View the job results.


In the target system, users are provisioned but groups are missing.

**Reason:**

In the source system transformations, group provisioning is disabled \(ignored\) by default.

**Solution:**

To enable group provisioning, manually change the *ignore* condition to:

> ### Sample Code:  
> ```
> "group": { 
>         "ignore": false, 
>         "mappings": [ 
>            {
> ...
> ```

> ### Sample Code:  
> Related Information:
> 
> [Transformation Expressions](../transformation-expressions-bb8537b.md)



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_rl4_tpk_wbc"/>

## Identity Authentication: Provisioned Users Can't Log On

In Identity Authentication target systems, the behavior of the provisioning jobs depends on the constant value set for `$.userType` \(in the JSON transformation\).

-   `"constant": "public"`

    This means that all passwords will be written by default in theIdentity Authentication. All provisioned users will therefore be able to successfully log into the administration console for SAP Cloud Identity Services.

-   `"constant": "employee"`

    In this case, the login behavior of the provisioned users depends on whether users have been created with or without a password, and where these passwords are stored. You therefore need to modify the target transformations accordingly in order for the users to successfully log in to the administration console for SAP Cloud Identity Services.

    Find your use case from the options below:




### Users Are Created Without a Password

This occurs in scenarios in whichIdentity Authentication acts as a proxy to delegate the authentication to a corporate identity provider.

**Solution** 

Open the Identity Authentication target system transformation and remove the`"constant": "39"` mapping below.

As a result, you should have:


<table>
<tr>
<th valign="top">

Identity Authentication \(SCIM API version 1\)

</th>
<th valign="top">

Identity Authentication \(SCIM API version 2\)

</th>
</tr>
<tr>
<td valign="top">

```
{
    "constant": "false",
    "targetPath": "$.sendMail",
    "scope": "createEntity"
},
{
    "constant": "true",
    "targetPath": "$.mailVerified",
    "scope": "createEntity"
},
{
    "constant": "disabled",
    "targetPath": "$.passwordStatus",
    "scope": "createEntity"
},

// Remove: 
{
    "constant": "39",
    "targetPath": "$.sourceSystem",
    "scope": "createEntity"
},

// Make sure you have this target path with "constant" set to "employee".
{
    "constant": "employee",
    "targetPath": "$.userType"
}, 
```



</td>
<td valign="top">

```
{
    "constant": false,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sendMail']",
    "scope": "createEntity"
},
{
    "constant": true,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
    "scope": "createEntity"
},
{
    "constant": "disabled",
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']",
    "scope": "createEntity"
},
// Remove the mapping starting with "constant": "<your-source-system-type-code>", if its value is set to 39.
// Alternatively, set "ignore" to true.
{
    "constant": 39,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    "scope": "createEntity",
    "ignore": true
},
// Remove this mapping. Alternatively, set "ignore" to true.
{
     "constant": "<your-source-system-id>",
     "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
     "scope": "createEntity",
     "ignore": true
}
// Make sure you have this target path with "constant" set to "employee".
{
    "constant": "employee",
    "targetPath": "$.userType"
},
```



</td>
</tr>
</table>

> ### Tip:  
> If you don't want to delete the `"constant": "39"` section from the transformation, you can configure the *Corporate User Store* in the administration console for SAP Cloud Identity Services so as to reuse the corporate passwords. To learn how, see: [Corporate User Store](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/461d71c148594608b9c8b6d016e0a0c5.html#loio2c3ede1d7c454b8a8f820248ee3b705c).

Related information: [Identity Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/target-identity-authentication?locale=en-US&version=Cloud)

**Users Still Cannot Log on**

Your problem requires deeper analysis by SAP. Please create an incident for component BC-IAM-IPS.

In the incident, specify also:

-   The IDs of your global account and subaccount, or your bundle tenant.

-   To which region your account/tenant belongs. You can find it in this list:[\(Discovery Center\) Identity Provisioning](https://discovery-center.cloud.sap/index.html#/serviceCatalog/identity-provisioning) -\> *Service Plan*


Before you create a support case, read:

[2654164 - What to consider before opening a Support Ticket for SAP Business Technology Platform](https://launchpad.support.sap.com/#/notes/2654164)

For contract-related questions, read:

[1660069 - How to contact SAP Contracts Department for questions or issues](https://launchpad.support.sap.com/#/notes/1660069) 



### Passwords Are Stored in Corporate User Store

In this case, users are authenticated by Corporate User Store. This is relevant to scenarios that require integration with Cloud Connector. The source system can be AS ABAP, Microsoft Active Directory, or LDAP.

**Solution** 

Open the Identity Authentication target system transformation. For mapping `"targetPath": "$.passwordStatus"`, change `"constant": "disabled"` to `"enabled"`.

Also, if using Identity Authentication \(SCIM API version 2\), set the value of the `"constant": "<your-source-system-type-code>",` mapping to `39` and set your source system identifier in `"constant": "<your-source-system-id>"`.

As a result, you should have:


<table>
<tr>
<th valign="top">

Identity Authentication \(SCIM API version 1\)

</th>
<th valign="top">

Identity Authentication \(SCIM API version 2\)

</th>
</tr>
<tr>
<td valign="top">

```
{
    "constant": "false",
    "targetPath": "$.sendMail",
    "scope": "createEntity"
 },
 {
    "constant": "true",
    "targetPath": "$.mailVerified",
    "scope": "createEntity"
 },
 {
"constant": "enabled",
    "targetPath": "$.passwordStatus",
    "scope": "createEntity"
 },
 {
    "constant": "39",
    "targetPath": "$.sourceSystem",
    "scope": "createEntity"
 },
// Make sure you have this target path with "constant" set to "employee".
{
 "constant": "employee",
 "targetPath": "$.userType"
 },
```



</td>
<td valign="top">

```
{
    "constant": false,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sendMail']",
    "scope": "createEntity"
},
{
    "constant": true,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
    "scope": "createEntity"
},
{
"constant": "enabled",
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']",
    "scope": "createEntity"
},
// Set the value of the "constant": "<your-source-system-type-code>", mapping to 39.
// Make sure "ignore" is set to false. 
{
    "constant": 39,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    "scope": "createEntity",
    "ignore": false
},

// Set the value of the "constant": "<your-source-system-id>", mapping.
// Make sure "ignore" is set to false.
{
     "constant": "<your-source-system-id>",
     "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
     "scope": "createEntity",
     "ignore": false
}
// Make sure you have this target path with "constant" set to "employee".
{
    "constant": "employee",
    "targetPath": "$.userType"
}, 
```



</td>
</tr>
</table>

Related information: [Identity Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/target-identity-authentication?locale=en-US&version=Cloud)



### Passwords Are Stored in Identity Authentication \(initial password\)

This use case requires creating an initial password. Users will enter it on their logon to the Identity Authentication service. They can later change this password.

**Solution** 

In the Identity Authentication target system transformation, modify the following JSON mappings:

-   For `"$.passwordStatus"`, set "constant" to `"initial"`
-   Enter an additional mapping, starting with `"constant": "<initial password defined by customer>"`. Replace `"<initial password defined by customer>"` with an actual initial password.

    In Identity Authentication \(SCIM API version 2\), the mapping, starting with `"constant": "<your-initial-password>"`, is part of the default transformation. You only need to replace `<your-initial-password>` with an actual initial password and set `"ignore": "true"` to `"false"`.


-   Remove the mapping in bold below.

As a result, you should have:


<table>
<tr>
<th valign="top">

Identity Authentication \(SCIM API version 1\)

</th>
<th valign="top">

Identity Authentication \(SCIM API **version 2**\)

</th>
</tr>
<tr>
<td valign="top">

```
{
    "constant": "initial",
    "targetPath": "$.passwordStatus",
    "scope": "createEntity"
},

{
    "constant": "<initial password defined by customer>",
    "targetPath": "$.password",
    "scope": "createEntity"
},
{
    "constant": "false",
    "targetPath": "$.sendMail",
    "scope": "createEntity"
},
{
    "constant": "true",
    "targetPath": "$.mailVerified",
    "scope": "createEntity"
},
// Make sure you have this target path with "constant" set to "employee".
{   "constant": "employee",
    "targetPath": "$.userType"
},

// Remove this mapping:
{
    "constant": "39",
    "targetPath": "$.sourceSystem",
    "scope": "createEntity"
},
```



</td>
<td valign="top">

```
{
    "constant": "initial",
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']",
    "scope": "createEntity"
},
{
    "constant": "<your-initial-password>",
    "targetPath": "$.password",
    "scope": "createEntity",
    "ignore": "false"
},
{
    "constant": false,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sendMail']",
    "scope": "createEntity"
},
{
    "constant": true,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
    "scope": "createEntity"
},
// Remove the mapping starting with "constant": "<your-source-system-type-code>", if its value is set to 39.
// Alternatively, set "ignore" to true.
{
    "constant": 39,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    "scope": "createEntity",
    "ignore": true
},

// Remove this mapping. Alternatively, set "ignore" to true.
{
     "constant": "<your-source-system-id>",
     "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
     "scope": "createEntity",
     "ignore": true
}
// Make sure you have this target path with "constant" set to "employee".
{ 
 "constant": "employee",
 "targetPath": "$.userType"
},
```



</td>
</tr>
</table>

> ### Tip:  
> If you don't want the initial password to be visible in the transformation, you can create a credential property called *initial.password* in the *Properties* section of the target system. Then, use the following substitution of the property as a mapping in the transformation:


<table>
<tr>
<th valign="top">

Identity Authentication \(SCIM API version 1\)

</th>
<th valign="top">

Identity Authentication \(SCIM API version 2\)

</th>
</tr>
<tr>
<td valign="top">

```
{
   "constant": "%initial.password%",
   "targetPath": "$.password",
   "scope": "createEntity"
}
```



</td>
<td valign="top">

```
{
   "constant": "%initial.password%",
   "targetPath": "$.password",
   "scope": "createEntity",
   "ignore": "false"
}
```



</td>
</tr>
</table>

> ### Tip:  
> If you don't want to delete the `"constant": "39"` section from the transformation, you can configure the Corporate User Store in the administration console for SAP Cloud Identity Services so as to reuse the corporate passwords. To learn how, see: [Corporate User Store](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/461d71c148594608b9c8b6d016e0a0c5.html#loio2c3ede1d7c454b8a8f820248ee3b705c)

Related information: [Identity Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/target-identity-authentication?locale=en-US&version=Cloud)



### Passwords Are Stored in Identity Authentication \(activation e-mail\)

This use case requires sending an activation e-mail \(without verifying it\). Via this e-mail, users can logon to the Identity Authentication service. They can later change their password.

**Solution** 

Open the Identity Authentication target system transformation and modify the following JSON mappings:

-   For `"$.sendMail"`, change `"constant": "false"` to **true**.
-   For `"$.mailVerified"`, change `"constant": "true"` to **false**.
-   Remove the mappings in bold below.

As a result, you should have:


<table>
<tr>
<th valign="top">

Identity Authentication \(SCIM API version 1\)

</th>
<th valign="top">

Identity Authentication \(SCIM API version 2\)

</th>
</tr>
<tr>
<td valign="top">

```
{
    "constant": "true",
    "targetPath": "$.sendMail",
    "scope": "createEntity"
},
{
    "constant": "false",
    "targetPath": "$.mailVerified",
    "scope": "createEntity"
},

// Remove these mappings:
{
    "constant": true,
    "targetPath": "$.active"
},
{
    "constant": "enabled",
    "targetPath": "$.passwordStatus",
    "scope": "createEntity"
},
{
    "constant": "39",
    "targetPath": "$.sourceSystem",
    "scope": "createEntity"
},  */
```



</td>
<td valign="top">

```
{
    "constant": true,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sendMail']",
    "scope": "createEntity"
},
{
     "constant": false,
     "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
     "scope": "createEntity"
},

// Remove these mappings:
{    
     "constant": true,
     "targetPath": "$.active"
},
{
     "constant": "enabled",
     "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']",
     "scope": "createEntity"
},
// Remove the mapping starting with "constant": "<your-source-system-type-code>", if its value is set to 39.
// Alternatively, set "ignore" to true.
{
    "constant": 39,
    "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
    "scope": "createEntity",
    "ignore": true
},
// Remove this mapping. Alternatively, set "ignore" to true.
{
     "constant": "<your-source-system-id>",
     "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
     "scope": "createEntity",
     "ignore": true
}
```



</td>
</tr>
</table>

> ### Tip:  
> If you don't want to delete the `"constant": "39"` section from the transformation, you can configure the Corporate User Store in the administration console for SAP Cloud Identity Services so as to reuse the corporate passwords. To learn how, see: [Corporate User Store](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/461d71c148594608b9c8b6d016e0a0c5.html#loio2c3ede1d7c454b8a8f820248ee3b705c)

Related information: [Identity Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/target-identity-authentication?locale=en-US&version=Cloud)



### Passwords are Migrated from SAP SuccessFactors 

**Problem** 

1.  You have SAP SuccessFactors \(SFSF\) as a source system and Identity Authentication as a target system.
2.  You have configured your *SFSF* application so as to migrate user passwords to the administration console for SAP Cloud Identity Services, as described on [Configure Authentication Provider To Migrate User Passwords from SAP SuccessFactors Systems to Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/671d2e6de90e44caaa6dede4ab315b48.html).
3.  You might have **missed** to make the [additional transformation modifications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/configure-source-system-to-migrate-user-passwords-from-sap-successfactors-systems-to-identity-authentication?version=Cloud&locale=en-US), and then you have run your first provisioning job between SFSF and Identity Authentication.
4.  The provisioning job is successful but the migrated passwords of SFSF users are disabled in Identity Authentication, thus users cannot login to the administration console for SAP Cloud Identity Services.

The reason: In the Identity Authentication target transformation, the `“passwordStatus”` mapping has been left with its default value - `"disabled"`.

**Solution** 

1.  You have properly configured your SFSF source system so as to migrate user passwords to Identity Authentication. To learn how, see: [Configure Source System To Migrate User Passwords from SAP SuccessFactors Systems to Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/671d2e6de90e44caaa6dede4ab315b48.html)

    [Migrating Passwords from SAP SuccessFactors to the SAP Cloud Identity Services](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/b25f3f36deed40ddb3aee14c6818df06.html)

2.  Make sure you have done the following modifications in the Identity Authentication transformation:
    -   You have added two extra mappings with constants `<SF_Company_ID>` and *100* \(see the code block below\).
    -   You have removed the `"constant": "39"` mapping.
    -   For the `passwordStatus` mapping, you have changed `"disabled"` to `"enabled"`

3.  To fix your issue, you also need to remove the `"createEntity"` scope from the `passwordStatus` mapping!

    So, after you have done the modifications listed above, your Identity Authentication transformation should look like this:


    <table>
    <tr>
    <td valign="top">
    
    **Explanation:** 

    This way, on the next provisioning jobs, the Identity Provisioning will always update the password status of the users, even if they get locked in Identity Authentication. Also, the migrated passwords will be set first in Identity Authentication when a user logs in for the first time to one of their assigned applications \(like SAP SuccessFactors or *User Profile*\).
    
    </td>
    </tr>
    </table>
    

    <table>
    <tr>
    <th valign="top">

    Identity Authentication \(SCIM API version 1\)
    
    </th>
    <th valign="top">

    Identity Authentication \(SCIM API **version 2**\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    ```
    {
        "constant": "<SF_Company_ID>",
        "targetPath": "$.sourceSystemId"
    },
    
    {
        "constant": "100",
        "targetPath": "$.sourceSystem"
    },
    
    {
        "constant": "enabled",
        "targetPath": "$.passwordStatus"
       
    },
    
    {
        "constant": "false",
        "targetPath": "$.sendMail",
        "scope": "createEntity"
    },
    
    {
        "constant": "true",
        "targetPath": "$.mailVerified",
        "scope": "createEntity"
    },
    ```


    
    </td>
    <td valign="top">
    
    ```
    {
         "constant": "<SF_Company_ID>",
         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
         "scope": "createEntity",
         "ignore": false
    },
    {
         "constant": 100,
         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
         "scope": "createEntity",
         "ignore": false
    },
    
    {
        "constant": "enabled",
        "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']" 
       
    },
    {  
        "constant": false,
        "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sendMail']",
        "scope": "createEntity"
    },
    
    {
        "constant": true,
        "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['mailVerified']",
        "scope": "createEntity"
    },
    ```


    
    </td>
    </tr>
    </table>
    
4.  Run a successful **Read** job.
5.  Make sure that SFSF users can now successfully login to the administration console for SAP Cloud Identity Services.
6.  Then open the Identity Authentication transformation again, and add `"scope": "createEntity"` back to the `passwordStatus` mapping. This way, newly created users will get their password status set by the Identity Provisioning. And since this status stays *"enabled"*, their passwords won't be locked.

**Additional Information** 

Another \(more simple\) way to have all users provisioned and their passwords - successfully migrated to Identity Authentication, is to delete all SFSF users from Identity Authentication, and recreate them again. Also, you might need to change the value of the `sf.user.filter` property so as to read only SFSF users who have already existed in Identity Authentication and have *Administrator* role there. This way, the admin users will be kept and all the other SFSF users will be deleted from Identity Authentication.

> ### Caution:  
> You must perform the user deletion via the Identity Provisioning service! If you delete them manually from Identity Authentication, the Identity Provisioning will still "remember" that these users were previously created by it, thus - will have marked them with a flag that would not allow their passwords to be migrated. **Password migration can happen only during user creation via an Identity Provisioning job!**

To learn more, see:[Identity Authentication: Provisioned Users Are Duplicated in SAP Jam or SAP Work Zone](job-and-transformation-issues-dbe3c08.md#loiodbe3c08ebe7c47fb98422680c6580cc0__section_kwf_lbw_bcc) 



### Recreate users that have been provisioned with disabled passwords

**Problem** 

You have provisioned users from a source system to Identity Authentication. When users try to login to the administration console for SAP Cloud Identity Services though, they cannot do that because their passwords are locked.

The reason for that is improper transformation mappings, which have caused users to be provisioned with password status *"disabled"*.

**Solution** 

A simple solution would be to delete all provisioned users from Identity Authentication and re-create them again, this time - with active passwords. You can do that via an Identity Provisioning job, and changing the value of the user filter property, so as to read only users who have already existed in Identity Authentication and have *Administrator* role there. To do that, proceed as follows:

1.  Open your Identity Authentication target transformation.
2.  Search for the `"user"` mapping below and change `"disabled"` to <code><b>"enabled"</b></code>:


    <table>
    <tr>
    <th valign="top">

    Identity Authentication \(SCIM API **version 1**\)
    
    </th>
    <th valign="top">

    Identity Authentication \(SCIM API **version 2**\)
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    ```
    {
        "constant": "disabled",
        "targetPath": "$.passwordStatus",
        "scope": "createEntity"
    },
    ```


    
    </td>
    <td valign="top">
    
    ```
    {
        "constant": "disabled",
        "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['passwordDetails']['status']",
        "scope": "createEntity"
    },
    ```


    
    </td>
    </tr>
    </table>
    
3.  Go to the source system and change the user filter so as to read only users who have already existed in Identity Authentication and have *Administrator* role there.

    For example, if you have an SAP SuccessFactors \(SFSF\) source system, go to the `sf.user.filter` property and extend its value to: `status eq 'active' and username in '<username1>','<username2>',...` 

    This way, the Identity Authentication admin users will be kept, and all the other SFSF users will be deleted from Identity Authentication.

4.  Run a successful **Read** job. It will delete all users that **Identity Provisioning** has previously created and that are not in the filter list.
5.  Open the user filter property again and change it back to its default value. For example, change the `sf.user.filter` value back to: `status eq 'active'`
6.  Run a successful **Read** job again to have all the SFSF users re-created.

Check if users can now perform their first login using their source system passwords.



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_kwf_lbw_bcc"/>

## Identity Authentication: Provisioned Users Are Duplicated in SAP Jam or SAP Work Zone



### Problem

You have executed direct user provisioning from the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services to SAP Jam.

Then you go to the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services, set up Identity Authentication as a source system, and SAP Jam Collaboration as a target system, and run a job.

As a result, multiple users are created twice \(duplicated\) in SAP Jam.

The same issue may happen when the target system is SAP Work Zone. In this case, you can use the same solution here.



### Reason

-   When provisioned from Identity Authentication to SAP Jam via Identity Authentication console, a user `id` in Identity Authentication is mapped to a `userName` in SAP Jam.
-   When provisioned from Identity Authentication to SAP Jam via IPS console, an `userName` in Identity Authentication is mapped to a `userName` in SAP Jam.

As a result, one and the same user can be created twice in SAP Jam - by its `id`, and by its `userName`.

1.  Stop provisioning users to SAP Jam from the administration console for SAP Cloud Identity Services. See: [Configure SAP Jam Target Systems for User Provisioning](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/a9234273c390469ab711c92530c2f962.html)
2.  Then navigate to the *Identity Provisioning* \> *Target Systems*.
3.  Open your SAP Jam Collaboration target system and modify its transformation removing the following two mappings:

    ```
    {
                 "sourceVariable": "entityIdTargetSystem",
                 "targetPath": "$.id",
                 "scope": "deleteEntity"
             },
    
    
    
            {
                 "constant": false,
                 "targetPath": "$.active",
                 "scope": "deleteEntity"
            },
    ```

4.  Now open your Identity Authentication source system and reset it. To do that, select the system and choose *Edit* \> *Reset*.
5.  Then modify the Identity Authentication transformation the following way:

    Change this mapping:

    ```
    {
         "sourcePath": "$.userName",
         "optional": true,
         "targetPath": "$.userName",
         "correlationAttribute": true
      }
    ```

    To:

    ```
    {
         "sourcePath": "$.id",
         "targetPath": "$.userName",
         "correlationAttribute": true
      }
    ```

6.  Run a **Read** job for the Identity Authentication system. All entities created before directly from the Identity Authentication console to SAP JAM will be updated in SAP JAM. This way, the Identity Provisioning already knows about these entities and can manage them. Entities created from provisioning through the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services will remain.
7.  Go to the SAP Jam target system, and add the following \(Standard\) system property: `ips.delete.existedbefore.entities` = `true`
8.  Now go back to the Identity Authentication source system and add a special condition in the `"user"` section. Your mapping should look like this:

    ```
    "user":
     {
      "condition": "($.name.familyName EMPTY false) && ($.name.familyName == 'DUMMY_NAME')",
    "mappings": [
    ```

9.  Run a new **Read** job for the Identity Authentication system. At this step, all users provisioned through Identity Authentication console should be deleted from SAP JAM.
10. Now go to the SAP Jam target system and return the mappings you have removed on step 3.
11. Then go back to the Identity Authentication source system and delete the condition from step 8.

**Next steps** 

From now on, use only the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services for provisioning users \(and groups\) from Identity Authentication to SAP Jam. All future *Read/Resync* jobs will provision your users correctly, mapping `userName` to `userName`, without duplicating entities anymore.



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_qt2_ldw_bcc"/>

## Identity Authentication: Some Additional Users Should Not Be Provisioned to SAP Jam



### Problem

1.  You have an SAP Jam product, which contains Identity Authentication and Identity Provisioning.
2.  When your product is activated, all users from Identity Authentication are initially provisioned to SAP Jam, which is a default and desired behavior.
3.  Later on, additional users were added to Identity Authentication \(either created manually, or come from another product\).
4.  All these new users are automatically provisioned to SAP Jam too, but some of them **should not be**.



### Reason

The default SAP Jam transformation is set so as to be synchronized with all changes that take place in the source system \(Identity Authentication\). That means - both updating existing users, or creating newly added ones.

However, you want some of these users to stay only in Identity Authentication and not to be provisioned to SAP Jam. For example, specific users coming from another products.



### Solution 1

You can set a filter that will read, create and update only **"pure Identity Authentication"** users \(originally existing in Identity Authentication, or manually created later\).

1.  You have to assign all these Identity Authentication users to a specific group. Let's say, the group name is called `IAS_Specific`.
2.  All additional users \(coming from other products\) must belong to other groups or to no groups at all.
3.  To set a filter, open your SAP Jam target system.
4.  Go to the *Properties* tab and choose *Edit*.
5.  Add property `scim.user.filter` and set its value to `groups eq 'IAS_Specific'`

This way, if a new user appears in Identity Authentication, and it doesn't belong to *IAS\_Specific*, it will not be provisioned to SAP Jam.



### Solution 2

If it's too complicated or cumbersome to assign all **"pure Identity Authentication"** users to a single group, you can instead assign the newly come **foreign** users to a specific group. Then, you can set a condition in the transformation so as to skip only this specific group.

1.  Let's say, the **foreign** users come from SAP Marketing Cloud, so you assign the relevant users to a group named `Marketing_Cloud`.
2.  To set a condition, open your Identity Authentication source system.
3.  Go to the *Transformations* tab and choose *Edit*.
4.  Under `"user":{` enter the following condition:

```

{
   "user": {
       "condition": "$.groups EMPTY true || $.groups[?(@.value == 'Marketing_Cloud' )] == []",
       "mappings": [
       {
           "sourcePath": "$.id",
           "targetVariable": "entityIdSourceSystem"
       },
. . .
```

This way, the Identity Provisioning service:

-   Will provision all users that don't belong to any groups.
-   Will **not** provision anything from group *Marketing\_Cloud*.
-   Will provision all users that belong to any group different than *Marketing\_Cloud*.

**See also: [Identity Authentication: Provisioned Users Are Duplicated in SAP Jam or SAP Work Zone](job-and-transformation-issues-dbe3c08.md#loiodbe3c08ebe7c47fb98422680c6580cc0__section_kwf_lbw_bcc)**



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_k5x_32w_bcc"/>

## Identity Authentication: Send activation email in users preferred language

When provisioning users from SAP SuccessFactors to Identity Authentication, you want the newly created users in Identity Authentication to get the activation emails in their preferred language. For this, you need to configure the transformations of both SAP SuccessFactors \(source\) and Identity Authentication \(target\) systems.

Proceed as follows:

1.  In your SAP SuccessFactors system, select the *Transformations* tab and add one of the following transformation codes in the user mapping section:


    <table>
    <tr>
    <th valign="top">

    Use `preferredLanguage` attribute
    
    </th>
    <th valign="top">

    Use `defaultLocale` attribute
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    ```
    {
        "sourcePath": "$.preferredLanguage",
        "optional": true,
        "targetPath": "$.locale"
    },
    ```


    
    </td>
    <td valign="top">
    
    ```
    {
        "sourcePath": "$.defaultLocale",
        "optional": true,
        "targetPath": "$.locale"
    },
    ```


    
    </td>
    </tr>
    </table>
    
    Normally, `defaultLocale` is used for onboardees \(new hires\). If a user inSAP SuccessFactors does not have the `defaultLocale` attribute filled in as desired, you can set it by following the procedure described in KBA: [2395445](https://launchpad.support.sap.com/#/notes/2395445)- Default Locale | How to control the user language in SuccessFactors

    For more information, see: [Configuring Email Templates](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/configuring-e-mail-templates?locale=en-US&version=Cloud)

2.  Select the *Properties* tab and append the attribute of your choice \(`preferredLanguage` or `defaultLocale`\) to the already listed attributes in the value field of the `sf.user.attributes` property.
3.  Save your changes.
4.  In your Identity Authentication target system, select the *Transformations* tab and add the following transformation code in the user mapping section for `"locale"`:

    ```
    {
       "sourcePath":"$.locale",
       "optional":true,
       "targetPath":"$.locale",
       "functions":[
       {
          "function":"toUpperCaseString"
       },
       {
          "function":"substring",
          "beginIndex":0,
          "endIndex":"2"
       }
      ]
    },
    ```

    This is needed because language formats differ in SAP SuccessFactors and Identity Authentication.

    For more information, see: [2269945](https://userapps.support.sap.com/sap/support/knowledge/en/2269945) - List of Supported Languages with Locales for SuccessFactors

5.  Save your changes.
6.  Run a provisioning job in SAP SuccessFactors source system.
7.  Verify that the newly created users in Identity Authentication receive the activation emails in their preferred language.

For other solutions on how to send welcome e-mails in a predefined language, see SAP KBA [3035482](https://launchpad.support.sap.com/#/notes/3035482)



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_ubc_j2w_bcc"/>

## Job Is Successful but Statistics Are Missing



### Problem

1.  You've added a source and a target system in your *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services.
2.  You've started a provisioning job \(*Read* or *Sync*\).
3.  In the *Job Logs* section, you see that the job has finished successfully. However, the *Statistics* table is empty.


<table>
<tr>
<th valign="top">

Reason

</th>
<th valign="top">

Solution

</th>
</tr>
<tr>
<td valign="top">

You have set a filter in the *Properties* tab that does not match any of the entities in the system.

</td>
<td valign="top">

Change the filter so that it matches at least one entity.

</td>
</tr>
<tr>
<td valign="top">

No changes have been made in the source system since the last provisioning job.

</td>
<td valign="top">

You'll see the statistics if you change at least one entity in the source system, and then run a new job.

</td>
</tr>
<tr>
<td valign="top">

Your source system is SAP SuccessFactors, and the technical user is missing *Export* permissions to read employee data from the SAP SuccessFactors system.

</td>
<td valign="top">

Obtain *Export* permissions for SAP SuccessFactors. To learn how, see: [Permissions](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/3d71f690709243db99102127557a3d73.html?locale=en-US&version=2405).

</td>
</tr>
</table>



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_vd1_yfw_bcc"/>

## Microsoft AD: Nested Groups Are Not Resolved in the Target System



### Problem

Your source system is Microsoft Active Directory and you want to provision all users and groups, along with all group members. However, some of the groups contain "nested" subgroups. All these groups and subgroups contain users.

When the provisioning job is done, in the target system only the direct members of the parent group are provisioned. The user assignments from all subgroups are missing.



### Reason

Some target systems don't support nested groups \(group structures\). Such target systems are:

-   SAP Jam Collaboration
-   Identity Authentication

Therefore, if you provision group structures to one of these target system types, the user assignments from the subgroups will be missing.



### Solution

Luckily, you can enable recursive reading of such group structures. All you need is to set the following two properties:

-   `ad.group.flatten` = `true`
-   `ldap.group.filter` = `(cn=<parent_group>)`

As a result, in the target system all users will be written in one parent group, which has the same name as the source parent group.



### Example

-   Let's say, in your Microsoft AD system there is a parent group *"Canteen"* that contains nested subgroups. If you set `ldap.group.filter` = `(cn=Canteen)`, the Identity Provisioning will resolve all the direct users and groups of *"Canteen"*, along with all the users of its subgroups \(and their subgroups\). In the target system, all users will be written in one parent group named also *"Canteen"*.

-   If you have multiple parent groups \(for example, *Canteen*, *Finances* and *Support\_Team*\) that contain nested subgroups, you can set the filter property like this:

`ldap.group.filter = (|(cn=Canteen)(cn=Finance)(cn=Support_Team))` 



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_bnb_sgw_bcc"/>

## Microsoft Azure: Emails Are Missing



### Problem

When you add Microsoft Active Director as a source system and you run a provisioning job, some of the populated users in the target system have missing e-mail addresses. This issue can be a provisioning blocker for target systems that require a mail attribute \(for example, Identity Authentication\).



### Reason

> ### Note:  
> The image/data used is from SAP internal systems, sample data, or demo systems. Any resemblance to real data is purely coincidental.

There can be two reasons for such a behavior:

-   Some users don't have a Microsoft Office 365 license.
-   They have this license but their `mail` attribute is not tied to Microsoft Exchange Online, which leads to lack of synchronization between user data on the on-premise Microsoft AD andAzure AD.

In both cases, after the provisioning job, the value of the user's emails attribute in both the source and the target system is *null*. For example:


<table>
<tr>
<th valign="top">

User details in the source system

</th>
<th valign="top">

User details in the target system

</th>
</tr>
<tr>
<td valign="top">

```
"displayName": "Johnny123",  
"givenName": "John",  
"surname": "Smith",  
"mail": "null",  
"userPrincipalName": "JohnSmith",      
... 
```



</td>
<td valign="top">

```
"displayName": "Johnny123",      
"givenName": "John",  
"familyName": "Smith",  
"emails": null,  
"userName": "JohnSmith",      
... 
```



</td>
</tr>
</table>



### Solution

You need to map the user e-mail to another attribute, for example `userPrincipalName`. In the source transformation, modify the following JSON lines:

```
/* Remove this part:
	{ 
		"sourcePath": "$.mail",
		"targetPath": "$.emails[0].value"
	}, */

// Change the following part to:
	}
		"sourcePath": "$.userPrincipalName",
		"targetPath": "$.emails[0].value"
	},
	{
		"sourcePath": "$.displayName",
		"optional": true,
		"targetPath": "$.displayName"
	},
...
```



### Result

User details in the target system \(after modifying the transformation\):

```
"displayName": "Johnny123", 
"givenName": "John", 
"familyName": "Smith", 
"emails": null, 
"userName": "john.smith@acme.com", 
...
```

Related information: [Microsoft AD \(Source System\)](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/microsoft-active-directory?locale=en-US&version=Cloud)



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_lv5_zt2_ccc"/>

## Multiple Users from a Source System Are Created as One in the Target

The problem described on this page illustrates a scenario involving SAP SuccessFactors \(SFSF\) as a source system and Identity Authentication as a target one. However, this issue may occur to any source system while provisioning users to the following targets:

-   Identity Authentication
-   SAP Analytics Cloud
-   SAP Datasphere

> ### Note:  
> The problem will happen only if you use *email* as a unique attribute in the target.
> 
> If you have modified the *email* to **NOT** be unique \(for example - in [Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/8b9fa88649ae4d86a4ab4baf8fb0e007.html)\), **ignore this section!** 



### Problem

1.  You've added SAP SuccessFactors as a source system and Identity Authentication as a target one.
2.  You haven't set any specific filters. Thus, the provisioned users are expected to be the same number as the ones in SFSF..
3.  You've started a **Read Job**, which finishes successfully.
4.  When you check the populated entities, though, you notice that the users created in Identity Authentication are fewer \(or significantly fewer\) than the original number of users in SFSF.



### Reason

The user e-mail is optional for SFSF \(it might not be unique\). However, it's mandatory and unique for Identity Authentication.

Therefore, it's very likely that some users have **duplicate** e-mail addresses in SFSF, which causes the improper provisioning. The Identity Provisioning service stores a **relation** for every source entity and its corresponding target entity. When multiple users have duplicate e-mails and the provisioning is triggered, the stored relation is "**many** source entities that point to **a single** target entity".

> ### Remember:  
> Before you start provisioning SFSF users to Identity Authentication for the first time, make sure that all users **have** e-mails, which are **unique**, even if these entities are only meant for test purposes. This way, you won't encounter the problem described in this guided answer.



### Prerequisites

To solve the occurred problem, you first need to edit the e-mails of all affected SFSF users. You can do this in two ways - manually or programmatically.

-   Manually

    Edit the e-mail of each affected user in SFSF.

-   Programmatically

    You have to modify the SF source system transformation so as to create a unique e-mail address for each conflicting user during the next **Read** Job.

    -   If you use SFSF source system with SAP SuccessFactors Workforce SCIM API \(SF API version 2\), follow the procedure in KBA: [3308246](https://launchpad.support.sap.com/#/notes/3308246)

    -   If you use SFSF source system with SAP SuccessFactors HCM Suite OData API \(SF API version 1\), follow the procedure below:

        To do this, enhance the default email mapping:

        ```
        {
          "sourcePath": "$.email",
            "targetPath": "$.emails[0].value"
         },
        ```

        to:

        ```
        {
           "sourcePath": "$.email",
           "optional": true,
           "targetPath": "$.emails[0].value"
        },
        
        {
           "condition": "!($.email EMPTY false) || $.email == '' || $.email == ' ' || $.email == 'user123@companyname.com' ",
           "sourcePath": "$.userId",
           "targetPath": "$.emails[0].value",
           "functions": [
              {
                "type": "concatString",
                "suffix": "@sap-test.de"
              }]
        }
        ```

        **What does the condition above mean?**

        -   `$.email == !($.email EMPTY false)` means that the user lacks an email attribute.

        -   `$.email == ''` means the SFSF user has no business e-mail set.

        -   `$.email == ' '` means the SFSF user has a space character set as an e-mail address.

        -   `$.email == 'user123@companyname.com'` means that multiple users in SFSF have a business e-mail *user123@companyname.com*, which results in errors in the Identity Authentication target system. This email address is just an example! In your condition, the listed emails can refer to your actual company domain, or to another non-existing one.


        > ### Note:  
        > **@sap-test.de** is the recommended test domain approved by SAP for customer dummy \(testing\) requests. Thus, please use only this one for the *concatString* function! If you use another non-existing domain, it might get blocked for security reasons.

        > ### Note:  
        > Bare in mind that the condition is case sensitive! Thus, make sure that all SFSF e-mails contain low-case letters only. If some of them contain capital letters, you can either go and manually change them to low case, or list all emails like that in the condition.

        Using the code above, each provisioned user will be created in Identity Authentication with a unique e-mail in format `<userId>@sap-test.de`. Users that have valid unique business e-mails set in SFSF will be provisioned with the same valid e-mails in the administration console for SAP Cloud Identity Services.





### Solution

After you have executed the prerequisite steps, follow the final steps below:

1.  Reset the Identity Authentication target system. To do this, select the system and choose *Edit* \> *Reset*. This way, all previous entity relations will be deleted. System configurations and all existing provisioned entities, along with their authorizations, will be preserved.
2.  In the *Properties* tab, add a standard property `ips.delete.existedbefore.entities` and set it to *true*. This property provides correct behavior if a user is later deleted from SFSF. If this happens, during the next **Read/Resync** Job, the Identity Provisioning will recognize this user as **"existed before but now deleted from the source system"** and will delete it from the target system as well. To learn more, see [List of Properties](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/list-of-properties?locale=en-US&version=Cloud).
3.  Add a standard property `scim.user.unique.attribute` and set it to `userName`. This way, if the Identity Provisioning reads two different users with the same e-mail, it will try to resolve the second one by *user name*. Since these two users have different user names, this second entity will fail with an error for duplicate e-mail. You will see it in the *Job Logs*. This approach is safe because it won't affect the successfully created users in the target system, and will only prompt you to edit the SFSF e-mails of newly added conflicting users.
4.  Now open the SAP SuccessFactors source system.
5.  Start a new **Read** Job.
6.  As a result, all source entities will be read and then created/updated in the Identity Authentication target system. The Identity Provisioning will store a new unique relation between each source entity and its corresponding target entity.



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_thb_hjw_bcc"/>

## Provisioning Jobs Take Extremely Long Time

**Problem**

1.  You have added a source and a target system in your *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services.
2.  You start a **Resync** job.
3.  The job is taking an extremely long time to execute, even if it finishes successfully.

**Reasons**

There can be a few reasons for such a behavior, depending on your type of system, or the location of your business applications and the data centers where your tenants reside.

Choose the option that applies to your scenario:



### **Your source system is SAP SuccessFactors, SuccessFactors LMS, Microsoft AD, or Identity Authentication**

-   **Overview Information**

    Your source system type is one of the following:

    -   SAP SuccessFactors
    -   Microsoft Active Directory
    -   SAP Cloud Identity Authentication

    These three systems support **delta read** provisioning.

    **Delta read** is a concept for optimizing the amount of data retrieved from the source system. Delta read is much faster than **full read** as only modified data is read from the source system and triggered to the target one. Modified data means: new entities, deleted entities, and updates on existing entities. This is useful when you schedule the read jobs. For example, every 10th job can be a full read, and the rest will be delta read jobs, which can significantly improve the execution time of the provisioning job.


    <table>
    <tr>
    <td valign="top">
    
    **SAP SuccessFactors**
    
    </td>
    <td valign="top" rowspan="2">
    
    By default, delta read is **enabled** for these systems. That means, the first ever **Read** job will be a full one, meaning - reading all source entities. If it's successful and you have set schedule jobs to be executed on a certain time interval, the next executed job will be a **delta** one \(reading only modified data\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **SAP SuccessFactors LMS**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Microsoft Active Directory**
    
    </td>
    <td valign="top" rowspan="2">
    
    By default, delta read is **disabled** for these systems. That means, the first ever **Read** job will be a full one, meaning - reading all source entities. If it's successful and you have set schedule jobs to be executed on a certain time interval, the next executed job will be again a **full** one \(reading again everything from the source system\).

    To activate delta read, go to the *Properties* tab, and set the following property:

    `ips.delta.read`=`enabled`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **SAP Cloud Identity Authentication**
    
    </td>
    </tr>
    </table>
    
-   **Possible Reason**

    Instead of **Read**, you might have run a **Resync** job. What's the difference?

    -   A **Read** job will read all users, but provision only the **delta** to the target systems. That means, only newly created, updated, or deleted users in the source system be respectively created, updated, or deleted in the target systems by the Identity Provisioning service. When the first full provisioning is successful, the next read jobs will work in **delta read** mode.

    -   A **Resync** job would read all users from the source system \(based on the configured filter\), and provision all of them to the target system, even if previous provisioning job already did this and most of the users have not changed since the previous job. It is like executing a provisioning job for the first time. If some users were already provisioned before, the Identity Provisioning service will perform update for them.

        In addition, if the users are already present in the target systems by other means, and not from an Identity Provisioning job, the service will try to create them - which operation would fail - and then the service will fetch every user from the target and update it. This additional operation could further slow down the job execution.


    **Recommendation:**

    We recommend that you use a **Resync** job when manual changes have been made in the target systems, which the Identity Provisioning is unaware of. In this case, the service can sync all users data from the source to the target with a **Resync** job. In all other cases, it is sufficient to execute **Read** jobs only.

    **Solution**

    Next time, manually execute a **Read** job. Make sure the delta read is set for your system!

    If the result is sufficient to you, you can schedule your read jobs in order to be automatically executed on a certain period of time.

    **Recommendation:**

    We recommend that you enforce full reads once in a while if your provisioning system is set in **delta read** mode. To achieve this, you need to set up the following source system property like, for example:

    `ips.full.read.force.count`=`10`

    This will result in alternating full reads after every **10 delta reads** are performed. This property only impacts scheduled runs. Manually triggered runs are ignored.




### Your Source System is of Another Type

**Reason**

Your source and target business applications are placed in one location, and the data center where your SAP Cloud Identity Services tenant resides is in a very distant region.

For example, your SAP Cloud Identity Services tenant is located in Europe, while your business application instances are located in the US. This makes the connection between the system significantly slower.

**Solution**

-   Migrate your tenants, or request new ones.

    > ### Note:  
    > The provided solution is only applicable to **bundle tenants**!

-   You can migrate your SAP Cloud Identity Services tenant to another data center - where your source system is. To request that change, create an incident to component **BC-IAM-IDS**. You will receive details about the procedure, or you can request a new SAP Cloud Identity Services tenant to be created in the region where your source system is.
-   Currently you cannot migrate your SAP Cloud Identity Services tenants. But you can request a new one for the region where your source system is. The old SAP Cloud Identity Services tenant can be deleted or preserved - depending on whether you will need it in future for business applications whose instances are located in the initial region. To request that change, create an incident to component BC-IAM-IPS.



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_jkl_llw_bcc"/>

## Provisioning Job Fails for One of Multiple Target Systems

**Problem**

1.  You added one source and multiple target systems in your *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services.
2.  You started a provisioning job.
3.  The job fails for one of the multiple target systems.

**Reason**

Provisioning to one of the target systems may fail due to exception.



### Provisioning Job Fails with Exception

**Problem** 

1.  You added one source and multiple target systems in your *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services.
2.  You started a provisioning job.
3.  The job fails with one of the following exceptions:

-   *Caused by: Timeout exception has occurred while processing entity for <URL of the source system\>*
-   *Caused by: Timeout exception occurred*

**Reason** 

Those exceptions occur when provisioning to one of the multiple target systems fails, for example, due to connectivity issues.

**Solution**

Start the provisioning job again.



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_eqx_fsx_bcc"/>

## Not All Users are Provisioned to the Target Systems



### Problem

1.  You added one source and multiple target systems in your *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services.
2.  You started a provisioning job.
3.  You get one of the following results and you want to know why:
    -   Not all users are read from the source system, and yet, their number is greater than the number of users provisioned to the target system.

    -   All users are read from the source system but less are provisioned to the target system.





### Reasons

Possible reasons when **not all users** are read from the source system, and yet, their number is greater than the number of users provisioned to the target system.

-   There are inactive users in the source system. Identity Provisioning only provisions active users.
-   Provisioning job is run in delta read mode.
-   Connection to the source system fails.

Possible reasons when **all users** are read from the source system but less are provisioned to the target system:

-   Provisioning to one of the multiple target systems has failed. See: [Provisioning Job Fails for One of Multiple Target Systems](job-and-transformation-issues-dbe3c08.md#loiodbe3c08ebe7c47fb98422680c6580cc0__section_jkl_llw_bcc)
-   A full Read job has been run. After that, there were no changes on users in the source system. Next run of a full Read job reads all users from the source system but provisions "0" users to the target due to lack of changes.



### Provisioning Job Fails for One of Multiple Target Systems

**Problem** 

1.  You added one source and multiple target systems in your *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services.
2.  You started a provisioning job.
3.  The job fails for one of the multiple target systems.

**Reason** 

Provisioning to one of the target systems may fail due to exception. See: [Provisioning Job Fails with Exception](error-messages-ad525a4.md#loioad525a4ae37c4efab2710f7664fec548__section_lgh_wp3_mbc)



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_dn5_zsx_bcc"/>

## Scheduled Jobs Are Not Running



### Problem

1.  In the *Identity Provisioning* admin consoleadministration console for SAP Cloud Identity Services, add a source and a target system.
2.  Open the source system, then the *Jobs* tab.
3.  Choose *Schedule* and enter a number \(of minutes\).
4.  Choose *OK* and wait for a while.
5.  Open *Job Logs* to check the job's status. However, you don't even see the job, which means it's not started yet.
6.  No matter how long you wait, the job does not appear on the screen.



### Solution

After you've set up a schedule job, you must always choose the **On** button to actually start the job. This is a one-time manual step.

Once you've selected *On*, the job starts automatically, according to the predefined period of time.



### I Still Have Problems with Job Scheduling

Your problem requires deeper analysis by SAP. Please create an incident for component BC-IAM-IPS.

In the incident, specify also:

-   The IDs of your global account and subaccount, or your bundle tenant.

-   To which region your account/tenant belongs. You can find it in this list:[\(Discovery Center\) Identity Provisioning](https://discovery-center.cloud.sap/index.html#/serviceCatalog/identity-provisioning) -\> *Service Plan*


Before you create a support case, read:

[2654164 - What to consider before opening a Support Ticket for SAP Business Technology Platform](https://launchpad.support.sap.com/#/notes/2654164)

For contract-related questions, read:

[1660069 - How to contact SAP Contracts Department for questions or issues](https://launchpad.support.sap.com/#/notes/1660069) 



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_wm2_gtx_bcc"/>

## SAP IBP: Avoid Restoring Decimal Format, Time Zone and Language to Their Defaults

When updating a user in SAP Integrated Business Planning \(or any other SAP S/4HANA Cloud-based system\), you want to make sure that only specified attribute values are updated, while others remain unchanged.

> ### Note:  
> In addition to SAP IBP, this guided answer is also applicable to SAP S/4HANA Cloud, SAP BTP ABAP environmentand SAP Marketing Cloud.



### Problem & Reason

Currently, if a user is created in SAP IBP target system and later on you update the user without providing values for attributes in the User node \(such as, decimal format, time zone and language\), these values are restored to their defaults.

To reproduce this behavior, proceed as follows:

1.  Run a provisioning job from a source system \(for example, Identity Authentication\) to SAP IBP. Users are created with the default values:

    -   **Decimal Format**: 1.234.567,89
    -   **Time Zone**: No value
    -   **Language**: English United States

2.  In SAP IBP, modify the attributes of a given user:

    -   Change the **Decimal Format**, for example to `1,234,567.89`
    -   Select a **Time Zone**, for example `Eastern Europe`.
    -   Leave the English United States **Language** as-is or change it.

3.  In Identity Authentication, update the user, for example change its last name only.

4.  In Identity Provisioning, run a provisioning job.

    As a result, the user’s last name in SAP IBP is updated. Since no values are provided for decimal format, time zone and language, in SAP IBP expect the following:

    -   **Time Zone and Decimal Format** are restored to their default values.
    -   **Language** is removed.




### Solution

To ensure that only specified attribute values are updated, while others remain unchanged, you need to modify the SAP IBP target transformation.

1.  Add the bolded attribute mapping at the end of the user entity as follows:

    ```
    {
    
                    "condition": "$.active == false",
                    "constant": "true",
                    "targetPath": "$.user.lockedIndicator"
                },             
    		{
                    "constant": "02",
                    "targetPath": "$.user.actionCode"
                },
                {
                    "constant": "01",
                    "targetPath": "$.user.actionCode",
                    "scope": "createEntity"
                }
            ]
        },  
    ```

    ```
               
    ```

    -   `"constant": "02"`

        This means that Action code 02 \(representing update operation\) is applied for attributes in the User node.

    -   `"constant": "01"`

        This means that Action code 01 \(representing create operation\) is applied for attributes in the User node. The scope of this mapping is createEntity, which means that the entity attribute is only processed during creation.


2.  Modify some user's attributes and run a provisioning job.


As a result, only the specified attribute values are updated. Others for which no value is provided remain unchanged.



<a name="loiodbe3c08ebe7c47fb98422680c6580cc0__section_pym_ztx_bcc"/>

## SAP SuccessFactors: Some Entities are Unexpectedly Deleted from Target System



### Problem

1.  You set SAP SuccessFactors as a source system and have enabled **delta read** for it.
2.  You set a target system \(any kind\).
3.  You have been running manual or scheduled jobs for some time. When a job finishes with an error, you have noticed that no entities have been deleted.
4.  If you run a new job after **October 1, 2020**, you see that some or many entities are unexpectedly deleted.



### Reason

**Expected behavior:**

If a provisioning job has successfully read all entities from a source system \(with **delta read**enabled\) but fails due to problems with provisioning of some entities, the entities that have to be deleted **should be deleted**.



**Actual behavior before October 1, 2020**

Entities that should have been deleted were **not deleted** during delta read. This behavior was incorrect but is now fixed.

> ### Note:  
> If a provisioning job was successful, this problem would not have been observed. Read entities were created/updated, and unread entities were deleted from the target.



### Solution

Effective **October 1, 2020** this bug has been fixed in the Identity Provisioning service, and now the default behavior happens. That's why you observe "unusual deletion" of entities in your target system, which is how it's supposed to be.



### Related Information

If you want the service to read only part of the entities in your source system but to **save** the unread ones from deletion in the target, see: [Entities Should Not Be Deleted in the Target System](job-and-transformation-issues-dbe3c08.md#loiodbe3c08ebe7c47fb98422680c6580cc0__section_nrt_rxx_rbc)

**Related Information**  


[Administration Issues](administration-issues-90ce2d5.md "")

[Error Messages](error-messages-ad525a4.md "")

[Entity Deletion Issues](entity-deletion-issues-d6acc19.md "Learn how to troubleshoot the most frequent reasons for deletion of users or groups from a target system by the Identity Provisioning.")

[Additional Information](additional-information-7463572.md "")

[Handling Specific Attributes](handling-specific-attributes-e957782.md "")

