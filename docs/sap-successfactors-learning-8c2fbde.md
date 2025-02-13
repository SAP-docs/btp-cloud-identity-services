<!-- loio8c2fbde0f0364657b66a5118973ca39e -->

# SAP SuccessFactors Learning

Follow this procedure to set up SAP SuccessFactors Learning as a proxy system.



<a name="loio8c2fbde0f0364657b66a5118973ca39e__prereq_gvh_45y_rdb"/>

## Prerequisites

You have created a technical user with administrator permissions that will be used to call the SAP SuccessFactors Learning API for provisioning user information.

> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loio8c2fbde0f0364657b66a5118973ca39e__context_vxy_lff_jrb"/>

## Context

SAP SuccessFactors Learning is a learning solution which helps organizations to improve employee skills and talent management, align learning outcomes with performance goals, boost compliance, and train external audiences.

You can use the Identity Provisioning user interface \(UI\) to connect to SAP SuccessFactors Learning as a proxy system and configure it in hybrid scenarios. For example, when SAP SuccessFactors Learning is exposed as a proxy system, you can connect it to an external identity management system, such as SAP Identity Management, without making a direct connection between both systems. You can provision users and groups to the external backend system, which can trigger CRUD \(create, read, update, delete\) operations on users and group members back to the SAP SuccessFactors Learning.

> ### Restriction:  
> Provisioning **groups** is not supported.



<a name="loio8c2fbde0f0364657b66a5118973ca39e__steps_wxy_lff_jrb"/>

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

5.  Add *SAP SuccessFactors Learning* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

6.  Choose the *Properties* tab to configure the connection settings for your system.

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
    
    Specify the URL to the API of your SAP SuccessFactors Learning system. It follows the pattern: <code>https://<i class="varname">&lt;root URL&gt;</i>/learning/public-api/rest/admin/Integration.svc/ias</code> 
    
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
    
    Enter the technical user ID for SAP SuccessFactors Learning.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Enter the password for the SAP SuccessFactors Learning technical user. For more information, see [Learning Technical User](https://help.sap.com/docs/SAP_SUCCESSFACTORS_LEARNING/82cf7c83c7db42a8aa1d3bbdbc39e93d/8009aa4bef254d3da888aa864528c695.html).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `lms.user.filter`
    
    </td>
    <td valign="top">
    
    When specified, only those users matching the filter expression will be read.

    **Possible values:**

    -   *userName eq "testName"*

    -   *externalID eq "testID"*

    -   *active eq "true"*

    -   *sourceSystem eq "Learning"* - indicates that the user is created directly in SAP SuccessFactors Learning with no involvement of Identity Provisioning.

    -   *sourceSystem eq "Identity Provisioning"* - indicates that the user is created in SAP SuccessFactors Learning by Identity Provisioning.



    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    > ### Note:  
    > The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).

7.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP SuccessFactors Learning* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP SuccessFactors Learning system. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    [SAP Business Accelerator Hub: SAP SuccessFactors Learning](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fapi.sap.com%2Fpackage%2FSuccessFactorsLMSCurriculawithSAPHCMQualification%3Fsection%3DOverview)

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
    
    ```
    {
      "user": {
        "scimEntityEndpoint": "Users",
        "mappings": [
          {
            "sourcePath": "$.id",
            "targetPath": "$.id",
            "targetVariable": "entityIdSourceSystem"
          },
          {
            "sourceVariable": "entityBaseLocation",
            "targetPath": "$.meta.location",
            "targetVariable": "entityLocationSourceSystem",
            "functions": [
              {
                "type": "concatString",
                "suffix": "${entityIdSourceSystem}"
              }
            ]
          },
          {
            "sourcePath": "$.schemas",
            "preserveArrayWithSingleElement": true,
            "targetPath": "$.schemas"
          },
          {
            "sourcePath": "$.userName",
            "optional": true,
            "targetPath": "$.userName",
            "correlationAttribute": true
          },
          {
            "sourcePath": "$.externalId",
            "optional": true,
            "targetPath": "$.externalId"
          },
          {
            "sourcePath": "$.locale",
            "optional": true,
            "targetPath": "$.locale"
          },
          {
            "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
            "optional": true,
            "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
          },
          {
            "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['siteID']",
            "optional": true,
            "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['siteID']"
          },
          {
            "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['sourceSystem']",
            "optional": true,
            "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['sourceSystem']"
          },
          {
            "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['applicationID']",
            "optional": true,
            "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['applicationID']"
          },
          {
            "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['110']",
            "optional": true,
            "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['110']"
          },
          {
            "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['120']",
            "optional": true,
            "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['120']"
          },
          {
            "sourcePath": "$.emails",
            "preserveArrayWithSingleElement": true,
            "optional": true,
            "targetPath": "$.emails"
          },
          {
            "sourcePath": "$.emails[?(@.primary== true)].value",
            "correlationAttribute": true
          },
          {
            "sourcePath": "$.name.givenName",
            "optional": true,
            "targetPath": "$.name.givenName"
          },
          {
            "sourcePath": "$.name.middleName",
            "optional": true,
            "targetPath": "$.name.middleName"
          },
          {
            "sourcePath": "$.name.familyName",
            "targetPath": "$.name.familyName"
          },
          {
            "sourcePath": "$.phoneNumbers",
            "preserveArrayWithSingleElement": true,
            "optional": true,
            "targetPath": "$.phoneNumbers"
          },
          {
            "sourcePath": "$.active",
            "targetPath": "$.active"
          }
        ]
      }
    }
    ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourcePath": "$.schemas",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.schemas"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "optional": true,
    >         "targetPath": "$.userName"
    >       },
    >       {
    >         "sourcePath": "$.externalId",
    >         "optional": true,
    >         "targetPath": "$.externalId"
    >       },
    >       {
    >         "sourcePath": "$.locale",
    >         "optional": true,
    >         "targetPath": "$.locale"
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >         "optional": true,
    >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['siteID']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['siteID']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['110']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['110']"
    >       },
    >       {
    >         "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['120']",
    >         "optional": true,
    >         "targetPath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['customColumns']['120']"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary== true)] empty false",
    >         "sourcePath": "$.emails[?(@.primary== true)].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.emails[?(@.value)]"
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary== true)] empty true",
    >         "sourcePath": "$.emails[0].value",
    >         "targetPath": "$.emails[0].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.name.givenName"
    >       },
    >       {
    >         "sourcePath": "$.name.middleName",
    >         "optional": true,
    >         "targetPath": "$.name.middleName"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "targetPath": "$.name.familyName"
    >       },
    >       {
    >         "condition": "$.phoneNumbers[?(@.primary== true)] empty false",
    >         "sourcePath": "$.phoneNumbers[?(@.primary== true)].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.phoneNumbers[?(@.value)]"
    >       },
    >       {
    >         "condition": "$.phoneNumbers[?(@.primary== true)] empty true",
    >         "sourcePath": "$.phoneNumbers[0].value",
    >         "targetPath": "$.phoneNumbers[0].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.active",
    >         "targetPath": "$.active"
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
    >     ]
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
8.  Connect the external consumer to Identity Provisioning with the technical user you have created in step 2.

    If the external consumer system is **SAP Identity Management**, you can export the newly created proxy system as a SCIM repository from Identity Provisioning and import it in SAP Identity Management. This will create a SCIM repository in SAP Identity Management where most of the repository constants will be automatically filled in. You need to provide the technical user credentials that you have set up in step 2 and the SCIM assignment method as described below:

    -   For AUTH\_USER and AUTH\_PASSWORD, enter your client ID and secret.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    -   For AUTH\_USER and AUTH\_PASSWORD, enter the user ID and password of the Identity Authentication technical user for which you have set permission *Access Proxy System API*.

    -   For the SCIM\_ASSIGNMENT\_METHOD constant, make sure the value is **PUT**.


    > ### Note:  
    > For external consumer systems, other than SAP Identity Management, you should also use the **PUT** method for modifying entities.




<a name="loio8c2fbde0f0364657b66a5118973ca39e__postreq_cf4_lgj_kfb"/>

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

