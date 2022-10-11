<!-- loio77e6811e698948418179202bcf775e7a -->

# Groups Search \(Deprecated\)

The group search method of the Identity Authentication implementation of the SCIM REST API protocol allows you to perform a request for group search. Group search is implemented as defined by the System for Cross-domain Identity Management \(SCIM\) protocol.



## Request

**URI:**`https://<tenant ID>.accounts.ondemand.com/service/scim/Groups`

**HTTP Method:***GET*

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

`count`



</td>
<td valign="top">

No



</td>
<td valign="top">

Paginates the response. Represents the number of groups which will be returned per page.

The maximum number of groups returned per page is limited to 100. If you have more than 100 groups, and you want to get the full list, you have to perform multiple requests.



</td>
</tr>
<tr>
<td valign="top">

`startIndex`



</td>
<td valign="top">

No



</td>
<td valign="top">

Paginates the response. Represents the start index from which the results are returned.



</td>
</tr>
</table>

> ### Note:  
> If none of the request parameters are included, the number of items which will be returned per page will be at most 100 starting from index `1`.



### Request Example

```
GET /service/scim/Groups?count=10&startIndex=1
Content-Type: application/scim+json

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

Lists all the groups in a tenant.

> ### Note:  
> The maximum number of group members in a group returned in the response is limited to 100.
> 
> If you have more than 100 group members, and you want to get the full list, you have to perform multiple requests via the Users Search SCIM REST API. For more information, see [Users Search \(Deprecated\)](users-search-deprecated-3af7dfa.md).



</td>
</tr>
</table>

For more information about the general error codes that may be returned, see [General Error Codes](general-error-codes-182352d.md).



### Response Example



```
{
    "schemas": [
        "urn:ietf:params:scim:api:messages:2.0:ListResponse"
    ],
    "totalResults": 2,
    "itemsPerPage": 2,
    "startIndex": 1,
    "Resources": [
        {
            "id": "57aadecee4b0c8e9241d1635",
            "displayName": "New Administrators",
            "schemas": [
                "urn:ietf:params:scim:schemas:core:2.0:Group",
                "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group"
            ],
            "members": [
                {
                    "value": "P000001",
                    "$ref": "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000001",
                    "display": "Dona Moore"
                },
{
                    "value": "P000002",
                    "$ref": "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000002",
                    "display": "Michael Adams"
                },
                
            ],
            "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group": {
                "name": "Administrators",
                "description": "Group Administrators description."
                "groupId": "e56a7d8b-8a89-54k5-7s89-5689d681e381i"	
            },
            "meta": {
                "location": "https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/57aadecee4b0c8e9241d1635",
                "resourceType": "Group",
                "version": "1.0"
            }
        },
        {
            "id": "35asdfqaass50s8r8751d1721",
            "displayName": "Managers",
            "schemas": [
                "urn:ietf:params:scim:schemas:core:2.0:Group",
                "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group"
            ],
            "members": [
                {
                    "value": "P000001",
                    "$ref": "https://<tenant ID>.accounts.ondemand.com/service/scim/Users/P000001",
                    "display": "Dona Moore"
                },
                ],
            "urn:sap:cloud:scim:schemas:extension:custom:2.0:Group": {
                "name": "Managers"
                "description": "Group Managers description."
                "groupId": "319805v-2as7-45c7-9f50-97vidkos0in2"
            },
            "meta": {
                "location": "https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/35asdfqaass50s8r8751d1721",
                "resourceType": "Group",
                "version": "1.0"
            }
        }
    ]
}
```

**Related Information**  


[Group Resource \(Deprecated\)](group-resource-deprecated-8c6ebd7.md "The group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on a known group.")

[Create Group Resource \(Deprecated\)](create-group-resource-deprecated-a831c94.md "The create group resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user group.")

[Update Group Resource \(Deprecated\)](update-group-resource-deprecated-81ca50e.md "The update group method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the update of an existing group. The method does not create a new group.")

[Delete Group Resource \(Deprecated\)](delete-group-resource-deprecated-41bb519.md "The delete group resource method of the Identity Authentication implementation of the SCIM REST API protocol allows you to delete an existing group. Delete group resource is implemented as defined by the System for Cross-domain Identity Management (SCIM) protocol.")

[SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md "This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management (SCIM) REST API protocol.")

