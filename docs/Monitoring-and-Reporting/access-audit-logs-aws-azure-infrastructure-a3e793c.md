<!-- loioa3e793c9096c4fee9c98ecdcb8791cfc -->

# Access Audit Logs \(AWS, Azure Infrastructure\)

Access the audit logs for changes in the personal data, successful, and failed authentications for Identity Authentication tenants on the AWS and Azure infrastructure.



<a name="loioa3e793c9096c4fee9c98ecdcb8791cfc__prereq_kmy_vlf_mqb"/>

## Prerequisites

You have a subaccount in your global account on SAP BTP, Cloud Foundry. For more information, see [Create a Subaccount](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/05280a123d3044ae97457a25b3013918.html).



## Context

> ### Note:  
> The content in this document is only for tenants on the AWS and Azure infrastructure.
> 
> For tenants on the SAP infrastructure, see [Access Audit Logs \(SAP Infrastructure\)](access-audit-logs-sap-infrastructure-9f6b9a4.md).

To view the audit logs for tenants on the AWS and Azure infrastructure you must add configurations in the SAP BTP cockpit and the administration console for SAP Cloud Identity Services first.

The audit log entries for tenants on the AWS and Azure infrastructure are retained for 90 days.

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

    In the *New Instance or Subscription* dialog box, `Audit Log Viewer` for *Service*, and `free` for *Plan* are already preselected.

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

1.  Sign in to the administration console for SAP Cloud Identity Services.

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
    
    **Region**


    
    </td>
    <td valign="top">
    
    SAP BTP, Cloud Foundry region. You can choose a region from the options in the dropdown. For more information, see the mapping table.


    
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
    
    **Identity Authentication - Cloud Foundry Regions Mapping**


    <table>
    <tr>
    <th valign="top" colspan="2">

    Identity Authentication


    
    </th>
    <th valign="top" colspan="3">

    Cloud Foundry Regions


    
    </th>
    </tr>
    <tr>
    <th valign="top">

    Region


    
    </th>
    <th valign="top">

    Infrastructure


    
    </th>
    <th valign="top">

    Technical Name


    
    </th>
    <th valign="top">

    Name


    
    </th>
    <th valign="top">

    Default


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    North America \(Canada Central\) / Canada \(Toronto\)


    
    </td>
    <td valign="top">
    
    azure-canadacentral


    
    </td>
    <td valign="top">
    
    cf-ca10


    
    </td>
    <td valign="top">
    
    Canada \(Montreal\)


    
    </td>
    <td valign="top">
    
    Yes


    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="5">
    
     


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="4">
    
    US West / West US 2


    
    </td>
    <td valign="top" rowspan="4">
    
    azure-westus2


    
    </td>
    <td valign="top">
    
    cf-us20


    
    </td>
    <td valign="top">
    
    US West \(WA\)


    
    </td>
    <td valign="top">
    
    Yes


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    cf-us21


    
    </td>
    <td valign="top">
    
    US East \(VA\)


    
    </td>
    <td valign="top">
    
    No


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    cf-us10


    
    </td>
    <td valign="top">
    
    US East \(VA\)


    
    </td>
    <td valign="top">
    
    No


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    cf-us30


    
    </td>
    <td valign="top">
    
    US Central \(IA\)


    
    </td>
    <td valign="top">
    
    No


    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="5">
    
     


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="2">
    
    Singapore


    
    </td>
    <td valign="top" rowspan="2">
    
    aws-ap-southeast-1


    
    </td>
    <td valign="top">
    
    cf-ap11


    
    </td>
    <td valign="top">
    
    Singapore


    
    </td>
    <td valign="top">
    
    Yes


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    cf-ap21


    
    </td>
    <td valign="top">
    
    Singapore


    
    </td>
    <td valign="top">
    
    No


    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="5">
    
     


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    South Korea / South Korea \(Seoul\)


    
    </td>
    <td valign="top">
    
    aws-ap-northeast-2


    
    </td>
    <td valign="top">
    
    cf-ap12


    
    </td>
    <td valign="top">
    
    South Korea \(Seoul\)


    
    </td>
    <td valign="top">
    
    Yes


    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="5">
    
     


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="4">
    
    Europe / Germany Frankfurt\(\)


    
    </td>
    <td valign="top" rowspan="4">
    
    aws-eu-central-1


    
    </td>
    <td valign="top">
    
    cf-eu11


    
    </td>
    <td valign="top">
    
    Europe \(Frankfurt\) EU Access


    
    </td>
    <td valign="top">
    
    Yes


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    cf-eu10


    
    </td>
    <td valign="top">
    
    Europe \(Frankfurt\)


    
    </td>
    <td valign="top">
    
    No


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    cf-eu20


    
    </td>
    <td valign="top">
    
    Europe \(Netherlands\)


    
    </td>
    <td valign="top">
    
    No


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    cf-eu30


    
    </td>
    <td valign="top">
    
    Europe \(Frankfurt\) GCP


    
    </td>
    <td valign="top">
    
    No


    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="5">
    
     


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Europe / Switzerland


    
    </td>
    <td valign="top">
    
    azure-switzerlandnorth


    
    </td>
    <td valign="top">
    
    cf-ch20


    
    </td>
    <td valign="top">
    
    Switzerland \(Zurich\) Azure EU Access


    
    </td>
    <td valign="top">
    
    Yes


    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="5">
    
     


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Asia Pacific


    
    </td>
    <td valign="top">
    
    aws-ap-south-1


    
    </td>
    <td valign="top">
    
    cf-in30


    
    </td>
    <td valign="top">
    
    India \(Mumbai\)


    
    </td>
    <td valign="top">
    
    Yes


    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="5">
    
     


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Brazil


    
    </td>
    <td valign="top">
    
    aws-sa-east-1


    
    </td>
    <td valign="top">
    
    cf-br10


    
    </td>
    <td valign="top">
    
    Brazil \(São Paulo\)


    
    </td>
    <td valign="top">
    
    Yes


    
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



<a name="task_yvb_pk1_rdb__postreq_m4d_nth_fwb"/>

## Next Steps

\(Optional\) Retrieve the audit logs via the Audit Log Retrieval API. See [Audit Log Retrieval API Usage for Subaccounts in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retrieval-api-usage-for-subaccounts-in-cloud-foundry-environment).

