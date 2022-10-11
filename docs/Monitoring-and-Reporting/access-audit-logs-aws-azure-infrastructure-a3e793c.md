<!-- loioa3e793c9096c4fee9c98ecdcb8791cfc -->

# Access Audit Logs \(AWS, Azure Infrastructure\)

You can access the audit logs for changes in the personal data, successful, and failed authentications for your Identity Authentication tenant.



<a name="loioa3e793c9096c4fee9c98ecdcb8791cfc__prereq_kmy_vlf_mqb"/>

## Prerequisites

You have a subaccount in your global account on SAP BTP, Cloud Foundry. For more information, see [Create a Subaccount](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/05280a123d3044ae97457a25b3013918.html).



## Context

> ### Note:  
> The content in this document is only for tenants on the AWS and Azure infrastructure.
> 
> For tenants on the SAP infrastructure, see [Access Audit Logs \(SAP Infrastructure\)](access-audit-logs-sap-infrastructure-9f6b9a4.md).

To view the audit logs for tenants on the AWS and Azure infrastructure you must add configurations in the SAP BTP cockpit and the administration console for Identity Authentication first.

To view the audit logs, follow the procedures below:

 <a name="task_obm_ytf_mqb"/>

<!-- task\_obm\_ytf\_mqb -->

## 1. Configure the Service Plans



<a name="task_obm_ytf_mqb__steps_lkd_15f_mqb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the corresponding subaccount. For more information, see [Navigate in the Cockpit.](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0874895f1f78459f9517da55a11ffebd.html)

2.  In the navigation area on the left, choose *Entitlements*. Then choose *Configure Entitlements* \> *Add Service Plans*.

3.  From the dialog, search for and select *Audit Log Viewer*, select the *free* checkbox, and then choose *Add 1 service plan*.

4.  Save your changes.


 <a name="task_wmz_hgg_mqb"/>

<!-- task\_wmz\_hgg\_mqb -->

## 2. Configure Audit Log Viewer Instance



<a name="task_wmz_hgg_mqb__steps_xmz_hgg_mqb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the corresponding subaccount. For more information, see [Navigate in the Cockpit.](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0874895f1f78459f9517da55a11ffebd.html)

2.  Navigate to *Services* \> *Service Marketplace*, and select *Audit Log Viewer*.

3.  Choose *Create*.

    In the *New Instance or Subscription* dialog box, ***Audit Log Viewer*** for *Service*, and ***free*** for *Plan* are already preselected.

4.  Choose *Create* and close the information message.


 <a name="task_jbz_qck_mqb"/>

<!-- task\_jbz\_qck\_mqb -->

## 3. Create and Assign Role Collection and Roles



<a name="task_jbz_qck_mqb__steps_bpl_hgk_mqb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the corresponding subaccount. For more information, see [Navigate in the Cockpit.](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0874895f1f78459f9517da55a11ffebd.html)

2.  Choose *Security* \> *Roles Collections* in the navigation area.

3.  Choose the plus button to create a role collection.

    The new role collection in the *Role Collections* list.

4.  Select the newly created role collection from the list.

5.  Choose the *Edit* button.

6.  Under the *Roles* tab, expand the *Role Name* list and select the auditlog viewer and auditlog-management roles.

    If the roles don't exist, create them. For more information, see [Configure Application Roles and Assign Roles to Users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/56a71531fc154717bf221f9e293ba215.html).

7.  Choose *Add*.

8.  Navigate back to the subaccount and choose *Security* \> *Users* and assign the role collection to the user.


 <a name="task_yvb_pk1_rdb"/>

<!-- task\_yvb\_pk1\_rdb -->

## 4. Add Configuration in Administration Console and View Audit Logs



<a name="task_yvb_pk1_rdb__steps_mkb_bl1_rdb"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Choose the *Audit and Change Logs* tile.

3.  Choose *Add Configuration*.

4.  Fill in the required information in the pop up and save your changes.


    <table>
    <tr>
    <th valign="top">

    Configuration


    
    </th>
    <th valign="top">

    Notes


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    **Tenant ID**


    
    </td>
    <td valign="top">

    Required. The tenant ID of your Cloud Foundry account.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Subdomain**


    
    </td>
    <td valign="top">

    Optional. If you provide it, a link to the *Audit Log Viewer* is added in the *Audit Service Configuration*, and you can access the audit logs directly from the administration console.


    
    </td>
    </tr>
    </table>
    
5.  Save your changes.

6.  View the audit logs. You have two options to do that:

    -   \(if subdomain is configured\) choose the link to the *Audit Log Viewer* in the *Audit Service Configuration* in the administration console
    -   in the cockpit, navigate to *Services* \> *Instances and Subscriptions* \> *Audit Log Viewer*.




<a name="task_yvb_pk1_rdb__result_vpf_z5k_mqb"/>

## Results

The configuration will be enabled with the next 15 minutes.

