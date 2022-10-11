<!-- loioa831c947a58b40228318f551dcb35895 -->

# Create Group Resource \(Deprecated\)

The create group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user group.



> ### Note:  
> This API will be deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead.



> ### Note:  
> Create group resource is implemented as defined by the System for Cross-domain Identity Management \(SCIM\) protocol.

> ### Remember:  
> The maximum number of groups assigned to a user is 500.



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/scim/Groups`

**HTTP Method:***POST*

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

Attributes



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

`displayName`



</td>
<td valign="top">

Yes



</td>
<td valign="top">

String



</td>
<td valign="top">

Human readable name for the group.



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

> ### Note:  
> If `name` is missing, `displayName` is taken as name of the group.



</td>
<td valign="top">

String



</td>
<td valign="top">

The name of the group.

> ### Remember:  
> The name must be unique within the Identity Authentication tenant.



</td>
<td valign="top">

Request body



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

Description for the group.



</td>
<td valign="top">

Request body



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

The members of the group. Use it to assign users to the group at the creation of the group.

Sub-attribute: `value` - takes the `id` of the user



</td>
<td valign="top">

Request body



</td>
</tr>
</table>



### Request Example

```

POST /service/scim/Groups
Content-Type: application/scim+json
{
   "displayName": "Identity Authentication Administrators",
   "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group": {
         "name": "Administrators",
         "description": "Group Administrators description"
   },
   "members": [
         {
            "value": "P000001"
         }
   ]
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

201



</td>
<td valign="top">

Created



</td>
<td valign="top">

Indicates success.

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

-   The group cannot be created, because the maximum number of 10,000 groups for the tenant have been reached.
-   The group cannot be created, because the syntax of the sent request is invalid.
-   The group cannot be created, because there is a user who has reached the limit of 500 assigned groups.



</td>
</tr>
<tr>
<td valign="top">

409



</td>
<td valign="top">

Conflict



</td>
<td valign="top">

The group cannot be created, because a group with the same name already exists.



</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [General Error Codes](general-error-codes-182352d.md).



### Response Example

 



```
{
    "id": "57aadecee4b0c8e9241d1635",
    "displayName": "Administrators",
    "schemas": [
        "urn:ietf:params:scim:schemas:core:2.0:Group",
        "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group"
    ],
    "members": [
        {
            "value": "P000001",
            "$ref": "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000001",
            "display": "Dona Moore"
        }
    ],
    "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group": {
        "name": "Administrators",
        "description": "Group Administrators description"
        "groupId" : "6986381a-3pis-56o5-6813-w05cd64q9f1o"
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

[Update Group Resource \(Deprecated\)](update-group-resource-deprecated-81ca50e.md "The update group method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the update of an existing group. The method does not create a new group.")

[Delete Group Resource \(Deprecated\)](delete-group-resource-deprecated-41bb519.md "The delete group resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing group. Delete group resource is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

