<!-- loioafc915f14bc64807ba6727b91482c699 -->

# Structure of the Data Control Language \(DCL\)

Use DCL syntax to define authorization policies, including rules, actions, resources, conditions, attributes, and a schema. They are essential for controlling access to data and resources.



The data control language uses the following syntax for the definition of simple and instance-based authorizations.

![](images/DCL_Elements_Overview_c2281a6.png)



<a name="loioafc915f14bc64807ba6727b91482c699__section_dnz_3cl_fpb"/>

## Authorization Policy

Collection of rules. Administrators can use base authorization policies to create custom authorization policies, change the rules, and assign the policies to users.



<a name="loioafc915f14bc64807ba6727b91482c699__section_zgr_lcl_fpb"/>

## Rule

Grants actions such as `read` or `write`. Rules handle actions on resources on resources such as `resource1` or `resource2`. A rule can also be restricted in multiple ways.

An action is granted on a resource. Use the following syntax:

```sql
GRANT <action> ON <resource> ;
```

-   > ### Sample Code:  
    > ```sql
    > GRANT read ON * ;
    > ```




<a name="loioafc915f14bc64807ba6727b91482c699__section_xkt_lcl_fpb"/>

## Resource

Entities protected by the rule or authorization policy. The application that provides the authorization policy defines the resource. Examples for resources are a data object or an endpoint. A resource has arbitrary attributes that can be used to refine rules.



<a name="loioafc915f14bc64807ba6727b91482c699__section_cst_lcl_fpb"/>

## Condition

A logical expression that is mainly used for filtering. It can be based on attributes with a name and a data type. Before allowing a granted action on a specific entity of a resource, the condition is evaluated with the attribute values of that entity. A condition is a Boolean function over attributes.

```sql
WHERE <attribute_name> = '<attribute_value>' ;
```

-   > ### Sample Code:  
    > `WHERE Country IN ('USA', 'Germany');`


For more information, see [Condition Operators](condition-operators-867d328.md).



<a name="loioafc915f14bc64807ba6727b91482c699__section_shs_rxb_xpb"/>

## Attribute

You can restrict authorization policies by using a set of conditions with attributes and attribute values. Attributes are defined in a schema or they're provided by an external source, for example an identity provider. When using attributes, you must take care that you declare their data type in a schema. All schema attributes usages are validated to refer to existing names and their usage types.

For more information, see [Attribute Constraints](attribute-constraints-5810179.md).



<a name="loioafc915f14bc64807ba6727b91482c699__section_dh2_3zb_hpb"/>

## Schema

A schema defines names and types of attributes you want to use for the application. Only one schema can be defined. Define the schema using a file named `schema.dcl` and locate it in the root folder. All schema attributes usages are validated to refer to existing names and their types.

For more information, see [Schema Definition](schema-definition-eee7014.md).



<a name="loioafc915f14bc64807ba6727b91482c699__section_o4q_dmn_kpb"/>

## Package

The name of the root folder where the DCL files are located. The package content comprises all of the DCL files in the folder.

For more information, see [Package Definition](package-definition-c0df43e.md).

**Related Information**  


[Grammar and Syntax Rules](grammar-and-syntax-rules-7b50037.md "DCL has a set of grammar and syntax rules you must observe when you define authorization policies.")

[Advanced Features](advanced-features-779bfd2.md "You find advanced configuration techniques for authorization policies, focusing on annotations, formatting conventions, and internal functions for enterprise-grade authorization policies.")

