<!-- loiof54b9002538b4c95855fc5be35e2a23e -->

# Import CSV File with Full User Profile

As a tenant administrator, you can create new users or update existing ones with all user data, including attributes from a custom schema, via a CSV file upload.



## Prerequisites

-   You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).




## Context

With the CSV file, you can import up to 25000 users to create new users or to update existing users.

> ### Remember:  
> The `SCIM ID` serves as the primary identifier if it is found in the CSV file. The users will only be updated, but not created if there are users with a new `SCIM ID`. This process works within the same tenant because the SCIM IDs differ across tenants.
> 
> If the`SCIM ID` doesn't exist in the CSV file, the create and update functionality will function as expected, but the administrator won't be able to modify the `username` or `email`.

The attributes can take one of the following types:


<table>
<tr>
<th valign="top">

Attribute Type

</th>
<th valign="top">

Column Name \(Example\)

</th>
<th valign="top">

Value \(Example\)

</th>
</tr>
<tr>
<td valign="top">

`multivalued complex`

</td>
<td valign="top">

emails\[0\].value

</td>
<td valign="top">

michael.adams@example.com

</td>
</tr>
<tr>
<td valign="top">

`complex`

</td>
<td valign="top">

name.familyName

</td>
<td valign="top">

Adams

</td>
</tr>
<tr>
<td valign="top">

`single value`

</td>
<td valign="top">

displayName

</td>
<td valign="top">

Michael Adams

</td>
</tr>
<tr>
<td valign="top">

`multivalue`

</td>
<td valign="top">

urn:sap:cloud:scim:schemas:extension:custom:2.0:CustomSchema:arrayOfStringsAttr

</td>
<td valign="top">

test1;test2

</td>
</tr>
</table>

The following attributes must be a valid master data text:

****


<table>
<tr>
<th valign="top">

Attribute

</th>
<th valign="top">

Where to find it

</th>
</tr>
<tr>
<td valign="top">

`locale`

</td>
<td valign="top">

-   administration console - *Master Data Texts tile* \> *Language tab*
-   API - GET `https://<tenant ID>.accounts.ondemand.com/service/resource?resourceType=RESOURCE_MD_LANGUAGES&locale=en`



</td>
</tr>
<tr>
<td valign="top">

`timeZone`

</td>
<td valign="top">

API - GET `https://<tenant ID>.accounts.ondemand.com/service/resource?resourceType=RESOURCE_MD_TIMEZONES&locale=en`

</td>
</tr>
<tr>
<td valign="top">

`addresses[0].country`

</td>
<td valign="top">

-   administration console - *Master Data Texts tile* \> *Countries tab*
-   API - GET `https://<tenant ID>.accounts.ondemand.com/service/resource?resourceType=RESOURCE_MD_COUNTRIES&locale=en`



</td>
</tr>
<tr>
<td valign="top">

`addresses[0].region`

</td>
<td valign="top">

API - GET `https://<tenant ID>.accounts.ondemand.com/service/resource?resourceType=RESOURCE_MD_STATES&locale=en`

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department`

</td>
<td valign="top">

-   administration console - *Master Data Texts tile* \> *Departments tab*
-   API - GET `https://<tenant ID>.accounts.ondemand.com/service/resource?resourceType=RESOURCE_MD_DEPARTMENTS&locale=en`



</td>
</tr>
<tr>
<td valign="top">

`name.honorificPrefix`

</td>
<td valign="top">

-   administration console - *Master Data Texts tile* \> *Salutations tab*
-   API - GET `https://<tenant ID>.accounts.ondemand.com/service/resource?resourceType=RESOURCE_MD_SALUTATIONS&locale=en`



</td>
</tr>
</table>

> ### Remember:  
> The CSV file must contain at least the following three columns:
> 
> -   `userName` or `loginName`
> -   `emails[0].value` or `mail`
> -   `name.familyName` or `lastName`

> ### Remember:  
> If there is a column with the name of a certain attribute, and you provide a value for that column, the attribute will be updated.
> 
> If there is a column with the name of a certain attribute, and you don't provide a value for that column, the attribute will be deleted.
> 
> If there is no column with the name of a certain attribute, the value of the attribute remains unchanged.
> 
> If the names of the columns are not from the core schema, they must be written with the `urn:attribute name`.

> ### Tip:  
> To update the `emails` or `userName` attribute you must provide the `SCIM ID` for the users that you want to update.

> ### Note:  
> The user import doesn’t assign any special rights or roles to the created or updated users for the specific application.

The CSV file can contain only columns with no spaces between them, with all the attributes whose names are compliant with SCIM specification, plus the attributes from a custom schema that exist in the tenant of Identity Authentication. If you include columns with other attributes, their values in the table are ignored.

If you enter the data in the CSV file as text, you must separate the entries with commas. Beware not to put any spaces before or after the comas. If you enter more than one value in a single entry, separate the values within the entry with semicolons.

Values shouldn't contain semicolons. If there is a semicolon, in the import the value will be split by that semicolon and more than one attribute value will be added.

Depending on your *Logon Alias* configuration in the administration console, you must consider the following:

-   If *Email* is required and unique, in the csv file at least one `emails[0].value` must be present and unique.
-   If *Login Name* is required and unique, in the csv file at least one `userName` must be present and unique.
-   If *Display Name* is required and unique, in the csv file at least one `displayName` must be present unique.

> ### Restriction:  
> The user import doesn’t support the `groups` and `spCustomAttribute1`

You can view all of the supported schemas attributes and their definitions in the administration console of Identity Authentication under schemas. For more information, see[Manage Custom Schemas via Administration Console](manage-custom-schemas-via-administration-console-d492d70.md).

> ### Example:  
> > ### Sample Code:  
> > ```
> > emails[0].value,emails[0].primary,emails[0].type,name.familyName,name.givenName,name.middleName,name.formatted,name.honorificPrefix,name.honorificSuffix,userName,displayName,nickName,profileUrl,title,userType,active,addresses[0].type,addresses[0].streetAddress,addresses[0].locality,addresses[0].region,addresses[0].postalCode,addresses[0].country,addresses[0].formatted,addresses[0].primary,addresses[1].type,addresses[1].streetAddress,addresses[1].locality,addresses[1].region,addresses[1].postalCode,addresses[1].country,addresses[1].formatted,phoneNumbers[0].value,phoneNumbers[0].type,phoneNumbers[1].value,phoneNumbers[1].type,ims[0].value,ims[0].type,ims[1].value,ims[1].type,photos[0].value,photos[0].type,photos[1].value,photos[1].type,urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division,urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department,urn:ietf:params:scim:schemas:extension:sap:2.0:User:mailVerified,urn:ietf:params:scim:schemas:extension:sap:2.0:User:validFrom,urn:ietf:params:scim:schemas:extension:sap:2.0:User:validTo,urn:sap:cloud:scim:schemas:extension:custom:2.0:User:attributes[0].name,urn:sap:cloud:scim:schemas:extension:custom:2.0:User:attributes[0].value
> > dona.moore@example.com,TRUE,work,Moore,Dona,Moore,Dona Moore Moore,Ms.,III,donaM,Dona Moore Moore,random,https://test.com,Dr,public,TRUE,work,100 Universal City Plaza,Hollywood,CA,91608,US,100 Universal City Plaza Hollywood CA 91608 US,true,home,456 Hollywood Blvd,Hollywood,CA,91608,US,456 Hollywood Blvd Hollywood CA 91608 US,555-555-5555,work,555-555-4444,mobile,someaimhandle,aim,someaimhandle2,aim,https://photos.example.com/profilephoto/72930000000Ccne/F,photo,https://photos.example.com/profilephoto/72930000000Ccne/T,thumbnail,Theme Park,Real Estate Management,true,2021-10-04T06:48:20Z,2023-10-04T06:48:20Z,customAttribute1,test
> > ```

To import users for an application into Identity Authentication, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  Press the *Import* button.

4.  Choose the *Browse...* button and specify the location of the CSV file.

    > ### Note:  
    > Use a UTF-8 encoded file with up to 25000 users and an extension `.csv`. If your file contains more than 25000 users, you have to import the user information in iterations within the user number limit.

5.  Choose the *Save* button.

    If the operation is successful, the system displays a message with the number of imported and updated users.


**Related Information**  


[SCIM Common Attributes](https://datatracker.ietf.org/doc/html/rfc7643#section-3.1)

