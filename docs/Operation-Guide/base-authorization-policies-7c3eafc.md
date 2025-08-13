<!-- loio7c3eafc956ae4d89accfe6046c7f927b -->

# Base Authorization Policies

Base authorization policies are delivered with the respective application.



In the administration console, administrators can use them to create their own refined custom authorization policies, which they assign to users. We recommend that application developers define the base policies with the basic authorizations that are required for the specific application. For more information, see [Configuring Authorization Policies](configuring-authorization-policies-982ac5f.md).

You can define an authorization policy as a base authorization policy by using the `DEFAULT` element.

> ### Sample Code:  
> ```sql
> DEFAULT POLICY baseSalesOrders {
>     GRANT read ON SalesOrders, SalesOrderItems WHERE salesGroup IN $user.groups
> }
> ```

The `baseSalesOrders` base policy can't be assigned to a user because it's automatically evaluated by the runtime. If the policy is a tenant-specific policy \(for administrators\), the runtime automatically evaluates this policy but only for this specific tenant.

> ### Note:  
> Currently, the administration console doesn't support the creation of tenant-specific base policies.

