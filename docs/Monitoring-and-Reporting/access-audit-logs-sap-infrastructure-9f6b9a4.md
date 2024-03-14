<!-- loio9f6b9a41db6c43b09f2b39b0e262f92b -->

# Access Audit Logs \(SAP Infrastructure\)

Access the audit logs for changes in the personal data, successful, and failed authentications for Identity Authentication tenants on the SAP infrastructure.



## Context

> ### Note:  
> The content in this section is only relevant for tenants on the SAP infrastructure.

To view the audit logs, you should generate Client ID and Client Secret for audit logs in the administration console for SAP Cloud Identity Services first. After that you should obtain an access token, and then call the audit log retrieval API to access the data.

The audit log entries for tenants on the SAP infrastructure are retained for 201 days.

To access the audit logs, follow the procedures below:

<a name="task_yvb_pk1_rdb"/>

<!-- task\_yvb\_pk1\_rdb -->

## 1. Generate Client Credentials for Audit Logs



<a name="task_yvb_pk1_rdb__context_lkb_bl1_rdb"/>

## Context

The Client ID and Client Secret for the current tenant are generated in the administration console for SAP Cloud Identity Services.



<a name="task_yvb_pk1_rdb__steps_mkb_bl1_rdb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Audit and Change Logs* tile.

3.  Choose one of the following options:

    -   *NEO* tab
        -   Under *Generate Client Credentials for Audit Logs* choose the *Generate* button.

            A dialog box with the generated Client ID and Client Secret appears.

            > ### Remember:  
            > Make sure that you copy the Client Secret from the dialog box. When you choose *OK*, the dialog box closes, and you can’t retrieve the Client Secret from the system anymore.

            The generated Client ID can be seen in the *Generate Client Credentials for Audit Logs* section under the *NEO* tab.

            > ### Tip:  
            > To delete the client credentials, choose the ![](../Operation-Guide/images/delete_icon_4801c38.png) icon next to the generated Client ID. This deletes the Client ID and Client Secret from the system.


    -   *Cloud Foundry* tab

        1.  Choose *\+Add*.
        2.  Fill in the required information in the pop up and save your changes.


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
            
            *Tenant ID*
            
            </td>
            <td valign="top">
            
            Required. The tenant ID of your Cloud Foundry account.
            
            </td>
            </tr>
            <tr>
            <td valign="top">
            
            *Region*
            
            </td>
            <td valign="top">
            
            SAP BTP, Cloud Foundry region. You can choose a region from the options in the dropdown. For more information, see the mapping table.
            
            </td>
            </tr>
            <tr>
            <td valign="top">
            
            *Subdomain*
            
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
            <td valign="top">
            
            US West / East US
            
            </td>
            <td valign="top">
            
            azure-eastus
            
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
            
             
            
            </td>
            <td valign="top">
            
             
            
            </td>
            <td valign="top">
            
             
            
            </td>
            <td valign="top">
            
             
            
            </td>
            <td valign="top">
            
             
            
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
            
            Europe / Germany \(Frankfurt\)
            
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
            <tr>
            <td valign="top" colspan="5">
            
             
            
            </td>
            </tr>
            <tr>
            <td valign="top" rowspan="4">
            
            Europe / Germany \(Frankfurt\)
            
            </td>
            <td valign="top" rowspan="4">
            
            eu-de-2
            
            </td>
            <td valign="top">
            
            cf-eu10
            
            </td>
            <td valign="top">
            
            Europe \(Frankfurt\)
            
            </td>
            <td valign="top">
            
            Yes
            
            </td>
            </tr>
            <tr>
            <td valign="top">
            
            cf-eu11
            
            </td>
            <td valign="top">
            
            Europe \(Frankfurt\) EU Access
            
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
            <td valign="top" rowspan="2">
            
            Australia \(Sydney\)
            
            </td>
            <td valign="top" rowspan="2">
            
            ap-au-1
            
            </td>
            <td valign="top">
            
            cf-ap10
            
            </td>
            <td valign="top">
            
            Australia \(Sydney\)
            
            </td>
            <td valign="top">
            
            Yes
            
            </td>
            </tr>
            <tr>
            <td valign="top">
            
            cf-ap20
            
            </td>
            <td valign="top">
            
            Australia \(Sydney\)
            
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
            
            Japan \(Tokyo\)
            
            </td>
            <td valign="top" rowspan="2">
            
            ap-jp-1
            
            </td>
            <td valign="top">
            
            cf-jp10
            
            </td>
            <td valign="top">
            
            Japan \(Tokyo\)
            
            </td>
            <td valign="top">
            
            Yes
            
            </td>
            </tr>
            <tr>
            <td valign="top">
            
            cf-jp20
            
            </td>
            <td valign="top">
            
            Japan \(Tokyo\)
            
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
            
            US East / East US
            
            </td>
            <td valign="top" rowspan="2">
            
            na-us-2
            
            </td>
            <td valign="top">
            
            cf-us10
            
            </td>
            <td valign="top">
            
            US East \(VA\)
            
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
            <td valign="top" colspan="5">
            
             
            
            </td>
            </tr>
            <tr>
            <td valign="top" rowspan="4">
            
            Europe / Netherlands \(Amsterdam\)
            
            </td>
            <td valign="top" rowspan="4">
            
            eu-nl-1
            
            </td>
            <td valign="top">
            
            cf-eu10
            
            </td>
            <td valign="top">
            
            Europe \(Frankfurt\)
            
            </td>
            <td valign="top">
            
            Yes
            
            </td>
            </tr>
            <tr>
            <td valign="top">
            
            cf-eu11
            
            </td>
            <td valign="top">
            
            Europe \(Frankfurt\) EU Access
            
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
            <td valign="top" rowspan="2">
            
            US East / East US
            
            </td>
            <td valign="top" rowspan="2">
            
            na-us-1
            
            </td>
            <td valign="top">
            
            cf-us10
            
            </td>
            <td valign="top">
            
            US East \(VA\)
            
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
            </table>
            
        3.  Save your changes.

            > ### Caution:  
            > If your SAP Cloud Identity Services tenant is migrated to a new region, you must remove the current configuration and repeat procedure with the new region.

        4.  View the audit logs. You have two options to do that:
            -   \(if subdomain is configured\) choose the link to the *Audit Log Viewer* in the *Audit Service Configuration* in the administration console

            -   in the cockpit, navigate to *Services* \> *Instances and Subscriptions* \> *Audit Log Viewer*.


        The configuration will be enabled with the next 15 minutes.

        **Next Steps**: \(Optional\) Retrieve the audit logs via the Audit Log Retrieval API. See [Audit Log Retrieval API Usage for Subaccounts in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retrieval-api-usage-for-subaccounts-in-cloud-foundry-environment).



<a name="task_h2l_qk1_rdb"/>

<!-- task\_h2l\_qk1\_rdb -->

## 2. Obtain an Access Token



<a name="task_h2l_qk1_rdb__context_rly_bt1_rdb"/>

## Context

Use the Client ID and Client Secret generated for the current tenant in the administration console for SAP Cloud Identity Services to obtain an access token. For more information about how to obtain the access token see **2. Get an OAuth Access Token** in [Using Platform APIs](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/392af9d162694d6595499f1549978aa6.html).

> ### Tip:  
> The URL for the POST request looks like this: <code>https://api.&lt;SAP BTP Host&gt;/oauth2/apitoken/v1?grant_type=client_credentials</code>
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Cluster
> 
> </th>
> <th valign="top">
> 
> Tenant Region
> 
> </th>
> <th valign="top">
> 
> SAP BTP Host in Request
> 
> </th>
> </tr>
> <tr>
> <td valign="top" rowspan="2">
> 
> Europe
> 
> </td>
> <td valign="top" rowspan="2">
> 
> Amsterdam
> 
> </td>
> <td valign="top">
> 
> `eu1.hana.ondemand.com` \(primary\)
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> `eu3.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top" rowspan="2">
> 
> Asia Pacific
> 
> </td>
> <td valign="top" rowspan="2">
> 
> Sydney/Tokyo
> 
> </td>
> <td valign="top">
> 
> `ap1.hana.ondemand.com` \(primary\)
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> `jp1.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Japan
> 
> </td>
> <td valign="top">
> 
> Tokyo/Osaka
> 
> </td>
> <td valign="top">
> 
> `jp1.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top" rowspan="2">
> 
> US-East
> 
> </td>
> <td valign="top" rowspan="2">
> 
> Sterling/Toronto
> 
> </td>
> <td valign="top">
> 
> `us3.hana.ondemand.com` \(primary\)
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> `us1.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Saudi Arabia
> 
> </td>
> <td valign="top">
> 
> Riyadh/Dammam
> 
> </td>
> <td valign="top">
> 
> `sa1.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> China
> 
> </td>
> <td valign="top">
> 
> Shanghai
> 
> </td>
> <td valign="top">
> 
> `cn1.platform.sapcloud.cn`
> 
> </td>
> </tr>
> </table>
> 
> Use the primary host for your search. If the audit log is not found there, use the other hosts.
> 
> For more information, see [Regional Availability](../regional-availability-be600ca.md) and [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).

<a name="task_pxw_5k1_rdb"/>

<!-- task\_pxw\_5k1\_rdb -->

## 3. Call the Audit Log Retrieval API



<a name="task_pxw_5k1_rdb__context_cl3_151_rdb"/>

## Context

To access the audit logs, you should call the audit log retrieval API. You need the Client ID and Client Secret for the current tenant, generated in the administration console for SAP Cloud Identity Services, and the access token. For more information, see [Audit Log Retrieval API Usage](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e4d818da43af43e1983df8e9e5caadb2.html).

You can filter the audit logs by time and/or categories. The categories that you can filter are:

-   audit.authentication - audit logs related to authentication \(failed, successful, type\)
-   audit.data-change - audit logs related to changes in personal data

> ### Remember:  
> The URI for the GET request looks like this:
> 
> <code>https://api.&lt;SAP BTP Host&gt;/auditlog/v1/accounts/&lt;Tenant ID&gt;/AuditLogRecordsIds?$filter=(Time ge '2018-05-17T13.00.00' and Time le '2018-05-18T05.00.00') and Category eq '&lt;category&gt;'</code>
> 
> The timestamp is in Coordinated Universal Time \(UTC\).
> 
> Use that URI in the examples in [Audit Log Retrieval API Usage](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e4d818da43af43e1983df8e9e5caadb2.html).
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*.
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Cluster
> 
> </th>
> <th valign="top">
> 
> Tenant Region
> 
> </th>
> <th valign="top">
> 
> SAP BTP Host in Request
> 
> </th>
> </tr>
> <tr>
> <td valign="top" rowspan="2">
> 
> Europe
> 
> </td>
> <td valign="top" rowspan="2">
> 
> Amsterdam
> 
> </td>
> <td valign="top">
> 
> `eu1.hana.ondemand.com` \(primary\)
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> `eu3.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top" rowspan="2">
> 
> Asia Pacific
> 
> </td>
> <td valign="top" rowspan="2">
> 
> Sydney/Tokyo
> 
> </td>
> <td valign="top">
> 
> `ap1.hana.ondemand.com` \(primary\)
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> `jp1.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Japan
> 
> </td>
> <td valign="top">
> 
> Tokyo/Osaka
> 
> </td>
> <td valign="top">
> 
> `jp1.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top" rowspan="2">
> 
> US-East
> 
> </td>
> <td valign="top" rowspan="2">
> 
> Sterling/Toronto
> 
> </td>
> <td valign="top">
> 
> `us3.hana.ondemand.com` \(primary\)
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> `us1.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Saudi Arabia
> 
> </td>
> <td valign="top">
> 
> Riyadh/Dammam
> 
> </td>
> <td valign="top">
> 
> `sa1.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> China
> 
> </td>
> <td valign="top">
> 
> Shanghai
> 
> </td>
> <td valign="top">
> 
> `cn1.platform.sapcloud.cn`
> 
> </td>
> </tr>
> </table>
> 
> Use the primary host for your search. If the audit log is not found there, use the other hosts.
> 
> For more information, see [Regional Availability](../regional-availability-be600ca.md) and [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).

