<!-- loio93807cf4c7324bc38e4e4ef31aaa95e1 -->

# SAP BTP Platform Members \(Cloud Foundry\)

Follow this procedure to set up the SAP BTP Platform Members \(Cloud Foundry\) as а proxy system.



<a name="loio93807cf4c7324bc38e4e4ef31aaa95e1__prereq_l4f_cnz_scc"/>

## Prerequisites

-   You have а global account in SAP BTP with at least one multi-environment subaccount with enabled Cloud Foundry environment.

-   You have established trust between your SAP Cloud Identity Services tenant as custom identity provider for platform users and your global account\(s\) containing these subaccounts. For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users](https://help.sap.com/docs/btp/sap-business-technology-platform/establish-trust-and-federation-of-custom-identity-providers-for-platform-users?locale=en-US&version=Cloud).

-   You have created a CF provisioning user \(which is a regular user of type *Employee* in the local identity directory of your SAP Cloud Identity Services tenant\) that will be used for provisioning. Give this user an email address with the following pattern `cf-user-provisioning-<origin_key>@sap.invalid`, where `<origin_key>` is the origin key of the trust configuration for BTP platform users which points to your SAP Cloud Identity Services tenant. You have set an initial password for the user and marked its email adress as *verified*. For more information, see [Create a New User](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/create-new-user?locale=en-US&version=Cloud) and [List and Edit User Details](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/list-and-edit-user-details?locale=en-US&version=Cloud).

    > ### Note:  
    > The password lifetime for the CF provisioning user depends on the password policy set for the *SAP Business Technology Platform* application in the administration console of SAP Cloud Identity Services. For more information, see [Set a Password Policy for an Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/set-password-policy-for-application?version=Cloud).

-   You have activated the account of the CF provisioning user by opening the *Profile Page* of SAP Cloud Identity Services, in a separate browser session, and changing its initial password. The URL has the following pattern: `https://<tenant ID>.accounts.ondemand.com` or `https://<tenant ID>.accounts.cloud.sap`
-   You have created the group *cf-user-provisioning* in your SAP Cloud Identity Services tenant and added the CF provisioning user to it. For more information, see [Create a New Group](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/create-new-user-group?locale=en-US&version=Cloud) and [Add Users to a Group](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/add-users-to-group?locale=en-US&version=Cloud).

-   You have added the CF provisioning user as org member with role **Org Manager** to each Cloud Foundry organization where you want to provision users, in the SAP BTP cockpit. For more information, see [Add Org Members](https://help.sap.com/docs/btp/sap-business-technology-platform/add-org-members-using-cockpit?locale=en-US&version=Cloud) and [About Roles in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/about-roles-in-cloud-foundry-environment?version=Cloud).


> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



## Context

The Cloud Foundry environment enables you to create polyglot cloud applications in Cloud Foundry. It contains the SAP BTP, Cloud Foundry runtime service, which is based on the open-source application platform managed by the Cloud Foundry Foundation. For more information, see [Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/cloud-foundry-environment?version=Cloud).

When you enable the Cloud Foundry environment in your subaccount, the system automatically creates a Cloud Foundry organization for you. You are able to add platform users as org members and space members and assign roles to grant these users platform access.

SAP BTP Platform Members \(Cloud Foundry\) connector manages org and space members, as well as their role assignments, in the Cloud Foundry environment of a multi-environment subaccount, where a **single** SAP Cloud Identity Services tenant acts as custom identity provider. We recommend that you use the Identity Provisioning service enabled in this SAP Cloud Identity Services tenant.

> ### Note:  
> Identity Provisioning bundle tenants delivered before March 15, 2022, and Identity Provisioning standalone tenants delivered before September 1, 2020, run on SAP BTP, Neo environment. Customers with tenants on Neo environment are encouraged to migrate them to the SAP Cloud Identity Services infrastructure.
> 
> For more information, see [Migrate Identity Provisioning Bundle Tenant](https://help.sap.com/docs/identity-provisioning/identity-provisioning/migrate-identity-provisioning-bundle-tenant).

In SAP BTP Platform Members \(Cloud Foundry\), groups correspond to roles in particular Cloud Foundry orgs or spaces, thus group members are user assignments of a role in a specific Cloud Foundry org or space.

You can use SAP BTP Platform Members \(Cloud Foundry\) as a proxy connector to execute hybrid scenarios. That means, it can provision its entities to another \(external\) back-end system by request, and then can continue executing CRUD operations back to SAP BTP Platform Members \(Cloud Foundry\), whenever the external back-end requests such.

> ### Remember:  
> This connector enables you to write users and user role assignments to Cloud Foundry on *subaccount* level. For provisioning of users and groups to Cloud Foundry on *application* level, refer to [SAP BTP XS Advanced UAA \(Cloud Foundry\)](sap-btp-xs-advanced-uaa-cloud-foundry-ecddce6.md). For more information, see [SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario?version=Cloud).

The proxy system consumes User Account and Authentication API and Cloud Foundry V3 API provided by Cloud Foundry.

> ### Note:  
> In case you have Cloud Foundry environment enabled in multiple Cloud Foundry landscapes or more than one SAP Cloud Identity Services tenants, you must configure a separate SAP BTP Platform Members \(Cloud Foundry\) connector for each of them.

> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



## Procedure

1.  To enable provisioning of platform users and user role assignments to and from Cloud Foundry environment, create a Support Ticket on component BC-CP-CF-SEC-IAM.

    Specify your SAP Cloud Identity Services tenant ID and the origin key of the trust configuration for BTP platform users which points to your SAP Cloud Identity Services tenant. You can find the origin key value in the SAP BTP cockpit. Go to your SAP BTP subaccount, choose *Trust Configuration* and see the value under *Origin Key* for the relevant *Custom Identity Provider for Platform Users*.

2.  Open your subaccount in SAP BTP cockpit \(valid for OAuth authentication to the Identity Provisioning proxy system\).

    > ### Note:  
    > If you have a bundle tenant, then in the cockpit → *Neo* → *Overview*, you can see the Global account, which SAP provides for your bundle in the corresponding Identity Provisioning region. Then, in the global account, you can see your subaccount, where the Identity Provisioning is enabled as a service for the bundle. The display name of the subaccount starts with **SAP\_BUNDLE**.

3.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Users & Authorizations* \> *Administrators*.

4.  Create a technical user with the necessary authorizations. It will later be used by the external consumer to connect to Identity Provisioning.

    -   For **Certificate-based authentication**, follow the procedure in [Manage Certificates for Inbound Connection](Operation-Guide/manage-certificates-for-inbound-connection-952e7c7.md) → *SAP BTP, Neo Environment*

    -   For **OAuth authentication**, proceed as follows:

        1.  Go to *Security* \> *OAuth* \> *Clients* and choose *Register New Client*.

        2.  From the *Subscription* combo box, select **<provider\_subaccount\>/ipsproxy**.

        3.  From the *Authorization Grant* combo box, select **Client Credentials**.

        4.  In the *Secret* field, enter a password \(client secret\) and remember it. You will need it later, for the repository configuration in the external system.

        5.  Copy/paste and save \(in a notepad\) the generated *Client ID*. You will need it later, too.

        6.  From the left-side navigation, choose *Subscriptions* \> *Java Applications* \> *ipsproxy* .

        7.  From the left-side navigation, choose *Roles* \> *IPS\_PROXY\_USER*.

        8.  Choose *Assign* and enter **oauth\_client\_<client\_ID\>**.

            For *<client\_ID\>*, enter the one you have saved in the previous main step.


    -   For **Certificate-based authentication**, upload the certificate for the technical user of type *System*, as described in [Add System as Administrator](https://help.sap.com/docs/identity-authentication/identity-authentication/add-administrators?version=Cloud#add-system-as-administrator) and enable the *Access Proxy System API* permission.

    -   For **Basic authentication**, proceed as follows:

        1.  Add an administrator user of type **System** and configure the basic authentication method for this user.

            If you already have a technical user, skip this step.

        2.  Save your changes.

        3.  Select your administrator user of type **System** and enable the *Access Proxy System API* permission.

        4.  Save your changes.



5.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

6.  Add *SAP BTP Platform Members \(Cloud Foundry\)* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

7.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Enter the `email` of the CF provisioning user \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for the CF provisioning user \(see **Prerequisites**\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `btp.cf.pm.origin`
    
    </td>
    <td valign="top">
    
    Enter the origin key of your SAP Cloud Identity Services tenant \(see **Step 1**\).

    The value of this property is a string, which always ends with the suffix *\-platform*.

    It will be used as the *origin* attribute in the system transformation.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `btp.cf.pm.landscape`
    
    </td>
    <td valign="top">
    
    Enter the technical key of the landscape in which your multi-environment subaccount with enabled Cloud Foundry environment is located. For more information, see [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-and-api-endpoints-available-for-cloud-foundry-environment?version=Cloud).

    For example: `cf-eu10-002`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `btp.cf.pm.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP BTP Platform Members \(Cloud Foundry\) users matching the filter expression will be read.

    For example: *userName eq "SmithJ"*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

8.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP BTP Platform Members \(Cloud Foundry\)* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    > ### Note:  
    > Update operation is skipped for users in the default proxy write transformation.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP BTP Platform Members \(Cloud Foundry\) system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [Cloud Foundry V3 API](https://v3-apidocs.cloudfoundry.org/version/3.178.0/index.html)

    > ### Caution:  
    > Keep in mind that when you add or delete users and user role assignments in SAP BTP Platform Members \(Cloud Foundry\), the operations order must adhere to the Cloud Foundry Environment hierarchy. In this case, you can expect the following behavior:
    > 
    > -   When adding a user as space member, it must already be present as member of the relevant organization with assigned role **Org User**. When deleting an org member, it should be first removed from the spaces of the relevant organization. In case you end up with erroneous entity structure, you can manually add or delete users via the administration console for SAP Cloud Identity Services.
    > 
    > -   When adding user role assignments, you should first add the org roles and afterwards proceed with the space roles. Also, when deleting user role assignments, you should first delete the space roles and then proceed with the org roles. If this condition is not fullfiled the job will finish with error. In that case, you can rerun the job until it finishes successfully.

    Default read and write transformations:

    > ### Tip:  
    > The proxy *Read Transformation* is used when the external client application \(for example, SAP Identity Management\) makes initial load. That is, executing GET requests to the resource endpoints \(**/Users** or **/Groups**\) to retrieve the corresponding entities of the particular type. The external client application can also execute GET requests to a single resource endpoint \(querying a single resource is supported\). In this case, the proxy system acts as a *source* one.
    > 
    > The proxy *Write Transformation* is used when the external application manages the entities in the proxy system – creates new entities, updates existing ones, or deletes existing ones. In this case, the proxy system acts as a *target* one.
    > 
    > However, after a *Create* or *Update* operation is performed on the proxy system, the *Read Transformation* is applied to the result, so that the created or updated entity is sent back to the external application. This behavior demonstrates that the proxy *Read Transformation* is used for *write* cases, as well.


    <table>
    <tr>
    <th valign="top">

    Read Transformation
    
    </th>
    <th valign="top">

    Write Transformation
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.name",
    >         "targetPath": "$.name",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.verified",
    >         "targetPath": "$.verified",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.meta",
    >         "targetPath": "$.meta",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.origin",
    >         "targetPath": "$.origin",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.zoneId",
    >         "targetPath": "$.zoneId",
    >         "optional": true
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourcePath": "$.id",
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']"
    > 	   //The attribute group extension name is used to map the read users and user assignments of a role 
    > 	   //to the relevant Cloud Foundry organization or space.
    > 	   //the organization group extension name follows the pattern: <org_ID> <org_role>
    > 	   //the space group extension name follows the pattern: <org_ID> <space_ID> <space_role>
    >       },
    >       {
    >         "constant": [
    >           "urn:ietf:params:scim:schemas:core:2.0:Group"
    >         ],
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName",
    > 	   //the organization group display name follows the pattern: <btp.cf.pm.group.prefix>_<btp.cf.pm.landscape>:<org_name>:<org_role>
    > 	  //the space group display name follows the pattern: <btp.cf.pm.group.prefix>_<btp.cf.pm.landscape>:<org_name>:<space_name>:<space_role>
    >         "functions": [
    >           {
    >             "condition": "'%btp.cf.pm.group.prefix%' !== 'null'",
    >             "function": "concatString",
    >             "prefix": "%btp.cf.pm.group.prefix%"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       },
    >       {
    >         "constant": "authorization",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']"
    >       },
    >       {
    >         "constant": "userOnlyMembership",
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['supportedOperations']"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "skipOperations": [
    >       "update"
    >     ],
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
    >         "sourcePath": "$.name.givenName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.formatted",
    >         "targetPath": "$.name.formatted",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.emails",
    >         "targetPath": "$.emails",
    >         "preserveArrayWithSingleElement": true
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value == []",
    >         "targetPath": "$.emails[0].primary",
    >         "constant": true
    >       },
    >       {
    >         "constant": "urn:scim:schemas:core:1.0",
    >         "targetPath": "$.schemas[0]"
    >       }
    >     ],
    >     "scimEntityEndpoint": "Users"
    >   },
    >   "group": {
    >     "mappings": [
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:Group']['name']",
    > 	   //The attribute group extension name is used to map the users and user assignments of a role 
    > 	   //to the relevant Cloud Foundry organization or space.
    > 	   //the organization group extension name follows the pattern: <org_ID> <org_role>
    > 	   //the space group extension name follows the pattern: <org_ID> <space_ID> <space_role>
    >         "targetVariable": "entityIdTargetSystem",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.displayName"
    > 	   //the organization group display name follows the pattern: <btp.cf.pm.group.prefix>_<btp.cf.pm.landscape>:<org_name>:<org_role>
    > 	  //the space group display name follows the pattern: <btp.cf.pm.group.prefix>_<btp.cf.pm.landscape>:<org_name>:<space_name>:<space_role>
    >       },
    >       {
    >         "sourcePath": "$.members",
    >         "targetPath": "$.members",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.Operations",
    >         "targetPath": "$.Operations",
    >         "preserveArrayWithSingleElement": true,
    >         "scope": "patchEntity"
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "targetPath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "scope": "patchEntity"
    >       }
    >     ],
    >     "scimEntityEndpoint": "Groups"
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
9.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.

10. Run an initial load job.




<a name="loio93807cf4c7324bc38e4e4ef31aaa95e1__postreq_cf4_lgj_kfb"/>

## Next Steps

When a proxy system is connected to an external backend system \(in the case of SAP Identity Management this means the exported CSV file is imported into the Identity Management Admin UI and a repository is configured\), you can start managing the users and groups into this external system. Usually, the first operation is the initial load of the existing entities into your external system. When this load has finished, changes in the external system, such as creating new users or updating existing ones, can trigger CRUD requests back to the proxy system.

To see an example with SAP Identity Management, see [Hybrid Scenario: SAP Identity Management](https://help.sap.com/docs/identity-provisioning/identity-provisioning/hybrid-scenario-sap-identity-management?version=Cloud) → sections **Next Steps** and **Future Identity Lifecycle**.

> ### Caution:  
> Effective **September 2020**, Shanghai \(China\) tenants that reside on SAP BTP, Neo environment can be only accessed on the following domain: `dispatcher.cn1.platform.sapcloud.cn`
> 
> So make sure you use the correct domain when you construct your REST API requests.
> 
> For example: **GET** *https://ipsproxyabcd12345-xyz789.dispatcher.cn1.platform.sapcloud.cn/ipsproxy/api/v1/scim/bbb111aa-1234-aaaa-7777-1234567abcde/Users/s123456789*
> 
> To learn more, see: [Proxy Systems](proxy-systems-b10d68a.md)

**Related Information**  


[SAP BTP Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-btp-integration-scenario)

