<!-- loio2f215687fcf34170b0bbc8b36b60f2e9 -->

# SCIM REST API \(Deprecated\)

This section contains information about the Identity Authentication implementation of the System for Cross-domain Identity Management \(SCIM\) REST API protocol.



> ### Note:  
> This API will be deprecated. Please use [Identity Directory SCIM REST API](https://api.sap.com/api/IdDS_SCIM/overview) instead.



## Prerequisites

To call the methods of this SCIM REST API you must have a system as administrator with an assigned *Manage Users* role. For more details about how to add a system as administrator and assign administrator roles, see [Add System as Administrator](../Operation-Guide/add-administrators-bbbdbdd.md#loiocefb742a36754b18bbe5c3503ac6d87c), and [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).



<a name="loio2f215687fcf34170b0bbc8b36b60f2e9__additional_supported_values"/>

## Additional Attributes Supported Values

Some of the attributes have predefined supported values. They are returned as a map of key value pairs. See some examples in the table below. For the full set of attributes, copy the URL from the table, replace `<tenant ID>` with your *Tenant ID*, and open the edited URL in a web browser.

> ### Note:  
> The URL has the following pattern:
> 
> `https://<tenant ID>.accounts.ondemand.com/admin`
> 
> *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
> 
> If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.


<table>
<tr>
<th valign="top">

Attribute



</th>
<th valign="top">

Examples



</th>
<th valign="top">

Full Sets



</th>
</tr>
<tr>
<td valign="top">

 `name.honorificPrefix` 



</td>
<td valign="top">

-   \[Mr., Ms.\]




</td>
<td valign="top">

-   **`https://<tenant ID>.accounts.ondemand.com/md/salutations`**




</td>
</tr>
<tr>
<td valign="top">

 `addresses.country` 



</td>
<td valign="top">

-   \[AF, AX\]




</td>
<td valign="top">

-   **`https://<tenant ID>.accounts.ondemand.com/md/countries`**




</td>
</tr>
<tr>
<td valign="top">

 `addresses.region` 



</td>
<td valign="top">

-   \[NY\]

-   \[AB\]




</td>
<td valign="top">

-   **`https://<tenant ID>.accounts.ondemand.com/md/states/us`**

-   **`https://<tenant ID>.accounts.ondemand.com/md/states/ca`**




</td>
</tr>
<tr>
<td valign="top">

 `industryCrm` 



</td>
<td valign="top">

-   \[Aerospace and Defense\]




</td>
<td valign="top">

-   **`https://<tenant ID>.accounts.ondemand.com/md/industries`**




</td>
</tr>
<tr>
<td valign="top">

 `timeZone` 



</td>
<td valign="top">

-   \[Africa/Abidjan\]




</td>
<td valign="top">

-   **`https://<tenant ID>.accounts.ondemand.com/md/timezones`**




</td>
</tr>
<tr>
<td valign="top">

 `department` 



</td>
<td valign="top">

-   \[Administration\]




</td>
<td valign="top">

-   **`https://<tenant ID>.accounts.ondemand.com/md/departments`**




</td>
</tr>
<tr>
<td valign="top">

 `companyRelationship` 



</td>
<td valign="top">

-   \[Consultant\]




</td>
<td valign="top">

-   **`https://<tenant ID>.accounts.ondemand.com/md/relationships`**




</td>
</tr>
<tr>
<td valign="top">

 `locale` 



</td>
<td valign="top">

-   \[EN\]




</td>
<td valign="top">

-   **`https://<tenant ID>.accounts.ondemand.com/md/languages`**




</td>
</tr>
</table>



<a name="loio2f215687fcf34170b0bbc8b36b60f2e9__section_m2y_xz5_xcb"/>

## Restricted Characters

The characters `<`, `>`, `:` are not allowed for the attributes `displayName`, `name.familyName`, and `name.givenName`.



<a name="loio2f215687fcf34170b0bbc8b36b60f2e9__section_mh4_lh2_nbb"/>

## Methods

 

**Manage Users**


<table>
<tr>
<th valign="top">

HTTP Method



</th>
<th valign="top">

Action



</th>
<th valign="top">

URI



</th>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

[Users Search \(Deprecated\)](users-search-deprecated-3af7dfa.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Users/`**



</td>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

[User Resource \(Deprecated\)](user-resource-deprecated-7ae17a6.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Users/<id>`**



</td>
</tr>
<tr>
<td valign="top">

*POST*



</td>
<td valign="top">

[Create User Resource \(Deprecated\)](create-user-resource-deprecated-cea8778.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Users`**



</td>
</tr>
<tr>
<td valign="top">

*PUT*



</td>
<td valign="top">

[Update User Resource \(Deprecated\)](update-user-resource-deprecated-9e36479.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Users/<id>`**



</td>
</tr>
<tr>
<td valign="top">

*DELETE*



</td>
<td valign="top">

[Delete User Resource \(Deprecated\)](delete-user-resource-deprecated-436015d.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Users/<id>`**



</td>
</tr>
</table>

**Manage Groups**


<table>
<tr>
<th valign="top">

HTTP Method



</th>
<th valign="top">

Action



</th>
<th valign="top">

URI



</th>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

[Groups Search \(Deprecated\)](groups-search-deprecated-77e6811.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/`**



</td>
</tr>
<tr>
<td valign="top">

*GET*



</td>
<td valign="top">

[Group Resource \(Deprecated\)](group-resource-deprecated-8c6ebd7.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/<id of the group>`**



</td>
</tr>
<tr>
<td valign="top">

*POST*



</td>
<td valign="top">

[Create Group Resource \(Deprecated\)](create-group-resource-deprecated-a831c94.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Groups`**



</td>
</tr>
<tr>
<td valign="top">

*PUT*



</td>
<td valign="top">

[Update Group Resource \(Deprecated\)](update-group-resource-deprecated-81ca50e.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/<id of the group>`**



</td>
</tr>
<tr>
<td valign="top">

*DELETE*



</td>
<td valign="top">

[Delete Group Resource \(Deprecated\)](delete-group-resource-deprecated-41bb519.md)



</td>
<td valign="top">

**`https://<tenant ID>.accounts.ondemand.com/service/scim/Groups/<id of the group>`**



</td>
</tr>
</table>

**Related Information**  


[System for Cross-Domain Identity Management](https://tools.ietf.org/html/draft-ietf-scim-api-19)

[SCIM Data Types](https://tools.ietf.org/html/rfc7643#section-2.3)

