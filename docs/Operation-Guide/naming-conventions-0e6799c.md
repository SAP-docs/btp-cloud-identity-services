<!-- loio0e6799ca5c7e4764baf98b8fd3236e9f -->

# Naming Conventions

Naming conventions in Authorization Management involve using regular or delimited identifiers for objects like policies, actions, resources, and attributes, ensuring consistency and clarity in application development. This content is useful for developers to understand how to properly name and manage authorization elements within their applications, promoting uniformity and preventing naming conflicts.



The objects of Authorization Management include authorization policies, actions, resources, and attributes. The names of actions, resources, and attributes are defined in the application and are sent to Authorization Management using the authorization content. A set of valid characters makes it possible for developers to define the names in the same style as all other elements used for development.

The user names and user groups names are defined in the identity provider. There is no naming convention from DCL side. Within DCL, we must handle all kinds of users and group names. It's possible to use unquoted and double-quoted names for users and user groups.

-   The name for an object \(authorization policy, action, resource, or attribute\) can be specified using regular \(unquoted\) identifiers or delimited \(double-quoted\) identifiers:

    -   Policy name specified using a regular identifier in a `POLICY` statement

        > ### Sample Code:  
        > ```
        > POLICY readAll { ... };
        > ```

    -   Policy name specified using a delimited identifier in a `POLICY` statement:

        > ### Sample Code:  
        > ```
        > POLICY "read All"  { ... };
        > ```

    -   Action name specified using a regular identifier:

        > ### Sample Code:  
        > ```
        > GRANT read ON * ;
        > ```

    -   Action name specified using a delimited identifier:

        > ### Sample Code:  
        > ```
        > GRANT "read" ON * ;
        > ```


-   The maximum length of an authorization policy is 127 characters.

-   A name can't be identical to another object of Authorization Management with the same type. For example: there is only one authorization policy with name `Admin`.


String values of attributes are always quoted with `'` \(single quotes\). This is also valid for identifiers.

> ### Sample Code:  
> ```
> POLICY salesOrders {
>     GRANT read ON SalesOrders, SalesOrderItems WHERE Country = 'DE'
> }
> ```

