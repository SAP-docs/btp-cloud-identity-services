<!-- loio25b632b9c6d84fd68eb9325975a339d3 -->

# Delete Applications

As a tenant administrator, you can delete one or more charged or bundled applications in a tenant of Identity Authentication.



## Prerequisites

-   You are assigned the *Manage Applications* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have at least one bundled or charged application that you want to delete.




## Context

A *Delete Applications* operation removes the application and all of its configurations from the tenant of Identity Authentication.

> ### Note:  
> You can only delete charged or non-SAP managed bundled applications. The system applications and the SAP managed bundled applications in your tenant are hidden when you enter *Delete Applications* mode in the administration console. For more information, see [Configure an Application's Type](configure-an-application-s-type-6fee9c3.md).

Follow the procedure below for each application that you want to delete:



<a name="loio25b632b9c6d84fd68eb9325975a339d3__steps_dzw_kd1_2qb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Select the application that you want to delete.

    > ### Tip:  
    > Type the name of the application in the search field to filter the list items.

4.  Choose the *Delete* button in the right-hand panel to delete the selected application.

5.  Confirm the operation in the pop-up dialog.

    Once the application has been deleted, the system displays the message ***Application <application name\> deleted***.


