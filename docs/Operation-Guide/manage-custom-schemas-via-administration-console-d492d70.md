<!-- loiod492d70e84e248b6b54eeb2dafd7a9f9 -->

# Manage Custom Schemas via Administration Console

You can view and define your custom schema via the administration console for SAP Cloud Identity Services.



## Context

The administration console shows information about all existing schemas, predefined, and custom, in the tenant.

If you need your own custom attributes for users you can define your own custom schema, and once the schema is defined, the custom attributes that it defines can be used.

To be used, the custom attributes must be assigned to the user first. For more information, see [Configuring Attributes Based on Flexible Expressions](configuring-attributes-based-on-flexible-expressions-a2f1e46.md).

> ### Note:  
> When the attributes are assigned to a user, they can be sent to the application. For more information, see [Configuring User Attributes from the Identity Directory](configuring-user-attributes-from-the-identity-directory-d361407.md).

You can define a schema either by importing a JSON file, which must comply with the SCIM standard, or by creating it manually via the administration console.

You can check the available schemas in the tenant, and use one of the predefined schemas. You can also import, or manually create your custom schema. The maxim number of all custom schemas, imported and manually created, per tenant is 20. Each schema can have up to 20 attributes. Each multivalued attribute of type `complex` can have up to 20 subattributes.

You can also download a schema template or any of the already existing schemas. You can use the template to define your own schema extensions.

> ### Caution:  
> The schemas in the administration console are read-only. To edit a custom schema, you must delete it and import a new one with the necessary changes. If you delete a schema this will also delete the attributes and subattributes in this schema and their values, and remove all already assigned attributes to users from this schema.
> 
> You can delete only custom schemas.

> ### Note:  
> For more information about the SCIM Core Schema, see [7. Schema Definition](https://datatracker.ietf.org/doc/html/rfc7643#section-7).



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Schemas* tile.

    This operation opens the *Schemas* page with all the schemas in the tenant, predefined, and custom.

3.  Choose *Actions* button, then choose one of the options:

    -   *Template* - Download a schema template. You can use the template to define your own schema extensions.

        > ### Note:  
        > To download an existing scema, select the schema in the list on the left and choose the *Export* button in the right top corner.

    -   *Import* - Upload the JSON file with your SCIM-compliant schema.

        The following singular and multivalued attributes are defined:

        **Singular Attributes**


        <table>
        <tr>
        <th valign="top">

        Attributes
        
        </th>
        <th valign="top">

        Notes
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        `id`
        
        </td>
        <td valign="top">
        
        Required

        Example: `"id": "urn:sap:cloud:scim:schemas:extension:custom:2.0:MyCustomSchema",`
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `name`
        
        </td>
        <td valign="top">
        
        Optional

        > ### Note:  
        > If present, it’s validated against the `id`, and must match it.

        Example: `"name": "MyCustomSchema",`
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `description`
        
        </td>
        <td valign="top">
        
        Optional

        Example: `"description": "Custom schema description",`
        
        </td>
        </tr>
        </table>
        
        **Multi-Valued Attributes**


        <table>
        <tr>
        <th valign="top">

        Attribute
        
        </th>
        <th valign="top">

        Subattributes
        
        </th>
        <th valign="top">

        Notes
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="13">
        
        `attributes`
        
        </td>
        <td valign="top">
        
         
        
        </td>
        <td valign="top">
        
        Required.

        A set of schema attribute objects which contains the attribute qualifications.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `name`
        
        </td>
        <td valign="top">
        
        Required
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `type`
        
        </td>
        <td valign="top">
        
        Required

        Values: "string", "boolean", "decimal", "integer", "dateTime", "reference", and "complex".

        > ### Remember:  
        > "type=complex" fits only to attribute.
        > 
        > If an attribute is marked as "type=complex" and "multiValued = true" this attribute must have at least one subattribute.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `subAttributes`
        
        </td>
        <td valign="top">
        
        Optional.

        > ### Remember:  
        > Required, when main attribute is of type "complex".

        "subAttributes" has the same schema qualification settings as "attributes".
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `multiValued`
        
        </td>
        <td valign="top">
        
        Required

        Boolean

        > ### Remember:  
        > When attribute is marked as "multiValued=true", the type can only be "complex".
        > 
        > If an attribute is marked as "type=complex" and "multiValued = true" this attribute must have at least one subattribute.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `description`
        
        </td>
        <td valign="top">
        
        Optional
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `required`
        
        </td>
        <td valign="top">
        
        Required

        Boolean
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `canonicalValues`
        
        </td>
        <td valign="top">
        
        Optional

        A set of supported values for the attribute.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `caseExact`
        
        </td>
        <td valign="top">
        
        Required

        Boolean
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `mutability`
        
        </td>
        <td valign="top">
        
        Required

        Values: "readOnly", "readWrite", "immutable", and "writeOnly".
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `returned`
        
        </td>
        <td valign="top">
        
        Required

        Valid key words: "always", "default", "never", and "request".
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `uniqueness`
        
        </td>
        <td valign="top">
        
        Required

        Valid key words: "none", "server", and "global".
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `referenceTypes`
        
        </td>
        <td valign="top">
        
        Optional

        Valid values:

        -   A SCIM resource type \(for example "User" or "Group"\)
        -   "external" - indicating that the resource is an external resource
        -   "uri" - indicating that the reference is to a service endpoint or an identifier


        
        </td>
        </tr>
        </table>
        
    -   *Create* - Manually create a custom schema. Fill in the required information and add the attributes.

        The following singular and multivalued attributes are defined:


        <table>
        <tr>
        <th valign="top">

         
        
        </th>
        <th valign="top">

         
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        Attribute Name
        
        </td>
        <td valign="top">
        
        Provide a name for the attribute. Each attribute must be unique within the schema.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Parent Attribute
        
        </td>
        <td valign="top">
        
        Choose a parent for the attribute from the existing attributes of type complex.

        > ### Note:  
        > A parent attribute is a previously configured "multiValued" attribute of type "complex".


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Type
        
        </td>
        <td valign="top">
        
        Select a value from the drop-down:

        -   "string" \(default value\)
        -   "boolean"
        -   "decimal"
        -   "integer"
        -   "dateTime"
        -   "reference"
        -   "complex"

        > ### Remember:  
        > If an attribute is marked as "Type=complex" and "Multi-Valued = true" this attribute must have at least one subattribute.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Mutable
        
        </td>
        <td valign="top">
        
        Select a value from the drop-down:

        -   "readOnly" \(default value\)
        -   "readWrite"
        -   "immutable"
        -   "writeOnly"


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Returned
        
        </td>
        <td valign="top">
        
        Select a value from the drop-down:

        -   "always" \(default value\)
        -   "default"
        -   "never"
        -   "request"


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Unique
        
        </td>
        <td valign="top">
        
        Select a value from the drop-down:

        -   "none" \(default value\)
        -   "server"
        -   "global"


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Description
        
        </td>
        <td valign="top">
        
        Optional.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Canonical
        
        </td>
        <td valign="top">
        
        Optional.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Required
        
        </td>
        <td valign="top">
        
        Boolean. When checkbox is selected, the value is "true". Default value is "false".
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Case Exact
        
        </td>
        <td valign="top">
        
        Boolean. When checkbox is selected, the value is "true". Default value is "false".
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Multi-Valued
        
        </td>
        <td valign="top">
        
        Boolean. When checkbox is selected, the value is "true". Default value is "false".
        
        </td>
        </tr>
        </table>
        




<a name="loiod492d70e84e248b6b54eeb2dafd7a9f9__result_n52_xfs_1rb"/>

## Results

The newly created schemas appear in the list on the left. The schemas are listed in alphabetical order.

**Related Information**  


[System for Cross-domain Identity Management: Core Schema](https://datatracker.ietf.org/doc/html/rfc7643)

[Attribute Data Types](https://datatracker.ietf.org/doc/html/rfc7643#section-2-3)

[Identity Directory API - Create Users](https://api.sap.com/api/IdDS_SCIM/resource/createUser)

