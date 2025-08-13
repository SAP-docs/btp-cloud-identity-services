<!-- loio2fad2acffd3c4bf39ef9ff649461b92a -->

# Input Parameters for Authorization Policies

In authorization policies, you define rules with conditions using attribute constraints like `IS RESTRICTED` and `IS NOT RESTRICTED`, allowing for flexible user permissions based on attributes while restricting actions and resources.



In an authorization policy, you can define rules with conditions that contain the attribute constraint `IS NOT RESTRICTED`. If you assign such a policy to a user, it means that this user is fully authorized based on the attributes. Only the actions and resources are restricted.

In contrast, a condition containing the attribute constraint `IS RESTRICTED` means that this user's attribute-based authorization is restricted. This condition can be refined in a `USE` clause.

See the difference between `IS RESTRICTED` and `IS NOT RESTRICTED` in the example below. It shows how user authorizations only differ if no condition is given. In that case, `IS RESTRICTED` defaults to false, and `IS NOT RESTRICTED` defaults to true. However, if a condition is given \(`CountryCode = 'IT'` in the example below\), the behavior is the same.

> ### Example:  
> > ### Sample Code:  
> > ```
> > POLICY readAll {
> >     GRANT read ON * WHERE CountryCode IS RESTRICTED;
> >     GRANT write ON * WHERE CountryCode IS NOT RESTRICTED;
> > }
> > 
> > POLICY readAllNoCondition {
> >     USE readAll; 
> > }
> > 
> > POLICY readAllItaly {
> >     USE readAll RESTRICT CountryCode = 'IT';
> > }
> > 
> > TEST readAll {
> >     // Policy assigned directly
> >     EXPECT DENY FOR read ON * POLICY readAll; // If the policy is assigned directly, IS RESTRICTED evaluates to false
> >     EXPECT GRANT FOR write ON * POLICY readAll; // If the policy is assigned directly, IS NOT RESTRICTED evaluates to true
> > 
> >     // Policy USEd, but no condition for CountryCode is given
> >     EXPECT DENY FOR read ON * POLICY readAllNoCondition; // If the policy is USEd, but no condition for CountryCode is given, IS RESTRICTED evaluates to false
> >     EXPECT GRANT FOR write ON * POLICY readAllNoCondition; // If the policy is USEd, but no condition for CountryCode is given, IS NOT RESTRICTED evaluates to true
> >     
> >     // Policy USEd, and a condition for CountryCode is given
> >     EXPECT GRANT FOR read, write ON * POLICY readAllItaly INPUT {CountryCode: 'IT'}; // If the policy is USEd and a condition for CountryCode is given, both IS RESTRICTED and IS NOT RESTRICTED behave the same way
> >     EXPECT DENY FOR read, write ON * POLICY readAllItaly INPUT {CountryCode: 'DE'} // The same applies if the condition is not met
> > }
> > ```

In the example below, the user is assigned to the `salesOrders` policy and is thus allowed to read all `SalesOrders`.

> ### Example:  
> > ### Sample Code:  
> > ```
> > POLICY salesOrders {
> >     GRANT read ON SalesOrders WHERE ( Country IS NOT RESTRICTED AND SalesID IS NOT RESTRICTED )
> >                                  OR ( Country IS NOT RESTRICTED AND Name IS NOT RESTRICTED);
> > }
> > ```

With the assignment to the `salesOrdersWinter` policy, users can read all `SalesOrders`, which include the string '`Winter`' in their name.

> ### Example:  
> > ### Sample Code:  
> > ```
> > POLICY salesOrdersWinter {
> >     GRANT read ON SalesOrders WHERE ( Country IS NOT RESTRICTED
> >                                       AND SalesID IS NOT RESTRICTED AND Name IS NOT RESTRICTED )
> >                                  OR ( Country IS NOT RESTRICTED AND Name LIKE '%Winter%' );
> > }
> > ```

These policy parameters can be filled while another policy is used. Here, the assignment of `use_salesOrders` allows users to read `salesOrders` in the countries DE, FR, or IT and with `SalesID` `200`, or read `salesOrders` in the countries DE, FR, or IT and with a name that contains the string '`Winter`'.

> ### Example:  
> > ### Sample Code:  
> > ```
> > POLICY use_salesOrders {
> >     USE salesOrders RESTRICT Country IN ('DE','FR','IT'), SalesID = 200, Name LIKE '%WINTER%';
> > }
> > ```

You can repeat the `RESTRICT` section of a policy multiple times and thus define a list of tuples.

> ### Example:  
> > ### Sample Code:  
> > ```
> > POLICY salesOrders{
> >     GRANT read ON SalesOrders WHERE Country IS NOT RESTRICTED AND SalesID IS NOT RESTRICTED ;
> > }
> > 
> > POLICY use_salesOrders {
> >     USE salesOrders RESTRICT Country = 'DE', SalesID = 300
> >                     RESTRICT Country = 'FR', SalesID = 200
> >                     RESTRICT Country = 'IT', SalesID = 100;
> > }
> > ```

The previous definition is not equivalent to the following since it allows any combination of `Country` and `SalesID` \(9 combinations in contrast to 3 combinations\).

> ### Example:  
> > ### Sample Code:  
> > ```
> > POLICY use_salesOrders {
> >     USE salesOrders RESTRICT Country IN ('DE','FR','IT'), SalesID IN (300,200,100);
> > }
> > ```

The `WHERE` clause is deprecated for `USE` statements. It's going to be removed.

The `WHERE` fragment isn't equivalent to the `RESTRICT` section in a `USE` statement. The following `POLICY SamplePolicy1` can't be used with a `WHERE` clause.

> ### Example:  
> > ### Sample Code:  
> > ```
> > POLICY SamplePolicy1 {
> >     GRANT read ON SalesOrders WHERE Country IS RESTRICTED;
> > }
> > 
> > POLICY use_SamplePolicy_Works {
> >     USE SamplePolicy1 RESTRICT Country IN ('DE','FR','IT');
> >     /* Logically creates: GRANT read ON SalesOrders WHERE Country IN ('DE','FR','IT'); */
> > }
> > 
> > POLICY use_SamplePolicy_Fails {
> >     USE SamplePolicy1 WHERE Country IN ('DE','FR','IT');
> >     /* Logically creates: GRANT read ON SalesOrders WHERE false;
> > 
> >     Described as a sequence of steps by DCL (1), the compiler (2) and the DCL Runtime (3): 
> >     1. GRANT read ON SalesOrders WHERE (Country IS RESTRICTED) AND (Country IN ('DE','FR','IT'));
> >     2. GRANT read ON SalesOrders WHERE (false                ) AND (Country IN ('DE','FR','IT'));
> >     3. GRANT read ON SalesOrders WHERE false;
> >     */
> > }
> > ```

