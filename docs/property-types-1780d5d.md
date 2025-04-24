<!-- loio1780d5d3f5a14fc1a90946e3aa10fb60 -->

# Property Types

Properties can help you filter which entities and entity attributes are read from the source system or written to the target system. According to their usability, properties can be categorized as follows:



<a name="loio1780d5d3f5a14fc1a90946e3aa10fb60__section_pgk_l1x_1cb"/>

## Standard System Properties

Each source, target, and proxy system support specific types of properties. For example:

**Examples:**


<table>
<tr>
<th valign="top">

AS ABAP System

</th>
<th valign="top">

SAP SuccessFactors

</th>
</tr>
<tr>
<td valign="top">

jco.client.r3name=PSE

jco.destination.peak\_limit=10

jco.destination.pool\_capacity=5

</td>
<td valign="top">

sf.page.size=100

sf.user.filter=firstName John

sf.user.attributes=email

</td>
</tr>
</table>



<a name="loio1780d5d3f5a14fc1a90946e3aa10fb60__section_vb4_nxk_yfb"/>

## Credential Properties

The values of these properties contain sensitive information that must **not** be displayed as plain text. The default credential property name is *Password*, which can represent standard passwords, private keys, or OAuth client secrets. When you add a credential property, its value is displayed as an encrypted string. For better security, the encrypted string is always displayed as 40 characters, no matter how long your password actually is.

> ### Note:  
> Properties whose values contain sensitive information can be added only as *Credential* in the Identity Provisioning UI. The values of these properties are stored as encrypted data. They are excluded from the file during system configuration export.

**Examples:**


<table>
<tr>
<th valign="top">

SAP HANA Database

</th>
<th valign="top">

SSH Server

</th>
</tr>
<tr>
<td valign="top">

hana.jdbc.db.password=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

hana.jdbc.ssh.tunnel.cf.password=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

hana.jdbc.ssh.tunnel.private.key=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

</td>
<td valign="top">

ssh.password=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

ssh.private.key=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

ssh.totp.secret.key=\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

</td>
</tr>
</table>

> ### Note:  
> When you update the URL or the host name of аn existing provisioning system, you must re-enter the values of the configured credential properties. The only exception to this are the credential properties of systems that are created with a connectivity destination.



<a name="loio1780d5d3f5a14fc1a90946e3aa10fb60__section_i3b_f1x_1cb"/>

## Default System Properties

These properties depend on the particular connector type. They exist in the transformations by default. It is possible to delete some of them but this may cause a loss of provisioned data. Example:

**Examples:**


<table>
<tr>
<th valign="top">

LDAP Server

</th>
</tr>
<tr>
<td valign="top">

ldap.group.object.class=groupOfNames

ldap.user.object.class=inetOrgPerson

ldap.attribute.user.mobile=mobile

ldap.group.filter=<empty\>

ldap.user.filter=<empty\>

</td>
</tr>
</table>



<a name="loio1780d5d3f5a14fc1a90946e3aa10fb60__section_m1c_vzw_1cb"/>

## Parameterized System Transformations

They use parameters taken from the system property sets. The parameters consist of a *unique key* and a *value*. Like the standard properties, they can be configured in the system's *Properties* tab, and/or in the system's destination properties \(in the platform cockpit\). When one parameter exists in both property sets, the system properties have priority over the system destination properties. In the system transformations, the parameter is referenced by the unique key surrounded by the percent character \(*%<key\>%*\).

Parameters can be used within almost all JSON value parts in a transformation when the following conditions are fulfilled:

-   The JSON structure is not broken. For more information see, [Introducing JSON](https://www.json.org/json-en.html).

-   The structure of the mapping transformation is not broken. For more information, see [Transformations](transformations-81f5204.md).


During the transformation evaluation, each occurrence of *%<...\>%* is interpreted as a parameter reference and is replaced by the corresponding parameter's value as text literal. If the parameter is missing from the system configuration, that literal is *null*.

The example below shows how the mapping transformations work in case of existing parameter configuration:


<table>
<tr>
<th valign="top" align="center">

**System Properties** 

</th>
<th valign="top" align="center">

**Mapping Transformation** 

</th>
<th valign="top" align="center">

**Evaluated Transformation** 

</th>
</tr>
<tr>
<td valign="top">

`ldap.attribute.user.mail`=`mail`

`ldap.attribute.user.givenName`=`givenName`

`ldap.attribute.user.groups`=`memberOf`

</td>
<td valign="top">

```
{
 "sourcePath": "$.%ldap.attribute.user.mail%[0]",
 "targetPath": "$.emails[0].value",
 "optional": true
},
                                                
{
 "sourcePath": "$.%ldap.attribute.user.givenName%[0]",
 "targetPath": "$.name.givenName",
 "optional": true
},
```



</td>
<td valign="top">

```
{
   "sourcePath": "$.mail[0]",
   "targetPath": "$.emails[0].value",
   "optional": true
},
{
   "sourcePath": "$. givenName[0]",
   "targetPath": "$.name.givenName",
   "optional": true
}

```



</td>
</tr>
</table>

You can add also optional parameters to the system properties configuration. These parameters do not appear by default at system creation and can be added on demand.

The tables below show how a system transformation including an optional parameter is evaluated:

**Evaluation of Mapping Transformation with an Optional Parameter**


<table>
<tr>
<th valign="top" align="center">

**System Properties** 

</th>
<th valign="top" align="center">

**Mapping Transformation** 

</th>
<th valign="top" align="center">

**Evaluated Transformation** 

</th>
</tr>
<tr>
<td valign="top">

`sac.group.prefix`=`SAC_GROUP` 

</td>
<td valign="top">

```
{
   "sourcePath": "$.displayName",
   "targetPath": "$.displayName",
   "functions": [
      {
        "condition": "'%sac.group.prefix%' !== 'null'",
        "function": "concatString",
        "prefix": "%sac.group.prefix%"
      }
   ]
}

```



</td>
<td valign="top">

```
{
   "sourcePath": "$.displayName",
   "targetPath": "$.displayName",
   "functions": [
      {
        "condition": "' SAC_GROUP' !== 'null'",
	   // the condition is true
        "function": "concatString",
        "prefix": "%sac.group.prefix%"
      }
   ]
}

```



</td>
</tr>
<tr>
<td valign="top">

No optional parameter configured

</td>
<td valign="top">

```
{
   "sourcePath": "$.displayName",
   "targetPath": "$.displayName",
   "functions": [
      {
        "condition": "'%sac.group.prefix%' !== 'null'",
        "function": "concatString",
        "prefix": "%sac.group.prefix%"
      }
   ]
}

```



</td>
<td valign="top">

```
{
   "sourcePath": "$.displayName",
   "targetPath": "$.displayName",
   "functions": [
      {
        "condition": "'null' !== 'null'",
	   // the condition is false
        "function": "concatString",
        "prefix": "%sac.group.prefix%"
      }
   ]
}

```



</td>
</tr>
</table>

> ### Note:  
> A possibility for incorrect interpretation of a *%<...\>%* character sequences occurs if a text literal already contains more than one *%* characters itself.

The table below includes an example of incorrect interpretation in case of a missing parameter configuration:


<table>
<tr>
<th valign="top" align="center">

**System Properties** 

</th>
<th valign="top" align="center">

**Mapping Transformation** 

</th>
<th valign="top" align="center">

**Evaluated Transformation** 

</th>
</tr>
<tr>
<td valign="top">

No parameters configured

</td>
<td valign="top">

```
"condition": "$.email =~ /^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+
\\.[a-zA-Z]{2,})$/ || $.ExternalEmail[0] =~ /^([a-zA-Z0-9._%-]+
@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,})$/"
```



</td>
<td valign="top">

```
"condition": "$.email =~ /^([a-zA-Z0-9null-]+
@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,})$/"
```



</td>
</tr>
</table>

Such cases can be avoided by extracting the parts containing *%* into separate parameters in the system configuration, as displayed in the table below:


<table>
<tr>
<th valign="top" align="center">

**System Properties** 

</th>
<th valign="top" align="center">

**Mapping Transformation** 

</th>
</tr>
<tr>
<td valign="top">

*email-regex* = `/^([a-zA-Z0-9._%-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,})$/`

</td>
<td valign="top">

`"condition": "$.email =~ %email-regex% || $.ExternalEmail[0] =~ %email-regex%"`

</td>
</tr>
</table>

Parameter values may contain character sequences matching a parameter reference, but such sequences are not interpreted as parameters themselves. For more information, see the table below:


<table>
<tr>
<th valign="top" align="center">

**System Properties** 

</th>
<th valign="top" align="center">

**Mapping Transformation** 

</th>
<th valign="top" align="center">

**Evaluated Transformation** 

</th>
</tr>
<tr>
<td valign="top">

*parameter-A*=`value-A`

*parameter-B*=`value-B %parameter-A%`

</td>
<td valign="top">

```
"constant": "%parameter-A%", 
 ..
 "constant": "%parameter-B%",
 ..

```



</td>
<td valign="top">

```
"constant": "value-A", 
 ..
"constant": " value-B %parameter-A%",
 ..

```



</td>
</tr>
</table>

> ### Note:  
> Avoid using special regex characters such as `()`, `[]`, `{}`, `.`, `+`, `*`, `?`, `\`, `^`, and `|` within property values. They are evaluated in transformations - specifically in conditions involving regex strings and functions with regex parameters - and may lead to errors. For example, the following configuration will result in an error due to unfulfilled conditions:
> 
> -   *Property*: xsuaa.group.prefix=\[XSUAA\]
> 
> -   *Condition*: \('%xsuaa.group.prefix%' === 'null'\) || \($.displayName =~ /%xsuaa.group.prefix%.\*/\)



<a name="loio1780d5d3f5a14fc1a90946e3aa10fb60__section_mwj_l2z_vtb"/>

## Internal Properties

> ### Note:  
> Identity Provisioning uses internal properties in various cases. Internal properties must not be used by customers.

For example:


<table>
<tr>
<th valign="top">

Property Name

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`destinationName`

</td>
<td valign="top">

The name of the destination created in SAP BTP cockpit.

</td>
</tr>
</table>

**Related Information**  


[List of Properties](list-of-properties-d6f3577.md "On this page you can find all the available properties to use in the Identity Provisioning service. You can filter them by system type name, &quot;All Systems&quot;, by a word or only part of it.")

[Manage Properties](Operation-Guide/manage-properties-4e2bc9d.md "You can add, delete and modify properties for a system in Identity Provisioning.")

