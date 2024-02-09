<!-- loioe664db0715bc4826ac51a6c34cbeac99 -->

# Change Logging and Audit Logging

Change logging records changes to personal data, while audit logging provides access to personal data, successful, and failed authentications. You may be required to gather this information for auditing purposes or legal requirements.



<a name="loioe664db0715bc4826ac51a6c34cbeac99__section_zwk_tyg_jdb"/>

## Audit Logs

Tenant administrators can access the audit logs for changes in the personal data, successful, and failed authentications in Identity Authentication. If you want to view the audit logs, you should generate Client ID and Client Secret for audit logs in the administration console for SAP Cloud Identity Services, obtain an access token, and call the audit log retrieval API to access the data. For more information, see [Access Audit Logs \(SAP Infrastructure\)](../Monitoring-and-Reporting/access-audit-logs-sap-infrastructure-9f6b9a4.md).

The audit log entries are retained for:

-   SAP BTP, Cloud Foundry environment \(for tenants on the AWS and Azure infrastructure.\) - 90 days
-   SAP BTP, Neo environment \(for tenants on the SAP infrastructure\)- 201 days



<a name="loioe664db0715bc4826ac51a6c34cbeac99__section_e3x_21h_jdb"/>

## Change Logs

Tenant administrators can access information about configuration changes made by administrators in Identity Authentication. You can download a CSV file with a history of the operations performed by administrators. For more information, see [Export Change Logs with a History of Administration Operations](../Monitoring-and-Reporting/export-change-logs-with-a-history-of-administration-operations-9d96aae.md).

