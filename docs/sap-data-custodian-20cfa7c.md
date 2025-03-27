<!-- loio20cfa7c33fe5414b870e760eb37a82c1 -->

# SAP Data Custodian

Follow this procedure to set up SAP Data Custodian as a proxy system.



<a name="loio20cfa7c33fe5414b870e760eb37a82c1__prereq_j3x_mf3_dwb"/>

## Prerequisites

> ### Restriction:  
> This system is available for all standalone tenants and bundle tenants running on SAP Cloud Identity Services infrastructure. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have created an SAP Data Custodian tenant.

-   You have created a user within your tenant with the required roles for your scenario.

-   You have added your user to SAP Identity Service Management \(SAP ISM\).


> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loio20cfa7c33fe5414b870e760eb37a82c1__context_nmb_sg3_dwb"/>

## Context

SAP Data Custodian is a robust Software as a Service \(SaaS\) solution that protects sensitive data stored in public, private, hybrid, and multicloud environments. This solution integrates with partnered public hyperscalers, SAP applications, and SAP managed clouds.

You can use Identity Provisioning to configure SAP Data Custodian as a proxy system to execute hybrid scenarios. For example, when SAP Data Custodian is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management, without making a direct connection between both systems. You can provision entities to the external backend system, which can trigger CRUD \(create, read, update, delete\) operations back to the SAP Data Custodian. This scenario supports provisioning **users** and **user assignments to groups**.

SCIM API 2.0 does not support managing of group assignments via the SCIM user resource. The "groups" attribute of the user is read-only. This means that the user group assignments should be managed via the SCIM group resources using the "members" attribute \(as it is defined by the SCIM standard\).

> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



<a name="loio20cfa7c33fe5414b870e760eb37a82c1__steps_zj2_zg3_dwb"/>

## Procedure

1.  Open your subaccount in SAP BTP cockpit \(valid for OAuth authentication to the Identity Provisioning proxy system\).

    > ### Note:  
    > If you have a bundle tenant, then in the cockpit → *Neo* → *Overview*, you can see the Global account, which SAP provides for your bundle in the corresponding Identity Provisioning region. Then, in the global account, you can see your subaccount, where the Identity Provisioning is enabled as a service for the bundle. The display name of the subaccount starts with **SAP\_BUNDLE**.

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Users & Authorizations* \> *Administrators*.

3.  Create a technical user with the necessary authorizations. It will later be used by the external consumer to connect to Identity Provisioning.

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



4.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

5.  Add SAP Data Custodian as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

6.  Set up the communication between Identity Provisioning and SAP Data Custodian and configure the authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP Data Custodian source system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/76867db8ce534becbfc08b050695df8e.html?version=Cloud).

        Skip this step if you use basic authentication. The next steps are performed in SAP Data Custodian and are relevant for certificate-based authentication only.

    2.  Login to SAP Data Custodian tenant and create a tenant operations technical user \(TOTU\), as described in [Create a Tenant Operations Technical User in SAP Data Custodian](https://help.sap.com/docs/sap-data-custodian/key-management-service/create-tenant-operations-technical-user-sap-data-custodian-certificate).

    3.  Upload the outbound certificate that you downloaded in **substep a.** to the TOTU, as described in [Register the Outbound Certificate to Your Tenant Operations Technical User](https://help.sap.com/docs/sap-data-custodian/key-management-service/register-outbound-certificate).


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

    Value
    
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
    
    Specify the URL to the SAP Data Custodian SCIM API excluding the path information.

    `https://<SCIM_API_URL>`

    For more information, see [Identity Provisioning](https://help.sap.com/docs/sap-data-custodian/key-management-service/identity-provisioning).
    
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
    
    Enter your authentication method:

    -   *BasicAuthentication*

    -   *ClientCertificateAuthentication*



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication*

    Enter the OAuth client key, created for your SAP Data Custodian tenant.

    For more information, see [Basic Authentication Prerequisites](https://help.sap.com/docs/sap-data-custodian/key-management-service/basic-authentication-prerequisites).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication*

    \(Credential\) Enter the OAuth client secret, created for your SAP Data Custodian tenant.

    For more information, see [Certificate Authentication Prerequisites](https://help.sap.com/docs/sap-data-custodian/key-management-service/identity-provisioning-certificate-authentication-prerequisites).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `OAuth2TokenServiceURL`
    
    </td>
    <td valign="top">
    
    Specify the URL of the access token provider service for your SAP Data Custodian instance:

    `https://<SCIM_API_URL>/kms/scim/v1/Oauth2/Token`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dc.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those SAP Data Custodian users matching the filter expression will be read. You can filter users by *userName*, *displayName* or *externalId*.

    **Possible values:**

    For example: *****userName eq "Smith.J"*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dc.group.filter`
    
    </td>
    <td valign="top">
    
    This property filters groups by display name or externalId.

    When specified, only those groups matching the filter expression will be read.

    **Possible values:**

    -   *SAP\_Data\_Custodian\_Auditor*

    -   *SAP\_Data\_Custodian\_Service\_Admin*

    -   *SAP\_Data\_Custodian\_Key\_Admin*

    -   *SAP\_Data\_Custodian\_Key\_User*


    For example: *displayName eq "SAP\_Data\_Custodian\_Auditor"*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dc.support.patch.operation`
    
    </td>
    <td valign="top">
    
    This property controls how modified users in the source system are updated in the target system.

    -   If set to *true*, `PATCH` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, only this change will be provisioned and applied in the target system.

    -   If set to *false*, `PUT` operations are used to update users in the target system. This means, for example, that if a user attribute is modified, all user attributes are replaced in the target system, instead of updating only the modified ones.


    Users can be updated in the target system in various cases, such as:

    -   In the source system, some user attributes are modified, or new attributes are added.

    -   In the source system, a condition or a filter is set for users not to be read anymore.

    -   A user is deleted from the source system.


    In the last two cases, it's possible to keep the entity in the target system – it will not be deleted but only disabled. To do this, use the `deleteEntity` scope in the transformation of your target or proxy system. See: [Transformation Expressions](transformation-expressions-bb8537b.md) → **deleteEntity**.

    **Possible values:**

    -   *true*
    -   *false*

    Default value: *false*
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

8.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the SAP Data Custodian proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    > ### Note:  
    > When Identity Authentication is configured as a source system, the default transformation logic:
    > 
    > -   Provisions only groups and user group assignments if they are part of the following predefined group list:
    >     -   *SAP\_Data\_Custodian\_Auditor*
    > 
    >     -   *SAP\_Data\_Custodian\_Service\_Admin*
    > 
    >     -   *SAP\_Data\_Custodian\_Key\_Admin*
    > 
    >     -   *SAP\_Data\_Custodian\_Key\_User*
    > 
    > 
    > -   Skips some of the attributes from the identity records.
    > -   Sets primary email for `userName` of the user.
    > 
    > This way, the transformation logic ensures that the identity data, sent to the Identity Provisioning SCIM REST API, is consistent.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP Data Custodian. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP Data Custodian SCIM 2.0 API](https://api-kms-devel.datacustodian.cloud.sap/kms/scim/v1/ui/)

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
    > 
    > {
    >     "user": {
    >         "scimEntityEndpoint": "Users",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.name",
    >                 "targetPath": "$.name",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "targetPath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "targetPath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true
    >             },
    >             {
    >                 "sourceVariable": "entityBaseLocation",
    >                 "targetVariable": "entityLocationSourceSystem",
    >                 "targetPath": "$.meta.location",
    >                 "functions": [
    >                    {
    >                       "type": "concatString",
    >                       "suffix": "${entityIdSourceSystem}"
    >                    }
    >                  ]
    >             }
    >         ]
    >     },
    >     "group": {
    >         "scimEntityEndpoint": "Groups",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "targetPath": "$.members",
    >                 "optional": true,
    >                 "preserveArrayWithSingleElement": true
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId",
    >                 "optional": true
    >             },
    >             {
    >                 "sourceVariable": "entityBaseLocation",
    >                 "targetVariable": "entityLocationSourceSystem",
    >                 "targetPath": "$.meta.location",
    >                 "functions": [
    >                    {
    >                       "type": "concatString",
    >                       "suffix": "${entityIdSourceSystem}"
    >                    }
    >                  ]
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
    >     "user": {
    >         "scimEntityEndpoint": "Users",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": ["urn:ietf:params:scim:schemas:core:2.0:User","urn:ietf:params:scim:schemas:extension:enterprise:2.0:User","urn:ietf:params:scim:schemas:extension:sap:2.0:User","urn:sap:cloud:scim:schemas:extension:custom:2.0:User"],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "condition": "$.externalId EMPTY false",
    >                 "sourcePath": "$.externalId",
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional":true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.name.givenName",
    >                 "optional":true,
    >                 "targetPath": "$.name.givenName"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional":true,
    >                 "targetPath": "$.name.familyName"
    >             },
    >             {
    >                 "sourcePath": "$.name.formatted",
    >                 "optional":true,
    >                 "targetPath": "$.name.formatted"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificPrefix",
    >                 "optional":true,
    >                 "targetPath": "$.name.honorificPrefix"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificSuffix",
    >                 "optional":true,
    >                 "targetPath": "$.name.honorificSuffix"
    >             },
    >             {
    >                 "sourcePath": "$.name.middleName",
    >                 "optional":true,
    >                 "targetPath": "$.name.middleName"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "optional":true,
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "constant":"urn:ietf:params:scim:api:messages:2.0:PatchOp",
    >                 "targetPath":"$.schemas[0]",
    >                 "scope":"patchEntity"
    >             },
    >             {
    >                 "sourcePath": "$.Operations",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.Operations",
    >                 "scope": "patchEntity"
    >             }
    >         ]
    >     },
    >     "group": {
    >         "scimEntityEndpoint": "Groups",
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                 "targetPath": "$.schemas[0]"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.members",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.members",
    >                 "optional": true
    >             },
    >             {
    >                 "sourcePath": "$.Operations",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.Operations",
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "targetPath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "scope": "patchEntity"
    >             }
    >         ]
    >     }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
9.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PATCH**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PATCH**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PATCH** method for modifying entities.


**Related Information**  


[SAP Data Custodian](https://help.sap.com/docs/sap-data-custodian?version=latest&locale=en-US)

