<!-- loioe09dbb57263442f5a34ab507f38d8296 -->

# Formats

Here you find rules for creating valid identifiers in DCL, such as how to quote and how to separate packages. Identifiers are basically similar to Java identifiers.



## Identifier Format

1.  An unquoted identifier must begin with a Unicode character

    -   Uppercase letter

    -   Lowercase letter

    -   Title case letter

    -   Modifier letter

    -   Other letter

    -   Letter number

    -   Currency symbol

    -   Connector punctuation


2.  Next, you can use the following characters.

    -   A start character from above

    -   Digit



> ### Note:  
> Don't use the following characters.

-   Surrogate

-   Formatting character

-   Modifier symbol

-   Modifier letter


Identifiers are basically similar to Java identifiers.

> ### Example:  
> `µSeconds`, `PublicTransport`

An identifier can be enclosed by the double quotes \(`" ... "`\). This is required if a DCL keyword like `POLICY` is used.

A quoted identifier can contain any character that isn't a surrogate.

> ### Example:  
> `/value$to`

In a quoted identifier, the character `"` \(double quote\) must be escaped. See [escaping rules](formats-e09dbb5.md#loioe09dbb57263442f5a34ab507f38d8296__section_j1b_l3m_xfc).

Identifiers are case-sensitive. For example, `CUSTOMER` and `Customer` are not the same identifiers.

An unquoted identifier is equal to the same text in double quotes.



<a name="loioe09dbb57263442f5a34ab507f38d8296__section_gz2_f3m_xfc"/>

## String Constant Format

A string constant must begin and end with a single quote \(`'`\).



<a name="loioe09dbb57263442f5a34ab507f38d8296__section_gtt_33m_xfc"/>

## Keywords

> ### Note:  
> Keywords are case insensitive. This means that `KEYWORD`, `keyword`, `Keyword`, or `KeyWoRd` are all valid notations for the same.



<a name="loioe09dbb57263442f5a34ab507f38d8296__section_j1b_l3m_xfc"/>

## Escaping Rules

The following escape sequences are defined within string constants and quoted identifiers.

**Escaping Rules**


<table>
<tr>
<th valign="top">

Sequence

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`\"` 

</td>
<td valign="top">

`"` 

</td>
</tr>
<tr>
<td valign="top">

`\\` 

</td>
<td valign="top">

`\` 

</td>
</tr>
<tr>
<td valign="top">

`\t` 

</td>
<td valign="top">

Tabulator

</td>
</tr>
<tr>
<td valign="top">

`\uHHHH` 

</td>
<td valign="top">

Unicode `HHHH` 

</td>
</tr>
<tr>
<td valign="top">

`\n` 

</td>
<td valign="top">

New line

</td>
</tr>
<tr>
<td valign="top">

`\r` 

</td>
<td valign="top">

Carriage return

</td>
</tr>
<tr>
<td valign="top">

`\f` 

</td>
<td valign="top">

Form feed

</td>
</tr>
<tr>
<td valign="top">

`\b` 

</td>
<td valign="top">

Backspace

</td>
</tr>
<tr>
<td valign="top">

`\/` 

</td>
<td valign="top">

`/` \(compliance for JSON\)

</td>
</tr>
</table>



<a name="loioe09dbb57263442f5a34ab507f38d8296__section_xzy_n3m_xfc"/>

## Hints for Tools to Generate DCL

-   Avoid generating an unquoted identifier format. Always use double-quoted strings and escape at least the characters `"` \(double quote\) and `\` \(backspace\).

-   When generating string constants, escape at least the characters `'` \(single quote\) and `\` \(backspace\).

-   It's not necessary to quote package qualifiers like `a.b.c.d` because a package name mustn't contain special characters. However, package segments can be quoted, for example `"a"."b"."c"."d"."Policy Name"` is equal to `a.b.c.d."Policy Name"` in a DCL source file.


