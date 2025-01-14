<!-- loiod45425fa2981496dac4e2918edfeac56 -->

# SAP SuccessFactors

Follow this procedure to set up SAP SuccessFactors as a proxy system.



<a name="loiod45425fa2981496dac4e2918edfeac56__prereq_bns_xn4_vdb"/>

## Prerequisites

-   You have created a technical user with permissions to **call** the SAP SuccessFactors HCM Suite OData API and to **export** employee data from the SAP SuccessFactors system. For more information, see [Permissions](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/3d71f690709243db99102127557a3d73.html?version=Latest) and [URI Conventions \(OData Version 2.0\)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).

-   Consumers of the SAP SuccessFactors Workforce SCIM API can either create a technical user and assign the necessary permissions, or use the predefined technical user with built-in permissions for communication between SAP SuccessFactors and Identity Provisioning using certificate authentication. For more information, see [Permissions](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html?version=Latest#permissions) and [Upgrade to X.509 Certificate-Based Authentication for Incoming Calls](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/2b8f220f51ce455da3f349ef851d264c.html?version=Latest).


> ### Note:  
> Administrators of bundle tenants on Neo environment should enable the *Manage OAuth Clients* permission, as described in *Neo Environment* section in [Manage Authorizations](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/544de9b504214372b4479dc1f6b08cca.html "Manage the authorizations of Identity Provisioning administrators, when your bundle or standalone tenant is running on SAP BTP, Neo environment.") :arrow_upper_right:.



<a name="loiod45425fa2981496dac4e2918edfeac56__context_zhf_2vx_ybb"/>

## Context

You can use SAP SuccessFactors as a proxy connector to execute *hybrid* scenarios. That means, it can provision its entities to another \(external\) back-end system by request, and then can continue executing CRUD operations back to SAP SuccessFactors, whenever the external back-end requests such.

SAP SuccessFactors provides two APIs for its integration with Identity Provisioning: SAP SuccessFactors HCM Suite OData API and SAP SuccessFactors Workforce SCIM API. The value of `sf.api.version` property controls which API you use.

-   When the value is set to `1`, or the property is not defined - SAP SuccessFactors HCM Suite OData API \(in short, OData API\) is used. This is the default value. SAP SuccessFactors source systems created before the introduction of `sf.api.version` property, use OData API. This version allows you to read users and groups, both static and dynamic. It also supports writing users, updating dynamic groups and group members.

    > ### Restriction:  
    > Note the following restrictions when using SAP SuccessFactors HCM Suite OData API:
    > 
    > -   You cannot *create* or *delete* groups as these operations are currently not supported.
    > 
    > -   Managing SAP SuccessFactors **static groups** is not supported.

-   When the value is set to `2` - SAP SuccessFactors Workforce SCIM API \(in short, SCIM API\) is used.

    This version allows you to provision static permission groups and user's group assignments. Provisioning of user's group assignments from a given external system to SAP SuccessFactors proxy system is possible if the user is an active employee with a work assignment.

    To update a group from the external system, a group with the same name should already exist in SAP SuccessFactors. For more information about the difference between static and dynamic groups in SAP SuccessFactors, see [Permission Groups](https://help.sap.com/docs/SAP_SUCCESSFACTORS_ONBOARDING/12be6a11886846cba1de18bf9027a0b6/edcaffe1b2e64e2683347de16325750c.html?version=2305).

    > ### Restriction:  
    > Note the following restrictions when using SAP SuccessFactors Workforce SCIM API:
    > 
    > -   You cannot *create* or *delete* groups using the `Groups` APIs.
    > 
    > -   The `Groups` patch API only supports updating membership of static permission groups.
    > 
    > 
    > For more information, see [Overview of SAP SuccessFactors Workforce System for Cross-Domain Identity Management API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html?version=2311).


For more information on how to update to version 2, see [Update Connector Version](Operation-Guide/update-connector-version-8558733.md).

> ### Note:  
> The Identity Provisioning implementation of the Proxy System SCIM API \(based on the [SCIM Query](https://datatracker.ietf.org/doc/html/rfc7644#section-3.4.2)\) supports single entity and delta read filtering for users and groups. For more information, see [Query Parameters for Proxy System SCIM API](https://help.sap.com/docs/identity-provisioning/identity-provisioning/proxy-systems?version=Cloud#query-parameters-for-proxy-scim-api).



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

5.  Add *SAP SuccessFactors* as a proxy system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

6.  Set up the communication between Identity Provisioning and SAP SuccessFactors and configure your authentication method \(basic or certificate-based\).

    > ### Note:  
    > We recommend that you use certificate-based authentication.

    1.  In your newly added SAP SuccessFactors proxy system, select the *Certificate* tab and choose *Generate* \> *Download*, as described in [Generate and Manage Certificates for Outbound Connection](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/76867db8ce534becbfc08b050695df8e.html?version=Cloud).

        Skip this step if you use basic authentication. The next steps are performed in SAP SuccessFactors Admin Center and are relevant for certificate-based authentication only.

    2.  Login to SAP SuccessFactors and go to *Admin Center*. Follow the procedure described in [Upgrade to X.509 Certificate-Based Authentication for Incoming Calls](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/568fdf1f14f14fd089a3cd15194d19cc/2b8f220f51ce455da3f349ef851d264c.html).

        Make sure you select *Identity Provisioning Service* in the *Integration Name* field.


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
    
    `URL`
    
    </td>
    <td valign="top">
    
    Specify the URL to your SAP SuccessFactors API.

    For example:

    -   For version 1: `https://apitest.successfactors.com/odata/v2`

    -   For version 2: `https://apitest.successfactors.com`


    To see the list of all SAP SuccessFactors data centers, see: [SAP SuccessFactors API Reference Guide \(OData V2\): List of SAP SuccessFactors API Servers](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/af2b8d5437494b12be88fe374eba75b6.html?version=2311) and [System for Cross-domain Identity Management for Workforce in SuccessFactors](https://api.sap.com/api/PLTScim/resource) 
    
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
    
    \(Optional\) `sf.api.version`
    
    </td>
    <td valign="top">
    
    Handles the version of the API which is consumed by the SAP SuccessFactors system.

    **Possible values:**

    -   *1* - Indicates that SAP SuccessFactors HCM Suite OData API \(in short, OData API\) is used.

    -   *2* - Indicates that SAP SuccessFactors Workforce SCIM API \(in short, SCIM API\) is used.


    Default value: *1*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `User`
    
    </td>
    <td valign="top">
    
    Valid if *BasicAuthentication* is configured as authentication method.

    Enter the *userID* of your SAP SuccessFactors technical user in the following format: **<user\_ID\>@<company\_ID\>**
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `Password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Valid if *BasicAuthentication* is configured as authentication method.

    Enter the password for your SAP SuccessFactors technical user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sf.company.id`
    
    </td>
    <td valign="top">
    
    Valid if *ClientCertificateAuthentication* is configured as authentication method.

    Enter the Company ID of your SAP SuccessFactors system.

    The Company ID is a short string of characters that identifies each SAP SuccessFactors system. It is like a username for your organization. All users of the same system share the same Company ID.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sf.user.attributes`
    
    </td>
    <td valign="top">
    
    Default property. It's a string representing a comma-separated list of user attributes that have to be loaded \(read\) from SAP SuccessFactors. You can leave the default property value \(all listed attributes\), or leave only some of them.

    > ### Remember:  
    > -   Always make sure that attribute `lastModifiedDateTime` is in the list of values. If you don't specify it, the provisioning from SAP SuccessFactors will fail.
    > -   If a user in SAP SuccessFactors is missing this attribute, it will break the provisioning. You can exclude them from the provisioning \(either by using the `sf.user.filter` property, or by setting a condition in the transformation logic\).

    **Connector version**: SAP SuccessFactors version 1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.user.attributes.expand`
    
    </td>
    <td valign="top">
    
    This property reads additional user data related to *complex attributes*, which are specified in `sf.user.attributes`.

    Default value: *personKeyNav*

    **Connector version**: SAP SuccessFactors version 1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.user.filter`
    
    </td>
    <td valign="top">
    
    The possible values of this property depend on the API version which your SAP SuccessFactors system consumes.

    Use this property to filter users from SAP SuccessFactors. The filter obtains values as described in the OData 2.0 syntax, except any statements with attribute `lastModifiedDateTime`. To learn more, see:

    -   [OData version 2](http://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → **4.5. Filter System Query Option \($filter\)**.
    -   [SAP SuccessFactors API Reference Guide \(OData V2\)](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?version=2311) 
    -   [SAP SuccessFactors Workforce SCIM API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html) and [System for Cross-domain Identity Management for Workforce in SuccessFactors](https://api.sap.com/api/PLTScim/resource)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.user.read.deactivatedafter`
    
    </td>
    <td valign="top">
    
    This property filters SAP SuccessFactors inactive users from a particular date on. It is an optional property which does not appear by default at system creation. It accepts a value in the `yyyy-MM-dd` format. For example: `2023-07-17`

    The `sf.user.read.deactivatedafter` property works together with the `sf.user.filter` property which is added at system creation with the default value: *active eq true*. Using it can further narrow down the filtering results.

    To filter active users along with inactive ones from a particular date on, the following configuration must be in place:

    -   Set the `sf.user.read.deactivatedafter` value to a date in the expected format. For example: *2023-07-17*

    -   `sf.user.filter` = *active eq true*


    As a result, Identity Provisioning reads SAP SuccessFactors active users and the users set to inactive from that date on using the 2023-07-17T00:00:00Z date-time format.

    Depending on the value you define for `sf.user.filter`, expect the following results:

    -   `sf.user.filter` = *active eq false*

        All inactive users will be returned.

    -   `sf.user.filter` = *active eq false and userName sw "Test\_"*

        All inactive users with username starting with Test\_ will be returned.

        > ### Note:  
        > When you filter by `sf.user.filter` = *active eq false* along with the property `sf.user.read.deactivatedafter`, the users that match the two critera will be read twice.

    -   `sf.user.filter` = *active eq true and userName sw "Test\_"*

        Inactive users from the provided date on and all active users with username starting with Test\_ will be returned.


    **Connector version**: SAP SuccessFactors version 2
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.group.filter`
    
    </td>
    <td valign="top">
    
    The possible values of this property depend on the API version which your SAP SuccessFactors system consumes.

    Use this property to filter dynamic groups in SAP SuccessFactors. The filter obtains values as described in the OData 2.0 syntax, except any statements with attribute `lastModifiedDateTime`. To learn more, see:

    -   [OData version 2](http://www.odata.org/documentation/odata-version-2-0/uri-conventions/) → **4.5. Filter System Query Option \($filter\)**
    -   [SAP SuccessFactors API Reference Guide \(OData V2\)](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?version=2311) → **DynamicGroup**
    -   [SAP SuccessFactors Workforce SCIM API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html) and [System for Cross-domain Identity Management for Workforce in SuccessFactors](https://api.sap.com/api/PLTScim/resource)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sf.group.unique.attribute`
    
    </td>
    <td valign="top">
    
    If the service tries to create a group that already exists in the target system, the creation will fail. In this case, the existing group only needs to be updated. This group can be found via search, based on an attribute \(default or specific\).

    To make the search filter by a specific attribute, specify this attribute as a value for the `sf.group.unique.attribute` property.

    If the property is not specified, the search is done by the default attribute: *displayName*

    **Connector version**: SAP SuccessFactors version 2
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\) `sf.page.size`
    
    </td>
    <td valign="top">
    
    Defines the paging size.

    -   Default value: **100**

    -   Maximum value: **1000**


    **Connector version**: SAP SuccessFactors version 1
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \(Optional\)`sf.group.members.paging.enabled`
    
    </td>
    <td valign="top">
    
    This property enables paging of group members.

    The maximum number of group members returned per request is 100. To read more than 100 group members, paging must be enabled.

    **Possible values:**

    -   *true* - Paging is enabled.
    -   *false* - Paging is disabled.

    Default value: *false*

    **Connector version**: SAP SuccessFactors version 2
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

    Exemplary destination \(configuration\):


    <table>
    <tr>
    <td valign="top">
    
    `Type`=*HTTP*

    `Authentication`=*BasicAuthentication*

    `ProxyType`=*Internet*

    `URL`=*https://apitest.successfactors.com/odata/v2*

    `User`=*sfsf\_admin@mycompany.com*

    `Password`=\*\*\*\*\*\*\*\*\*\*\*\*

    `sf.user.attributes`=*userId,username,addressLine1,lastName,country,email,location,firstName,lastModifiedDateTime,personKeyNav,manager/username*

    `sf.user.attributes.expand`=*personKeyNav,manager*

    `sf.user.filter`=*department ne 'Manufacturing'*

    `sf.group.filter`=*groupType eq 'permission'*

    `sf.page.size`=*70*
    
    </td>
    </tr>
    </table>
    
8.  Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SAP SuccessFactors* proxy system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SAP SuccessFactors. For more information, see:

    [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md)

    [SAP SuccessFactors HCM Suite OData API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?locale=en-US&version=latest)

    [SAP SuccessFactors Workforce SCIM API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html)

    **Default read and write transformations for SAP SuccessFactors HCM Suite OData API version 1**:

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
    >         "sourcePath": "$.userId",
    >         "targetPath": "$.id",
    >         "targetVariable": "entityIdSourceSystem"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "targetPath": "$.meta.location",
    >         "functions": [
    >           {
    >             "type": "concatString",
    >             "suffix": "${entityIdSourceSystem}"
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.username",
    >         "targetPath": "$.userName",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.personKeyNav.userAccountNav.username",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "sourcePath": "$.firstName",
    >         "targetPath": "$.name.givenName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.lastName",
    >         "targetPath": "$.name.familyName",
    >         "optional": true
    >       },
    >       {
    >         "sourcePath": "$.email",
    >         "targetPath": "$.emails[0].value",
    >         "optional": true,
    >         "correlationAttribute": true
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.personKeyNav.personIdExternal",
    >         "targetPath": "$.externalId",
    >         "optional": true,
    >         "correlationAttribute": true
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "mappings": [
    >       {
    >         "sourcePath": "$.groupID",
    >         "targetVariable": "entityIdSourceSystem",
    >         "targetPath": "$.id"
    >       },
    >       {
    >         "sourceVariable": "entityBaseLocation",
    >         "targetPath": "$.meta.location",
    >         "targetVariable": "entityLocationSourceSystem",
    >         "functions": [
    >             {
    >                 "type": "concatString",
    >                 "suffix": "${entityIdSourceSystem}"
    >             }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.groupName",
    >         "targetPath": "$.displayName"
    >       },
    >       {
    >         "constant": "urn:ietf:params:scim:schemas:core:2.0:Group",
    >         "targetPath": "$.schemas[0]"
    >       },
    >       {
    >         "sourcePath": "$.users[*].userId",
    >         "preserveArrayWithSingleElement": true,
    >         "targetPath": "$.members[?(@.value)]",
    >         "optional": true
    >       },
    >       {
    >         "constant": "User",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "targetPath": "$.members[*].type"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > 
    > {
    >   "user": {
    >     "scimEntityEndpoint": "Users",
    >     "skipOperations": [
    >       "delete"
    >     ],
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.userId"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "targetPath": "$.userId",
    >         "scope": "createEntity"
    >       },
    >       {
    >         "constant": "t",
    >         "targetPath": "$.status"
    >       },
    >       {
    >         "condition": "$.active == false",
    >         "constant": "f",
    >         "targetPath": "$.status"
    >       },
    >       {
    >         "sourcePath": "$.userName",
    >         "optional": true,
    >         "targetPath": "$.username"
    >       },
    >       {
    >         "sourcePath": "$.name.familyName",
    >         "optional": true,
    >         "targetPath": "$.lastName",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$.name.givenName",
    >         "optional": true,
    >         "targetPath": "$.firstName",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$.name.honorificPrefix",
    >         "optional": true,
    >         "targetPath": "$.salutation",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$.name.honorificSuffix",
    >         "optional": true,
    >         "targetPath": "$.suffix",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$.emails[0].value",
    >         "optional": true,
    >         "targetPath": "$.email",
    >         "defaultValue": null
    >       },
    >       {
    >         "condition": "$.emails[?(@.primary == true)].value != []",
    >         "sourcePath": "$.emails[?(@.primary == true)].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "defaultValue": null,
    >         "targetPath": "$.email",
    >         "functions": [
    >           {
    >             "function": "elementAt",
    >             "index": 0
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.timezone",
    >         "optional": true,
    >         "targetPath": "$.timeZone",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$.nickName",
    >         "optional": true,
    >         "targetPath": "$.nickname",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$.addresses[0].country",
    >         "optional": true,
    >         "targetPath": "$.country",
    >         "defaultValue": null
    >       },
    >       {
    >         "condition": "$.addresses[?(@.primary == true)].country != []",
    >         "sourcePath": "$.addresses[?(@.primary == true)].country",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "defaultValue": null,
    >         "targetPath": "$.country",
    >         "functions": [
    >           {
    >             "function": "elementAt",
    >             "index": 0
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.addresses[0].locality",
    >         "optional": true,
    >         "targetPath": "$.city",
    >         "defaultValue": null
    >       },
    >       {
    >         "condition": "$.addresses[?(@.primary == true)].locality != []",
    >         "sourcePath": "$.addresses[?(@.primary == true)].locality",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "defaultValue": null,
    >         "targetPath": "$.city",
    >         "functions": [
    >           {
    >             "function": "elementAt",
    >             "index": 0
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$.addresses[0].formatted",
    >         "optional": true,
    >         "defaultValue": null,
    >         "targetPath": "$.addressLine1"
    >       },
    >       {
    >         "sourcePath": "$.addresses[1].formatted",
    >         "optional": true,
    >         "targetPath": "$.addressLine2",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$.addresses[2].formatted",
    >         "optional": true,
    >         "targetPath": "$.addressLine3",
    >         "defaultValue": null
    >       },
    >       {
    >         "condition": "$.phoneNumbers[?(@.type == 'work')].value != []",
    >         "sourcePath": "$.phoneNumbers[?(@.type == 'work')].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "defaultValue": null,
    >         "targetPath": "$.businessPhone",
    >         "functions": [
    >           {
    >             "function": "elementAt",
    >             "index": 0
    >           }
    >         ]
    >       },
    >       {
    >         "condition": "$.phoneNumbers[?(@.type == 'fax')].value != []",
    >         "sourcePath": "$.phoneNumbers[?(@.type == 'fax')].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "defaultValue": null,
    >         "targetPath": "$.fax",
    >         "functions": [
    >           {
    >             "function": "elementAt",
    >             "index": 0
    >           }
    >         ]
    >       },
    >       {
    >         "condition": "$.phoneNumbers[?(@.type == 'mobile')].value != []",
    >         "sourcePath": "$.phoneNumbers[?(@.type == 'mobile')].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "defaultValue": null,
    >         "targetPath": "$.cellPhone",
    >         "functions": [
    >           {
    >             "function": "elementAt",
    >             "index": 0
    >           }
    >         ]
    >       },
    >       {
    >         "condition": "$.phoneNumbers[?(@.type == 'home')].value != []",
    >         "sourcePath": "$.phoneNumbers[?(@.type == 'home')].value",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "defaultValue": null,
    >         "targetPath": "$.homePhone",
    >         "functions": [
    >           {
    >             "function": "elementAt",
    >             "index": 0
    >           }
    >         ]
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['employeeNumber']",
    >         "optional": true,
    >         "targetPath": "$.empId",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >         "optional": true,
    >         "targetPath": "$.division",
    >         "defaultValue": null
    >       },
    >       {
    >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >         "optional": true,
    >         "targetPath": "$.department",
    >         "defaultValue": null
    >       }
    >     ]
    >   },
    >   "group": {
    >     "scimEntityEndpoint": "Groups",
    >     "skipOperations": [
    >       "create",
    >       "delete"
    >     ],
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.groupID"
    >       },
    >       {
    >         "sourcePath": "$.displayName",
    >         "targetPath": "$.groupName"
    >       },
    >       {
    >         "constant": "DynamicGroup",
    >         "targetPath": "$.__metadata.uri"
    >       },
    >       {
    >         "constant": "permission",
    >         "targetPath": "$.groupType"
    >       },
    >       {
    >         "optional": true,
    >         "preserveArrayWithSingleElement": true,
    >         "sourcePath": "$.members[*].value",
    >         "targetPath": "$.members[?(@.value)]"
    >       }
    >     ]
    >   }
    > }
    > ```


    
    </td>
    </tr>
    </table>
    
    **Default read and write transformations for SCIM API version 2**:


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
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourceVariable": "entityBaseLocation",
    >                 "targetPath": "$.meta.location",
    >                 "targetVariable": "entityLocationSourceSystem",
    >                 "functions": [
    >                     {
    >                         "type": "concatString",
    >                         "suffix": "${entityIdSourceSystem}"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.userType",
    >                 "targetPath": "$.userType"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional": true,
    >                 "targetPath": "$.name.familyName"
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
    >                 "sourcePath": "$.name.honorificPrefix",
    >                 "optional": true,
    >                 "targetPath": "$.name.honorificPrefix"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificSuffix",
    >                 "optional": true,
    >                 "targetPath": "$.name.honorificSuffix"
    >             },
    >             {
    >                 "sourcePath": "$.name.formatted",
    >                 "optional": true,
    >                 "targetPath": "$.name.formatted"
    >             },
    >             {
    >                 "sourcePath": "$.nickName",
    >                 "optional": true,
    >                 "targetPath": "$.nickName"
    >             },
    >             {
    >                 "sourcePath": "$.preferredLanguage",
    >                 "optional": true,
    >                 "targetPath": "$.preferredLanguage"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.title",
    >                 "optional": true,
    >                 "targetPath": "$.title"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.locale",
    >                 "optional": true,
    >                 "targetPath": "$.locale"
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "optional": true,
    >                 "targetPath": "$.timezone"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['perPersonUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['perPersonUuid']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['loginMethod']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['loginMethod']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['personIdExternal']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['personIdExternal']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['customFields']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['customFields']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']"
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
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['$ref']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['$ref']"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.phoneNumbers"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "sourcePath": "$.emails[?(@.primary == true)].value",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.groups",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups"
    >             }
    >         ],
    >         "scimEntityEndpoint": "Users"
    >     },
    >     "group": {
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetPath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    >             {
    >                 "sourceVariable": "entityBaseLocation",
    >                 "targetPath": "$.meta.location",
    >                 "targetVariable": "entityLocationSourceSystem",
    >                 "functions": [
    >                     {
    >                         "type": "concatString",
    >                         "suffix": "${entityIdSourceSystem}"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas"
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
    >         ],
    >         "scimEntityEndpoint": "Groups"
    >     }
    > }
    > ```


    
    </td>
    <td valign="top">
    
    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:extension:successfactors:2.0:User",
    >                     "urn:ietf:params:scim:schemas:core:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:sap:2.0:User",
    >                     "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "targetPath": "$.userName"
    >             },
    >             {
    >                 "sourcePath": "$.nickName",
    >                 "optional": true,
    >                 "targetPath": "$.nickName"
    >             },
    >             {
    >                 "sourcePath": "$.preferredLanguage",
    >                 "optional": true,
    >                 "targetPath": "$.preferredLanguage"
    >             },
    >             {
    >                 "sourcePath": "$.userType",
    >                 "targetPath": "$.userType"
    >             },
    >             {
    >                 "sourcePath": "$.externalId",
    >                 "optional": true,
    >                 "targetPath": "$.externalId"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "optional": true,
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.locale",
    >                 "optional": true,
    >                 "targetPath": "$.locale"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:sap:2.0:User']['userUuid']"
    >             },
    >             {
    >                 "sourcePath": "$.emails",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.emails"
    >             },
    >             {
    >                 "condition": "$.emails.length() > 0",
    >                 "targetPath": "$.emails[*].type",
    >                 "constant": "work"
    >             },
    >             {
    >                 "sourcePath": "$.timezone",
    >                 "optional": true,
    >                 "targetPath": "$.timezone"
    >             },
    >             {
    >                 "sourcePath": "$.name.formatted",
    >                 "optional": true,
    >                 "targetPath": "$.name.formatted"
    >             },
    >             {
    >                 "sourcePath": "$.name.familyName",
    >                 "optional": true,
    >                 "targetPath": "$.name.familyName"
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
    >                 "sourcePath": "$.name.honorificPrefix",
    >                 "optional": true,
    >                 "targetPath": "$.name.honorificPrefix"
    >             },
    >             {
    >                 "sourcePath": "$.name.honorificSuffix",
    >                 "optional": true,
    >                 "targetPath": "$.name.honorificSuffix"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['perPersonUuid']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['perPersonUuid']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['loginMethod']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['loginMethod']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['personIdExternal']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['personIdExternal']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['customFields']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:successfactors:2.0:User']['customFields']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['department']"
    >             },
    >             {
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['division']"
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
    >                 "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['$ref']",
    >                 "optional": true,
    >                 "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['$ref']"
    >             },
    >             {
    >                 "sourcePath": "$.title",
    >                 "optional": true,
    >                 "targetPath": "$.title"
    >             },
    >             {
    >                 "sourcePath": "$.phoneNumbers",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.phoneNumbers"
    >             },
    >             {
    >                 "sourcePath": "$.active",
    >                 "targetPath": "$.active"
    >             },
    >             {
    >                 "sourcePath": "$.groups[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.groups[?(@.value)]",
    >                 "functions": [
    >                     {
    >                         "entityType": "group",
    >                         "function": "resolveEntityIds"
    >                     }
    >                 ]
    >             },
    >             {
    >                 "sourcePath": "$.Operations",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.Operations",
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas",
    >                 "scope": "patchEntity"
    >             }
    >         ],
    >         "scimEntityEndpoint": "Users"
    >     },
    >     "group": {
    >         "skipOperations": [
    >             "create",
    >             "delete"
    >         ],
    >         "mappings": [
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id"
    >             },
    >             {
    >                 "sourcePath": "$.Operations",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.Operations",
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "sourcePath": "$.displayName",
    >                 "targetPath": "$.displayName"
    >             },
    >             {
    >                 "sourcePath": "$.schemas",
    >                 "preserveArrayWithSingleElement": true,
    >                 "targetPath": "$.schemas",
    >                 "scope": "patchEntity"
    >             },
    >             {
    >                 "constant": [
    >                     "urn:ietf:params:scim:schemas:core:2.0:Group",
    >                     "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group"
    >                 ],
    >                 "targetPath": "$.schemas"
    >             },
    >             {
    >                 "targetPath": "$.members",
    >                 "type": "remove"
    >             },
    >             {
    >                 "sourcePath": "$.members[*].value",
    >                 "preserveArrayWithSingleElement": true,
    >                 "optional": true,
    >                 "targetPath": "$.members[?(@.value)]"
    >             }
    >         ],
    >         "scimEntityEndpoint": "Groups"
    >     }
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


[URI Conventions \(OData Version 2.0\)](http://www.odata.org/documentation/odata-version-2-0/uri-conventions)

[SAP SuccessFactors HCM Suite OData API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html?version=latest)

[SAP SuccessFactors Workforce SCIM API](https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/534356acc0ab4b0e8977ebfb2eb432f7/895a0d10d4984152b9f6d0cd9f9f850c.html)

