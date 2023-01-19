<!-- loio44dd6368b6ed4e9994c45b3eeffac320 -->

# Choose a Corporate Identity Provider as Default

You choose a corporate identity provider to be the default identity provider for your application.



<a name="loio44dd6368b6ed4e9994c45b3eeffac320__prereq_irh_1cs_bdb"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have a configured corporate identity provider. For more information how to configure a corporate identity provider, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md).




## Context

To choose a corporate identity provider as default, follow the procedures:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under the *Conditional Authentication* section, choose the *Conditional Authentication* list item.

6.  Select from the drop down the corporate identity provider that the application will use as the default identity provider.

7.  Save your changes.

    Once the application has been updated, the system displays the message ***Conditional Authentication updated***.




<a name="loio44dd6368b6ed4e9994c45b3eeffac320__result_lsv_pcs_bdb"/>

## Results

When the choice is a corporate identity provider, you are not able to access the custom configurations for the applications. The *Authentication and Access* and *Branding and Layout* tabs are not visible.

