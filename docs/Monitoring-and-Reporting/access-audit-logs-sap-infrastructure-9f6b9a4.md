<!-- loio9f6b9a41db6c43b09f2b39b0e262f92b -->

# Access Audit Logs \(SAP Infrastructure\)

You can access the audit logs for changes in the personal data, successful, and failed authentications, in Identity Authentication



## Context

> ### Note:  
> The content in this section is only relevant for tenants on the SAP infrastructure.

To view the audit logs you should generate Client ID and Client Secret for audit logs in the administration console for Identity Authentication first. After that you should obtain an access token, and then call the audit log retrieval API to access the data.

The audit log entries are retained for:

-   SAP BTP, Cloud Foundry environment \(for tenants on the AWS and Azure infrastructure.\) - 90 days
-   SAP BTP, Neo environment \(for tenants on the SAP infrastructure\)- 201 days

To access the audit logs, follow the procedures below:

 <a name="task_yvb_pk1_rdb"/>

<!-- task\_yvb\_pk1\_rdb -->

## 1. Generate Client Credentials for Audit Logs



<a name="task_yvb_pk1_rdb__context_lkb_bl1_rdb"/>

## Context

The Client ID and Client Secret for the current tenant are generated in the administration console for Identity Authentication.



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

3.  Under *Generate Client Credentials for Audit Logs* choose the *Generate* button.

    A dialog box with the generated Client ID and Client Secret appears.

    > ### Remember:  
    > Make sure that you copy the Client Secret from the dialog box. When you choose *OK*, the dialog box closes, and you can’t retrieve the Client Secret from the system anymore.




<a name="task_yvb_pk1_rdb__result_rg4_bm1_rdb"/>

## Results

The generated Client ID can be seen under *Generate Client Credentials for Audit Logs* in the *Audit and Change Logs* page.

> ### Tip:  
> To delete the client credentials, choose the ![](../Operation-Guide/images/delete_icon_4801c38.png) icon next to the generated Client ID. This deletes the Client ID and Client Secret from the system.

 <a name="task_h2l_qk1_rdb"/>

<!-- task\_h2l\_qk1\_rdb -->

## 2. Obtain an Access Token



<a name="task_h2l_qk1_rdb__context_rly_bt1_rdb"/>

## Context

Use the Client ID and Client Secret generated for the current tenant in the administration console for Identity Authentication to obtain an access token. For more information about how to obtain the access token see **2. Get an OAuth Access Token** in [Using Platform APIs](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/392af9d162694d6595499f1549978aa6.html).

> ### Tip:  
> The URL for the POST request looks like this: <code>https://api.&lt;SAP BTP host&gt;/oauth2/apitoken/v1?grant_type=client_credentials</code>
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*.
> 
> For tenants in Australia \(Sydney\), you should use `ap1.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For tenants in Brazil \(São Paulo\), you should use `br1.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For tenants in Europe, you should use `eu1.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For tenants in Japan \(Tokyo\), you should use `jp1.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For tenants in United States \(US East\), you should use `us3.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For more information, see [Regional Availability](../regional-availability-be600ca.md) and [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).

 <a name="task_pxw_5k1_rdb"/>

<!-- task\_pxw\_5k1\_rdb -->

## 3. Call the Audit Log Retrieval API



<a name="task_pxw_5k1_rdb__context_cl3_151_rdb"/>

## Context

To access the audit logs you should call the audit log retrieval API. You need the Client ID and Client Secret for the current tenant, generated in the administration console for Identity Authentication, and the access token. For more information, see [Audit Log Retrieval API Usage](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e4d818da43af43e1983df8e9e5caadb2.html).

You can filter the audit logs by time and/or categories. The categories that you can filter are:

-   audit.authentication - audit logs related to authentication \(failed, successful, type\)
-   audit.data-change - audit logs related to changes in personal data

> ### Remember:  
> The URI for the GET request looks like this:
> 
>  <code>https://api.&lt;SAP BTP host&gt;/auditlog/v1/accounts/&lt;Tenant ID&gt;/AuditLogRecordsIds?$filter=(Time ge '2018-05-17T13.00.00' and Time le '2018-05-18T05.00.00')and Category eq '&lt;category&gt;'</code>
> 
> The timestamp is in Coordinated Universal Time \(UTC\).
> 
> Use that URI in the examples in [Audit Log Retrieval API Usage](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e4d818da43af43e1983df8e9e5caadb2.html).
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*.
> 
> For tenants in Australia \(Sydney\), you should use `ap1.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For tenants in Brazil \(São Paulo\), you should use `br1.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For tenants in Europe, you should use `eu1.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For tenants in Japan \(Tokyo\), you should use `jp1.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For tenants in United States \(US East\), you should use `us3.hana.ondemand.com` for the SAP BTP host in the request.
> 
> For more information, see [Regional Availability](../regional-availability-be600ca.md) and [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).

