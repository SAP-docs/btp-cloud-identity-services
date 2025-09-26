<!-- loio38baa251132c4b088f41261fb3158fb3 -->

# Data Control Language

Developers define rules and authorization policies in SAP Cloud Identity Services. They use an SQL-like language - the data control language \(DCL\). Administrators can combine these rules within authorization policies and assign them to users.



<a name="loio38baa251132c4b088f41261fb3158fb3__section_dft_thn_5pb"/>

## Prerequisites

The following services must be activated in your Cloud Foundry SAP BTP subaccount. Check your services in your subaccount by using `cf marketplace` in the Cloud Foundry command line.

-   Authorization Management is part of the Identity service. You can activate Authorization Management for all applications that are created in SAP Cloud Identity Services.




Using this language, developers define authorizations. Administrators can refine them by combining rules within authorization policies. In the administration console, they assign the authorization policies to users.

This is what a policy definition looks like.

> ### Note:  
> Choose the links in the sample code. They take you to a description of the DCL elements.

> ### Sample Code:  
> ```
> {
> SCHEMA {
> 	SalesOrderType: number
> }
> POLICY readSalesOrders_Type {
> 	GRANT read ON salesOrders WHERE SalesOrderType BETWEEN 100 AND 500;
> }
> }
> ```

