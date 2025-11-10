<!-- loio27ad9a4295ef4c03a98b8e05d651f12b -->

# Authorization Policy Definition

You can grant basic actions like `read` or `write` on resources with an SQL-like syntax. The authorizations are grouped under an authorization policy. You can also combine authorization policies.



You define basic actions in applications. Application developers must make sure that the applications query the actions and resources that are defined in the DCL files. Applications can use actions and resources in the code for authorization checks.

The syntax of an authorization for granting actions looks like this:

```sql
POLICY <policy_name> {
    GRANT <action> ON <resource> ;
}
```



### Examples

-   A simple policy that enables the user to perform a `read` action on all resources.

    > ### Sample Code:  
    > ```sql
    > POLICY readAll {
    >     GRANT read ON * ;
    > }
    > ```

-   A simple policy that enables the user to perform `read` and `write` actions on all resources.

    > ### Sample Code:  
    > ```sql
    > POLICY readAndWriteAll {
    >     GRANT read, write ON * ;
    > }
    > ```

-   A simple policy, which restricts all resources only on defined attribute values without any action. Use the `WHERE` condition to refer to attributes.

    > ### Sample Code:  
    > ```sql
    > POLICY CountryCode {
    >     GRANT * ON * WHERE Country = 'US' OR Country = 'DE';
    > }
    > ```

-   A rule that allows the user to do action `read` on all resources with an special attribute value. Use `WHERE` to implement a condition that restricts a `read` action on resources by attributes. You can also use multiple conditions on resources, for example according to a list of attribute values, a range of numbers, or a part of a name.

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read ON * WHERE Country = 'US';
    > }
    > ```

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read ON * WHERE Country IN ('US','DE','FR');
    > }
    > ```

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read ON * WHERE Country = 'DE' AND SalesID BETWEEN 100 AND 200;
    > }
    > ```

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read ON SalesOrders WHERE Name LIKE 'Winter%'
    > }
    > ```

-   This is a policy that allows all actions with restriction on special resources. Asterisk \(`*`\) means that all actions are granted. No attribute conditions restrict the policy.

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT * ON SalesOrders;
    > }
    > ```

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT * ON SalesOrders, SalesOrderItems, SalesOrderLists;
    > }
    > ```

-   A policy with actions on special resources where additionally attribute values restrict the user authorization.

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read, activate ON SalesOrders WHERE SalesOrders.Country = 'US' 
    >                                           AND SalesOrders.SalesID BETWEEN 100 AND 300;
    > }
    > ```

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read, activate ON SalesOrders, SalesOrderItems WHERE SalesOrders.Country = 'US' 
    >                                                            AND SalesOrders.SalesID BETWEEN 100 AND 300 
    >                                                            AND SalesOrderItems.Country = 'US' 
    >                                                            AND SalesOrderItems.SalesID BETWEEN 100 AND 200;
    > }
    > ```

-   Maybe if all attributes are related to all resources, you can keep the code short by entering only attributes with values which then relates to all resources.

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read, activate ON SalesOrders, SalesOrderItems WHERE Country = 'US' 
    >                                                            AND SalesID BETWEEN 100 AND 300;
    > }
    > ```

-   A policy with multiple rules.

    > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read ON * WHERE Country = 'US' AND SalesID BETWEEN 100 AND 200;
    >     GRANT write ON * WHERE Country = 'DE' AND SalesID BETWEEN 100 AND 200;
    > }
    > ```




You can create a policy with actions and restrict it to defined resources. Here you use `WHERE` with multiple conditions.

```sql
POLICY <policy_name> {
    GRANT <action1>, <action2> ON <resource> WHERE <attribute_name> = '<attribute_value>' 
                                         AND <attribute_name> BETWEEN <number> AND <number>;
}
```

-   > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read, activate ON salesGroup WHERE salesGroup.Country = 'US' 
    >                                          AND salesGroup.SalesID BETWEEN 100 AND 300;
    >                                          }
    > ```

-   > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read, activate ON salesGroup, salesGroupItems WHERE salesGroup.Country = 'US' 
    >                                                           AND salesGroup.SalesID BETWEEN 100 AND 300 
    >                                                           AND salesGroupItems.Country = 'US' 
    >                                                           AND salesGroupItems.SalesID BETWEEN 100 AND 200;
    >                                                           }
    > ```

-   > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read, activate ON salesGroup, salesGroupItems WHERE Country = 'US' 
    >                                                           AND SalesID BETWEEN 100 AND 300;
    > }
    > ```




### 



You can also create a policy with multiple actions on the same resources depending on different conditions with attribute values.

```sql
POLICY <policy_name> {
    GRANT <action1> ON <resource> WHERE <attribute1> = '<attribute_value1>' AND <attribute2> BETWEEN <number1> AND <number2>;
    GRANT <action2> ON <resource> WHERE <attribute1> = '<attribute_value2>' AND <attribute2> BETWEEN <number1> AND <number2>;
}
```

-   > ### Sample Code:  
    > ```sql
    > POLICY salesOrders {
    >     GRANT read ON * WHERE Country = 'US' AND SalesID BETWEEN 100 AND 200;
    >     GRANT write ON * WHERE Country = 'DE' AND SalesID BETWEEN 100 AND 200;
    >     }
    > ```




<a name="loio27ad9a4295ef4c03a98b8e05d651f12b__section_cpz_4zg_4fc"/>

## Combining Authorization Policies

To combine multiple authorization policies, define a new policy, which includes already existing policies by `USE`.

```sql
POLICY <policy_name> {
    USE <policy_name1>;
    USE <policy_name2>;
}
```

-   > ### Sample Code:  
    > ```sql
    > POLICY allAdmins {
    >     USE salesOrders;
    >     USE readAll;
    >     }
    > ```

-   You can give this new compound policy its own rules.

    > ### Sample Code:  
    > ```sql
    > POLICY allAdmins {
    >     USE salesOrders;
    >     USE readAll;
    >     GRANT write ON salesOrders WHERE Country IN ('US', 'DE);
    >     }
    > ```


The `RESTRICT` clause allows you to narrow down the scope of an authorization policy. It enforces that an operation is permitted only when certain attribute-based conditions are true.

> ### Sample Code:  
> ```
> POLICY "SalesICADelUpdAdmins" {
>    USE users.DELETE_USERS
>       RESTRICT
>          user.costCenter = 'SalesICA'
> 
>    USE users.UPDATE_USERS
>       RESTRICT
>          user.costCenter = 'SalesICA'
> ;
> }
> ```



### Combination Algorithms

The combination algorithms for policies, rules, and the list entries for actions and resources are fixed.

**Combination Algorithms**


<table>
<tr>
<th valign="top">

Syntax Element

</th>
<th valign="top">

Combination Algorithm

</th>
</tr>
<tr>
<td valign="top">

Policy

</td>
<td valign="top">

Always `OR` 

</td>
</tr>
<tr>
<td valign="top">

Rule

</td>
<td valign="top">

`OR` 

</td>
</tr>
<tr>
<td valign="top">

Action

</td>
<td valign="top">

`OR` 

</td>
</tr>
<tr>
<td valign="top">

Resource

</td>
<td valign="top">

`OR` 

</td>
</tr>
</table>

