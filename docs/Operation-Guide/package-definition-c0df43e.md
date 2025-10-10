<!-- loioc0df43e48d5b41a796b34b1b6463bcc1 -->

# Package Definition

A package is the root folder where the DCL document is located.



A package can contain multiple DCL documents.

> ### Restriction:  
> -   Only `[a-zA-Z_][a-zA-Z_0-9]*` can be used for a package name, which is the name of the path relative to the DCL root.
> 
> -   The total length \(including package separator\) of a package hierarchy is 250 characters.



<a name="loioc0df43e48d5b41a796b34b1b6463bcc1__section_nyy_rsn_gpb"/>

## Cross Package Reuse

Policies from other packages can be reused based on qualified references.



<a name="loioc0df43e48d5b41a796b34b1b6463bcc1__section_hms_xxn_gpb"/>

## References

Qualified references are used to specify elements across package boundaries. The parts of a qualified reference are connected by a "`.`" \(period\) in DCL.



### Examples

-   `sales.SalesOrder:`Package \[`"sales"`\], Policy:`salesOrder`

-   `sales.basic.salesOrder`: Package \[`sales/basic`\], Policy: `salesOrder`


You can introduce qualified references in a compatible way with an additional qualification prefix.

> ### Sample Code:  
> ```sql
> POLICY <policy_name1> {
>     USE <package>.<policy_name2>; // <policy_name2> is qualified by <package>
>     USE <policy_name3>;           // local policy (same package)
> }
> ```

-   > ### Sample Code:  
    > ```sql
    > POLICY allAdmins {
    >     USE sales.salesOrders; // fully qualified name to 'salesOrders' in package 'sales'
    >     USE readAll;           // local policy
    > }
    > ```


