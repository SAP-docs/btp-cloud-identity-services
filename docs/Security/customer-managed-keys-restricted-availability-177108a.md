<!-- loio177108a1e129486983e7c4bc125db3bb -->

# Customer Managed Keys \(Restricted Availability\)

Your organization can control the encryption keys for data stored in SAP Cloud Identity Services using [SAP Data Custodian Key Management Service](https://help.sap.com/docs/sap-data-custodian/key-management-service/what-is-key-management-service-page).

> ### Caution:  
> Operations with keys at SAP Data Custodian side must be executed with caution. For example, disabling a key could block the SAP Cloud Identity Services tenant and you won't able to enable the key again.
> 
> You can set up workflow approvals to safeguard against unwanted operations changes. For more information, see [Workflow Approval Operations](https://help.sap.com/docs/sap-data-custodian/help-guide/workflow-approval-operations?version=2305).

Before using the customer managed keys, be aware of the following specifics:

<a name="concept_ch4_gg5_tyb"/>

<!-- concept\_ch4\_gg5\_tyb -->

## Limitations



<a name="concept_ch4_gg5_tyb__section_pqd_jg5_tyb"/>

## Identity Authentication



### Identity Directory SCIM REST API

-   SCIM filtering operators "`co`" and "`sw`" are not supported. Identity Directory SCIM REST API returns response *Bad Request \(400\)*.

-   SCIM filtering operators "`gt`" and "`lt`" are supported only for parameters `meta.created` and `meta.lastModified`.


For more information, see [Identity Directory API](../Development/identity-directory-api-5be5692.md).



### Administration Console

-   *Users Authorizations* \> *User Management* - \(Filtered and Unfiltered Search\) only exact search is supported for *User ID*, *Global User ID*, *Email*, *Login Name*, *First Name* and *Last Name*.

    For more information, see [Search Users](../Operation-Guide/search-users-06078a6.md).

-   *Users Authorizations* \> *Groups* - when adding users to a group, only exact search is supported for *First Name*, *Last Name*, *Email*, *Login Name* and *SCIM ID*.

    For more information, see [Add Users to a Group](../Operation-Guide/add-users-to-a-group-d2e1a01.md).




<a name="concept_ch4_gg5_tyb__section_alq_jg5_tyb"/>

## Identity Provisioning

-   An encrypted SAP Cloud Identity Services tenant allows you to search for job and real-time logs by providing the complete name of the source system and the entity ID. This means that if you want to search for the job logs of a source system named `IAS_Source`, you must enter its complete name in the search field. The same applies for entity IDs. You must enter the complete ID of the user or group.

    For more information, see [Monitor Provisioning Job Logs](https://help.sap.com/docs/identity-provisioning/identity-provisioning/search-and-view-provisioning-job-logs?version=Cloud) and [Monitor Real-Time Logs](https://help.sap.com/docs/identity-provisioning/identity-provisioning/search-and-view-provisioning-job-logs?version=Cloud).

-   Filtering operators other than `eq` are not supported for Identity Authentication \(version 2\) and Local Identity Directory source systems. If your tenant is encrypted, this results in failed provisioning jobs.

    For more information, see [List of Properties](https://help.sap.com/docs/identity-provisioning/identity-provisioning/list-of-properties?version=Cloud) → `ias.user.filter` and `idds.user.filter`


<a name="concept_u2z_gg5_tyb"/>

<!-- concept\_u2z\_gg5\_tyb -->

## Unencrypted Data

Meta information used in general processing, for example data model Version, tenant IdentifierTemporary Data with limited lifetime.

<a name="concept_vwf_hg5_tyb"/>

<!-- concept\_vwf\_hg5\_tyb -->

## Configuration

To configure the customer managed keys in the administration console for SAP Cloud Identity Services, follow the procedure described in [Configure Customer Managed Keys in Administration Console \(Restricted Availability\)](../Operation-Guide/configure-customer-managed-keys-in-administration-console-restricted-availability-fe6e30c.md).

