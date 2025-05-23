<!-- loio901c759381d649158f8d9b5b07b095ec -->

# Transformation Examples

The following examples explain how transformations work.



<a name="loio901c759381d649158f8d9b5b07b095ec__section_m1c_hcl_x5b"/>

## Basic Transformation

The basic transformation copies all attributes from the input JSON messages to the output JSON ones.

> ### Code Syntax:  
> ```
> {
> 	"sourcePath": "$",
> 	"targetPath": "$"
> },
> ```



<a name="loio901c759381d649158f8d9b5b07b095ec__section_qbk_vtc_ykb"/>

## Source, Intermediate, and Target Data

In this example, the source system JSON data contains the **sn\[0\]** attribute. The read transformation converts this attribute to **name.familyName** in the intermediate JSON data. Then, the write transformation reads the **name.familyName** attribute and maps it to **name.familyName** in the target system.

**Source entity data \(from Microsoft Active Directory\)**

```
{
	"sAMAccountName": ["jsmith"],
	"mail": ["john.smith@company.com"],
	"givenName": ["John"],
	"sn": ["Smith"],
	"memberOf": ["group1"],
	"memberOf_2": ["group21", "group22"],
	"memberOf_3": ["group31", "group32", "group33"]
}
```

**Read transformation \(intermediate JSON Data\)**

```

{
    "user": {
        "mappings": [

...

            {
                "sourcePath": "$.%ldap.attribute.user.id%[0]",
                "targetVariable": "entityIdSourceSystem",
                "correlationAttribute": true
            },
            {
                "condition": "('%ldap.attribute.user.id%' == '%ldap.attribute.dn%')",
                "constant": "",
                "targetVariable": "nestedPathRegex",
                "functions": [
                    {
                        "function": "concatString",
                        "prefix": "(?i)cn=.*?,(.*?)",
                        "suffix": ",%ldap.user.path%"
                    }
                ]
            },
            {
                "condition": "('%ldap.attribute.user.id%' == '%ldap.attribute.dn%')",
                "sourcePath": "$.%ldap.attribute.user.id%[0]",
                "targetPath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:User']['nestedPath']",
                "functions": [
                    {
                        "function": "getMatchedRegexGroup",
                        "regex": "${nestedPathRegex}",
                        "groupIndex": 1
                    }
                ],
                "defaultValue": ""
            },
            {
                "sourcePath": "$.sAMAccountName[0]",
                "targetPath": "$.userName",
                "correlationAttribute": true
            },
            {
                "sourcePath": "$.displayName[0]",
                "optional": true,
                "targetPath": "$.displayName"
            },
            {
                "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
                "targetPath": "$.schemas[0]"
            },
            {
                "sourcePath": "$.mail[0]",
                "optional": true,
                "targetPath": "$.emails[0].value",
                "correlationAttribute": true
            },
            {
                "sourcePath": "$.givenName[0]",
                "optional": true,
                "targetPath": "$.name.givenName"
            },
            {
                "sourcePath": "$.sn[0]",
                "optional": true,
                "targetPath": "$.name.familyName"
            },
            {
                "sourcePath": "$.memberOf",
                "preserveArrayWithSingleElement": true,
                "optional": true,
                "targetPath": "$.groups[?(@.value)]"
            },

...
```

**Write transformation \(intermediate JSON Data\)**

```

{
    "user": {
        "condition": "($.emails.length() > 0) && ($.name.familyName EMPTY false)",
        "mappings": [
            {
                "sourcePath": "$.groups",
                "preserveArrayWithSingleElement": true,
                "optional": true,
                "targetPath": "$.corporateGroups"
            },
            {
                "sourceVariable": "entityIdTargetSystem",
                "targetPath": "$.id"
            },
            {
                "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
                "targetPath": "$.schemas[0]"
            },
            {
                "constant": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
                "targetPath": "$.schemas[1]"
            },
            {
                "sourcePath": "$.userName",
                "optional": true,
                "targetPath": "$.userName"
            },
            {
                "sourcePath": "$.emails[*].value",
                "preserveArrayWithSingleElement": true,
                "targetPath": "$.emails[?(@.value)]"
            },
            {
                "sourcePath": "$.userType",
                "optional": true,
                "targetPath": "$.userType"
            },
            {
                "sourcePath": "$.name.givenName",
                "optional": true,
                "targetPath": "$.name.givenName"
            },
            {
                "sourcePath": "$.name.middleName",
                "optional": true,
                "targetPath": "$.name.middleName"
            },
            {
                "sourcePath": "$.name.familyName",
                "optional": true,
                "targetPath": "$.name.familyName"
            },
            {
                "sourcePath": "$.displayName",
                "optional": true,
                "targetPath": "$.displayName"
            },
...
```

**Target entity data \(result in Identity Authentication\)**

```
{
	"schemas": [
		"urn:ietf:params:scim:schemas:core:2.0:User",
		"urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
	],
	"id": "P000100",
	"userName": "jsmith",
	"name": {
		"familyName": "Smith",
		"givenName": "John"
	},
	"emails": [
		{
			"value": "john.smith@company.com",
			"primary": "true",
			"type": "work"
		}
	],
	"groups": [
		{
			"value": "group1"
		}
	],
	"groups_2": [
		{
			"value": "group21"
		},
		{
			"value": "group22"
		}
	],
	"groups_3": [
	{
			"value": "group31"
		},
		{
			"value": "group32"
		},
		{
			"value": "group33"
		}
	]
}
```

For more information about condition examples, see [Transformation Conditions](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/condition-examples-in-transformations?version=Cloud).

**Related Information**  


[Transformation Types](transformation-types-1a92c56.md "Learn about the types of JSON transformations needed for the provisioning jobs.")

[Transformation Expressions](transformation-expressions-bb8537b.md "")

[Transformation Functions](transformation-functions-0cdac7c.md "")

[Transformation Variables](transformation-variables-8376adb.md "")

[Transformation Conditions](transformation-conditions-f47bd39.md "A condition defines a JSON filter expression that can be applied to entity types (such as users, groups, and roles) or within attribute mappings. It can be combined with strings, constants, variables, and functions, or used within functions.")

[Transformation Editors](transformation-editors-9ea770b.md "Identity Provisioning provides graphical and JSON text editor for managing provisioning system transformations.")

[Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md "You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.")

