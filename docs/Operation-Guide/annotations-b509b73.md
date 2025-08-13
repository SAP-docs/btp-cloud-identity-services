<!-- loiob509b73f65c1426d846ce9215c0a09c0 -->

# Annotations

Use annotations, for example, to insert a description of the authorization policy.



## @description

Use a `@description` annotation to define a description of the policy.

```sql
@description: '<policy_description'
POLICY <policy_name> {
    GRANT <action> ON <resource1>, <resource2> WHERE <attribute_name> = '<attribute_value>'
}
```

-   > ### Sample Code:  
    > ```sql
    > @description: 'Policy for reading sales orders for USA'
    > POLICY salesOrders {
    >     GRANT read ON salesGroup, salesGroupItems WHERE Country = 'US'
    > }
    > ```




<a name="loiob509b73f65c1426d846ce9215c0a09c0__section_sqr_bsz_pfc"/>

## @label

Use this annotation to define a policy display name that can be changed by the customer.

> ### Sample Code:  
> ```sql
> @label: 'Sales Order Policy'
> POLICY salesOrders {
>     GRANT read ON salesOrders, salesOrderItems WHERE Country = 'US'
> }
> ```



<a name="loiob509b73f65c1426d846ce9215c0a09c0__section_c1h_tsz_pfc"/>

## @valueHelp

You can apply the annotation to schema attributes. For more information, see [Schema Definition](schema-definition-eee7014.md).

The @valueHelp annotation can be used in two modes:

1.  Disable value help with `@valueHelp: false`

2.  Specify `valueHelp` parameters with the following annotation:


> ### Sample Code:  
> ```sql
> @valueHelp: {
>     path: <string constant>,
>     valueField: <string constant>,
>     labelField: <string constant>,
>     filters: <structure>
> }
> ```

The fields `path`, `valueField`, `labelField`, and `filters` are optional. They check whether the values have a correct data type. Additional fields are not permitted.

The full feature description for value help is located here [Value Help Service and DCL Annotations](value-help-service-and-dcl-annotations-b6d9b3a.md).

