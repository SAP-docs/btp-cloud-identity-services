<!-- loio79b84ffca5c7480288ceadfb730d3014 -->

# SAP Market Communication for Utilities Bundle

SAP Market Communication for Utilities bundles with SAP Cloud Identity Services – Identity Authentication and Identity Provisioning.



> ### Note:  
> As of March 15, 2022, Identity Provisioning bundle tenants are created only on the infrastructure of SAP Cloud Identity Services. These tenants come with most of the provisioning systems \(connectors\) enabled by default. Identity Provisioning bundle tenants running on SAP BTP, Neo environment have a limited number of connectors enabled by default. These are illustrated in the diagram that follows.



<a name="loio79b84ffca5c7480288ceadfb730d3014__section_vlv_1fb_jlb"/>

## How to Obtain

After purchasing SAP Market Communication for Utilities, the technical contact person of your organization receives two onboarding e-mails from SAP. Each of them provides a tenant URL for accessing the SAP Cloud Identity Services administration console. One of the tenant URLs is for testing purposes, the other one is for productive usage. The technical contact person is granted the administrator permissions of the tenants and performs the initial logon to the SAP Cloud Identity Services administration console.



### Bundle Tenant on Neo Environment

![](images/IPS_MaCo_Bundle_807c540.png)



<a name="loio79b84ffca5c7480288ceadfb730d3014__section_vd1_tlt_21c"/>

## How to Use

This bundle tenant is provisioned to your organization with preconfigured source and target systems.

The Identity Authentication system \(named **IAS for MaCo – source**\) is configured as the source, while the SAP Market Communication for Utilities system \(named **MaCo-<subdomain\>**\) is configured as the target that reads from this source.

Default user groups for SAP Market Communication for Utilities are created in Identity Authentication. Communication between SAP Market Communication for Utilities and Identity Provisioning is already established, using **ClientCertificateAuthentication**. For more information, see [What has the system automatically prepared for the synchronization?](https://help.sap.com/docs/market-communication-utilities/administration-guide/synchronizing-users-with-cloud-abap-tenants#what-has-the-system-automatically-prepared-for-the-synchronization?).

> ### Note:  
> A single SAP Cloud Identity Services tenant with configured Identity Authentication source system is used for provisioning to all SAP Market Communication for Utilities tenants that you obtain.

The transformations in the preconfigured systems \(provided below\) differ from the default Identity Provisioning transformations in [Identity Authentication \(source system\)](identity-authentication-e4e25f1.md) and [SAP Market Communication for Utilities \(target system\)](sap-market-communication-for-utilities-5aa97c7.md), as they are adapted to the scenarios relevant to this bundle.


<table>
<tr>
<th valign="top">

Identity Authentication \(source system\)

</th>
<th valign="top">

SAP Market Communication for Utilities \(target system\)

</th>
</tr>
<tr>
<td valign="top">

> ### Code Syntax:  
> ```
> {
>        "user": {
>         "mappings": [
>             {
>                 "sourcePath": "$.id",
>                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['userId']",
>                 "targetVariable": "entityIdSourceSystem"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
>             },
>             {
>                 "sourcePath": "$.schemas",
>                 "preserveArrayWithSingleElement": true,
>                 "targetPath": "$.schemas"
>             },
>             {
>                 "sourcePath": "$.userName",
>                 "optional": true,
>                 "targetPath": "$.userName",
>                 "correlationAttribute": true
>             },
>             {
>                 "sourcePath": "$.name.givenName",
>                 "optional": true,
>                 "targetPath": "$.name.givenName"
>             },
>             {
>                 "sourcePath": "$.name.middleName",
>                 "optional": true,
>                 "targetPath": "$.name.middleName"
>             },
>             {
>                 "sourcePath": "$.name.familyName",
>                 "optional": true,
>                 "targetPath": "$.name.familyName"
>             },
>             {
>                 "sourcePath": "$.name.honorificPrefix",
>                 "optional": true,
>                 "targetPath": "$.name.honorificPrefix"
>             },
>             {
>                 "sourcePath": "$.emails[*].value",
>                 "preserveArrayWithSingleElement": true,
>                 "targetPath": "$.emails[?(@.value)]"
>             },
>             {
>                 "sourcePath": "$.emails[?(@.primary== true)].value",
>                 "correlationAttribute": true
>             },
>             {
>                 "sourcePath": "$.active",
>                 "targetPath": "$.active"
>             },
>             {
>                 "sourcePath": "$.userType",
>                 "optional": true,
>                 "targetPath": "$.userType"
>             },
>             {
>                 "sourcePath": "$.addresses",
>                 "preserveArrayWithSingleElement": true,
>                 "optional": true,
>                 "targetPath": "$.addresses"
>             },
>             {
>                 "sourcePath": "$.locale",
>                 "optional": true,
>                 "targetPath": "$.locale"
>             },
>             {
>                 "sourcePath": "$.phoneNumbers",
>                 "preserveArrayWithSingleElement": true,
>                 "optional": true,
>                 "targetPath": "$.phoneNumbers"
>             },
>             {
>                 "sourcePath": "$.timeZone",
>                 "optional": true,
>                 "targetPath": "$.timezone"
>             },
>             {
>                 "sourcePath": "$.displayName",
>                 "optional": true,
>                 "targetPath": "$.displayName"
>             },
>             {
>                 "sourcePath": "$.groups",
>                 "preserveArrayWithSingleElement": true,
>                 "optional": true,
>                 "targetPath": "$.groups"
>             },
>             {
>                 "condition": "$.displayName EMPTY true",
>                 "targetPath": "$.displayName",
>                 "type": "remove"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validFrom']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['validTo']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystemId']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['sourceSystem']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['costCenter']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['displayName']"
>             },
>             {
>                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']",
>                 "optional": true,
>                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']"
>             },
>             {
>                 "sourcePath": "$.company",
>                 "optional": true,
>                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['organization']"
>             }
>         ]
>     },
>     "group": {
>         "mappings": [
>             {
>                 "sourcePath": "$.id",
>                 "targetVariable": "entityIdSourceSystem"
>             },
>             {
>                 "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
>                 "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
>             },
>             {
>                 "sourcePath": "$.displayName",
>                 "targetPath": "$.displayName"
>             },
>             {
>                 "sourcePath": "$.members",
>                 "preserveArrayWithSingleElement": true,
>                 "optional": true,
>                 "targetPath": "$.members"
>             }
>         ]
>     }
> }
> ```



</td>
<td valign="top">

> ### Code Syntax:  
> ```
> {
>         "user": {
>         "condition": "$.groups[?(@.display== 'MaCo_BU_<subdomain>' || @.display== 'MaCo_PW_<subdomain>' || @.display== 'MaCo_DPP_<subdomain>')] EMPTY false ",
>         "mappings": [
>             {
>                 "sourcePath": "$.userName",
>                 "targetPath": "$.personExternalID"
>             },
>             {
>                 "sourcePath": "$.externalId",
>                 "optional": true,
>                 "targetPath": "$.personExternalID"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
>                 "optional": true,
>                 "targetPath": "$.personExternalID"
>             },
>             {
>                 "sourceVariable": "entityIdTargetSystem",
>                 "targetPath": "$.personID"
>             },
>             {
>                 "constant": "false",
>                 "targetPath": "$.markedForArchivingIndicator"
>             },
>             {
>                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
>                 "optional": true,
>                 "targetPath": "$.user.globalUserID"
>             },
>             {
>                 "targetPath": "$.businessPartnerRoleCode",
>                 "type": "valueMapping",
>                 "sourcePaths": [
>                     "$.userType"
>                 ],
>                 "defaultValue": "BUP003",
>                 "valueMappings": [
>                     {
>                         "key": [
>                             "Employee"
>                         ],
>                         "mappedValue": "BUP003"
>                     },
>                     {
>                         "key": [
>                             "Freelancer"
>                         ],
>                         "mappedValue": "BBP010"
>                     },
>                     {
>                         "key": [
>                             "Service Performer"
>                         ],
>                         "mappedValue": "BBP005"
>                     }
>                 ]
>             },
>             {
>                 "sourceVariable": "currentDate",
>                 "targetPath": "$.validityPeriod.startDate",
>                 "scope": "createEntity"
>             },
>             {
>                 "constant": "9999-12-31",
>                 "targetPath": "$.validityPeriod.endDate",
>                 "scope": "createEntity"
>             },
>             {
>                 "sourceVariable": "currentDate",
>                 "targetPath": "$.user.validityPeriod.startDate",
>                 "scope": "createEntity"
>             },
>             {
>                 "constant": "9999-12-31",
>                 "targetPath": "$.user.validityPeriod.endDate",
>                 "scope": "createEntity"
>             },
>             {
>                 "sourcePath": "$.name.givenName",
>                 "optional": true,
>                 "targetPath": "$.personalInformation.firstName"
>             },
>             {
>                 "sourcePath": "$.name.familyName",
>                 "targetPath": "$.personalInformation.lastName"
>             },
>             {
>                 "sourcePath": "$.name.middleName",
>                 "optional": true,
>                 "targetPath": "$.personalInformation.middleName"
>             },
>             {
>                 "sourcePath": "$.name.formatted",
>                 "optional": true,
>                 "targetPath": "$.personalInformation.personFullName"
>             },
>             {
>                 "sourcePath": "$.userName",
>                 "targetPath": "$.user.userName"
>             },
>             {
>                 "sourcePath": "$.locale",
>                 "optional": true,
>                 "targetPath": "$.user.logonLanguageCode"
>             },
>             {
>                 "sourcePath": "$.emails[0].value",
>                 "optional": true,
>                 "targetPath": "$.workplaceInformation.emailAddress"
>             },
>             {
>                 "constant": "false",
>                 "targetPath": "$.user.lockedIndicator"
>             },
>             {
>                 "condition": "$.active == false",
>                 "constant": "true",
>                 "targetPath": "$.user.lockedIndicator"
>             }
>         ]
>     },
>     "group": {
>         "condition": "$.displayName=='MaCo_BU_<subdomain>' || $.displayName=='MaCo_PW_<subdomain>' || $.displayName=='MaCo_DPP_<subdomain>'",
>         "mappings": [
>             {
>                 "targetPath": "$.ROLE_NAME",
>                 "targetVariable": "entityIdTargetSystem",
>                 "type": "valueMapping",
> 
>                 "defaultValue": "",
>                 "sourcePaths": [
>                     "$.displayName"
>                 ],
>                 "valueMappings": [
>                     {
>                         "key": [
>                             "MaCo_BU_<subdomain>"
>                         ],
>                         "mappedValue": "BR_CUSTOMER_USER_AGENT"
>                     },
>                     {
>                         "key": [
>                             "MaCo_PW_<subdomain>"
>                         ],
>                         "mappedValue": "BR_CUSTOMER_POWER_USER"
>                     },
>                     {
>                         "key": [
>                             "MaCo_DPP_<subdomain>"
>                         ],
>                         "mappedValue": "BR_CUSTOMER_DPP_USER"
>                     }
>                 ]
>             },
>             {
>                 "sourcePath": "$.members[*].value",
>                 "preserveArrayWithSingleElement": true,
>                 "optional": true,
>                 "targetPath": "$.members[?(@.value)]",
>                 "functions": [
>                     {
>                         "function": "resolveEntityIds"
>                     }
>                 ]
>             }
>         ]
>     }
> }
> ```



</td>
</tr>
</table>

In addition, bulk operations are enabled for the SAP Market Communication for Utilities target. The following properties are configured:

-   maco.bulk.operations.max.count = 50
-   maco.support.bulk.operation = true
-   maco.user.roles.overwrite = false
-   maco.hr.switch.active = false
-   ips.date.variable.format = yyyy-MM-dd

For more information about these properties, see [List of Properties](list-of-properties-d6f3577.md).

You can review the provisioning system configurations, adjust them if needed and schedule read jobs.

For more information on the manual tasks you can perform, see [What do you need to do manually?](https://help.sap.com/docs/market-communication-utilities/administration-guide/synchronizing-users-with-cloud-abap-tenants#what-do-you-need-to-do-manually?).

The other provisioning systems in the scope of this bundle are enabled. This means that you can start adding and configuring them in the Identity Provisioning UI. See: [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md)

**Related Information**  


[SAP Market Communication for Utilities](https://help.sap.com/docs/market-communication-for-utilities?locale=en-US)

