<!-- loiob5b1e1e3cc354618867e515edb86340f -->

# Multitenant Support

The data control language also supports multitenancy, but it's currently only usable under certain circumstances.



The data control language also implements support for multitenancy. Currently, you can only support multitenancy using the Authorization Management Service and the DCL compile server. If the Authorization Management Service feature is activated, the following rules for package definition and cross package reuse apply:

1.  One schema for the package hierarchy

    -   Define the schema in the root folder of the package hierarchy and the file `schema.dcl`.

    -   Make sure that the schema file only contains the schema definition.


2.  You can reuse schemas across different packages.

    -   DCL elements like authorization policies, functions, or test input are visible and reusable across all packages with fully qualified names \(for example `USE sales.salesOrders;`\).

    -   All packages use the global schema.


3.  `TENANT SCHEMA '' {}` defines a tenant-specific package and can appear in any `*.dcl` of a package.

    -   You can't reuse all elements of a tenant-specific package in other packages.



The runtime evaluates only the policies in non-tenant-specific packages and the tenant-specific package with the provided ID.



<a name="loiob5b1e1e3cc354618867e515edb86340f__section_nm5_p4s_nfc"/>

## Example Package Hierarchy

> ### Example:  
> > ### Sample Code:  
> > ```
> > ams                         //root
> > |- schema.dcl               // schema definition 
> > |- sales
> >     |- sales1.dcl           // policies can reuse elements from basic package
> > |- basic
> >     |- basic1.dcl
> > |- tenant1
> >     |- allAdmins.dcl        // policies can reuse elements from packages 'sales' and 'basic' but NOT 'tenant2'
> > |- tenant2
> >     |- allAdmins.dcl
> > 
> > ```

