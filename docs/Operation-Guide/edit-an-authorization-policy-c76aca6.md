<!-- loioc76aca60aa494355bfbc494242fa6151 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Edit an Authorization Policy

If Identity Authentication administrators want to change restrictions and their attributes, they can edit an existing custom authorization policy.



## Context

When you edit an existing custom authorization policy, you can add or delete restrictions and their attribute values. You can also assign users to the authorization policy.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Choose the application that supports authorization management. For more information, see the documentation of the application.

    The details page of your application has an *Authorization Policies* tab.

4.  Choose the *Authorization Policies* tab and select a custom authorization policy. Custom authorization policies appear with an :pencil2: \(Editable\) icon in the *Editable* column of the list of authorization policies. If the policy contains editable restrictions, it has an <span class="SAP-icons"></span> \(Editable Restrictions\) icon.

5.  Choose the :pencil2: *Edit* button.

    -   \(Optional\) To assign users, choose the *Assignment* tab. See [Assign Authorization Policies](assign-authorization-policies-eac8e5e.md).

    -   You display the rule that came with the custom authorization policy in the *Rules* tab.


6.  \(Optional\) You can enter a label and a description of the authorization policy or change them. The description is an optional comment.

7.  To edit the rules of the authorization policy, choose the *Rules* tab.

8.  Continue to edit the rules. Multiple options are available.

    -   Choose :heavy_plus_sign: to see the possible `RESTRICT` options. This button is either directly below `RESTRICT` or in an indented row below `RESTRICT`.

    -   Choose *Add USE* to add a `USE` rule to the selected authorization policy. Select a `USE` rule from the available base policies.



9.  For a `RESTRICT` rule, choose one of the available attributes, an operation, and enter a value. You can choose a value from the value help or type it in.

    > ### Note:  
    > All indented rows that appear in a list directly below `RESTRICT` or `USE` have an `AND` conjunction.
    > 
    > All rows starting with their own `RESTRICT` condition have an `OR` conjunction with the other `RESTRICT` rows.

10. Choose the conditions that come with the application in the dropdown list. Next, choose an operator and choose or enter a value.

11. Save your changes.


