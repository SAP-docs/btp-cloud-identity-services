<!-- loio81ca50e7e604474fa9ce53c831156cd2 -->

# Update Group Resource \(Deprecated\)

The update group method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the update of an existing group. The method does not create a new group.



> ### Note:  
> This API is deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead. For more information, see [Migrating Identity Authentication SCIM REST API to Identity Directory Service API](migrating-identity-authentication-scim-rest-api-to-identity-directory-service-api-106dbe0.md).



> ### Note:  
> Update group resource is implemented as defined by the System for Cross-domain Identity Management \(SCIM\) protocol.



**Prerequisites:**

You have the `id` of the group whose resource you want to update.

> ### Note:  
> To get the `id` of the group, list all the groups in the tenant and copy the `id` of the group whose resource you want to get. For more information, see [Groups Search \(Deprecated\)](groups-search-deprecated-77e6811.md).

> ### Caution:  
> `id` and `groupId` have different values. You must use the `id` value for the request.



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/<id of the group>`

**HTTP Method:***PUT*

**Authentication mechanisms:**

-   Client certificate

-   Basic authentication


> ### Note:  
> You must have a system as administrator with an assigned *Manage Users* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).



### Request Headers


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Required

</th>
<th valign="top">

Values

</th>
</tr>
<tr>
<td valign="top">

`Content-Type`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

application/scim+json

</td>
</tr>
</table>



### Request Attributes


<table>
<tr>
<th valign="top">

Attribute

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

`id`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

String

</td>
<td valign="top">

The `id` of the group whose resource you want to update.

> ### Caution:  
> `id` and `groupId` have different values. You must use the `id` value for the request.



</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`displayName`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

String

</td>
<td valign="top">

Use it to change the human readable name for the group.

</td>
<td valign="top">

Request Body

</td>
</tr>
<tr>
<td valign="top">

`members`

</td>
<td valign="top">

No

</td>
<td valign="top">

Complex

</td>
<td valign="top">

Use it to assign users to the group.

Sub-attribute: `value` - takes the `id` of the user.

> ### Remember:  
> The maximum number of groups assigned to a user is 500.
> 
> Only the users that are included in the request will be assigned to the group.
> 
> To assign new users to the group, and at the same time keep the existing users assigned, include both the new and existing users in the request.
> 
> If the `members` attribute is missing all the users will be unassigned from the group.



</td>
<td valign="top">

Request Body

</td>
</tr>
<tr>
<td valign="top">

`description`

</td>
<td valign="top">

No

</td>
<td valign="top">

String

</td>
<td valign="top">

Use it to update the description for the group.

> ### Caution:  
> Requires the `name` attribute.



</td>
<td valign="top">

Request body

</td>
</tr>
<tr>
<td valign="top">

`name`

</td>
<td valign="top">

No

> ### Caution:  
> The `name` attribute is required if you want to update the description of the group.



</td>
<td valign="top">

String

</td>
<td valign="top">

The name of the group whose `description` you want to update.

</td>
<td valign="top">

Request body

</td>
</tr>
</table>

> ### Caution:  
> Make sure that the **`id` of the group** in the URI and the `id` of the group in the request body match. If they differ, the system returns **400 Bad Request** with the ***Mismatched group id*** message.



### Request Example



### Assign Members to the Group Example

```

{
   "id": "<id of the group>",
   "displayName": "New Administrators",
   "members": [
        {
          "value": "P000001"
        },
         {
          "value": "P000002"
        }
              ]
}

```



### Update Description of the Group Example

```

{
    "id": "<id of the group>",
    "displayName": "New Administrators",
    "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group": {
      "description": "Application administrators",
      "name": "<the name of the group>"
    }
}
```



## Response



### Response Status and Error Codes


<table>
<tr>
<th valign="top">

Code

</th>
<th valign="top">

Reason

</th>
<th valign="top">

Description

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

Operation successful.

> ### Note:  
> The maximum number of group members in a group returned in the response is limited to 100.
> 
> If you have more than 100 group members, and you want to get the full list, you have to perform multiple requests via the Users Search SCIM REST API. For more information, see [Users Search \(Deprecated\)](users-search-deprecated-3af7dfa.md).



</td>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Bad Request

</td>
<td valign="top">

-   The group cannot be updated, because the syntax of the sent request is invalid.
-   The group cannot be updated, because there is a user who has reached the limit of 500 assigned groups.



</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [Error and Success Codes](error-and-success-codes-7f87a75.md).

> ### Note:  
> The `display` attribute returns the name of the user that is assigned to the group.



### Response Example





## Example

```

{
    "id": "57aadecee4b0c8e9241d1635",
    "displayName": "New Administrators",
    "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:Group",
        "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group"
    ],
    "members": [
        {
            "value": "P00001",
            "$ref": "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000001",
            "display": "Dona Moore"
        },
        {
            "value": "P000002",
            "$ref": "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000002",
            "display": "Michael Adams"
        }
    ],
    "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group": {
        "name": "Administrators"
        "groupId": "6986381a-3pis-56o5-6813-w05cd64q9f1o"
    },
    "meta": {
        "location": "https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/57aadecee4b0c8e9241d1635",
        "resourceType": "Group",
        "version": "1.0"
    }
}

```

**Related Information**  


[Groups Search \(Deprecated\)](groups-search-deprecated-77e6811.md "The group search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for group search. Group search is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[Group Resource \(Deprecated\)](group-resource-deprecated-8c6ebd7.md "The group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known group.")

[Create Group Resource \(Deprecated\)](create-group-resource-deprecated-a831c94.md "The create group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user group.")

[Delete Group Resource \(Deprecated\)](delete-group-resource-deprecated-41bb519.md "The delete group resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing group. Delete group resource is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

