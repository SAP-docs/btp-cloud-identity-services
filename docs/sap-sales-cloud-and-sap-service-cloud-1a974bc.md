<!-- loio1a974bcb1e6b4a6ebd5078e81ebf7875 -->

# SAP Sales Cloud and SAP Service Cloud

Follow this procedure to set up SAP Sales Cloud and SAP Service Cloud, formerly known as *SAP Cloud for Customer* \(in short, C4C\), as a target system.



<a name="loio1a974bcb1e6b4a6ebd5078e81ebf7875__prereq_kfb_sdl_5cb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Identity Access Governance** bundle option.

To integrate SAP Sales Cloud and SAP Service Cloud with Identity Provisioning, you need to use SAP Cloud Integration \(SAP CI\). This service provides a package with integration flows \(iFlows\) for enabling the creation of users and assignment of users to groups via SCIM API in SAP Sales Cloud and SAP Service Cloud.

-   To configure SAP Cloud Integration and SAP Sales Cloud and SAP Service Cloud, see: [Identity Provisioning in SAP Cloud for Customer using System for Cross-Domain Identity Management \(SCIM\)](https://help.sap.com/viewer/b5196c50731249cdb877bd3b44d9f48d/CLOUD/en-US/30727bdccd6a4646aa7087bebd783ecd.html)

-   To set up and use the *SAP Cloud for Customer Integration with Identity Provisioning via System for Cross-domain Identity Management* package, see: [SAP Business Accelerator Hub: SAP Cloud for Customer Integration with Identity Provisioning via System for Cross-domain Identity Management](https://api.sap.com/package/IdentityProvisioninginSAPCloudforCustomerviaSCIM/overview)




## Context

SAP Sales Cloud and SAP Service Cloud is a cloud-based solution that helps customers manage day-to-day sales and service interactions by sending and receiving signals between front- and back-office solutions and providing a single view of the customer.

You can use Identity Provisioning to configure SAP Sales Cloud and SAP Service Cloud as a target system where you can provision users and group members from source systems. Keep in mind that once you have provisioned the entities to SAP Sales Cloud and SAP Service Cloud, a *business user* and an *employee* are created for every provisioned user. The business user is required for the provisioned user to log into the SAP Sales Cloud and SAP Service Cloud system.

This scenario is relevant for new SAP Sales Cloud and SAP Service Cloud customers \(green-field approach\). This means that users are first provisioned to Identity Authentication \(uploaded from files or provisioned by Identity Provisioning from another source system\) and afterwards provisioned to SAP Sales Cloud and SAP Service Cloud using Identity Provisioning.

SAP Sales Cloud and SAP Service Cloud provides three versions of APIs. They differ in type and require configuration of specific set of properties \(see **step 3.** in the main **Procedure**\). By default, the Identity Provisioning service uses version **3**.



### Version 1 \(SOAP-based API\)

> ### Note:  
> The SOAP-based API version 1 is depricated.

When created via API version 1, users are initially transferred to a staging area, and then can be replicated to the C4C system manually or via a job, depending on your tenant setup. This API version is SOAP based. In the SAP Sales Cloud and SAP Service Cloud admin console you can distinguish it by its name – */humancapitalmanagementmasterd6*.

To learn how to replicate users \(using API v.1\), see: [Employee Master Data Replication](https://help.sap.com/viewer/cea15f900ca04c4faa35d3044577fe27/1811/en-US/187a97f8763d10148a1ee7f17f6a9dfa.html)



### Version 2 \(SOAP-based API\)

When using API version 2, users are created immediately – there is no need to transfer them to a staging area. This API version is SOAP based. In the C4C admin console, you can distinguish it by its name */employeereplicationin2*.



### Version 3 \(SCIM 2.0 based API\)

When using API version 3, users are created immediately. There is no need to transfer them to a staging area.

For more information on how to set up and use the *Identity Provisioning in SAP Cloud for Customer using a System for Cross-domain Identity Management \(SCIM\)* package, see the *Prerequisites* section.

> ### Note:  
> If, for some reason, you have access to all API versions, you must use **separate** provisioning systems for each version, to avoid data inconsistency errors.



<a name="loio1a974bcb1e6b4a6ebd5078e81ebf7875__steps_r2s_fdl_5cb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Target Systems*.

3.  Add *SAP Sales Cloud and SAP Service Cloud* as a target system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Choose the *Properties* tab to configure the connection settings for your system.

    > ### Note:  
    > If your tenant is running on SAP BTP, Neo environment, you can create a [connectivity destination](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/72696d6d06c0490394ac3069da600278.html) in your subaccount in the SAP BTP cockpit, and then select it from the *Destination Name* combo box in your Identity Provisioning User Interface.
    > 
    > If one and the same property exists both in the cockpit and in the *Properties* tab, the value set in the *Properties* tab is considered with higher priority.
    > 
    > We recommend that you use the *Properties* tab. Use a connectivity destination only if you need to reuse one and the same configuration for multiple provisioning systems.

    **Mandatory Properties**


    <table>
    <tr>
    <th valign="top">

    Property Name
    
    </th>
    <th valign="top">

    Description & Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `Type`
    
    </td>
    <td valign="top">
    
    Enter: *HTTP*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `URL`
    
    </td>
    <td valign="top">
    
    Enter SAP Cloud Integration runtime URL.

    See: [How to Get SAP Cloud Integration Runtime URL](https://help.sap.com/docs/sap-digital-manufacturing/integration-guide/how-to-get-sap-cloud-integration-runtime-url)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Enter: *Internet*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Authentication`
    
    </td>
    <td valign="top">
    
    Enter: *BasicAuthentication*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Enter SAP Cloud Integration user ID to connect to SAP Cloud Integration. See:

    -   [Setting Up Inbound HTTP Connections \(with Basic Authentication\), Neo Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/391c45cfcd0f4435952ab085283b7f7d.html)

    -   [Basic Authentication of IdP User for Integration Flow Processing \(Cloud Foundry environment\)](https://help.sap.com/docs/CLOUD_INTEGRATION/368c481cd6954bdfa5d0435479fd4eaf/5d46e56550a048e99995f23e1e20083a.html)



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter SAP Cloud Integration password to connect to SAP Cloud Integration. See:

    -   [Setting Up Inbound HTTP Connections \(with Basic Authentication\), Neo Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/391c45cfcd0f4435952ab085283b7f7d.html)

    -   [Basic Authentication of IdP User for Integration Flow Processing \(Cloud Foundry environment\)](https://help.sap.com/docs/CLOUD_INTEGRATION/368c481cd6954bdfa5d0435479fd4eaf/5d46e56550a048e99995f23e1e20083a.html)



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `c4c.api.version`
    
    </td>
    <td valign="top">
    
    The version of the SAP Sales Cloud and SAP Service Cloud API you use. Possible values – **1** \(deprecated\), **2**, or **3**. By default, the Identity Provisioning service uses version **3**.

    > ### Note:  
    > After you set up the communication arrangement, you can determine the API version used by your SAP Sales Cloud and SAP Service Cloud system. It represents the ID at the end of your generated URL – the name of API v.1 is *humancapitalmanagementmasterd6*, and for API v.2 is *employeereplicationin2*.


    
    </td>
    </tr>
    <tr>
    <td valign="top" align="center" colspan="2">
    
    **Relevant for API v.1** \(deprecated\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `RemoteSystemID`
    
    </td>
    <td valign="top">
    
    Enter the system instance ID, configured for the communication system setting in the C4C system.
    
    </td>
    </tr>
    <tr>
    <td valign="top" align="center" colspan="2">
    
    **Relevant for API v.2** 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `RecipientPartyID`
    
    </td>
    <td valign="top">
    
    Enter the recipient system name.

    Example: **0011SAP**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `SenderPartyID`
    
    </td>
    <td valign="top">
    
    Enter the name of the sender system name. It's equal to the value of property `RemoteSystemID` from API v.1.

    For example: **IPS**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`c4c.group.prefix`
    
    </td>
    <td valign="top">
    
    This property distinguishes SAP Sales Cloud and SAP Service Cloud groups by specific prefix. It is an optional property which does not appear by default at system creation.

    Example value: `C4C_`

    You can use the example value or provide your own.

    When **set in the target system**, only groups containing the `C4C_` prefix in their display name will be provisioned to SAP Sales Cloud and SAP Service Cloud. Groups without this prefix in the display name won't be provisioned.

    If the property is not set, the SAP Sales Cloud and SAP Service Cloud groups will be read and provisioned to the target system with their actual display names.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.groups`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of groups to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of groups, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `ips.delete.threshold.users`
    
    </td>
    <td valign="top">
    
    Use this property to control the number of users to be deleted in a target system by defining a threshold. This will prevent you from accidentally deleting a huge number of users, for example by adding a filter or condition.

    For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP Sales Cloud and SAP Service Cloud* target system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in C4C. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Business Accelerator Hub: C4C](https://api.sap.com/package/C4C?section=Artifacts)

    [SAP Cloud for Customer OData API v2 Reference](https://help.sap.com/doc/d0f9ba822c08405da7d88174b304df84/CLOUD/en-US/index.html)

    **Using API version 1** \(deprecated\)

    If you use the first version of the SAP Sales Cloud and SAP Service Cloud API \(SOAP based\) – *humancapitalmanagementmasterd6* – your systems will be created with *c4c.api.version=1*. You need to use the transformation below and specify the mandatory attribute *RemoteSystemID*. The following interface is used for replicating employee master data to SAP Sales Cloud and SAP Service Cloud: [Inbound Service HumanCapitalManagementMasterDataReplicationEmployeeMasterDataReplicationIn](https://help.sap.com/doc/8a98c5f7d5be4b40b3dd97bbdaf28cc4/CLOUD/en-US/PSM_ISI_R_II_HCM_MDR_EMPLOYEE_MD_REPL_IB.html)

    Along with replicating employees in SAP Sales Cloud and SAP Service Cloud, a business user is created for every user.

    Default transformation:

    > ### Code Syntax:  
    > ```
    > 
    > /* Attribute RemoteObjectID stores the user name from the source system into C4C. */
    > {
    >    "user": {
    >        "mappings": [
    >             {	
    > 		"sourcePath": "$.userName",
    > 		"targetPath": "$.RemoteObjectID"
    >        },
    > /* Statements that start with PersonalDetails are related to the employee created in C4C. */
    >        {
    >           "sourceVariable": "currentDate",
    >           "targetPath": "$.PersonalDetails.ValidityPeriod.StartDate",
    >           "functions": [
    >                {
    >                   "type": "manipulateDate",
    >                   "targetDateFormat": "yyyy-MM-dd"
    >                }
    >              ]
    >         },
    >       {
    >           "constant": "9999-12-31",
    >           "targetPath": "$.PersonalDetails.ValidityPeriod.EndDate"
    >         },
    >         {
    >           "sourcePath": "$.name.givenName",
    >           "optional": true,
    >           "targetPath": "$.PersonalDetails.GivenName"
    >         },
    > 
    >     {
    >     	"sourcePath": "$.name.familyName",
    >     	"targetPath": "$.PersonalDetails.FamilyName"
    >     },
    > 
    > /* Statements that start with EmployeeType are supported by the C4C system only for internal employees.
    > (Service agents are not supported as EmployeeType. The supported employee types are mandatory and relevant only to lean employees). 
    > The value of the currentDate variable (the date when the provisioning is executed) is set as validity start date of the employee. 
    > In the default transformation statement, it's converted to the format required by C4C via a transformation function. */
    >        {
    >       	"sourceVariable": "currentDate",
    >       	"targetPath": "$.EmployeeType.ValidityPeriod.StartDate",
    >       	"functions": [
    >          	{
    >       		"type": "manipulateDate",
    >       		"targetDateFormat": "yyyy-MM-dd"
    >         	 }
    >              ]
    >             },
    >            {
    >                "constant": "9999-12-31",
    >                "targetPath": "$.EmployeeType.ValidityPeriod.EndDate"
    >            },
    >            {
    >                "sourcePath": "$.userName",
    >                "targetPath": "$.Identity.ID"
    >            },
    >            {
    >                "constant": "false",
    >                "targetPath": "$.Identity.UserAccountsInactiveIndicator"
    >            },
    >            {
    >                "sourcePath": "$.phoneNumbers[?(@.type == 'mobile')].value",
    >                "optional": true,
    >                "targetPath": "$.WorkplaceAddress.MobilePhoneNumberDescription"
    >            },
    >            {
    >                "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
    >                "optional": true,
    >                "targetPath": "$.WorkplaceAddress.PhoneNumberDescription"
    >            },
    >            {
    >                "sourcePath": "$.emails[0].value",
    >                "optional": true,
    >                "targetPath": "$.WorkplaceAddress.EmailURI"
    >            }
    >         ]
    >     }
    > }
    > 
    > ```

    **Using API version 2**

    If you want to use the second C4C API \(SOAP based\) – *employeereplicationin2* – you have to set *c4c.api.version=2*, change the transformation with the one below, and specify the two mandatory attributes – *RecipientPartyID* and *SenderPartyID*.

    Default transformation:

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "condition" : "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User'].employeeNumber EMPTY false",
    >         "mappings": [
    >             {
    >                 "targetPath": "$.ReceiverEmployeeID",
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User'].employeeNumber"
    >             },
    >             {
    >                 "targetPath": "$.BusinessPartnerID",
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User'].employeeNumber"
    >             },
    >             {
    >                 "targetPath": "$.EmployeeType.ValidityPeriod.StartDate",
    >                 "sourceVariable": "currentDate",
    >                 "functions": [
    >                     {
    >                         "type": "manipulateDate",
    >                         "targetDateFormat" : "yyyy-MM-dd"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "targetPath": "$.EmployeeType.ValidityPeriod.EndDate",
    >                 "constant": "9999-12-31"
    >             },
    >             {
    >                 "targetPath": "$.Common.Name.GivenName",
    >                 "sourcePath": "$.name.givenName",
    >                 "optional": true
    >             },
    >             {
    >                 "targetPath": "$.Common.Name.FamilyName",
    >                 "sourcePath": "$.name.familyName"
    >             },
    > 
    > /* You can set a custom namespace for an attribute. For example, if your namespace prefix is called a123, 
    > enter the following lines in your transformation:
    > 		  {
    > 			"targetPath": "$['a123:PersonalDetails']['a123:FamilyName']",    
    > 			"sourcePath": "$.name.familyName"
    > 		  }
    > 
    > When sending the request to C4C, the Identity Provisioning service will transform this data into XML elements, as follows:
    > 			<a123:PersonalDetails>
    > 				<a123:FamilyName>...</FamilyName>
    > 			</a123:PersonDetails>   */
    >      
    > 
    >             {
    >                 "targetPath": "$.Identity.IdentityID",
    >                 "sourcePath": "$.userName"
    >             },
    >             {
    >                 "targetPath": "$.Identity.UserAccountsInactiveIndicator",
    >                 "constant": "false"
    >             },
    >             {
    >                 "condition": "$.active == false",
    >                 "targetPath": "$.Identity.UserAccountsInactiveIndicator",
    >                 "constant": "true"
    >             },
    >             {
    >                 "targetPath": "$.WorkplaceAddress.MobilePhoneNumberDescription",
    >                 "sourcePath": "$.phoneNumbers[?(@.type == 'mobile')].value",
    >                 "optional": true
    >             },
    >             {
    >                 "targetPath": "$.WorkplaceAddress.PhoneNumberDescription",
    >                 "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
    >                 "optional": true
    >             },
    >             {
    >                 "targetPath": "$.WorkplaceAddress.EmailURI",
    >                 "sourcePath": "$.emails[0].value",
    >                 "optional": true
    >             },
    >             {
    >                 "constant": "SALES_REP",
    >                 "targetPath": "$.Identity.BusinessRole[0].ID"
    >             },
    >             {
    >                 "constant": "SALES_MANAGER",
    >                 "targetPath": "$.Identity.BusinessRole[1].ID"
    >             }
    >         ]
    >     }
    > }
    > 
    > ```

    **Using API version 3**

    By default, the Identity Provisioning uses the latest C4C API \(SCIM based\), for which property *c4c.api.version=3* by default.

    Default transformation:

    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.emails[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.emails[?(@.value)]",
    >         "optional": true
    >       },
    >       {
    >         "constant": "work",
    >         "targetPath": "$.emails[0].type"
    >       },
    >       {
    >         "sourcePath": "$.userType",
    >         "targetPath": "$.userType",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "targetPath": "$.name.middleName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true,
    >         "defaultValue": true
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
    >         "targetPath": "$.schemas[1]"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:extension:sap:2.0:User",
    >         "targetPath": "$.schemas[2]"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true
    >       }
    >     ]
    >   },
    > 
    > // You cannot create groups but instead, you can create and update group members, provided that groups in the source system have the exact same display name 
    > // as the groups in C4C. The group deletion operation is skipped. 
    > 
    >   "group": {
    >     "condition": "('%c4c.group.prefix%' === 'null') || ($.displayName =~ /%c4c.group.prefix%.*/)",
    >     "skipOperations": [
    >       "delete"
    >     ],
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    >         "functions": [
    >           {
    >             "condition": "('%c4c.group.prefix%' !== 'null') && (@ =~ /%c4c.group.prefix%.*/)",
    >             "function": "replaceFirstString",
    >             "regex": "%c4c.group.prefix%",
    >             "replacement": ""
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members[*].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "functions": [
    >           {
    >             "function": "resolveEntityIds"
    >           }
    >         ],
    >         "defaultValue": []
    >       }
    >     ]
    >   }
    > }
    > 
    > ```

6.  Now, add a source system from which to read users. Choose from: [Source Systems](source-systems-58033be.md)




<a name="loio1a974bcb1e6b4a6ebd5078e81ebf7875__postreq_zqx_nqj_p1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

**Related Information**  


[Blog: Employee Replication FAQ \(relevant for version 1\)](https://blogs.sap.com/2016/08/05/employee-replication/)

