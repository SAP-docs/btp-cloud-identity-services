<!-- loioc76aca60aa494355bfbc494242fa6151 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Edit an Authorization Policy

If SAP Cloud Identity Services administrators want to change restrictions and their attributes, they can edit an existing custom authorization policy.



## Context

When you edit an existing custom authorization policy, you can add or delete restrictions and their attribute values. You can also assign users to the authorization policy.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Choose the application that supports Authorization Management. For more information, see the documentation of the application.

    The details page of your application has an *Authorization Policies* tab.

4.  Choose the *Authorization Policies* tab and select a custom authorization policy. Custom authorization policies appear as *Editable* in the *Editable* column of the list of authorization policies. If the policy contains editable restrictions, it is also marked as *Restricted Editing*.

5.  Choose the :pencil2: *Edit* button.

    -   \(Optional\) To assign users, choose the *Assignments* tab. See [Assign Authorization Policies](assign-authorization-policies-eac8e5e.md).

    -   The rule that came with the custom authorization policy appears in the *Rules* tab.


6.  \(Optional\) You can enter a label and a description of the authorization policy or change them. The description is an optional comment.

7.  To edit the rules of the authorization policy, choose the *Rules* tab.

8.  Continue to edit the rules. Multiple options are available.

    -   Choose :heavy_plus_sign: to see the possible `RESTRICT` options. This button is either directly below `RESTRICT` or in an indented row below `RESTRICT`.

    -   Choose *Add USE* to add a `USE` statement to the selected authorization policy. Select a `USE` statement from the available authorization policies.



9.  For a `RESTRICT` condition, choose one of the available attributes, an operation, and enter a value. You can choose a value from the value help or type it in. To add another `RESTRICT` condition, choose :heavy_plus_sign: or use the [Return\] key.

    > ### Note:  
    > All indented rows that appear in a list directly below `RESTRICT` or `USE` have an `AND` conjunction.
    > 
    > All rows starting with their own `RESTRICT` condition have an `OR` conjunction with the other `RESTRICT` rows.

    For more information, see [Data Control Language \(DCL\)](data-control-language-dcl-38baa25.md).

10. Choose the conditions that come with the application in the dropdown list. Next, choose an operator and choose or enter a value or choose a user attrribute.

11. Save your changes.

12. To assign users, choose the *Assignments* tab. See [Assign Authorization Policies](assign-authorization-policies-eac8e5e.md).


