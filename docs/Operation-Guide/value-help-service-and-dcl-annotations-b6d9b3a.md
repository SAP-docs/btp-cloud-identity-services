<!-- loiob6d9b3a4510d43afa9308e7da9c7147a -->

# Value Help Service and DCL Annotations

Developers can define value selections for authorization policies by querying an OData service for attribute values and labels, which are then displayed in the administration console.

The Authorization Management Service supports value help to help users fill in values for attributes in conditions and restrictions of authorization policies. The values and corresponding labels must be provided by the applications via an OData v4 web service \(see the [OData documentation](https://www.odata.org/documentation/)\). The Authorization Management Service is going to query this web service synchronously when a user opens the value help dialog in the administration console. A sample implementation is available under [sample app](https://github.wdf.sap.corp/CPSecurity/AMS/blob/master/ValueHelp_Conventions.md#example-implementation) \(CAN I LINK TO THE CLIENT LIBRARIES HERE?\).

This sequence demonstrates how a tenant administrator's request for attribute values using value help flows through multiple components and returns with the necessary information to the requesting tenant administrator.

1.  The tenant administrator requests value help from the administration console.

2.  The administration console forwards the value help request to the Authorization Management Service.

3.  The Authorization Management Service forwards the value help requests to the application.

4.  The application responds with the value help information and returns it to the Authorization Management Service.

5.  The Authorization Management Service passes the value help information back to the administration console.

6.  The administration console displays the attribute value information to the tenant administrator.


Use annotations in the schema to describe where to find the values for specific attributes in the service. If no annotations are defined, the Authorization Management Service tries to find a path in the service that matches the attributes name and type.



<a name="loiob6d9b3a4510d43afa9308e7da9c7147a__section_t4h_qbn_qfc"/>

## OData Web Service Implementation

The value help service protocol must implement a RESTful service that supports a subset of OData version 4. The minimal features that are required for the service to work with the Authorization Management Service are entity sets and a working filter implementation for the properties which provide label and value.

This means that you may use a full-fledged OData v4 service, but if you want to implement the bare minimum, you may respond with a list of JSON objects that is wrapped in an object under the `value` property.

> ### Example:  
> Your service is available at `my-server.com/my/service`, and you want to provide a value help list for the attribute called `country`. You must provide a list of entries with the URL `my-server/my/service/country`. It could look as follows:
> 
> > ### Sample Code:  
> > ```
> > {
> >   "value": [
> >     {
> >       "ID": "AD",
> >       "name": "Andorra(AD)"
> >     },
> >     {
> >       "ID": "AE",
> >       "name": "United Arab Emirates(AE)"
> >     },
> >     {
> >       "ID": "AF",
> >       "name": "Afghanistan(AF)"
> >     }
> >   ]
> > }
> > ```
> 
> This is the default behavior. If you choose to change the lookup behavior with annotations, the URL and the property names may look different.

The value help currently supports only a value and a label in the value help dialog. The label is shown to the user. When choosing the entry that displays the label, the corresponding value is selected.



### Prerequisites

-   The value must have a compatible type. For example, if the target attribute is a number, it can be an integer or decimal but not a string or a boolean value.

-   The label must be a string. This string is displayed in the value help dialog as plain text. There is no formatting. No other media types are supported. Depending on the screen size and the type of value help \(single or multi value\), the amount of text that can be shown to the user has different restrictions. We recommend to use a length of about 50 characters for this label to ensure that it shows completely.


You have the following configuration options:

-   Single select value help

-   Multiselect value help




### Authentication

The value help API endpoint in your application must be protected. The Authorization Management Service calls the API with a client certificate and an OAuth token.

Details how the authentication should be validated can be found [here](https://github.wdf.sap.corp/CPSecurity/cas-ams-server/blob/master/doc/ValueHelpCallbackUserAuth.md#authentication) \(LINK POINTS TO AN OUTDATED DOCUMENT. WHICH DOCUMENT SHOULD I LINK? TO [https://github.com/SAP/cloud-identity-developer-guide](https://github.com/SAP/cloud-identity-developer-guide) as central pubic link to client libraries or to the individual libraries: [https://github.wdf.sap.corp/CPSecurity/cloud-authorization-client-library-nodejs](https://github.wdf.sap.corp/CPSecurity/cloud-authorization-client-library-nodejs), [https://github.wdf.sap.corp/CPSecurity/cloud-authorization-client-library-java](https://github.wdf.sap.corp/CPSecurity/cloud-authorization-client-library-java) or [https://github.wdf.sap.corp/CPSecurity/go-ams](https://github.wdf.sap.corp/CPSecurity/go-ams).

> ### Note:  

If your application is deployed on Cloud Foundry, the `.cert` domain should be used for the value help callback URL. Cloud Foundry accepts client certificates only on this domain.



### Multitenancy

The value help callbacks support multitenant scenarios. The OAuth token used to call into your application is issued to the `app_tid` of the tenant that is currently active in the user interface of the Authorization Management Service.

However, the Authorization Management Service currently doesn't support different URLs per tenant. The value help data for all tenants must be made available using the same URL.



<a name="loiob6d9b3a4510d43afa9308e7da9c7147a__section_o31_dlk_5fc"/>

## Configuration of the Authorization Management Service

To enable value help in service instance of the Authorization Management Service, configure the value help callback URL to your OData v4 service in the authorization settings of the service instance configuration parameters.



### Service Instance Configuration

Value help must be enabled on the service instance by configuring the value help callback URL to your OData v4 service. This configuration is part of the other service instance configuration parameters.

> ### Example:  
> > ### Sample Code:  
> > ```
> > {
> >   // ... other configuration
> >   "authorization": {
> >     "enabled": true,
> >     "value_help_url": "https://myapp.cert.cfapps.sap.hana.ondemand.com/odata/v4/ValueHelpService/"
> >   },
> >   // other configuration
> > }
> > ```

The URL gets a postfix with the specific attribute name that is currently requested. For example, if the attribute name is `Country`, the URL `https://myapp.cert.cfapps.sap.hana.ondemand.com/odata/v4/ValueHelpService/Country` is used.



<a name="loiob6d9b3a4510d43afa9308e7da9c7147a__section_jhk_mtk_5fc"/>

## DCL Schema Configuration

After having [enabled value help](value-help-service-and-dcl-annotations-b6d9b3a.md#loiob6d9b3a4510d43afa9308e7da9c7147a__section_o31_dlk_5fc) for your service instance, you can add annotations to the attributes in your DCL schema \(`schema.dcl`\). The user interface only tries to show the value help dialog for the attributes that have an annotation. No annotation means that the value help for this attribute is disabled.



### Attribute Annotations

Each attribute can be annotated with the `@valueHelp` annotation.

The annotations are added to an attribute as an object literal with the name `valueHelp`, and they can contain up to three properties:

-   `path` - \(Optional\) The name of the entity set that provides the list of values

-   `valueField` - \(Optional\). The name of the property \(in the entity of the value help service\) that contains the value

-   `labelField` - \(Optional\) The name of the property \(in the entity of the value help service\) that contains the label that is shown to the user when listing the values


> ### Example:  
> > ### Sample Code:  
> > ```
> > SCHEMA {
> >   salesOrder: {
> >     @valueHelp: {
> >       path: 'sourceCountry', // Values for "salesOrder.SourceCountry" are found in the entity set named "country"
> >       valueField: 'code', // Values should be taken from the field named "code"
> >       labelField: 'Description' // The text shown to the user in the value help dialog comes from the field named "Description"
> >     }
> >     Country: String
> >   }
> > }
> > ```

> ### Restriction:  
> Only strings with quotation marks \(`'`\) are supported. Using double quotes \(`"`\) produces error messages.

All properties in the `@valueHelp{}` annotation are optional. Use them to describe more complex use cases, which can't be implemented using automatic mapping.



### Automatic Mapping

The default mapping goes through the following steps to find a valid entity set for each attribute:

1.  If the attribute name contains a dot, only the last part after the dot is used.

2.  If the service contains an entity set with a name that matches the attribute \(using case-insensitive comparison\), the corresponding entity type is validated. You must define the two properties `ID` and `name`. `ID` is used as the value, and `name` as the label in the list of values.

3.  The `ID` property must have the same type as the property for which you request the value help. For example, a string type, which suggests values for a numeric property can't be used.

4.  The `name` type property must be a string.




### Changing the Target Entity Set

The following example annotation overrides the default mapping. Without the `path` entry, the target entity set would be assumed to be `country` \(or any case-insensitive variation\). By adding the `path` entry, the list of values is taken from `/sourceCountry` of the value help service.

> ### Example:  
> > ### Sample Code:  
> > ```
> > SCHEMA {
> >   salesOrder: {
> >     @valueHelp: {
> >       // Values for "salesOrder.Country" are found in the entity set named "country"
> >       path: 'sourceCountry'
> >     }
> >     Country: String
> >   }
> > }
> > ```
> 
> OData response
> 
> > ### Sample Code:  
> > ```
> > GET
> > https://myapp.cert.cfapps.sap.hana.ondemand.com/odata/v4/ValueHelpService/sourceCountry
> > ```
> 
> > ### Sample Code:  
> > ```
> > {
> >  "value": [
> >    {
> >      "ID": "AD",
> >      "name": "Andorra(AD)"
> >    },
> >    {
> >      "ID": "AE",
> >      "name": "United Arab Emirates(AE)"
> >    },
> >    {
> >      "ID": "AF",
> >      "name": "Afghanistan(AF)"
> >      }
> >    ]
> >  }
> > ```



### Changing the Value Property

The following example shows how to override the field \(property name\) of the entity from which the value is taken. In this case, the automated mapping leads to the value help path being `/country`, and the label being taken from the property `name`. The value is taken from the entity property `code`.

> ### Sample Code:  
> ```
> SCHEMA {
>   department: {
>     @valueHelp: {
>       // Values should be taken from the field named "code"
>       valueField: 'code'
>     }
>     Country: String
>   }
> }
> ```

OData response

> ### Sample Code:  
> ```
> GET https://myapp.cert.cfapps.sap.hana.ondemand.com/odata/v4/ValueHelpService/Country
> ```

> ### Sample Code:  
> ```
> {
>   "value": [
>     {
>       "code": "AD",
>       "name": "Andorra(AD)"
>     },
>     {
>       "code": "AE",
>       "name": "United Arab Emirates(AE)"
>     },
>     {
>       "code": "AF",
>       "name": "Afghanistan(AF)"
>     }
>   ]
> }
> ```



### Changing the Label Source Property

The following example shows how to override the field \(property name\) of the entity from which the label that is shown in the value help dialog is taken. In this case, the automated mapping leads to the value help path being `/country`, and the value being taken from the property `ID`. The label is taken from the entity property `Description`.

> ### Sample Code:  
> ```
> SCHEMA {
>   department: {
>     @valueHelp: {
>       // The text shown to the user in the value help dialog comes from the field named "Description"
>       labelField: 'Description'
>     }
>     Country: String
>   }
> }
> ```

OData response

> ### Sample Code:  
> ```
> GET https://myapp.cert.cfapps.sap.hana.ondemand.com/odata/v4/ValueHelpService/Country
> ```

> ### Sample Code:  
> ```
> {
>   "value": [
>     {
>       "ID": "AD",
>       "Description": "Andorra(AD)"
>     },
>     {
>       "ID": "AE",
>       "Description": "United Arab Emirates(AE)"
>     },
>     {
>       "ID": "AF",
>       "Description": "Afghanistan(AF)"
>     }
>   ]
> }
> ```



### Overriding Everything

The following example shows how to use all available options to override value help behavior. The list of values is requested from `/country` using the content of the `code` property as value and the content of the `Description` property as the label shown in the value help dialog list.

> ### Sample Code:  
> ```
> SCHEMA {
>   salesOrder: {
>     @valueHelp: {
>       // Values for "salesOrder.Country" are found in the entityset named "sourceCountry"
>       path: 'sourceCountry',
>       // Values should be taken from the field named "code"
>       valueField: 'code',
>       // The text shown to the user in the value help dialog comes from the field named "Description"
>       labelField: 'Description'
>     }
>     Country: String
>   }
> }
> ```

OData response

> ### Sample Code:  
> ```
> GET https://myapp.cert.cfapps.sap.hana.ondemand.com/odata/v4/ValueHelpService/sourceCountry
> ```

> ### Sample Code:  
> ```
> {
>   "value": [
>     {
>       "code": "AD",
>       "Description": "Andorra(AD)"
>     },
>     {
>       "code": "AE",
>       "Description": "United Arab Emirates(AE)"
>     },
>     {
>       "code": "AF",
>       "Description": "Afghanistan(AF)"
>     }
>   ]
> }
> ```



### Disabling the Value Help for an Attribute

If no `@valueHelp` annotation is present for an attribute, the value help is disabled for this attribute. Alternatively, you can set the `valueHelp` annotation to `false` to explicitly disable the value help for an attribute.

For attributes with disabled value help, the user interface doesn't show any button or dialog.

> ### Sample Code:  
> ```
> CHEMA {
>   product: {
>     // Disable the value help for "product.Name"
>     @valueHelp: false
>     Name: String
>   }
> }
> ```

When the user interface displays the value help, it goes step by step through the following decision flow before showing the value help dialog. It selects the properties and handles the annotations related to `valueHelp` in a system.

1.  Start: The process begins with property selection.

2.  Annotation check: The first decision point checks if an annotation is present.

    -   No annotation: If no annotation is present, the flow directly leads to the end \(`"Done"`\).

    -   Annotation present: If an annotation is detected, the process continues.


3.  `valueHelp` annotation handling:

    -   `@valueHelp: true` or empty array: Check the `path` property:

        -   If the `path` property is set, use the `path` value from the `@valueHelp` annotation.

        -   If not, use the lowercase version of the last property part as the path.


    -   `@valueHelp: false`: If `@valueHelp` is set to false, the flow terminates \(`"Done"`\).


4.  `ValueField` property check: Assess whether a `valueField` property exists.

    -   Exists: Use the configured value as the property name for the value.

    -   Doesn't exist: Look for the value in the property labeled `ID`.


5.  `LabelField` property check: Determine if a `labelField` property exists.

    -   Exists: Use the configured value as the property name for the label.

    -   Doesn't exist: Look for the label in the property named `name`.


6.  Entity set request: Request the entity set from the application's value help service.

7.  Show *Value Help* dialog: Present the *Value Help* dialog using the previously determined properties as key-value pairs.

8.  End: The flow concludes as `"Done"`.




<a name="loiob6d9b3a4510d43afa9308e7da9c7147a__section_gvg_kyd_wfc"/>

## Value Dependent Filters

Sometimes values depend on other previously selected values. An example for this would be a `city` attribute that depends on a previously selected `country` attribute, where users can only selected cities of a specific country.

Since the value help service must implement a subset of OData version 4, we support this feature by adding filters to the value help request.

Not all attributes are related to others. It would be impractical to send all previously selected values as filters - especially since the filters are part of the URL. Thus large values or lists of values might exceed the length limit for browser URLs. For these reasons, filters are only transmitted if the targeted attribute is annotated with the names of the attributes that should be used as filters.



### Filters as Part of a `@valueHelp` Annotation

> ### Sample Code:  
> ```
> SCHEMA {
>   salesOrder: {
>     @valueHelp: {
>       filters: {
>         'salesOrder.country': 'country',
>         'salesOrder.cost': 'cost'
>       }
>     }
>     city: String
> 
>     /*
>      ...[some other definitions]...  
>     */
> 
>     country: String,
>     cost: Number
>   }
> }
> ```

The name referenced as key in the `filters` property of the `@valueHelp` annotation must be the full DCL name. The name referenced as value in the `filters` property of the `@valueHelp` annotation is the name of the filter used in the request.

Now, whenever the `salesOrder.city` value help is opened, the request contains the values of the referenced attributes. For example, if `salesOrder.country` is set to `us`, the query part of the request to the value help service would contain `$filter=country eq 'us'`.

The values for the filter are taken from the same `RESTRICT` statement.

> ### Note:  

This means that, by default, the input fields are ordered according to dependency. The field, which the other fields are dependent on, comes first. If there are circular dependencies, this is not possible, and the order of the fields is not defined.

This also means that values from other parts of the policy are not taken into consideration.

> ### Sample Code:  
> ```
> POLICY DependentExample01 {
>   USE DependentBase 
>     RESTRICT salesorder.country = 'us'
>     RESTRICT city = '';
> }
> 
> POLICY DependentExample02 {
>   USE DependentBase 
>     RESTRICT salesorder.country = 'us', salesorder.city = '';
> }
> ```

In the first example, the second `RESTRICT`-statement only filters the value help list of the `city` field if a `country` field is added to the second `RESTRICT` statement.

In the second example, the value helps service is called with the URL query `?$filters=country eq 'us`'.



### Filters and Operators

The filters depend on the operators used in the `RESTRICT` statement. In the previous example, the `salesorder.country` field used a `=`-operator. Let's use a different one:

> ### Sample Code:  
> ```
> POLICY DependentExample02 {
>   USE DependentBase 
>     RESTRICT salesorder.cost < 1000, city = '';
> }
> ```

Now, if we open the value help for the `city` field, a filter query for `salesOrder.cost` is generated, in this case `?$filters=cost lt 1000`.

Each DCL operator corresponds to an OData filter operator.

**Filter Operators**


<table>
<tr>
<th valign="top">

DCL Operator

</th>
<th valign="top">

OData Filer Query Operator

</th>
</tr>
<tr>
<td valign="top">

`=` 

</td>
<td valign="top">

`eq [value]` 

</td>
</tr>
<tr>
<td valign="top">

`<>` 

</td>
<td valign="top">

`ne [value]` 

</td>
</tr>
<tr>
<td valign="top">

`>` 

</td>
<td valign="top">

`gt [value]` 

</td>
</tr>
<tr>
<td valign="top">

`>=` 

</td>
<td valign="top">

`ge [value]` 

</td>
</tr>
<tr>
<td valign="top">

`<` 

</td>
<td valign="top">

`lt [value]` 

</td>
</tr>
<tr>
<td valign="top">

`<=` 

</td>
<td valign="top">

`le [value]` 

</td>
</tr>
<tr>
<td valign="top">

`BETWEEN` 

</td>
<td valign="top">

`ge [value1]` and `le [value2]` 

</td>
</tr>
<tr>
<td valign="top">

`NOT BETWEEN` 

</td>
<td valign="top">

`lt [value1]` or `gt [value2]` 

</td>
</tr>
<tr>
<td valign="top">

`IN` 

</td>
<td valign="top">

`in ( [value...] )` 

</td>
</tr>
<tr>
<td valign="top">

`NOT IN` 

</td>
<td valign="top">

`not(in [values...] ))` 

</td>
</tr>
<tr>
<td valign="top">

`IS NULL` 

</td>
<td valign="top">

`eq null` 

</td>
</tr>
<tr>
<td valign="top">

`IS NOT NULL` 

</td>
<td valign="top">

`ne nul`l

</td>
</tr>
<tr>
<td valign="top">

`LIKE` 

</td>
<td valign="top">

`matchesPattern( [field], [value] )` 

</td>
</tr>
<tr>
<td valign="top">

`NOT LIKE` 

</td>
<td valign="top">

`not(matchesPattern( [field], [value] ))` 

</td>
</tr>
<tr>
<td valign="top">

`IS RESTRICTED` 

</td>
<td valign="top">

Not relevant for value help

</td>
</tr>
<tr>
<td valign="top">

`IS NOT RESTRICTED` 

</td>
<td valign="top">

Not relevant for value help

</td>
</tr>
</table>



### Single or Multiple Values \(Lists\)

In a standard case, as described above, a simple `eq` filter is sent as part of the request. If multiple filter attributes are defined, these are combined with AND.



### Empty Selection

If a `filter` attribute is defined, but it doesn't contain a value, no `filter` query is generated for it.



<a name="loiob6d9b3a4510d43afa9308e7da9c7147a__section_t4w_qt3_wfc"/>

## Language Support

To provide localized value lists, the server may respond with different contents of the `label` field based on the `Accept-Language` header. The value in the `ID` field mustn't change depending on the header value.

The value in the `Accept-Language` header is set according to the language of the user interface, which is usually determined from the browser settings.

> ### Example:  
> List of items for `Accept-Language = "en-US"`
> 
> > ### Sample Code:  
> > ```
> > {
> >   "value": [
> >     {
> >       "ID": "0001",
> >       "name": "Some item"
> >     },
> >     {
> >       "ID": "0002",
> >       "name": "Yet another item"
> >     }
> >   ]
> > }
> > ```
> 
> List if items for `Accept-Language = "de-DE"`
> 
> > ### Sample Code:  
> > ```
> > {
> >   "value": [
> >     {
> >       "ID": "0001",
> >       "name": "Irgendein Gegenstand"
> >     },
> >     {
> >       "ID": "0002",
> >       "name": "Noch ein Gegenstand"
> >     }
> >   ]
> > }
> > ```



<a name="loiob6d9b3a4510d43afa9308e7da9c7147a__section_jdz_yt3_wfc"/>

## Example Implementation

See how to set up an example service using Core Data Services \(CDS\) in the LINK value help repository \(POSSIBLY LINK TO CLIENT LIBRARIES\); the annotations are defined in `schema.dcl`.

