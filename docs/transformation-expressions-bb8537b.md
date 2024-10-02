<!-- loiobb8537bd7ca445a591a1adaef4dee73a -->

# Transformation Expressions

The transformation logic is based on JSON. The order of the expressions in the file is decisive for how the transformation is executed. The transformation actions are performed in the sequence defined in the transformation logic.

There is a different transformation logic for every entity \(users, groups, roles\). Below are listed some of the JSON expressions you can use.

****


<table>
<tr>
<th valign="top">

Transformation Expression

</th>
<th valign="top">

Usage

</th>
</tr>
<tr>
<td valign="top">

applyOnElements

</td>
<td valign="top">

Use this JSON expression when the value referenced by the *sourcePath* is a multivalue structure \(a list or an array\), and you want to apply a function to its elements instead of to the whole structure.

You can use the *applyOnElements* expression in any function, for any provisioning system.

For example, you can see it in the default write transformation of the *SAP Application Server ABAP* proxy system. In this case, the **decode** function reads all members of a user list and converts this list into a byte array. Then, the **toString** function reads this byte-array and converts it back into a string \(a list of usernames\).

> ### Example:  
> ```
> 
> // Function toString will be applied to all members read from a user list.
> ...
> 	{
> 		"sourcePath": "$.members[*].value",
> 		"preserveArrayWithSingleElement": true,
> 		"optional": true,
> 		"targetPath": "$.USERLIST[?(@.USERNAME)]",
> 		"functions": [
> 			{
> 				"function": "decode",
> 				"algorithm": "base32",
> 				"skipPadding": true
> 			},
> 			{
> 				"function": "toString",
> 				"applyOnElements": true
> 			}
> 		  ]
> 		}
> ...
> ```

**Possible values:**

-   *true*
-   *false*

**Data type**: Boolean

</td>
</tr>
<tr>
<td valign="top">

applyOnJsonAttribute

</td>
<td valign="top">

This expression is deprecated. You can use the new one – *applyOnAttribute*.

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

applyOnAttribute

</td>
<td valign="top">

Use this JSON expression when the structure referenced by the *sourcePath* is a complex one \(a map\), and you want to apply a function to a single member of this map.

In the example below, all occurrences of "SAP" in the values of attribute COMPOSITE\_PRIVILEGE are replaced with "test" in the transformation result.

> ### Example:  
> Privileges in the source system:
> 
> ```
> 
> {
>     "PRIVILEGES": [
>         {
>             "COMPOSITE_PRIVILEGE": "SAP_01_COMP"
>         },
>         {
>             "COMPOSITE_PRIVILEGE": "SAP_02_COMP"
>         }
>     ]
> }
> 
> ```

> ### Example:  
> Source system transformation:
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
>                     "function": "replaceString",
>                     "applyOnElements": true,
>                     "target": "SAP",
>                     "replacement": "test",
>                     "applyOnAttribute": "COMPOSITE_PRIVILEGE"
>                 }
>             ]
>         }
>     ]
> }
> 
> ```

> ### Example:  
> Transformation result:
> 
> ```
> 
> {
>     "groups": [
>         {
>             "COMPOSITE_PRIVILEGE": "test_01_COMP"
>         },
>         {
>             "COMPOSITE_PRIVILEGE": "test_02_COMP"
>         }
>     ]
> }
> 
> ```

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

assignToAttribute

</td>
<td valign="top">

Use this JSON expression when the structure referenced by *targetPath* is a complex one \(a map\), and you want to assign the result of this mapping to a specific map entry.

In the example below, all occurrences of "SAP" in the values of attribute COMPOSITE\_PRIVILEGE are replaced with "test", and the result is assigned to the value of attribute "ASSIGNMENT".

> ### Example:  
> Privileges in the source system:
> 
> ```
> 
> {
>     "PRIVILEGES": [
>         {
>             "COMPOSITE_PRIVILEGE": "SAP_01_COMP"
>         },
>         {
>             "COMPOSITE_PRIVILEGE": "SAP_02_COMP"
>         }
>     ]
> }
> 
> ```

> ### Example:  
> Source system transformation:
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
>                     "function": "replaceString",
>                     "applyOnElements": true,
>                     "target": "SAP",
>                     "replacement": "test",
>                     "applyOnAttribute": "COMPOSITE_PRIVILEGE",
>                     "assignToAttribute": "ASSIGNMENT"
>                 }
>             ]
>         }
>     ]
> }
> 
> ```

> ### Example:  
> Transformation result:
> 
> ```
> 
> {
>     "groups": [
>         {
>             "ASSIGNMENT": "test_01_COMP",
>             "COMPOSITE_PRIVILEGE": "SAP_01_COMP"
>         },
>         {
>            "ASSIGNMENT": "test_02_COMP",
>             "COMPOSITE_PRIVILEGE": "SAP_02_COMP"
>         }
>     ]
> }
> 
> ```

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

condition

</td>
<td valign="top">

A condition specifies a JSON filter expression. It can be applied on a single mapping entity or on the whole entity type. You can use conditions on strings, constants, variables and functions.

-   Condition with **strings**

    > ### Example:  
    > ```
    > {
    > 	"mappings": [
    > 		… 
    > 		{
    > 			"condition": "$.memberOf contains 'group1'",
    >                 	"constant": "NewDisplayName",
    >                 	"targetPath": "$.displayName"
    >             }
    > 	]
    > }
    > ```

-   Condition with **constants** – AS ABAP \(proxy system\)

    > ### Example:  
    > ```
    > {
    > 	"condition": "($.emails.length() > 0) && ($.name.familyName EMPTY false)",
    > 	"mappings": [
    > 		{
    > 			"sourcePath": "$",
    > 			"targetPath": "$"
    > 		},
    > 	… 
    > }
    > ```

-   Condition with format **variables** – SAP S/4HANA Cloud \(source system\)

    > ### Example:  
    > ```
    > 
    > {
    >     "user": {
    >         "condition": "($.validityPeriod.startDate <= '${currentDate}') && ($.validityPeriod.endDate > '${currentDate}')",
    >         "mappings": [
    >             {
    >                 "sourcePath": "$.personID",
    >                 "targetVariable": "entityIdSourceSystem"
    >             },
    > ```

-   Conditions in **functions** – Microsoft Active Directory \(target system\)

    > ### Example:  
    > ```
    > 
    > "group": {
    > ...
    > 
    >       {
    >         "sourcePath": "$.members[*]",
    >         "targetVariable": "membersVariable",
    >         "preserveArrayWithSingleElement": true,
    >         "optional": true,
    >         "functions": [
    >           {
    >             "condition": "@.type != 'Group'",
    >             "entityType": "user",
    >             "applyOnElements": true,
    >             "type": "resolveEntityIds"
    >           },
    >           {
    >             "condition": "@.type == 'Group'",
    >             "entityType": "group",
    >             "applyOnElements": true,
    >             "type": "resolveEntityIds"
    >           },
    >           {
    >             "condition": "(@.type != 'Group') && ('%ldap.attribute.user.id%' != '%ldap.attribute.dn%')",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "value",
    >             "prefix": "%ldap.attribute.user.id%=",
    >             "suffix": ",%ldap.user.path%"
    >           },
    >           {
    >             "condition": "(@.type == 'Group') && ('%ldap.attribute.group.id%' != '%ldap.attribute.dn%')",
    >             "function": "concatString",
    >             "applyOnElements": true,
    >             "applyOnAttribute": "value",
    >             "prefix": "%ldap.attribute.group.id%=",
    >             "suffix": ",%ldap.group.path%"
    >           }
    >         ]
    > ...
    > ```

-   Conditions with **functions**

    > ### Example:  
    > ```
    > {
    >   "user": {
    >     "condition": "($.emails EMPTY false) && isValidEmail($.emails[0].value)",
    >     "mappings": [
    >       {
    >         "sourceVariable": "entityIdTargetSystem",
    >         "targetPath": "$.id"
    >       },
    >  .....
    > 
    > }
    > ```

-   Conditions and **skipOperations**

    > ### Example:  
    > > ### Code Syntax:  
    > > ```
    > > "condition":"$.groups empty false",
    > > "skipOperations":[
    > >    "update"
    > > ],
    > > ```

    First, the condition is evaluated. Users and groups who do not match the condition are skipped. After the condition is evaluated, the skip operation determines whether the remaining users will be skipped or provisioned.


**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

constant

</td>
<td valign="top">

Set a constant if the target system requires attributes that are not defined in the source system.

You can also use schemas to organize and combine multiple constants.

> ### Example:  
> ```
> {
> 	"targetPath": "$.emails[0].type",
> 	"constant": "work"
> },
> ```

**Data type**:

-   String
-   Integer
-   Boolean
-   JSONObject
-   StringArray
-   IntegerArray
-   BooleanArray
-   JSONObjectArray



</td>
</tr>
<tr>
<td valign="top">

correlationAttribute

</td>
<td valign="top">

Correlation attributes are used in the *"user"* mappings of the *Read Transformations* \(in source and proxy systems\). They mark attributes that are unique for a user in multiple source systems where this user is read from.

The purpose of `correlationAttribute` is to properly count managed identities \(users\) during the reading process. This is essential because the calculated value is compared to the customer's licensing quota.

-   *Use Case 1* – Same attribute in different systems

    > ### Example:  
    > Mapping from the *Microsoft Active Directory* read transformation:
    > 
    > ```
    > 
    >       {
    >         "sourcePath": "$.sAMAccountName[0]",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    > 
    > ```

    > ### Example:  
    > Mapping from the *SAP S/4HANA On-Premise* read transformation:
    > 
    > ```
    > 
    > 	{
    > 	   "sourcePath": "$.userAssignment.userID",
    > 	   "optional": true,
    > 	   "targetPath": "$.userName",
    > 	   "correlationAttribute": true
    > 	},
    > ```

    > ### Example:  
    > Mapping from the *LDAP Server* read transformation:
    > 
    > ```
    > 
    > 	{
    > 		"sourcePath": "$.%ldap.attribute.user.id%[0]",
    > 		"targetPath": "$.userName",
    > 		"correlationAttribute": true
    > 	},
    > ```

    *Result:* If the Identity Provisioning reads a user whose username is one and the same in all the three systems \(as listed above\), the service will consider and count these "3 users" as one managed identity.

-   *Use Case 2* – Different attributes from several systems

    > ### Example:  
    > Mapping from the *Microsoft Active Directory* read transformation:
    > 
    > ```
    > 
    >       {
    >         "sourcePath": "$.sAMAccountName[0]",
    >         "targetPath": "$.userName",
    >         "correlationAttribute": true
    >       },
    > 
    > ```

    > ### Example:  
    > Mapping from the *SAP Analytics Cloud* read transformation:
    > 
    > ```
    > 
    > 	{
    > 	   "sourcePath": "$.emails",
    > 	   "targetPath": "$.emails",
    > 	   "preserveArrayWithSingleElement": true
    > 	},
    > 	{
    > 	   "sourcePath": "$.emails[?(@.primary== true)].value",
    > 	   "correlationAttribute": true
    > 	},
    > ```

    > ### Example:  
    > Mapping from the *Identity Authentication* read transformation:
    > 
    > ```
    > 
    > 	{
    > 	   "sourcePath": "$.userName",
    > 	   "targetPath": "$.userName",
    > 	   "optional": true,
    > 	   "correlationAttribute": true
    > 	},
    > 
    >      ...
    > 
    > 	{
    > 	   "sourcePath": "$.emails[*].value",
    > 	   "preserveArrayWithSingleElement": true,
    > 	   "targetPath": "$.emails[?(@.value)]"
    > 	},
    > 	{
    > 	   "sourcePath": "$.emails[?(@.primary== true)].value",
    > 	   "correlationAttribute": true
    > 	},
    > 
    > ```

    *Result:* If the Identity Provisioning reads a user with a certain username from one system, then it reads a user with a particular e-mail from another system, and then finds a user with the same username and e-mail in a third system \(as listed above\), the service will consider and count these "3 users" as one managed identity.


**Possible values:**

-   *true*
-   *false*

**Data type**: Boolean

</td>
</tr>
<tr>
<td valign="top">

defaultValue

</td>
<td valign="top">

This JSON expression returns the default value of an attribute when it is set as optional and there is no specific value provided in the `sourcePath`. The **defaultValue** expression comes in handy in the following cases:

-   When an attribute of a previously provisioned entity is later deleted from the source system. After a new provisioning job, the target system will try to get some value for this missing attribute, and thus it will write its default one.
-   When the system transformation contains a *valueMapping* operation. If the value of the mapped attribute is not found as a key in the `"valueMappings"` definitions, or some of the source paths does not return a value, the JSON transformation will use the default one.

The default value of an attribute can be a *string*, *integer*, *Boolean*, *array*, or empty \(null\).

You can add `"defaultValue"` for any attribute, in the transformation of any provisioning system. For example, you can find it in the default transformation of the **Identity Authentication** target system:

> ### Example:  
> ```
> 
> ...
> 	 {
>         "sourcePath": "$.userType",
>         "targetPath": "$.userType",
>         "defaultValue": "employee",
>         "optional": true
>       },
> ...
> ```

**Data type**:

-   String
-   Integer
-   Boolean
-   JSONObject
-   StringArray
-   IntegerArray
-   BooleanArray
-   JSONObjectArray



</td>
</tr>
<tr>
<td valign="top">

ignore

</td>
<td valign="top">

Use the *ignore* expression if you would like to exclude certain parts of the transformation from being considered during the provisioning. Similar to *condition*, you can set *ignore* on various levels, including on entire entity types such as users or roles, or specific mapping entities. This is applicable for both source and target systems.

> ### Note:  
> Note that if an entity type is set to be ignored in the read transformations, you won't get any data in the job log statistics for this entity type.

> ### Example:  
> ```
> 
> "group": {
>         "ignore": true,
>         "mappings": [
>             {
>                 "sourcePath": "$.sAMAccountName[0]",
>                 "targetVariable": "entityIdSourceSystem"
>             },
>             {
>                 "sourcePath": "$.sAMAccountName[0]",
>                 "targetPath": "$.displayName"
>             },
> ...
> 
> ```

> ### Example:  
> ```
> 
>  "user": {
>         "mappings": [
>             {
>                 "ignore": true,
>                 "sourcePath": "$.sAMAccountName[0]",
>                 "targetVariable": "entityIdSourceSystem"
>             },
>             {
>                 "sourcePath": "$.sAMAccountName[0]",
>                 "targetPath": "$.userName"
>             },
> ...
> 
> ```

**Possible values:**

-   *true*
-   *false*

**Data type**: Boolean

</td>
</tr>
<tr>
<td valign="top">

preserveArrayWithSingleElement

</td>
<td valign="top">

This JSON expression converts an array into a single element. That means, when the Identity Provisioning service reads an array that contains only one element, then in the target system:

-   If **"preserveArrayWithSingleElement"** is set to *true*, this expression will keep the array with the single element as is.

    > ### Example:  
    > The following mapping keeps the array of group members, resolving their IDs, even if the array contains only one member.
    > 
    > ```
    > 
    > {
    > 	"sourcePath": "$.members[*].value",
    > 	"preserveArrayWithSingleElement": true,
    > 	"optional": true,
    > 	"targetPath": "$.members[?(@.value)]",
    > 	"functions": [
    > 	   {
    > 		"type": "resolveEntityIds"
    > 	   }
    >    ]
    > }
    > ...
    > 	
    > ```

-   If **"preserveArrayWithSingleElement"** is set to *false*, this expression will convert the array into the relevant single element.

    > ### Example:  
    > The following mapping converts the array into a single element \(a group member\), and resolves its ID.
    > 
    > ```
    > 
    > {
    > 	"sourcePath": "$.members[*].value",
    > 	"preserveArrayWithSingleElement": false,
    > 	"optional": true,
    > 	"targetPath": "$.members[?(@.value)]",
    > 	"functions": [
    > 	   {
    > 		"type": "resolveEntityIds"
    > 	   }
    >    ]
    > }
    > ...
    > 	
    > ```


**Possible values:**

-   *true*
-   *false*

**Data type**: Boolean

</td>
</tr>
<tr>
<td valign="top">

scope

</td>
<td valign="top">

You can set a scope for an entity attribute, based on its lifecycle. A scope can have the following values:

-   *createEntity* – an entity attribute is only processed during creation. To do this, tag the entity attribute with scope `createEntity` in the system transformation. Transformation mappings without scope are always processed.

    > ### Note:  
    > Currently, the `createEntity` scope is only applicable for entities created in **target systems**.

    > ### Example:  
    > The following mapping provides an initial password when a user is created.
    > 
    > ```
    > 
    > {
    >   "user": {
    > 	"mappings": [    
    > 	  { 
    >           "scope": "createEntity", 
    >           "targetPath": "$.Password", 
    >           "constant": "Initial1" 
    > 	  }
    >         
    >      ]
    >  }, 
    > ...
    > 	
    > ```

-   *patchEntity* – when using the *ipsproxy* application and a system that supports SCIM PATCH operation, you may need to perform certain transformations over the PATCH request. To do this, use the `patchEntity` scope in the system transformation. Only mappings with this scope will be processed.

    > ### Note:  
    > -   The Identity Provisioning service supports PATCH requests only for groups and group members \(assignments\).
    > -   The `patchEntity` scope is only applicable for write transformations in **proxy systems**.

    > ### Example:  
    > The following mapping decodes the group ID and preserves the patch request body \(payload\) into the target system.
    > 
    > ```
    > 
    >   {
    >        "scope": "patchEntity",
    >        "sourceVariable": "entityIdTargetSystem",
    >        "targetVariable": "entityIdTargetSystem",
    >        "functions": [
    >          {
    >            "type": "decode",
    >            "algorithm": "base32",
    >            "skipPadding": true
    >          },
    >          {
    >            "function": "toString"
    >          }
    >        ]
    >      },
    > 
    > 	{
    >        "scope": "patchEntity",
    >        "sourcePath": "$",
    >        "targetPath": "$"
    >      },
    > 	
    > ```

-   *deleteEntity* – If an entity has been deleted from the source system or has been set a condition for it not to be read anymore, this entity can "stay" in the target system for the following reasons:

    -   The target system does not support deletion of entities.
    -   You do not want to delete it but only temporary disable/deactivate it.
    -   You want to neither delete it, nor deactivate it but only remove its permissions, or exclude it from some corporate groups.

    If you have to fulfill some of these scenarios for an entity, use the `deleteEntity` scope. It prevents from deleting the entity from the target system as only updating its status instead. Also, bear in mind the following:

    -   For the affected entity, all transformation mappings that do not contain this scope will be ignored.
    -   If a condition exists on entity type level, it will be ignored as well.

    Use this scope for the following systems:

    -   Cloud Foundry UAA server
    -   Identity Authentication
    -   Local Identity Directory
    -   Microsoft Entra ID
    -   Sales Cloud – Analytics & AI
    -   SAP Advanced Financial Closing
    -   SAP Analytics Cloud
    -   SAP Ariba Applications
    -   SAP BTP Account Members \(Neo\)
    -   SAP BTP XS Advanced UAA \(Cloud Foundry\)
    -   SAP Business Network
    -   SAP Build Work Zone, advanced edition
    -   SAP Build Work Zone, standard edition
    -   SAP Central Business Configuration
    -   SAP Commerce Cloud
    -   SAP SuccessFactors Incentive Management
    -   SAP Concur version 2
    -   SAP CPQ
    -   SAP Data Custodian
    -   SAP Enterprise Portal
    -   SAP Fieldglass
    -   SAP Field Service Management
    -   SAP Intelligent Agriculture
    -   SAP Jam Collaboration
    -   SAP Sales Cloud and SAP Service Cloud
    -   SAP SuccessFactors Learning
    -   SAP SuccessFactors version 2
    -   SAP S/4HANA for procurement planning
    -   SCIM System

    > ### Example:  
    > **Concur**: The following mapping disables the user account:
    > 
    > ```
    > {
    >    "user": {
    > 	"mappings": [
    >        
    > 	  {
    >          "scope": "deleteEntity",
    >          "constant": "US",
    >          "targetPath": "$.Custom21"
    >        },
    >        {
    >          "scope": "deleteEntity",
    >          "constant": "",
    >          "targetPath": "$.Password"
    >        },
    >        {
    >          "scope": "deleteEntity",
    >          "constant": "DEFAULT",
    >          "targetPath": "$.LedgerCode"
    >       },
    >       {
    >          "constant": "N",
    >          "targetPath": "$.Active",
    >          "scope": "deleteEntity"
    >       },
    > ...
    > 
    > ```

    > ### Example:  
    > **Microsoft Entra ID**: The following mapping disables the user account:
    > 
    > ```
    > {
    >    "user": {
    > 	"mappings": [
    >        
    > 	  {
    >          "constant": false 
    >          "targetPath": "$.accountEnabled", 
    >          "scope": "deleteEntity",
    >        },
    > ...
    > 
    > ```

    > ### Example:  
    > **Identity Authentication \(SCIM API version 1\)**: The following mapping disables the user account and unassigns the user from all the groups it was a member of:
    > 
    > ```
    > {
    >    "user": {
    > 	"mappings": [
    > 	  {
    > 		"sourceVariable": "entityIdTargetSystem",
    > 		"targetPath": "$.id",
    > 		"scope": "deleteEntity"
    > 	  },
    > 	  {
    >          "constant": false,
    >          "targetPath": "$.active",
    >          "scope": "deleteEntity"
    >        },
    >        {
    >          "constant": [],
    >          "targetPath": "$.corporateGroups",
    >          "scope": "deleteEntity"
    >        },
    >        {
    >          "constant": [],
    >          "targetPath": "$.groups",
    >          "scope": "deleteEntity"
    >        },
    > ...
    > 
    > ```

    > ### Example:  
    > **Identity Authentication \(SCIM API version 2\)**: The following mapping disables the user account.
    > 
    > Disabling a user account is done with a PATCH operation which replaces the value of the `active` user attribute `true` with `false`. For this, you also need to set `ias.user.update.instead.delete=true` in the Identity Authentication target system.
    > 
    > For more information, see: [List of Properties](list-of-properties-d6f3577.md)
    > 
    > ```
    > {
    >    "user":{
    >       "mappings":[
    >          {
    >             "constant":"urn:ietf:params:scim:api:messages:2.0:PatchOp",
    >             "targetPath":"$.schemas[0]",
    >             "scope":"deleteEntity"
    >          },
    >          {
    >             "constant":"replace",
    >             "targetPath":"$.Operations[0].op",
    >             "scope":"deleteEntity"
    >          },
    >          {
    >             "constant":"active",
    >             "targetPath":"$.Operations[0].path",
    >             "scope":"deleteEntity"
    >          },
    >          {
    >             "constant":false,
    >             "targetPath":"$.Operations[0].value",
    >             "scope":"deleteEntity"
    >          },      
    > ...
    > 
    > ```

    > ### Example:  
    > **SAP Jam**: The following mapping disables the user account:
    > 
    > ```
    > 
    >  "user": {
    >         "mappings": [
    >     
    >             {
    >                 "sourceVariable": "entityIdTargetSystem",
    >                 "targetPath": "$.id",
    >                 "scope": "deleteEntity"
    >             },
    >             {
    >                 "constant": false,
    >                 "targetPath": "$.active",
    >                 "scope": "deleteEntity"   
    > 
    >             },
    > ...
    > 
    > ```


**Possible values**:

-   *createEntity*
-   *patchEntity*
-   *deleteEntity*

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

skipOperations

</td>
<td valign="top">

If you want the provisioning job to not execute operations of a certain type on groups and users , use the `skipOperations` expression. You can apply it when you need to avoid creating, deleting, or updating entities.

You can use `skipOperations` only in target system transformations.

-   In the following example, the transformation does not allow updating groups in the target system. This approach is valuable when you have done group changes in the target system, and after a new *Read* or *Resync* job, you want these changes to be kept instead of being overwritten by the groups in the source system.

    > ### Example:  
    > ```
    > 
    >    "group": {
    > 	"skipOperations": [
    > 		"update"
    > 	],
    > 	"mappings": [
    > 	  {
    > ```

-   In the following example, the transformation does not allow creating and deleting users in the target system:

    > ### Example:  
    > ```
    > {
    >    "user": {
    > 	"skipOperations": [
    > 		"create", "delete"
    > 	],
    > 	"mappings": [
    > 	  {
    > ```

    You can set the transformation to skip the "`create`" operation if you're sure that all entities from the source system already exist in the target – independently from the Identity Provisioning service. That means, they have been created in the target system manually or via a script. Thus, by skipping the "`create`" operation, the identity provisioning job will only provision the changes instead of creating the users all over again in the target.

    The Identity Provisioning service will skip creating the existing entities and will try to update them. There are two options for resolving the existing users by the service.

    **Option 1:** In case the update operation is executed via PATCH request, the Identity Provisioning service will search and resolve the existing users by the default or predefined unique attributes for the system.

    In case the update operation is executed via PUT request, the Identity Provisioning service will use the same users resolution flow if the target system is included in the list below:

    -   Cloud Foundry UAA server
    -   Identity Authentication
    -   Local Identity Directory
    -   Sales Cloud – Analytics & AI
    -   SAP Advanced Financial Closing
    -   SAP Analytics Cloud
    -   SAP Ariba Applications
    -   SAP BTP Account Members \(Neo\)
    -   SAP BTP XS Advanced UAA \(Cloud Foundry\)
    -   SAP Business Network
    -   SAP Build Work Zone, advanced edition
    -   SAP Build Work Zone, standard edition
    -   SAP Central Business Configuration
    -   SAP Commerce Cloud
    -   SAP SuccessFactors Incentive Management
    -   SAP Concur version 2
    -   SAP CPQ
    -   SAP Data Custodian
    -   SAP Enterprise Portal
    -   SAP Fieldglass
    -   SAP Field Service Management
    -   SAP Intelligent Agriculture
    -   SAP Jam Collaboration
    -   SAP Sales Cloud and SAP Service Cloud
    -   SAP SuccessFactors Learning
    -   SAP SuccessFactors version 2
    -   SAP S/4HANA for procurement planning
    -   SCIM System

    For more information about the unique attributes of your system, see [List of Properties](list-of-properties-d6f3577.md).

    **Option 2:** In all other cases that differ from the abovementioned, the existing users are resolved by retrieving their IDs. In order for the *skip create* operation to be executed without error, you also need to make a few adjustments in your source and target transformations. This way, the service will get and retrieve the IDs of the entities correctly.

    > ### Note:  
    > If an entity does not exist in the target system \(which means, a retrieved ID does not match any target entity\), this entity will neither be created, nor updated.

    In the following detailed example, *SAP SuccessFactors* is a source system and *Identity Authentication* is a target system. You want all users that exist on both systems to be skipped during creation and to only be updated on the target. If there are users existing only in the source system, they will not be created in the target. To do that:

    1.  Open your *SAP SuccessFactors* admin console. For every user that you want to be provisioned and updated in *Identity Authentication*, you need to set up one of its predefined custom attributes \(*custom01* – *custom15*\), entering the *Identity Authentication* unique identifier for that user. For example, you can do that in the **custom10** attribute.

        > ### Note:  
        > The unique identifier that you have to set up for the relevant SAP SuccessFactors users depends on the API version of your Identity Authentication system.
        > 
        > -   For Identity Authentication SCIM API \(in short, *SCIM API version 1*\), enter the **User ID** \(P-user\).
        > -   For Identity Directory SCIM API \(in short, *SCIM API version 2*\), enter the **User UUID**.

    2.  Then go to the *Identity Provisioning* admin console, and in the *Properties* tab update the `sf.user.attributes` property, adding **custom10** to the list of attributes.

    3.  In the *SAP SuccessFactors* source system, add the following extra user mapping. It maps **custom10** to a custom attribute in *Identity Authentication*, for example **custom\_IAS\_ID**:

        > ### Example:  
        > ```
        > 
        > {
        > 	"user": {
        > 		"mappings": [
        > 		   {
        > 			"sourcePath": "$.custom10",
        > 			"targetPath": "$.custom_IAS_ID",
        > 			"optional": true
        > 		   },
        > 
        > ...
        >             
        > ```

    4.  In the *Identity Authentication* target system, replace the following user mapping:

        > ### Example:  
        > ```
        > 
        > {
        > 	"user": {
        >         "mappings": [
        > 		  {
        > 			"sourceVariable": "entityIdTargetSystem",
        > 			"targetPath": "$.id"
        > 		  },
        > 
        > ...
        >             
        > ```

        with:

        > ### Example:  
        > ```
        > 
        > 
        >            {
        >                 "sourcePath": "$.custom_IAS_ID",
        >                 "targetVariable": "entityIdTargetSystem"
        >             },
        >             {
        >                 "sourcePath": "$.custom_IAS_ID",
        >                 "targetPath": "$.id"
        >             },
        > 
        >             
        > ```

    5.  \(Optional\) If there are users that exist only in the source system and you don't want them to be created in the target, enhance the following condition in the *Identity Authentication* target transformation:

        > ### Example:  
        > ```
        > 
        > {
        > 	"user": {  
        > 
        >         "condition": "($.emails.length() > 0) && ($.name.familyName EMPTY false) && ($.custom_IAS_ID EMPTY false)",
        > 	      "mappings": [
        > . . .
        > 
        > ```

    6.  Run the first *Read* provisioning job.
    7.  Check in the *Identity Authentication* admin console if the relevant "marked" users are updated, and that the rest are not. Also, check that users that exist only in *SAP SuccessFactors* \(if any\) are not created in *Identity Authentication*.

-   
-   
**Possible values**:

-   *create*
-   *update*
-   *delete*

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

sourcePath

</td>
<td valign="top">

The *sourcePath* expression denotes the path to an attribute in the input JSON message \(could be the source system JSON data or the intermediate one\).

> ### Example:  
> ```
> {
> 	"sourcePath": "$.name.familyName",
> "targetPath": "$.name.familyName"
> },
> ```

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

targetPath

</td>
<td valign="top">

The *targetPath* expression denotes the path where the attribute should be stored in the output JSON message \(could be the intermediate or the target system JSON data\).

> ### Example:  
> ```
> {
> 	"targetPath": "$.name.familyName",
> 	"sourcePath": "$.sn[0]"
> },
> ```

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

type

</td>
<td valign="top">

The type of action to be performed in the mapping. It could be *set*, *remove*, *rename* and *valueMapping*.

-   The *set* type maps an attribute from the source system to an attribute in the target JSON data. If no type is defined, `"type": "set"` is used by default.

    > ### Example:  
    > ```
    > {
    > 	"type": "set",
    > 	"targetPath": "$.groups"
    > }
    > ```

-   The *remove* type deletes an attribute during transformation. This attribute is not present in the target JSON data.

    > ### Example:  
    > ```
    > {
    > 	"type": "remove",
    > 	"targetPath": "$.groups"
    > }
    > ```

-   The *rename* type renames the last element of a complex targetPath.

    In the example below, the last element `.lastName` of the targethPath `$.name.lastName` will be renamed with the provided constant value `familyName`. This will result in the following targetPath: `"$.name.familyName",`.

    > ### Code Syntax:  
    > ```
    > {
    >                 "targetPath": "$.name.lastName",
    >                 "constant": "familyName",
    >                 "type": "rename",
    >                 "optional": true
    > }
    > ```

-   The *valueMapping* type allows multiple entity attributes \(read from the source system\) to be mapped to a single target attribute.

    For example, you can set a mapping condition for a user attribute **user.timeZoneCode**. After the provisioning job, its value will be mapped to a new attribute – **timezone**. The example below provides a number of world locations and their relevant timezone.

    > ### Note:  
    > If the value of **user.timeZoneCode** is not found as a key in the `valueMappings` definitions, or some of the source paths does not return a value, the JSON transformation will use the default one. \(In the example below, the default value is *Europe/Berlin*.\)

    > ### Example:  
    > JSON code for mapping user timezone:
    > 
    > ```
    > 
    >   "user": 
    > 	{
    > 	...
    > 		
    > 	       {
    >             "type": "valueMapping",
    >             "sourcePaths": ["$.user.timeZoneCode"],
    >             "targetPath": "$.timezone",
    >             "defaultValue": "Europe/Berlin",
    >             "valueMappings": [
    >                     { "key": ["WDFT"], "mappedValue": "Europe/Berlin" },
    >                     { "key": ["ISRAEL"], "mappedValue": "Asia/Jerusalem" },
    >                     { "key": ["RUS03"], "mappedValue": "Europe/Moscow" },
    >                     { "key": ["AUSNSW"], "mappedValue": "Australia/Sydney" },
    >                     { "key": ["UTC+4"], "mappedValue": "Asia/Dubai" },
    >                     { "key": ["BRAZIL"], "mappedValue": "America/Sao_Paulo" },
    >                     { "key": ["BRZLEA"], "mappedValue": "America/Sao_Paulo" },
    >                     { "key": ["MSTNO"], "mappedValue": "America/Phoenix" },
    >                     { "key": ["EST"], "mappedValue": "America/New_York" },
    >                     { "key": ["UTC"], "mappedValue": "Etc/UTC" },
    >                     { "key": ["UTC+3"], "mappedValue": "Asia/Riyadh" },
    >                     { "key": ["EST_"], "mappedValue": "America/Toronto" },
    >                     { "key": ["UTC+8"], "mappedValue": "Asia/Shanghai" },
    >                     { "key": ["JAPAN"], "mappedValue": "Asia/Tokyo" }
    >                 ]
    >             }
    > 
    > 	...
    >      
    > ```


**Possible values:**

-   *set*
-   *remove*
-   *rename*
-   *valueMapping*

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

valueMappings

</td>
<td valign="top">

Provides a list with mapped values. It can only be used when *type* is set to `valueMapping`. The list contains the keys, which are read from the source system and mapped to values in a single target attribute.

The example below provides the list of world locations and their relevant timezone.

> ### Example:  
> JSON code for mapping user timezone:
> 
> ```
> 
>   "user": 
> 	{
> 	...
> 		
> 	       {
>             "type": "valueMapping",
>             "sourcePaths": ["$.user.timeZoneCode"],
>             "targetPath": "$.timezone",
>             "defaultValue": "Europe/Berlin",
>             "valueMappings": [
>                     { "key": ["WDFT"], "mappedValue": "Europe/Berlin" },
>                     { "key": ["ISRAEL"], "mappedValue": "Asia/Jerusalem" },
>                     { "key": ["RUS03"], "mappedValue": "Europe/Moscow" },
>                     { "key": ["AUSNSW"], "mappedValue": "Australia/Sydney" },
>                     { "key": ["UTC+4"], "mappedValue": "Asia/Dubai" },
>                     { "key": ["BRAZIL"], "mappedValue": "America/Sao_Paulo" },
>                     { "key": ["BRZLEA"], "mappedValue": "America/Sao_Paulo" },
>                     { "key": ["MSTNO"], "mappedValue": "America/Phoenix" },
>                     { "key": ["EST"], "mappedValue": "America/New_York" },
>                     { "key": ["UTC"], "mappedValue": "Etc/UTC" },
>                     { "key": ["UTC+3"], "mappedValue": "Asia/Riyadh" },
>                     { "key": ["EST_"], "mappedValue": "America/Toronto" },
>                     { "key": ["UTC+8"], "mappedValue": "Asia/Shanghai" },
>                     { "key": ["JAPAN"], "mappedValue": "Asia/Tokyo" }
>                 ]
>             }
> 
> 	...
>      
> ```

**Data type**: JSONObjectArray

</td>
</tr>
<tr>
<td valign="top">

sourcePaths

</td>
<td valign="top">

Specifies the paths to an attribute in the input JSON message of the source system. The *sourcePaths* can only be used when *type* is set to `valueMapping`.

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

optional

</td>
<td valign="top">

Specifies whether attribute's availability is mandatory or optional for a given system.

-   If set to *true*, this means that the attribute is optional and even if it is missing, provisioning won't fail.

-   If set to *false* or not set at all, this means that the attribute is mandatory and if it is missing, provisioning will fail.


For example, the default read transformation of SAP SuccessFactors shows that if the first name of a user is missing in the source system, this user will be read and provisioned to a target system. However, if the last name of a user is missing, provisioning will fail as this is a mandatory attribute.

> ### Code Syntax:  
> ```
> {
>         "sourcePath": "$.firstName",
>         "optional": true,
>         "targetPath": "$.name.givenName"
>       },
>       {
>         "sourcePath": "$.lastName",
>         "targetPath": "$.name.familyName"
>       },
> ```

**Possible values:**

-   *true*
-   *false*

**Data type**: Boolean

</td>
</tr>
<tr>
<td valign="top">

sourceVariable

</td>
<td valign="top">

The *sourceVariable* expression denotes a variable that is valid only within a given provisioning system. It shows where the variable will be read from.

For more information, see [Transformation Variables](transformation-variables-8376adb.md)

**Data type**: String

</td>
</tr>
<tr>
<td valign="top">

targetVariable

</td>
<td valign="top">

The *targetVariable* expression denotes a variable that is valid only within a given provisioning system. It shows where the variable will be written to.

For more information, see [Transformation Variables](transformation-variables-8376adb.md)

**Data type**: String

</td>
</tr>
</table>

**Related Information**  


[Transformation Types](transformation-types-1a92c56.md "Learn about the types of JSON transformations needed for the provisioning jobs.")

[Transformation Examples](transformation-examples-901c759.md "The following examples explain how transformations work.")

[Transformation Functions](transformation-functions-0cdac7c.md "")

[Transformation Variables](transformation-variables-8376adb.md "")

[Transformation Editors](transformation-editors-9ea770b.md "Identity Provisioning provides graphical and JSON text editor for managing provisioning system transformations.")

