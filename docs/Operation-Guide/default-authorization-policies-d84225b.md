<!-- loiod84225b0732f4ad9a9fee588ecdf5583 -->

# Default Authorization Policies

Default authorization policies are special base policies applied at runtime without an explicit assignment to a user. They needn't be passed to the DCN runtime explicitly, similar to internal polices.



Both default and internal policies are special cases of base authorization policies. Base policies are all policies that are defined by the developers of the application and deployed together with the application. They exist in all tenants. However, custom policies are created specifically for a customer by administrators. Custom policies only exist in the customer's SAP Cloud Identity Services tenants.

You can define an authorization policy as a default authorization policy by using the `DEFAULT` element.

> ### Sample Code:  
> ```sql
> DEFAULT POLICY defaultSalesOrders {
>     GRANT read ON SalesOrders, SalesOrderItems WHERE salesGroup IN $user.groups
> }
> ```

The `defaultSalesOrders` default policy can't be assigned to a user because it's automatically evaluated by the runtime.

