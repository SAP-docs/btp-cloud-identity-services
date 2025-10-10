<!-- loiod16cb10487fc44ccbbba40052a2e8764 -->

# Reuse During Definition

Developers can use functions to implement reusable parts in a policy definition. They can also list policies when they define them.



## Functions

Functions can be used to implement reusable parts within a policy definition.

> ### Sample Code:  
> ```
> FUNCTION Boolean CheckStatus() {
> 	RETURN status = 'open'
> 	  OR status IS NULL;
> }
> 
> 
> POLICY salesOrder {
> 	GRANT read ON SalesOrder WHERE CheckStatus();
> }
> ```



## Optimizations

You can list policies using a semicolon \(`;`\).

> ### Sample Code:  
> ```sql
> POLICY name01 {}
> POLICY name02 {}
> POLICY name03 {}
> POLICY name04 {}
> 
> ```

-   > ### Sample Code:  
    > ```
    > POLICY allowViewReports {};
    > POLICY allowEditReports {};
    > POLICY denyDeleteReports {};
    > POLICY allowReadUserData {};
    > POLICY denyWriteUserData {};
    > POLICY allowManageRoles {};
    > POLICY allowAssignAuthorizationions {};
    > POLICY denyEditAuthorizations {};
    > POLICY allowAccessAuditLogs {};
    > ```


> ### Sample Code:  
> ```
> POLICY allowViewReports {};
> POLICY allowEditReports {};
> POLICY denyDeleteReports {};
> POLICY allowReadUserData {};
> POLICY denyWriteUserData {};
> POLICY allowManageRoles {};
> POLICY allowAssignAuthorizationions {};
> POLICY denyEditAuthorizations {};
> POLICY allowAccessAuditLogs {};
> ```

