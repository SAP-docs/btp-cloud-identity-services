<!-- loio114076db254b4ce29958a58adb124260 -->

# Restore Soft-Deleted User \(Restricted Availability\)

Restore a user that is soft-deleted \(blocked\) in the tenant of SAP Cloud Identity Services.



<a name="loio114076db254b4ce29958a58adb124260__section_lyw_cqf_n2c"/>

## Prerequisites

-   You are a tenant administrator of SAP Cloud Identity Services with а *Manage Users* role or assigned `CREATE_USERS` policy. For more information, see [Edit Administrator Authorizations \(Restricted Availability\)](edit-administrator-authorizations-restricted-availability-297b3b2.md) or [Configure User Authorizations](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/424b64c0831b466cbf5680faa58e92b8.html?locale=en-US&state=PRODUCTION&version=Cloud).

-   You have the *Soft Delete Users* option enabled in the Tenant Settings for your tenant. For more information, see [Enable Soft Delete for Users in Administration Console \(Restricted Availability\)](enable-soft-delete-for-users-in-administration-console-restricted-availability-25a6175.md).




## Context

The restore of a soft deleted \(blocked\) user is triggered during the user creation process. Since you must provide the `userUuid` attribute of the user that you want to restore, you should do the user creation via the [Identity |Directory API](https://api.sap.com/api/IdDS_SCIM/path/createUser).

You must provide in the create user request the `userUuid` of the user that you want to restore. The soft‑deleted \(blocked\) user with the same `userUuid` as provided in the request must exist. Only then the user is restored, otherwise a new user is created.

> ### Remember:  
> If a `userUuid` is provided and a soft‑deleted \(blocked\) user with the same `userUuid` exists, that user is restored, instead of a new user created.



For more information about how to list all soft-deleted \(blocked\) users, see [Read All Soft-Deleted Users \(Restricted Availability\)](read-all-soft-deleted-users-restricted-availability-89a99b9.md).

The following attributes of the user will be restored if they were present in the soft-deleted \(blocked\) user:

-   `id` - the SCIM ID of the user
-   name
-   `displayName`
-   `phoneNumbers`
-   `timeZone`
-   `profileUrl`
-   `userName`
-   `nickName`
-   `photos`
-   `active`
-   `title`
-   `roles`
-   `externalId`
-   `preferredLanguage`
-   `locale`
-   `userId` - part of "urn:ietf:params:scim:schemas:extension:sap:2.0:User“ schema
-   `userUuid` - part of "urn:ietf:params:scim:schemas:extension:sap:2.0:User“ schema



## Request

**URI:**<code>https://&lt;Cloud Identity Services domain&gt;/scim/Users</code>

> ### Note:  
> The domain part has the following pattern:
> 
> `<tenant ID>.accounts.ondemand.com` or `<tenant ID>.accounts.cloud.sap`. If you have a configured custom domain, the domain has the following pattern: <your custom domain\>.
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation email with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [View Assigned Tenants and Administrators](../view-assigned-tenants-and-administrators-f56e6f2.md).

**HTTP Method:***POST*



### Authentication

Any authentication supported by the [Identity Directory API](https://api.sap.com/api/IdDS_SCIM/overview) can be used.



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



### Request Parameters


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

Additional Information

</th>
<th valign="top">

Parameter Type

</th>
</tr>
<tr>
<td valign="top">

`userUuid`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

The `userUuid` number of the blocked user.

</td>
<td valign="top">

Body

</td>
</tr>
<tr>
<td valign="top">

all required user attributes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

string

</td>
<td valign="top">

All user attributes that are configured as required in the tenant.

</td>
<td valign="top">

Body

</td>
</tr>
<tr>
<td valign="top">

all user attributes

</td>
<td valign="top">

No

</td>
<td valign="top">

string

</td>
<td valign="top">

> ### Remember:  
> New attributes can be added during restore.
> 
> Attributes can be overridden with new values.



</td>
<td valign="top">

 

</td>
</tr>
</table>



### Request Example

```

POST
https://my-tenant.ondemand.com/scim/Users

{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:User",
    "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
  ],
  "name": {
    "familyName": "Moore",
    "givenName": "Dona"
  },
  "displayName": "Dona Moore",
  "emails": [
    {
      "value": "dona.moore@example.com",
      "primary": true
    }
  ],
  "phoneNumbers": [
    {
      "type": "work",
      "value": "555-555-5555",
      "display": "Phone",
      "primary": true
    }
  ],
  "urn:ietf:params:scim:schemas:extension:sap:2.0:User": {
    "emails": [
      {
        "verified": false,
        "value": "dona.moore@example.com",
        "primary": true
      }
    ],
    "userUuid": "s2691cbb-0sd2-4t23-99ia-d6de50td2ccs"
  }
}


```



## Response

The response returns information about the restored user.



### Response Example

> ### Sample Code:  
> ```
> 
> {
>   "schemas": [
>     "urn:ietf:params:scim:schemas:core:2.0:User",
>     "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
>   ],
>   "id": "s2691cbb-0sd2-4t23-99ia-d6de50td2ccs",
>   "meta": {
>     "created": "2026-03-13T12:23:12Z",
>     "lastModified": "2026-03-13T12:23:12Z",
>     "location": "https://auh3a3doa.accounts400.ondemand.com/scim/Users/c8250cbb-0bb2-4b23-99ae-d6de50fd2cce",
>     "resourceType": "User",
>     "version": "08cd47fa-15b0-464a-b633-581116f802e4"
>   },
>   "userName": "",
>   "name": {
>     "familyName": "Moore",
>     "givenName": "Dona"
>   },
>   "displayName": "Dona Moore",
>   "userType": "public",
>   "active": false,
>   "emails": [
>     {
>       "value": "dona.moore@example.com",
>       "primary": true
>     }
>   ],
>   "phoneNumbers": [
>     {
>       "value": "555-555-5555",
>       "type": "work",
>       "display": "Phone",
>       "primary": true
>     }
>   ],
>   "urn:ietf:params:scim:schemas:extension:sap:2.0:User": {
>     "emails": [
>       {
>         "verified": false,
>         "value": "dona.moore@example.com",
>         "primary": true
>       }
>     ],
>     "userUuid": "c8250cbb-0bb2-4b23-99ae-d6de50fd2cce",
>     "mailVerified": false,
>     "userId": "P123456",
>     "phoneNumbers": [
>       {
>         "display": "Phone",
>         "type": "work",
>         "value": "555-555-5555",
>         "primary": true
>       }
>     ],
>     "status": "inactive"
>   }
> }
> ```

> ### Remember:  
> The user is restored \(created\) by default with status inactive.



### Response Codes

[Identity Directory API Reference](https://api.sap.com/api/IdDS_SCIM/path/getUsers)

**Related Information**  


[Enable Soft Delete for Users in Administration Console \(Restricted Availability\)](enable-soft-delete-for-users-in-administration-console-restricted-availability-25a6175.md "Enable soft deletion (blocking) of users in SAP Cloud Identity Services.")

[Read Single Soft-Deleted User \(Restricted Availability\)](read-single-soft-deleted-user-restricted-availability-5adef17.md "Read the soft-deleted (blocked) but not permanently deleted user.")

[Read All Soft-Deleted Users \(Restricted Availability\)](read-all-soft-deleted-users-restricted-availability-89a99b9.md "Get a list of all soft-deleted (blocked) but not deleted users in the tenant of SAP Cloud Identity Services.")

[Permanently Delete User \(Restricted Availability\)](permanently-delete-user-restricted-availability-230fc2e.md "Permanently delete the soft-deleted (blocked) but not yet deleted from the system user whose SCIM ID is stated in the request.")

[Edit Administrator Authorizations \(Restricted Availability\)](edit-administrator-authorizations-restricted-availability-297b3b2.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

