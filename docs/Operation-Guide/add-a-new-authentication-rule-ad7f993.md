<!-- loioad7f9935691b44399f39905302b38674 -->

# Add a New Authentication Rule

You can add rules for authentication against different identity providers.



<a name="loioad7f9935691b44399f39905302b38674__prereq_nhl_c1s_tcb"/>

## Prerequisites

You are assigned the *Manage Applications* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

Each rule contains the following information:

-   *Identity Provider*

    Define the identity provider that will be used for authentication.

    The dropdown list includes the local identity provider and all corporate identity providers that are created in the administration console for SAP Cloud Identity Services. The corporate identity providers must be configured in the administration. For more information, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md).

    > ### Remember:  
    > This field is required.

-   *Domain*

    Specify the domain of the email address that comes after the @ symbol. If no is domain entered, the rule is valid for any domain.

-   *User Group*

    Specify the user group, which the authenticating user must be part of. If no user group is selected, the rule is valid for any of the groups.

    The user groups must be configured in the administration console for SAP Cloud Identity Services. For more information, see [User Groups](user-groups-ddd067c.md).

    > ### Note:  
    > The authenticating user must exist in the user store of Identity Authentication for the *User Group* criteria to be checked properly.

-   *User Type*

    Specify the type, which the authenticating user must have. If no user type is selected, the rule is valid for any of the types.

    > ### Note:  
    > The authenticating user must exist in the user store of Identity Authentication for the *Type* criteria to be checked properly.

-   *IP Range*

    Define the range of allowed IP addresses or proxies that the user logs on from. The value must be specified in Classless Inter-Domain Routing \(CIDR\) notation.

    > ### Note:  
    > By default the field is empty, meaning that any IP is allowed.

    > ### Example:  
    > Enter 123.45.67.1/24 to allow users to log on from any IP starting with 123.45.67.

    If no IP range is defined, the rule is valid for all IP ranges.


> ### Remember:  
> The fields *Domain*, *User Group*, *User Type*, and *IP Range* are not mandatory, but at least one of them has to be specified.



<a name="loioad7f9935691b44399f39905302b38674__steps_jtp_sqg_t5"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Conditional Authentication*, choose *Conditional Authenticating Identity Providers*.

6.  Choose *Add New Rule*.

7.  Fill in the fields on the *New Rule* window.

8.  Confirm your changes.


**Related Information**  


[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

