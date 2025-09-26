<!-- loioeee7014e3f7741be8f039dd237a105d7 -->

# Schema Definition

You can define only one schema. It defines the schema elements with data types that are valid for all policy definitions.



To describe the names and types of attributes, you define a schema. You must define a schema in a file called `schema.dcl`. It must be located in the DCL root folder. If attributes are defined In the schema, you can use the grammar elements `WHERE` and `FUNCTION` with these attributes. All usages of schema attributes are validated to refer to existing names and that their respective data types.

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

Elements in the schema can be used in the `WHERE` and `FUNCTION` grammar elements. The usage of all schema elements are validated to make sure that they refer to existing names and that their usage context complies with their type.

```
SCHEMA {
    <schema_element>: <data_type>
}
```

-   The following schema contains schema elements for a attribute of the data type "number" and an attribute name with the data type "string".

    > ### Sample Code:  
    > ```
    > SCHEMA {
    >     salesID: Number,
    >     Country: String
    > }
    > ```

-   The schema must always define all data types of the attribute values. In the following example code, `Sales` is n structure that groups different attributes related to `Sales`.

    > ### Sample Code:  
    > ```
    > SCHEMA {
    >      Sales: {
    >        Country: String,
    >        SalesID: Number}
    >  }
    > ```


Schema elements on the root level can be prefixed with the $ sign. It applies, for example, to attributes from identity providers \(see the related link\). This is currently reserved for internal use only.

There is a predefined default `$user` structure that is populated by the client libraries with OIDC token content in a standard setup.

> ### Sample Code:  
> ```
> SCHEMA {
>     ...
>     $user: { // Default $user definition. This is injected, if no custom $user definition is present
>         user_uuid: String,
>         groups: String[],
>         email: String
>     }
> ```

The `$user` structure can be extended with custom attributes.

**Related Information**  


 <?sap-ot O2O class="- topic/link " href="6652b28c17a04f2e8ac4d412d256d097.xml" text="" desc="" xtrc="link:1" xtrf="file:/home/builder/src/dita-all/wbz1500991557538/loio629f7cb06f6947988dcaf8bedbe45873_en-US/src/content/localization/en-us/eee7014e3f7741be8f039dd237a105d7.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

