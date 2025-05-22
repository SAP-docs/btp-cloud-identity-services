<!-- loiof47bd39ea1ba4cc4ac64fcb0f67b09ef -->

# Transformation Conditions

A condition defines a JSON filter expression that can be applied to entity types \(such as users, groups, and roles\) or within attribute mappings. It can be combined with strings, constants, variables, and functions, or used within functions.

You can add conditions in both source and target system transformations. When applied in the source transformation, entities that do not meet the condition are skipped after being read. When applied in the target transformation, entities that do not meet the condition are skipped before being written.

You can define conditions using the [JSONPath specification](https://github.com/json-path/JsonPath) in the Identity Provisioning editors: JSON editor and Graphical editor.


<table>
<tr>
<th valign="top">

Operators and Checks

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`==` 

</td>
<td valign="top">

Left-hand value is equal to right-hand value.

For example: `"condition": "$.emails[?(@.primary == true)].value == []",`

This condition checks if the user has no primary email defined. It evaluates to `true` if the `emails` array contains no entry where `primary` is set to `true`.

This condition is used in the default write transformations of SAP Commerce Cloud, where if the user has no primary email, the first email in the list is used instead.

The following explains each part of the filter expression:

-   `$` - Indicates the starting point for the JSONPath expressions.

-   `emails` - Accesses the emails array within the user entity.

-   `[?()]` - Starts a filter expression to evaluate the array.

-   `@` - Refers to the current element within the array.

-   `@.primary == true` - Filters the array to retrieve only the elements marked as the primary email.

-   `.value` - After applying the filter condition, this extracts the actual email address.

-   `== []` - Checks if the value on the left-hand side is equal to an empty array `[]`.


> ### Tip:  
> Use this pattern`[?(@. ...)]` for filtering elements within an array based on defined conditions.



</td>
</tr>
<tr>
<td valign="top">

`!=` or `!==` 

</td>
<td valign="top">

Left-hand value is not equal to right-hand value.

For example: `"condition": "$.name.familyName != 'Smith'",`

This condition checks if the user's `familyName` is not equal to `Smith`. Only users whose `familyName` is different from `Smith` fulfill this condition.

</td>
</tr>
<tr>
<td valign="top">

`=~` 

</td>
<td valign="top">

Left-hand value matches the regular expression on the right-hand side.

For example: `"condition": "$.emails[0].value =~ /.*@example.com/",`

This condition checks if the user's first email in the `emails` array ends with `@example.com`. Only users whose first email \(`emails[0].value`\) contains this domain fulfill this condition.

-   `/` - Marks the beginning and the end of a regex.

-   `.*` - Matches any sequence of characters, including an empty sequence.




</td>
</tr>
<tr>
<td valign="top">

`&&` 

</td>
<td valign="top">

AND: Returns `true` if both expressions are `true`.

For example: `"condition": "($.user.validityPeriod.startDate <= '${currentDate}') && ($.user.validityPeriod.endDate > '${currentDate}')",`

This condition checks whether the user is within their validity period. Only users whose validity period includes the current date will meet this condition, indicating that they are considered active.

This condition is used in the default read transformations of SAP S/4HANA Cloud source system to process only active users.

</td>
</tr>
<tr>
<td valign="top">

`||` 

</td>
<td valign="top">

OR: Returns `true` if at least one expression is `true`.

For example: `"condition": "((('%c4c.group.prefix%' === 'null') || ($.groups[?(@.display =~ /%c4c.group.prefix%.*/)] empty false)) && $.userName empty false && ($.userType === 'Employee' || $.userType === 'employee'))",`

Simplified pattern:

`(<group prefix check> || <group presence check>) && <username presence check> && (<user type 'Employee' check> || <user type 'employee' check>)`

This condition checks if the group prefix is null, or if there is at least one group in the user's groups array whose display name starts with the specified prefix. Additionally, it ensures that the `userName` is not empty and that the `userType` is either `"Employee"` or `"employee"`, allowing case insensitivity in the first letter only.

This condition is used in the default write transformations of SAP Sales Cloud and SAP Service Cloud connector version 4 target system.

</td>
</tr>
<tr>
<td valign="top">

`empty true` 

</td>
<td valign="top">

Left-hand value is considered empty \(null, empty string, empty array\).

For example: `"condition": "($.emails EMPTY true) || isValidEmail($.emails[0].value)",`

This condition checks if an email is either missing \(that is, the `emails` array is empty\) or the first email in the array is valid.

This condition is used in the default write transformations of SAP Advanced Workflow target system to ensure that an email is either provided and valid or missing.

</td>
</tr>
<tr>
<td valign="top">

`empty false` 

</td>
<td valign="top">

Left-hand value is not considered empty.

For example: `"condition": "($.emails EMPTY false) && ($.userName EMPTY false) && isValidEmail($.emails[0].value)",`

This condition checks if all parts are `true`. It expects at least one email to be present, the `userName` field to be filled, and the first email address in the `emails` array to be valid.

This condition is used for the user entity in the default write transformations of Identity Authentication version 2 and Local Identity Directory target systems.

</td>
</tr>
</table>

The following examples show how you can use conditions for filtering users based on group assignments.



<a name="loiof47bd39ea1ba4cc4ac64fcb0f67b09ef__section_wdx_qbp_cfc"/>

## Check if Users are Assigned to a Group with Specific Prefix

> ### Example:  
> > ### Code Syntax:  
> > ```
> > {
> >    "user":{
> >       "condition":"$.groups[?(@.display =~ /ABC.*/)] empty false",
> > ```

This condition evaluates to `true` if the user is a member of at least one group whose display name begins with `ABC`.



<a name="loiof47bd39ea1ba4cc4ac64fcb0f67b09ef__section_d2x_pgp_cfc"/>

## Check if Users are Not Assigned to a Particular Group

> ### Example:  
> > ### Code Syntax:  
> > ```
> > {
> >    "user":{
> >       "condition":"$.groups EMPTY true || $.groups[?(@.display === 'XYZ' )] empty true",
> > ```

This condition evaluates to `true` if the user has no group memberships at all, or if they are not a member of any group named `XYZ`. You can use it to exclude \(skip\) users who are specifically assigned to the `XYZ` group.



<a name="loiof47bd39ea1ba4cc4ac64fcb0f67b09ef__section_gpj_4tv_cfc"/>

## Check if Users are Assigned to One or Two Particular Groups

> ### Example:  
> > ### Code Syntax:  
> > ```
> > {
> >    "user":{
> >       "condition":"($.groups EMPTY false) && ( ($.groups[?(@.display ==='ABC' )] != []) || ($.groups[?(@.display ==='XYZ')] != []))",
> > ```

This condition evaluates to `true` if the user has at least one group assigned to them, and if they are a member of either the `ABC` group or the `XYZ` group or both.



<a name="loiof47bd39ea1ba4cc4ac64fcb0f67b09ef__section_zm1_ptv_cfc"/>

## Check for Particular Custom Attribute of Users

> ### Example:  
> > ### Code Syntax:  
> > ```
> > "sourcePath": "$['urn:sap:cloud:scim:schemas:extension:custom:2.0:User']['attributes'][?(@.name=='customAttribute1')]['value']",
> > 
> > ```

While not a condition itself, this source path expression can be used to retrieve the value of a given custom attribute \(`customAttribute1`\) from the user's data. It works by filtering the `attributes` array to find the attribute with the name `customAttribute1`, and then returns the value of that attribute.



<a name="loiof47bd39ea1ba4cc4ac64fcb0f67b09ef__section_zrv_x3r_dfc"/>

## Assign User to a Group Based on UserName

> ### Example:  
> > ### Code Syntax:  
> > ```
> > {
> > 	"condition": "$.userName =~ /.*explorer.*/",
> > 	"constant": "Explorers",
> > 	"targetPath": "$.groups[0].value"
> > },
> > {
> > 	"condition": "$.userName =~ /.*scifi.*/",
> > 	"constant": "Scientists",
> > 	"targetPath": "$.groups[1].value"
> > }
> > ```

This configuration assigns users to groups based on their `userName`: those with `explorer` in their `userName` are assigned to the `Explorers` group, and those with `scifi` are assigned to the `Scientists` group.

> ### Note:  
> This mapping works for systems that support group assignment via the user entity, for example, Identity Authentication SCIM API version 1. Make sure that the `group ID` in the target system matches the value defined in the constant field \(in this case, `Explorers` and `Scientists`\).

**Related Information**  


[Transformation Types](transformation-types-1a92c56.md "Learn about the types of JSON transformations needed for the provisioning jobs.")

[Transformation Expressions](transformation-expressions-bb8537b.md "")

[Transformation Functions](transformation-functions-0cdac7c.md "")

[Transformation Variables](transformation-variables-8376adb.md "")

[Transformation Examples](transformation-examples-901c759.md "The following examples explain how transformations work.")

[Transformation Editors](transformation-editors-9ea770b.md "Identity Provisioning provides graphical and JSON text editor for managing provisioning system transformations.")

