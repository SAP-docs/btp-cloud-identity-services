<!-- loioeee7014e3f7741be8f039dd237a105d7 -->

# Schema Definition

A schema defines attribute names and data types that can be used when defining an authorization policy.



To describe the names and types of attributes, you define a schema. You must define a schema in a file called `schema.dcl`. It must be located in the DCL root folder. If attributes are defined in the schema, you can use the grammar element `WHERE` with these attributes. All usages of schema attributes are validated to refer to existing names and that their usage context complies with the respective data types.

> ### Output Code:  
> ```
> ├─ <application>
> └─ ams-policies-deployer
>     ├─ package.json
>     └─ dcl
>         ├─ sales
>         │  └─ policy_a.dcl
>         │  └─ policy_b.dcl
>         └─ schema.dcl
> ```

Attributes in the schema can be used in the `WHERE` grammar element. The usage of all attributes are validated to make sure that they refer to existing names and that their usage context complies with their type.

```
SCHEMA {
    <attribute>: <data_type>
}
```

Data types for attribute values include String, Number, Boolean, and Structure, with options for arrays.

Use the following data types:

-   String, String\[\]

-   Number, Number\[\]

-   Boolean, Boolean\[\]

-   Structured type


You can also assign a special null value to an attribute.

A structured type allows specifying hierarchical types.

-   The following schema contains an attribute with the data type "number" and an attribute name with the data type "string".

    > ### Sample Code:  
    > ```
    > SCHEMA {
    >     salesID: Number,
    >     Country: String
    > }
    > ```

-   The schema must always define all data types of the attribute values. In the following example code, `Sales` is a structure that groups different attributes related to `Sales`.

    > ### Sample Code:  
    > ```
    > SCHEMA {
    >      Sales: {
    >        Country: String,
    >        SalesID: Number}
    >  }
    > ```


There is a predefined default `$user` structure that is populated by the client libraries with OIDC token content in a standard setup.

> ### Sample Code:  
> ```
> SCHEMA {
>     ...
>     $user: { // Default $user definition. This is injected if no custom $user definition is present
>         user_uuid: String,
>         scim_id: String,
>         groups: String[],
>         email: String
>     }
> ```

The `$user` structure can be extended with custom attributes.

**Related Information**  


[Formats](formats-e09dbb5.md "Here you find rules for creating valid identifiers in DCL, such as how to quote and how to separate packages. Identifiers are basically similar to Java identifiers.")

