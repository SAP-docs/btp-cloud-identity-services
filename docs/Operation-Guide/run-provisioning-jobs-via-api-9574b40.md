<!-- loio9574b40cc92b40b69857be348aa15b0c -->

# Run Provisioning Jobs via API

You can run a provisioning job via API requests.



<a name="loio9574b40cc92b40b69857be348aa15b0c__prereq_prb_chm_jvb"/>

## Prerequisites

You need a technical user with *Access Identity Provisioning Tenant Admin API* permission assigned. For more information, see [Managing Administrators](https://help.sap.com/docs/identity-authentication/identity-authentication/managing-administrators?version=Cloud).



## Context

Use the Identity Provisioning tenant admin API to run a provisioning job from an API client. The API is available on the SAP Business Accelerator Hub: [SAP Cloud Identity Services](https://api.sap.com/package/SCPIdentityServices/rest) *Identity Provisioning Service* \> *API Reference* \> *Jobs*. The URL for accessing the Tenant Admin API follows the pattern: <code>https://<i class="varname">&lt;ias-tenant-host&gt;</i>/ips/service/publicapi/v1/startJob/{SourceSystemId}/jobs/{JobType}</code>, where:

-   *<SourceSystemId\>* is the ID of the source system, displayed at the end of the system URL in the SAP Cloud Identity Services administration console.

-   *<JobType\>* is `READ` or `RESYNC`.


> ### Note:  
> This functionality is available only for Identity Provisioning tenants running on SAP Cloud Identity infrastructure.

