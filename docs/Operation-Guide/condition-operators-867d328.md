<!-- loio867d3284cb41469bbcd6ed695ce24032 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Condition Operators

Condition operators provide a set of tools for evaluating data, including equality, range, and pattern matching.



**Condition Operators**


<table>
<tr>
<th valign="top">

Operators

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`=` 

</td>
<td valign="top">

Equal

</td>
</tr>
<tr>
<td valign="top">

`<` 

</td>
<td valign="top">

Less than

</td>
</tr>
<tr>
<td valign="top">

`>` 

</td>
<td valign="top">

Greater than

</td>
</tr>
<tr>
<td valign="top">

`<=` 

</td>
<td valign="top">

Less than or equal

</td>
</tr>
<tr>
<td valign="top">

`>=` 

</td>
<td valign="top">

Greater than or equal

</td>
</tr>
<tr>
<td valign="top">

`<>` 

</td>
<td valign="top">

Not equal

</td>
</tr>
<tr>
<td valign="top">

`IN` 

</td>
<td valign="top">

To specify multiple possible values

</td>
</tr>
<tr>
<td valign="top">

`BETWEEN` lower `AND` upper

</td>
<td valign="top">

Between a certain range, including upper and lower

</td>
</tr>
<tr>
<td valign="top">

`LIKE` pattern

</td>
<td valign="top">

Search for a string pattern \(`%` any number of characters, `_` any single character\)

</td>
</tr>
<tr>
<td valign="top">

`LIKE` pattern

`ESCAPE` escape-char

</td>
<td valign="top">

Allows searching for `%` and `_` if they are prefixed and `escape-char.escape-char` is a string constant with exactly one character.

</td>
</tr>
<tr>
<td valign="top">

`NOT IN` 

</td>
<td valign="top">

To specify multiple values which are not possible

</td>
</tr>
<tr>
<td valign="top">

`NOT BETWEEN` 

</td>
<td valign="top">

Values, which aren't within a certain range

</td>
</tr>
<tr>
<td valign="top">

`NOT LIKE` 

</td>
<td valign="top">

Values, which don't match the pattern

</td>
</tr>
</table>



<a name="loio867d3284cb41469bbcd6ed695ce24032__section_e22_ghn_xfc"/>

## LIKE Operators

The `LIKE` operator matches a given value with a pattern. This pattern can contain `%` for a sequence of 0 to n arbitrary characters and `_` for exactly one character.

The escape clause allows specifying a single character, that escapes the pattern characters and hereby allows searching for this character in the input.

**LIKE Operators**


<table>
<tr>
<th valign="top">

Pattern

</th>
<th valign="top">

Escape

</th>
<th valign="top">

Input

</th>
<th valign="top">

Matches

</th>
<th valign="top">

Comment

</th>
</tr>
<tr>
<td valign="top">

`'AB'` 

</td>
<td valign="top">



</td>
<td valign="top">

`'AB'`

`'ABC'`

</td>
<td valign="top">

true

false

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

`'AB%'` 

</td>
<td valign="top">



</td>
<td valign="top">

`'AB'`

`'ABC'`

`'XABC'`

</td>
<td valign="top">

true

true

false

</td>
<td valign="top">

Implements "Starts with"

</td>
</tr>
<tr>
<td valign="top">

`'%AB'` 

</td>
<td valign="top">



</td>
<td valign="top">

`'AB'`

`'ABC'`

`'XAB'`

</td>
<td valign="top">

true

false

true

</td>
<td valign="top">

Implements "Ends with"

</td>
</tr>
<tr>
<td valign="top">

`'%AB%'` 

</td>
<td valign="top">



</td>
<td valign="top">

`'AB'`

`'ABCD'`

`'XABC'`

`'A-B'`

</td>
<td valign="top">

true

true

true

false

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

`'_'` 

</td>
<td valign="top">



</td>
<td valign="top">

`'AB'`

`'ABC'`

</td>
<td valign="top">

false

false

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

`'AB'` 

</td>
<td valign="top">

`'!'` 

</td>
<td valign="top">

'AB'

'ABCD'

</td>
<td valign="top">

true

false

</td>
<td valign="top">

Same as if no pattern were specified

</td>
</tr>
<tr>
<td valign="top">

`'AB!%'` 

</td>
<td valign="top">

`'!'` 

</td>
<td valign="top">

`'AB'`

`'ABC'`

`'AB%'`

</td>
<td valign="top">

false

false

true

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

'A!B'

</td>
<td valign="top">

`'!'` 

</td>
<td valign="top">

`'AB'`

`'A!B'`

</td>
<td valign="top">

false

true

</td>
<td valign="top">

Current implementation:

Cross-check with SQL standard

</td>
</tr>
<tr>
<td valign="top">

`'%%AB'` 

</td>
<td valign="top">

`'%'` 

</td>
<td valign="top">

`'AB'`

`'XAB'`

`'%AB'`

</td>
<td valign="top">

false

false

false

</td>
<td valign="top">

Current implementation:

Crosscheck with SQL standard

</td>
</tr>
</table>



<a name="loio867d3284cb41469bbcd6ed695ce24032__section_glj_lhn_xfc"/>

## Compatibility of Operators and Data Types

Some combinations of operators and data types aren't allowed in DCL as shown in the table below. The compiler enforces these rules.

**Compatibility of Operators and Data Types**


<table>
<tr>
<th valign="top">

Operator

</th>
<th valign="top">

String

</th>
<th valign="top">

Number

</th>
<th valign="top">

Boolean

</th>
<th valign="top">

Array \(String\[\], Number\[\], Boolean\[\]\)

</th>
<th valign="top">

Structure

</th>
</tr>
<tr>
<td valign="top">

`a = b` 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
</tr>
<tr>
<td valign="top">

`a < b` 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
</tr>
<tr>
<td valign="top">

`a > b` 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
</tr>
<tr>
<td valign="top">

`a <= b` 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
</tr>
<tr>
<td valign="top">

`a >= b` 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
</tr>
<tr>
<td valign="top">

`a <> b` 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
</tr>
<tr>
<td valign="top">

`a [NOT] IN b` 

</td>
<td valign="top">

:heavy_check_mark:\(for `a`\)

</td>
<td valign="top">

:heavy_check_mark:\(for `a`\)

</td>
<td valign="top">

:heavy_check_mark:\(for `a`\)

</td>
<td valign="top">

:heavy_check_mark:\(for `b`\)

</td>
<td valign="top">

:x: 

</td>
</tr>
<tr>
<td valign="top">

`a [NOT] BETWEEN b AND a` 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:x: 

</td>
</tr>
<tr>
<td valign="top">

`a [NOT] LIKE` pattern

</td>
<td valign="top">

:heavy_check_mark: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:x: 

</td>
<td valign="top">

:x: 

</td>
</tr>
</table>

