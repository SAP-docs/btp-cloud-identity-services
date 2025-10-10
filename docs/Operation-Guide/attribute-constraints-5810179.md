<!-- loio5810179bed4c457d9c6db3ddc58058d0 -->

# Attribute Constraints

Use attribute constraints in authorization policy definitions to define conditions for accessing data, such as `IS NULL` and `IS RESTRICTED`.



**Attribute Constraints**


<table>
<tr>
<th valign="top">

Constraint

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`IS RESTRICTED` 

</td>
<td valign="top">

Denies access until it's relaxed in a `RESTRICT` clause of the `USE` statement

</td>
</tr>
<tr>
<td valign="top">

`IS NOT RESTRICTED` 

</td>
<td valign="top">

Authorizes access until it's constrained in a `RESTRICT` clause of the `USE` statement

</td>
</tr>
</table>

> ### Sample Code:  
> ```
> POLICY salesOrders {
>     GRANT read, write ON SalesOrderItems WHERE Status IS NULL;
> }
> ```

> ### Sample Code:  
> ```
> POLICY CreateOrders {
>     GRANT create ON orders WHERE order.total IS RESTRICTED AND product.category IS NOT RESTRICTED;
> } 
> 
> POLICY CreateSmallOrders {
>      USE CreateOrders RESTRICT order.total < 50, product.category IS NOT RESTRICTED;
> }
> 
> POLICY CreateSmallAccessoryOrders {
>      USE CreateOrders RESTRICT order.total < 50, product.category = 'accessory';
> }
> ```

Only use the `IS (NOT) RESTRICTED` attribute constraint for attributes of the data type string, number, and Boolean. It's not allowed for arrays and structures.

