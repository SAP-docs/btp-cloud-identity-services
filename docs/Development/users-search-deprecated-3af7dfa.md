<!-- loio3af7dfae0aad4cf79ab8d822f8322e76 -->

# Users Search \(Deprecated\)

The user search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for user search. User search is implemented as defined by the System for Cross-domain Identity Management \(SCIM\) protocol for querying and filtering resources.



> ### Note:  
> This API will be deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead. For more information, see [Migrating Identity Authentication SCIM REST API to Identity Directory Service API](migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api-106dbe0.md).



You can search for users by specifying pagination parameters in the HTTP **GET** request to page through large number of resources. When searching for users, you can combine pagination with filtering.

Depending on the specified pagination parameters, there are two approaches when searching for users with pagination:

-   Id-Based pagination - that is, page through users by specifying `startId` parameter.

    > ### Remember:  
    > This is the recommended approach.

-   Index-Based pagination as defined in the SCIM 2.0 standard - that is, page through users by specifying `startIndex` parameter.



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/scim/Users/`

**HTTP Method:***GET*

**Content-Type: application/scim+json**

**Authentication mechanisms:**

-   Client certificate

-   Basic authentication


> ### Note:  
> You must have a system as administrator with an assigned *Manage Users* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).

**Request Parameters**

**Filtering**


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Required



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
<th valign="top">

Parameter Type



</th>
</tr>
<tr>
<td valign="top">

`filter`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

Defines the search criteria. If missing, the search criteria will depend on the other parameters.



</td>
<td valign="top">

Path



</td>
</tr>
</table>

**Supported Operators**


<table>
<tr>
<th valign="top">

Operator



</th>
<th valign="top">

Description



</th>
<th valign="top">

Behavior



</th>
</tr>
<tr>
<td valign="top">

eq



</td>
<td valign="top">

equal



</td>
<td valign="top">

The attribute and attribute values must be identical for a match.



</td>
</tr>
<tr>
<td valign="top">

and



</td>
<td valign="top">

Logical And



</td>
<td valign="top">

The filter is only a match if all expressions evaluate to true.



</td>
</tr>
</table>

**User Search Attributes**


<table>
<tr>
<th valign="top">

Attribute



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

id



</td>
<td valign="top">

Public user ID of the user



</td>
</tr>
<tr>
<td valign="top">

userUuid



</td>
<td valign="top">

User ID in the universally unique identifier \(UUID\)



</td>
</tr>
<tr>
<td valign="top">

emails



</td>
<td valign="top">

E-mail address of the user



</td>
</tr>
<tr>
<td valign="top">

userName



</td>
<td valign="top">

Custom logon name of the user



</td>
</tr>
<tr>
<td valign="top">

name.familyName



</td>
<td valign="top">

Last name of the user



</td>
</tr>
<tr>
<td valign="top">

addresses.country



</td>
<td valign="top">

The \[home\]country of the user. The value is in the ISO 3166-1 alpha 2 "short" code format. \[[ISO3166](https://tools.ietf.org/html/draft-ietf-scim-core-schema-17#ref-ISO3166)\].



</td>
</tr>
<tr>
<td valign="top">

groups



</td>
<td valign="top">

User group assignment information



</td>
</tr>
</table>

**Pagination**


<table>
<tr>
<th valign="top">

Approach



</th>
<th valign="top">

Parameter



</th>
<th valign="top">

Required



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
<th valign="top">

Parameter Type



</th>
</tr>
<tr>
<td valign="top" rowspan="2">

Id-Based Pagination

> ### Note:  
> This is the recommended approach.



</td>
<td valign="top">

`startId`



</td>
<td valign="top">

No



</td>
<td valign="top">

String



</td>
<td valign="top">

Default value: `None`

Possible values:

-   `initial`
-   `<user id>`

The first entry of the query result.

If no value is specified, the Index-based pagination is used.

If initial value is specified, the initial user is returned as the first entry of the query result.

If <user id\> value is specified, the user with this user id is returned as the first entry of the query result.

> ### Remember:  
> If you have more than 100 user, and you want to get the full list, you have to perform multiple requests.



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`count`



</td>
<td valign="top">

No



</td>
<td valign="top">

Integer



</td>
<td valign="top">

Represents the number of items which will be returned per page, for example 10. A negative value is interpreted as 0. A value of 0 indicates that no resource results are to be returned except for `totalResults`.

Default value: `100`.

> ### Note:  
> The maximum number of items returned per page is limited to 100.



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Index-Based Pagination



</td>
<td valign="top">

`startIndex`



</td>
<td valign="top">

No



</td>
<td valign="top">

Integer



</td>
<td valign="top">

Represents the start index from which the results are returned. Default value: `1`. A value less than `1` is interpreted as `1`.

> ### Remember:  
> If you have more than 100 user, and you want to get the full list, you have to perform multiple requests.



</td>
<td valign="top">

Path



</td>
</tr>
<tr>
<td valign="top">

`count`



</td>
<td valign="top">

No



</td>
<td valign="top">

Integer



</td>
<td valign="top">

Represents the number of items which will be returned per page, for example 10. A negative value is interpreted as 0. A value of 0 indicates that no resource results are to be returned except for `totalResults`.

Default value: `100`.

> ### Note:  
> The maximum number of items returned per page is limited to 100.



</td>
<td valign="top">

Path



</td>
</tr>
</table>

> ### Note:  
> If none of the request parameters are included, the number of items which will be returned per page will be at most 100 starting from index `1`.



## Request Examples



```
GET /service/scim/Users?filter=emails eq "john.smith@sap.com" and addresses.country eq "US"
```

```
GET /service/scim/Users?count=10&startIndex=1
```

```
GET /service/scim/Users?count=10&startId=initial
```

```
GET /service/scim/Users?count=10&startId=12abc315sa2qwe12ab3cdef567
```



## Response

**Format**: *JSON*

The response contains a list of users with the following attributes:



### Pagination Attributes

Depending on the pagination approach you choose, the following pagination attributes are returned in the response:


<table>
<tr>
<th valign="top">

Approach



</th>
<th valign="top">

Attribute



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="3">

Index-Based pagination



</td>
<td valign="top">

`totalResults`



</td>
<td valign="top">

Specifies the total number of results matching the query, for example: 100.



</td>
</tr>
<tr>
<td valign="top">

`itemsPerPage`



</td>
<td valign="top">

Specifies the number of query results returned in a query response page, for example: 3.



</td>
</tr>
<tr>
<td valign="top">

`startIndex`



</td>
<td valign="top">

The 1-based index of the first result in the current set of query results, for example: 1.



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Id-Based pagination



</td>
<td valign="top">

`totalResults`



</td>
<td valign="top">

Specifies the total number of results matching the query, for example: 100.



</td>
</tr>
<tr>
<td valign="top">

`itemsPerPage`



</td>
<td valign="top">

Specifies the number of query results returned in a query response page, for example: 3.



</td>
</tr>
<tr>
<td valign="top">

`startId`



</td>
<td valign="top">

Specifies the first entry of the query result, for example: ***initial*** or ***<user id\>***.



</td>
</tr>
<tr>
<td valign="top">

`nextId`



</td>
<td valign="top">

Specifies the next user id \(that is, the id of the first user on the next page\). For example: ***<user id\>*** or ***<end\>***. The ***<end\>*** value indicates that the last user of the total number of users matching the query is returned.



</td>
</tr>
</table>



### User Attributes

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

-   `addresses[home].postalCode`

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
    > 
    > 
    > </th>
    > <th valign="top">
    > 
    > Meaning
    > 
    > 
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > 39
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > Corporate User Store
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > 100
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > SuccessFactors
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > 101
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > SAP Learning Management System
    > 
    > 
    > 
    > </td>
    > </tr>
    > </table>
    > 
    > You can find information about the user's source system type and source system ID under the legal tab in the user details section. For more information, see [List and Edit User Details](../Operation-Guide/list-and-edit-user-details-045cb01.md).

-   `sourceSystemId`

    > ### Note:  
    > An identifier assigned by the source system administrator.

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

-   `passwordLoginTime`

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
        > `value` must be a string with a maximum length of 256 characters.



The response does not contain the whole **User resource object**. It returns only the specified attributes here, as if you have limited the response to those attributes using the attributes `query` parameter. `totalResults` shows the total number of results matching the query.

**Response Status and Error Codes**

**Success Codes**


<table>
<tr>
<th valign="top">

Response Code



</th>
<th valign="top">

Meaning



</th>
<th valign="top">

Response Description



</th>
</tr>
<tr>
<td valign="top">

200



</td>
<td valign="top">

OK



</td>
<td valign="top">

Operation Successful



</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [General Error Codes](general-error-codes-182352d.md).

**Related Information**  


[User Resource \(Deprecated\)](user-resource-deprecated-7ae17a6.md "The user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known user.")

[Create User Resource \(Deprecated\)](create-user-resource-deprecated-cea8778.md "The create user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user.")

[Update User Resource \(Deprecated\)](update-user-resource-deprecated-9e36479.md "The update user method of the implementation of the SCIM REST API protocol provides information on the update of a known user. The method does not create a new user.")

[Delete User Resource \(Deprecated\)](delete-user-resource-deprecated-436015d.md "The delete user resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing user. Delete user resource is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

