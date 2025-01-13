<!-- loio0cdac7ce593548d38b5a78dbf1bb444c -->

# Transformation Functions

A function is a hardcoded piece of transformation logic that receives a value denoted by the input specified by a source path or a source variable. As a result, the value is replicated into the target path or target variable, accordingly.

The Identity Provisioning service uses two types of functions: [*conditional*](transformation-functions-0cdac7c.md#loio0cdac7ce593548d38b5a78dbf1bb444c__section_ct1_v4z_czb) and [*mapping*](transformation-functions-0cdac7c.md#loio0cdac7ce593548d38b5a78dbf1bb444c__section_kvn_r4z_czb) functions. The conditional functions are functions which can be used only in conditional statements. The mappting functions are used in entity transformations and are included as mappings.

Functions can also be chained – that means, the output of one function is the input for the next one. See an example with such functions in the **encode / decode** section below.

For more information, see the tables below.



<a name="loio0cdac7ce593548d38b5a78dbf1bb444c__section_ct1_v4z_czb"/>

## Conditional Functions

****


<table>
<tr>
<th valign="top">

Function

</th>
<th valign="top">

Parameters

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

isValidEmail

</td>
<td valign="top">

-   JSON path attribute which holds the email value

    Required: Yes

    Type: String

-   Possible values:

    -   `$.emails[0].value`
    -   `$.emails[*].value`




</td>
<td valign="top">

This function verifies whether an e-mail address is valid by checking if the given String value matches the following regex pattern:

```
"[a-zA-Z0-9!#$%&‘*+/=?^_`{|}~-]+(?>\\.[a-zA-Z0-9!#$%&‘*+/=?^_`{|}~-]+)*@(?>[a-zA-Z0-9][a-zA-Z0-9-]*[a-zA-Z0-9]?\\.)+[a-zA-Z0-9](?>[a-zA-Z0-9-]*[a-zA-Z0-9])?"
```

After the check, the function returns a Boolean result.

This function can be used only as part of a conditional statement.

EXAMPLE 1:

In this example, the source JSON code contains the following e-mail address of a user:

```
{
	"userName": "test",
	"emails": [
		{
			"value": "example@company.com",
			"primary": true
		}
	]
}
```

The condition with function *isValidEmail* is the following:

```
{
  "condition": "isValidEmail($.emails[0].value)",
  "mappings": [
      {
          "sourcePath": "$.userName",
          "targetPath": "$.userName"
      },
      {
          "sourcePath": "$.emails[*].value",
          "preserveArrayWithSingleElement": true,
          "targetPath": "$.emails[?(@.value)]"
      }
   ]
}
```

EXAMPLE 2:

In cases where users have multiple emails, the following condition will validate each email in the emails array:

```
{
  "condition": "isValidEmail($.emails[*].value)",
  "mappings": [
      {
......          
```



</td>
</tr>
</table>



<a name="loio0cdac7ce593548d38b5a78dbf1bb444c__section_kvn_r4z_czb"/>

## Mapping Functions

****


<table>
<tr>
<th valign="top">

Function

</th>
<th valign="top">

Parameters

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

concatString

</td>
<td valign="top">

-   **`prefix`**

    Required: No

    Type: String

-   **`suffix`**

    Required: No

    Type: Integer; String; Boolean

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function concatenates a string with a prefix or a suffix.

EXAMPLE 1:

In the following transformation example, function *concatString* will be applied to all source logon names \(SAM-account user names\) read from *Microsoft AD*, adhering a prefix **\_ips** and a suffix **123** in the target system. For example, a *sAMAccountName* name **johnsmith** from the source system will be provisioned as **ips\_johnsmith123** in the target system.

> ### Example:  
> ```
> 
> {
> 	"user": {
> 	  "mappings": [
> 		{
> 		  "sourcePath": "$.sAMAccountName[0]",
> 		  "targetPath": "$.userName",
> 		  "functions": [
> 			{
> 			  "function": "concatString",
> 			  "prefix": "ips_",
> 			  "suffix": 123 
> 			}
> 		   ]
> 		}
> 	...
>   	
> }
> ```

EXAMPLE 2:

In the following transformation example, function *concatString* will be applied to all source user IDs in a source system, converting them into uniform e-mails in the *Microsoft Entra ID* target system. In this case, the *concatString* function takes the value of the *aad.domain.name* property \(which is the name of a verified Microsoft Entra ID domain\) and adheres it to the *userId*. For example, a source user ID **johnsmith123** can produce a target principal name **johnsmith123@mail.acme.com**.

> ### Example:  
> ```
> 
> 	{
> 		"sourcePath": "$.userId",
> 		"targetPath": "$.emails[0].value", 
> 		"correlationAttribute": true, 
> 		"functions": [
> 			{
> 				"function": "concatString",
> 				"suffix": "@%aad.domain.name%"
> 			}
> 		]
> 	},
> ...
> ```



</td>
</tr>
<tr>
<td valign="top">

convertCountryCode

</td>
<td valign="top">

-   **`outputFormat`**

    Required: Yes

    Possible values:

    -   `fullName`
    -   `alpha2`
    -   `alpha3`
    -   `numeric`

-   **`inputAttributes`**

    Required: Yes

    Possible values: Single value or list of address attributes which will be used. The function requires attribute `country`.

-   **`outputAttribute`**

    Required: Yes

    Possible values: `country`

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function converts the countries into format compliant with *ISO 3166-1*.

```
{
    "sourcePath": "$.addresses",
    "preserveArrayWithSingleElement": true,
    "optional": true,
    "targetPath": "$.addresses",
    "functions": [
      {
        "type": "convertCountryCode",
        "outputFormat": "alpha2",
        "inputAttributes": ["country"],
        "outputAttribute": "country"
      }
    ]
}

```

EXAMPLE:

In the following transformation example, function *convertCountryCode* will be applied to all source countries read from the source system, converting them in the wanted ISO format. For example, the `country` name *United States* from the source system will be provisioned in the target system as:

-   *US* if the `outputFormat` is *alpha2*;

-   *USA* if the `outputFormat` is *alpha3*;

-   *840* if the `outputFormat` is *numeric*;

-   *United States* if the `outputFormat` is *fullName*.




</td>
</tr>
<tr>
<td valign="top">

convertCountryRegion

</td>
<td valign="top">

-   **`outputFormat`**

    Required: Yes

    Possible values:

    -   `fullName`
    -   `alpha2`

-   **`inputAttributes`**

    Required: Yes

    Possible values:

    -   `country`
    -   `region`

-   **`outputAttribute`**

    Required: Yes

    Possible values: `region`

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function converts the countries into format compliant with *ISO 3166-2*.

```
{
    "condition": "($.addresses[*].region EMPTY false) && ($.addresses[*].country EMPTY false)",
    "sourcePath": "$.addresses",
    "preserveArrayWithSingleElement": true,
    "optional": true,
    "targetPath": "$.addresses",
    "functions": [
        {
            "type": "convertCountryRegion",
            "outputFormat": "alpha2",
            "inputAttributes": ["region","country"],
            "outputAttribute": "region"
        }
    ]
}

```

EXAMPLE:

In the following transformation example, function *convertCountryRegion* will be applied to all source regions read from the source system, converting them in the wanted ISO format. For example, the `region` name *US-AL* or only *AL* from the source system will be provisioned to the target system as:

-   *US-AL* if the `outputFormat` is *alpha2*;

-   *Alabama* if the `outputFormat` is *fullName*.




</td>
</tr>
<tr>
<td valign="top">

compositeId

</td>
<td valign="top">

-   **`separator`**

    Required: Yes

    Possible values: : \(colon\)

-   **`subId`**

    Required: Yes

    Type: String; JSONPath expression

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function appends the value referred by the source path to the value of the `subId` parameter, separated by ":".

> ### Example:  
> Input JSON code before transformation:
> 
> ```
> 
> {
> 	"qualifierId": "johnsmith"
> }
> ```

> ### Example:  
> Transformation using the function:
> 
> ```
> 
> {
>   "sourcePath": "$.qualifierId",
>   "targetPath": "$['composite_id.custom_separator.colon']",
>   "functions": [
>     {
>       "function": "compositeId",
>       "separator": ":",
>       "subId": "e0123456"
>     }
>   ]
> },
> ...
> 
> ```

> ### Example:  
> After the function execution, the output JSON results to:
> 
> ```
> 
> {
> 	"composite_id.default_separator": "johnsmith:e0123456",
> 	"composite_id.custom_separator.colon": "johnsmith:e0123456",
> 	"composite_id.custom_separator.dash": "johnsmith-e0123456"
> }
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

copyMapEntry

</td>
<td valign="top">

-   **`sourceKey`**

    Required: Yes

    Type: String

-   **`targetKey`**

    Required: Yes

    Type: String




</td>
<td valign="top">

This function copies a key-value pair from the source JSON and creates a similar one in the target JSON. The nelwy created pair consists of the specified `targetKey` String and the value copied from the initial pair. The two key-value pairs are written into the target system.

EXAMPLE:

For example, if the source entity contains the following roles:

```
{ "role": [{"roleName": "ROLE1"},{"roleName": "ROLE2"}] }
```

After applying the function:

```
{      
  "sourcePath": "$.user.role",
  "optional": true,
  "targetPath": "$.groups",
  "preserveArrayWithSingleElement": true,
  "functions": [
   {
    "function": "copyMapEntry",
    "sourceKey": "roleName",
    "targetKey": "value"
   }
  ]
}
```

Two pairs with `targetKey` `"value"` are added to the target JSON and the result is:

```
{ "groups":[{"roleName": "ROLE1", "value":"ROLE1"},{"roleName": "ROLE2", "value":"ROLE2"}] }
```



</td>
</tr>
<tr>
<td valign="top">

decode

</td>
<td valign="top">

-   **`algorithm`**

    Required: Yes

    Possible values:

    -   base32
    -   base64

-   **`skipPadding`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

    Default value: false

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

The function **decode** is part of the Write transformation of some proxy systems \(like AS ABAP\).It decodes the string value specified by the sourcePath or sourceVariable mapping attribute, by using specified decoding algorithm.

**Function result**: Byte array

EXAMPLE:

For example, if the input JSON code contains the following user name:

```

{
   "USERNAME": "JOHN*SMITH/Junior"
}

```

The base32 encoded result will be the following id:

> ### Example:  

```

{
   "id": "JJHUQTRKKNGUSVCIF5FHK3TJN5ZA===="
}

```

The *decode* function reads the **id** and converts it into a byte array. Afterward, the *toString* function reads this byte array and converts it into the original **USERNAME** string. The base32 padding symbols \(`==`\) are skipped.

> ### Example:  
> ```
> 
> // Write Transformation
> {
>     "user": {
>         "mappings": [
>             {
>                 "sourcePath": "$.id",
>                 "targetPath": "$.USERNAME",
>                 "functions": [
>                     {
>                         "function": "decode",
>                         "algorithm": "base32",
>                         "skipPadding": true
>                     },
>                     {
>                         "function": "toString"
>                     }
>                 ]
>             },
> ...
> ```



</td>
</tr>
<tr>
<td valign="top">

elementAt

</td>
<td valign="top">

-   **`index`**

    Required: Yes

    Type: Integer




</td>
<td valign="top">

This function is used to retrieve a specific element from an array based on its index. The index indicates the element you want to access.

Using the **elementAt** function with index 0 in this example results in requesting the first email within an array of primary emails. After evaluating the sourcePath, it returns all primary emails. Applying the **elementAt** function with index 0 then retrieves the first primary email from this array.

> ### Code Syntax:  
> ```
> {
>    "condition":"$.emails[?(@.primary == true)].value != []",
>    "sourcePath":"$.emails[?(@.primary == true)].value",
>    "preserveArrayWithSingleElement":true,
>    "optional":true,
>    "targetPath":"$.email",
>    "functions":[
>       {
>          "function":"elementAt",
>          "index":0
>       }
>    ]
> },
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

encode

</td>
<td valign="top">

-   **`algorithm`**

    Required: Yes

    Possible values:

    -   base32
    -   base64

-   **`skipPadding`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

    Default value: false

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

The function **encode** is part of the Read transformation of some proxy systems \(like AS ABAP\). It encodes the value specified by the sourcePath or sourceVariable mapping attribute, by using specified encoding algorithm.

The function can accept a Byte array or everything that has a string representation. The string is assumed in UTF-8 character encoding.

**Function result**: String

EXAMPLE:

For example, if the input JSON code contains the following user name:

```

{
   "USERNAME": "JOHN*SMITH/Junior"
}

```

The base32 encoded result will be the following id:

> ### Example:  

```

{
   "id": "JJHUQTRKKNGUSVCIF5FHK3TJN5ZA===="
}

```

The *encode* function reads the **USERNAME** string and writes the encoded value into the **id** path. The base32 padding symbols \(`==`\) are skipped.

> ### Example:  
> ```
> 
> // Read Transformation
> {
>     "user": {
>         "mappings": [
>             {
>                 "sourcePath": "$.USERNAME",
>                 "targetPath": "$.id",
>                 "targetVariable": "entityIdSourceSystem",
>                 "functions": [
>                     {
>                         "function": "encode",
>                         "algorithm": "base32",
>                         "skipPadding": true
>                     }
>                 ]
>             },
> ...
> 
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

getMatchedRegexGroup

</td>
<td valign="top">

-   **`regex`**

    Required: Yes

    Type: String

-   **`groupIndex`**

    Required: Yes

    Type: Integer

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function checks whether a given string matches the provided regular expression \(regex\), and returns the required group.

For example, when the value of groupIndex is:

-   *0* – the function returns the entire string
-   Positive number – the function returns a specific group from the string. For instance, `groupIndex` = *3* will return the third group.

> ### Example:  
> Initial user data:
> 
> ```
> 
> {
> 	"distinguishedName": [
> 	   "CN=test10,OU=subUsers,OU=testUsers"
> 	]
> }
> ```

> ### Example:  
> Transformation in the source system:
> 
> ```
> 
> {
> 	"group": {
> 	   "mappings": [
>           {
> 		...
> 	     "sourcePath": "$.distinguishedName[0]",
> 	     "functions": [
> 	   	{
> 	   	   "function": "getMatchedRegexGroup",
> 	   	   "regex": "(?i)cn=.*?,(.*?),OU=testUsers",
> 	   	   "groupIndex": 1
> 	   	}
> 	      ],
> 	    "targetPath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:User']['nestedPath']"
> 	 }
>    ]
> }
> ```

> ### Example:  
> Nested path extracted from the user DN, after the transformation:
> 
> ```
> 
> {
> 	"urn:sap:cloud:scim:schemas:extension:ad:2.0:User": {
> 	   "nestedPath": "OU=subUsers"
> 	}
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

manipulateDate

</td>
<td valign="top">

-   **`sourceDateFormat`**

    Required: No

    Type: Date; Time

-   **`targetDateFormat`**

    Required: No

    Type: Date; Time

-   **`years`**

    Required: No

    Type: Integer

-   **`months`**

    Required: No

    Type: Integer

-   **`days`**

    Required: No

    Type: Integer

-   **`hours`**

    Required: No

    Type: Integer

-   **`minutes`**

    Required: No

    Type: Integer

-   **`seconds`**

    Required: No

    Type: Integer

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function converts one date format into another after JSONPath transformations.

Use cases:

-   A Java date format can be converted into another Java date format.

    Example: "**2018–02–28 11:00:00.000**" to "**02/28/2018**"

-   A date format based on *Unix Time Stamp* can be converted into a Java one. That means, if the source system stores a date as a number of milliseconds, after the transformations this number will be converted and written in the target system as a human readable date.

    Example: "**Date\(1519809649123–0240\)**" to "**2018–02–28 UTC+1**"

    > ### Note:  
    > Bear in mind the following restrictions about *Unix Time Stamp* format:
    > 
    > -   It is mainly applicable for SAP SuccessFactors connectors.
    > -   If the source date format contains a timezone \(GMT, EST, ACT, etc.\), after converting from *Unix Time Stamp*, the date will be displayed as a UTC offset.
    > -   During calculation, the timezone is ignored – the milliseconds are converted to a "pure" date. The timezone is displayed \(as UTC offset\) but not taken into account.


The *manipulateDate* function supports the following operations:

-   \(**Java**\) Incrementing the date by the "**\+**" sign or when there is no sign
-   \(**Java**\) Decrementing the date by the "**–**" sign
-   \(**Unix Time Stamp**\) Converting a number of milliseconds into a human readable date

> ### Note:  
> The parameters `sourceDateFormat` and `targetDateFormat` accept values in short or full date & time format. For example: *yyyy-MM-dd'T'HH:mm:ss'Z'*.

> ### Example:  
> **Reads and writes the current date in standard *Java* date format**
> 
> ```
> 
> {
> 	"targetPath": "$.EmployeeType.ValidityPeriod.StartDate",
> 	"sourceVariable": "currentDate",
> 	"functions": [
> 		{
> 			"function": "manipulateDate",
> 			"targetDateFormat" : "MM/dd/yyyy",
> 			"sourceDateFormat" : "yyyy-MM-dd HH:mm:ss.SSS",
> 			"years":
> 			"months":
> 
>  // You can also, for example, increment the date with 3 days and 2 hours
> 			"days": "3"
> 			"hours": "+2" 
> 			"minutes": 
> 			"seconds": 
> 		}
> 	...
> }
> ```

> ### Example:  
> **Reads a given date in *Unix Time Stamp* format \(in milliseconds\) and writes the converted value in the target system as a standard *Java* date format**
> 
> ```
> 
> {
> 	"targetPath": "$.EmployeeType.ValidityPeriod.StartDate",
> 	"sourcePath": "$date",
> 	"functions": [
> 		{
> 			"function": "manipulateDate",                 
> 			"sourceDateFormat": "Date(milliseconds)",
> 			"targetDateFormat": "yyyy-MM-dd HH:mm:ss.SSS"		
> 		}
> 	...
> }
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

matchRegex

</td>
<td valign="top">

-   **`regex`**

    Required: Yes

    Type: String

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function checks whether a given string matches the provided regular expression and returns a Boolean result.

> ### Example:  
> **Checks whether the value of attribute "COMPOSITE\_PRIVILEGE" matches the regular expression "\*\_COMP", and assigns the result \(*true* or *false*\) to attribute "composite".**
> 
> ```
> 
> {
>     "mappings": [
>         {
>             "sourcePath": "$.PRIVILEGES",
>             "targetPath": "$.groups",
>             "functions": [
>                 {
>                     "function": "matchRegex",
>                     "regex": ".*_COMP",
>                     "applyOnAttribute": "COMPOSITE_PRIVILEGE",
>                     "assignToAttribute": "composite"
>                 }
>             ]
>         }
>     ]
> }
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

putIfAbsent

</td>
<td valign="top">

-   **`key`**

    Required: Yes

    Type: String

-   **`defaultValue`**

    Required: Yes

    Type: String; Array; Integer; another value type

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function works on user attributes of type array \(list of elements\), as each element consists of key-value pairs. If an element key misses a value, the putIfAbsent function will set a default value for this key.

> ### Example:  
> This function is part of the default **Identity Authentication** target and proxy write transformation. In this case, the user attribute "**addresses**" is a list of addresses. The **putIfAbsent** function is applied on every single address \(element\) of this list.
> 
> ```
> 
> ...
>  	{
>         "sourcePath": "$.addresses",
>         "targetPath": "$.addresses",
>         "preserveArrayWithSingleElement": true,
>         "defaultValue": [],
>         "optional": true,
>         "functions": [
>           {
>             "function": "putIfAbsent",
>             "key": "type",
>             "defaultValue": "work"
>           }
>         ]
> 	 },
> ...
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

putIfPresent

</td>
<td valign="top">

-   **`key`**

    Required: Yes

    Type: String

-   **`defaultValue`**

    Required: Yes

    Type: String; Array; Integer; another value type

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function works on user attributes of type **array** \(list of elements\), as each element consists of *key-value* pairs.

-   If an element key has a value but it's different than the default one, the **putIfPresent** function will set a default value for this key.
-   If an element has a value and it's equal to the default one, the **putIfPresent** function keeps this value as is.

> ### Example:  
> This function is part of the default **Identity Authentication** target and proxy write transformation. In this case, the user attribute "**addresses**" is a list of addresses. The **putIfPresent** function is applied on every single address \(element\) of this list.
> 
> ```
> 
> ...
>  	{
>         "sourcePath": "$.addresses",
>         "targetPath": "$.addresses",
>         "preserveArrayWithSingleElement": true,
>         "defaultValue": [],
>         "optional": true,
>         "functions": [
>           {
>             "condition": "(@.type NIN ['work', 'home'])",
>             "function": "putIfPresent",
>             "key": "type",
>             "defaultValue": "work"
>           }
>         ]
> 	 },
> ...
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

randomPassword

</td>
<td valign="top">

-   **`passwordLength`**

    Required: Yes

    Type: Integer

-   **`minimumNumberOfLowercaseLetters`**

    Required: Yes

    Type: Integer

-   **`minimumNumberOfUppercaseLetters`**

    Required: Yes

    Type: Integer

-   **`minimumNumberOfDigits`**

    Required: Yes

    Type: Integer

-   **`minimumNumberOfSpecialSymbols`**

    Required: Yes

    Type: Integer

-   **`specialSymbols`**

    Required: No

    Possible values: List of allowed special symbols \(no comma separation\)

    Default value: ~!@\#$%^&\*\(\)\_+

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function generates a random password. It picks characters from four character sets - digits, lowercase letters, uppercase letters, and special symbols.

Bear in mind the following tips:

-   The password length must be supplied along with the number of characters from each set. If a value “**0**” is supplied for a given parameter, no characters will be picked from the corresponding character set.
-   If the summed up number of characters \(from all sets\) exceeds the total password length, the function execution will result in error.
-   If the summed up number of characters \(from all sets\) is less than the total password length, the remaining characters will be randomly picked from all character sets.
-   A custom character set is supplied by the `specialSymbols` parameter.
-   If a custom set of special symbols is supplied, the parameter `minimumNumberOfSpecialSymbols` cannot have a value of “**0**”.

> ### Note:  
> The **randomPassword** function does not require `sourcePath`, `sourceVariable`, or `constant` to be specified in the mapping.

> ### Example:  
> ```
> 
> {
> 	"user": {
> 	   "mappings": [
> 		{
> 		   "targetPath": "$.password",
> 		   "functions": [
> 			{
> 			   "function": "randomPassword",
> 			   "passwordLength": 16,
> 			   "minimumNumberOfLowercaseLetters": 4,
> 			   "minimumNumberOfUppercaseLetters": 4,
> 			   "minimumNumberOfDigits": 4,
> 			   "minimumNumberOfSpecialSymbols": 4,
> 			   "specialSymbols": ",.<>/?~`!@#"
> 		}
> 	...
> }
> 
> ```



</td>
</tr>
<tr>
<td valign="top">

renameMapEntry

</td>
<td valign="top">

-   **`sourceKey`**

    Required: Yes

    Type: String

-   **`targetKey`**

    Required: Yes

    Type: String




</td>
<td valign="top">

This function reads the `sourceKey` String from the source JSON and renames it with the given `targetKey` String in the target JSON.

EXAMPLE:

For example, if the source entity contains the following roles:

```
{ "role": [{"roleName": "ROLE1"},{"roleName": "ROLE2"}] }
```

After applying the function:

```
{      
  "sourcePath": "$.user.role",
  "optional": true,
  "targetPath": "$.groups",
  "preserveArrayWithSingleElement": true,
  "functions": [
   {
    "function": "renameMapEntry",
    "sourceKey": "roleName",
    "targetKey": "value"
   }
  ]
}
```

The `sourceKey` String in the target JSON is replaced with the one given in the `targetKey` and the result is:

```
{ "groups":[{"value":"ROLE1"},{"value":"ROLE2"}] }
```



</td>
</tr>
<tr>
<td valign="top">

replaceString

</td>
<td valign="top">

-   **`target`**

    Required: Yes

    Type: String; number

-   **`replacement`**

    Required: Yes

    Type: String; number

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function reads strings from the source system and then replaces each substring that matches the value of the target parameter with the replacement one.

For example, let's say the source system contains a string "*National College of Linguistics and History*". The `target` substring is "**National**" and the `replacement` substring is "**European**". Then, in the target system the main string will be written as "*European College of Linguistics and History*".

> ### Example:  
> ```
> 
> {
> 	"user": {
> 	   "mappings": [
> 		{
> 		   "sourcePath": "$.sAMAccountName[0]",
> 		   "targetPath": "$.userName",
> 		   "functions": [
> 			{
> 			   "function": "replaceString",
> 			   "target": "iag",
> 			   "replacement": "ips"
> 			}
> 		   ]
> 		}
> 	...
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

replaceFirstString

</td>
<td valign="top">

-   **`regex`**

    Required: Yes

    Type: String; number

-   **`replacement`**

    Required: Yes

    Type: String; number

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function replaces the first substring of a given string that matches the provided regex with the string in replacement.

> ### Example:  
> ```
> 
> {
> 	"user": {
> 	  "mappings": [
> 		{
> 		  "sourcePath": "$.sAMAccountName[0]",
> 		  "targetPath": "$.userName",
> 		  "functions": [
> 			{
> 			  "function": "replaceFirstString",
> 			  "regex": "14\\d{1}",
> 			  "replacement": 123
> 			}
> 		   ]
> 		}
> 	...
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

replaceLastString

</td>
<td valign="top">

-   **`regex`**

    Required: Yes

    Type: String; number

-   **`replacement`**

    Required: Yes

    Type: String; number

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function replaces the last substring of a given string that matches the provided regex with the string in replacement.

> ### Example:  
> ```
> 
> {
> 	"user": {
> 	   "mappings": [
> 		{
> 		  "sourcePath": "$.sAMAccountName[0]",
> 		  "targetPath": "$.userName",
> 		  "functions": [
> 			{
> 			  "function": "replaceLastString",
> 			  "regex": "14\\d{1}",
> 			  "replacement": 123
> 			}
> 		   ]
> 		}
> 	...
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

replaceAllString

</td>
<td valign="top">

-   **`regex`**

    Required: Yes

    Type: String; number

-   **`replacement`**

    Required: Yes

    Type: String; number

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function replaces each substring of the given string that matches the provided regex with the string in replacement.

> ### Example:  
> ```
> 
> {
> 	"user": {
> 	   "mappings": [
> 		{
> 		  "sourcePath": "$.sAMAccountName[0]",
> 		  "targetPath": "$.userName",
> 		  "functions": [
> 			{
> 			  "function": "replaceAllString",
> 			  "regex": "14\\d{1}",
> 			  "replacement": 123
> 			}
> 		   ]
> 		}
> 	...
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

resolveEntityIds

</td>
<td valign="top">

**`entityType`**

Required: No

Possible values:

-   `user`
-   `group`

Default value: `user`

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String

-   **`sourceSystemName`**

    Required: No

    Type: String

-   **`targetSystemName`**

    Required: No

    Type: String




</td>
<td valign="top">

This function resolves the value of a source system attribute to an existing back-end key in the target system.

For example, it can resolve the value of a source system member attribute to the ID of an existing SCIM resource that represents this member in a SCIM target system.

> ### Example:  
> ```
> 
> {
> 	"sourcePath": "$.member",
> 	"preserveArrayWithSingleElement": true,
> 	"optional": true,
> 	"targetPath": "$.members[?(@.value)]",
> 	"functions": [
> 		{
> 			"entityType": "group",
> 			"function": "resolveEntityIds"
> 		}
> 	   ]
> 	...
> }
> 
> ```

> ### Example:  
> The resolveEntityIds function is part of the default Identity Authentication write transformation. In the example below, it resolves the value of the user manager in the source system to an existing entity in the target system. This means that in order to provision the user manager, the manager must exist in the target Identity Authentication.
> 
> As the order of reading users and their managers from the source system \(for example, Microsoft Entra ID\) is undefined, you may need to run two consecutive provisioning jobs to resolve the manager.
> 
> > ### Code Syntax:  
> > ```
> >  {
> >         "sourcePath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
> >         "targetPath": "$['urn:ietf:params:scim:schemas:extension:enterprise:2.0:User']['manager']['value']",
> >         "optional" : true,
> >         "functions": [
> >             {
> >               "function": "resolveEntityIds"
> >             }
> >           ]
> >       },
> > ```

The `sourceSystemName` and the `targetSystemName` parameters are typically used within this function to resolve group members.

In the following example, we assume that you have created two source systems reading entities from one and the same user store \(for example, Microsoft Entra ID\). You provision users from *SourceSystem1* and groups from *SourceSystem2* to one and the same target system. By specifying the `sourceSystemName` as *SourceSystem1*, the user IDs of the group members in *SourceSystem2* will be resolved against the user IDs in the *SourceSystem1*.

> ### Code Syntax:  
> ```
> "functions": [
> 		{
> 			"sourceSystemName": "SourceSystem1",
> 			"function": "resolveEntityIds"
> 		}
> 	   ]
> 	...
> ```



</td>
</tr>
<tr>
<td valign="top">

splitStringToArray

</td>
<td valign="top">

-   **`separator`**

    Required: Yes

    Type: String




</td>
<td valign="top">

This function splits the initial String using the defined separator and produces as a result an array of Strings or objects.

In the following examples, function *splitStringToArray* is applied to the `sourcePath`, read from the source system. Based on the `targetPath` defined, the initial String will be split into array of Strings or objects.

**Example 1**

In the first example, the initial String we use is:

```

"countries": "Serbia,Germany,Spain"
```

The transformation using the function is the following:

```
{
               "sourcePath": "$.countries",
               "targetPath": "$.countryList",
               "functions": [
                   {
                       "function": "splitStringToArray",
                       "separator": ","                   
                   }
               ]
           },
```

After the function execution, the output results to the following array of Strings:

```
"countryList": [
        "Serbia",
        "Germany",
        "Spain"
    ],
```

**Example 2**

In the second example, we use the same initial String:

```

"countries": "Serbia,Germany,Spain"
```

In this case, the `targetPath` in the transformation using the function supports multiple values:

```
 {
                "sourcePath": "$.countries",
                "targetPath": "$.countryList[?(@.name)]",
                "functions": [
                    {
                        "function": "splitStringToArray",
                        "separator": ","                    
                    }
                ]
            },
```

After the function execution, the output results to the following array of objects:

```
"countryList": [
        {
            "name": "Serbia"
        },
        {
            "name": "Germany"
        },
        {
            "name": "Spain"
        }
    ],
```



</td>
</tr>
<tr>
<td valign="top">

substring

</td>
<td valign="top">

-   **`beginIndex`**

    Required: Yes

    Type: Integer

-   **`endIndex`**

    Required: No

    Type: Integer

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function returns a string if `endIndex` is not provided. It begins at the specified `beginIndex` and extends either to the character at index `endIndex - 1` or to the end of this string.

> ### Example:  
> ```
> 
> {
> 	"user": {
> 	   "mappings": [
> 		{
> 		  "sourcePath": "$.sAMAccountName[0]",
> 		  "targetPath": "$.userName",
> 		  "functions": [
> 			{
> 			  "function": "substring",
> 			  "beginIndex": 3,
> 			  "endIndex": 5
> 			}
> 		   ]
> 		}
> 	...
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

toString

</td>
<td valign="top">

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function accepts a Byte array or a string representation. The string is assumed in UTF-8 character encoding. Function result: **String**.

To see a relevant example, go to function encode and decode.

</td>
</tr>
<tr>
<td valign="top">

toUpperCaseString

</td>
<td valign="top">

-   **`locale`**

    Required: No

    Possible values: Abbreviation of locale, such as `de_DE`, `ja_JP`, `ru_RU` and so on.

    Default value: `en_EN`

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function converts all the characters in the given string to upper case, using the provided locale, or if nothing defined – English.

> ### Example:  
> ```
> 
> {
> 	"user": {
> 	   "mappings": [
> 		{
> 			"sourcePath": "$.sAMAccountName[0]",
> 			"targetPath": "$.userName",
> 			"functions": [
> 			{
> 			  "function": "toUpperCaseString",
> 			  "locale": "en_EN"
> 			}
> 		   ]
> 		}
> 	...
> }
> ```



</td>
</tr>
<tr>
<td valign="top">

toLowerCaseString

</td>
<td valign="top">

-   **`locale`**

    Required: No

    Possible values: Abbreviation of locale, such as `de_DE`, `ja_JP`, `ru_RU` and so on.

    Default value: `en_EN`

-   **`condition`**

    Required: No

    Type: String

-   **`applyOnElements`**

    Required: No

    Type: Boolean

    Possible values:

    -   true
    -   false

-   **`applyOnAttribute`**

    Required: No

    Type: String

-   **`assignToAttribute`**

    Required: No

    Type: String




</td>
<td valign="top">

This function converts all the characters in the given string to lower case, using the provided locale, or if nothing defined – English.

> ### Example:  
> ```
> {
> 	"user": {
> 	  "mappings": [
> 		{
> 		  "sourcePath": "$.sAMAccountName[0]",
> 		  "targetPath": "$.userName",
> 		  "functions": [
> 			{
> 			  "function": "toLowerCaseString",
> 			  "locale": "en_EN"
> 			}
> 		   ]
> 		}
> 	...
> }
> ```



</td>
</tr>
</table>

**Related Information**  


[Transformation Types](transformation-types-1a92c56.md "Learn about the types of JSON transformations needed for the provisioning jobs.")

[Transformation Examples](transformation-examples-901c759.md "The following examples explain how transformations work.")

[Transformation Expressions](transformation-expressions-bb8537b.md "")

[Transformation Variables](transformation-variables-8376adb.md "")

[Transformation Editors](transformation-editors-9ea770b.md "Identity Provisioning provides graphical and JSON text editor for managing provisioning system transformations.")

