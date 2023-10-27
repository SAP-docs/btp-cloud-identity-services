<!-- loio7ae17a6da5314246a04d113f902d0fdf -->

# User Resource \(Deprecated\)

The user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known user.



> ### Note:  
> This API is deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead. For more information, see [Migrating Identity Authentication SCIM REST API to Identity Directory Service API](migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api-106dbe0.md).



> ### Note:  
> User resource is implemented as defined by the SCIM protocol.



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/scim/Users/<id>`

**HTTP Method:***GET*

**Content-Type: application/scim+json**

**Authentication mechanisms:**

-   Client certificate

-   Basic authentication


> ### Note:  
> You must have a system as administrator with an assigned *Manage Users* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).

**Request Parameters**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Required

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`path`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The current path parameter is id.

</td>
</tr>
</table>



## Request Example



## Example

```
GET /service/scim/Users/P000000
```



## Response

**Format**: *application/scim+json*

**Response**

The response contains user object with the following user attributes:

-   `meta`

-   `schemas`
-   `userType`

-   `id`

-   `userUuid`

-   `emails.value`

-   `name.honorificPrefix`

-   `name.givenName`

-   `name.familyName`

-   `name.middleName`

-   `userName`

-   `addresses[work].streetAddress`

-   `addresses[work].locality`

    > ### Note:  
    > The attribute equals to city.

-   `addresses[work].region`

    > ### Note:  
    > The attribute is relevant only for Canada and the United States of America. It equals to the *state* in these countries.

-   `addresses[work].postalCode`

-   `addresses[work].country`

-   `addresses[home].streetAddress`

-   `addresses[home].locality`

    > ### Note:  
    > The attribute equals to city.

-   `addresses[home].region`

    > ### Note:  
    > The attribute is relevant only for Canada and the United States of America. It equals to the *state* in these countries.

-   `addresses[home].country`

-   `locale`

-   `phoneNumbers[work].value`

-   `phoneNumbers[mobile].value`

-   `phoneNumbers[fax].value`

-   `timeZone`

-   `active`

    > ### Note:  
    > If the `active` parameter and its value are not present in the response, the user status is equivalent to the `new` status in Identity Authentication.

-   `displayName`

-   `sourceSystem`

    > ### Note:  
    > Valid values:
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > Value
    > 
    > </th>
    > <th valign="top">
    > 
    > Meaning
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > 39
    > 
    > </td>
    > <td valign="top">
    > 
    > Corporate User Store
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > 100
    > 
    > </td>
    > <td valign="top">
    > 
    > SuccessFactors
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > 101
    > 
    > </td>
    > <td valign="top">
    > 
    > SAP Learning Management
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > 102
    > 
    > </td>
    > <td valign="top">
    > 
    > SAP Fieldglass
    > 
    > </td>
    > </tr>
    > </table>

-   `sourceSystemId`

    > ### Note:  
    > An identifier assigned by the source system administrator.

-   `sourceSystemId`

-   `contactPreferenceEmail`

-   `contactPreferenceTelephone`

-   `industryCrm`

-   `company`

-   `companyRelationship`

-   `department`

-   `groups`

-   `corporateGroups`

    > ### Note:  
    > This attribute is applicable for the corporate user store scenarios and contains the groups the user in the corporate user store is assigned to.

-   `mailVerified`
-   `passwordStatus`

    > ### Note:  
    > Supported values: `initial`, `enabled`, and `disabled`.

-   `userType`

    > ### Note:  
    > Supported values: `public`, `partner`, `customer`, and `employee`.

-   `telephoneVerified`

    > ### Note:  
    > Supported values: `true` or `false`.

-   `telephoneVerificationAttempts`

    > ### Note:  
    > `telephoneVerificationAttempts` can take values from 0 to 5 including.

-   `passwordPolicy`

    > ### Note:  
    > Returns the URL of the valid password policy.

-   `passwordStatus`

    > ### Note:  
    > Supported values: `importedPassword`, `initial`, `enabled`, and `disabled`.

-   `passwordFailedLoginAttempts`

    > ### Note:  
    > `passwordFailedLoginAttempts` can take values from 0 to 5 including.

-   `otpFailedLoginAttempts`

    > ### Note:  
    > `otpFailedLoginAttempts` can take values from 0 to 4 including.

-   `termsOfUse`
    -   `timeOfAcceptance`
    -   `name`
    -   `id`
    -   `locale`
    -   `version`

-   `privacyPolicy`
    -   `timeOfAcceptance`
    -   `name`
    -   `id`
    -   `locale`
    -   `version`

-   `socialIdentities`

    > ### Note:  
    > Returns information about the social accounts that are linked to the user's account in Identity Authentication. Supported values: `socialId`, `socialProvider`, and `dateOfLinking`.

-   `passwordLoginTime `

    > ### Note:  
    > The value of the attribute is updated once per 24 hours.

-   `loginTime`

    > ### Note:  
    > The value of the attribute is updated once per 24 hours.

-   `passwordSetTime`

**Enterprise User Schema Extension**

> ### Note:  
> The values of the following attributes are returned when the Enterprise User Schema Extension is used.

-   `employeeNumber`

-   `costCenter`

-   `organization`

    > ### Note:  
    > Equals the `company` attribute from the Core schema.

-   `division`

-   `department`

    > ### Note:  
    > Equals the `department` attribute from the Core schema.

-   `manager`

    -   `value`

    -   `$ref`

    -   `displayName`

        > ### Note:  
        > Read only.



**Custom Attributes Schema Extension**

Administrators at Identity Authentication can store, read, create, and update customer specific data in up to 10 custom attributes via the SCIM API.

> ### Note:  
> The values of the following attributes are returned when the Custom Attributes Schema Extension \(urn:sap:cloud:scim:schemas:extension:custom:2.0:User\) is used.

-   `attributes`

    -   `name`

        > ### Note:  
        > `name` can take values from `customAttribute1` to `customAttribute10`.

    -   `value`

        > ### Note:  
        > `value` must be string with a maximum length of 256 characters.



**Related Information**  


[Users Search \(Deprecated\)](users-search-deprecated-3af7dfa.md "The user search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for user search. User search is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol for querying and filtering resources.")

[Create User Resource \(Deprecated\)](create-user-resource-deprecated-cea8778.md "The create user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user.")

[Update User Resource \(Deprecated\)](update-user-resource-deprecated-9e36479.md "The update user method of the implementation of the SCIM REST API protocol provides information on the update of a known user. The method does not create a new user.")

[Delete User Resource \(Deprecated\)](delete-user-resource-deprecated-436015d.md "The delete user resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing user. Delete user resource is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

