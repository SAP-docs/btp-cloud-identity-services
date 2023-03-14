<!-- loioc76aca60aa494355bfbc494242fa6151 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Edit an Authorization Policy

Identity Authentication administrators can edit an existing custom authorization policy by adding or deleting restrictions and their attribute values.



## Context

When you edit an existing custom authorization policy, you can add or delete restrictions and their attribute values. You can also assign users to the authorization policy.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose *Applications*.

3.  Choose your application that supports authorization management. For information, see the documentation of the application.

    The details page of your application has an *Authorization Policies* tab.

4.  Choose a custom authorization policy. You can recognize custom authorization policies at the :pencil2: \(Editable\) icon in the *Editable* column of the list of authorization policies. If the policy contains editable restrictions, it has the <span class="SAP-icons"></span> \(Editable Restrictions\) icon.

5.  Choose the *Edit* button.

    -   \(Optional\) To assign users, choose the *Assignment* tab. See [Assign Authorization Policies](assign-authorization-policies-eac8e5e.md).

    -   You see the rule that came with the custom authorization policy in the *Rules* tab.


6.  \(Optional\) To can enter a label and a description of the authorization policy or change them.

7.  To edit the rules of the authorization policy, choose the *Rules* tab.

8.  Choose :heavy_plus_sign: to see the possible `RESTRICT` options. This button is either directly below `RESTRICT` or on the left side at the bottom of the page.

9.  Choose one the available attributes, an operation, and enter a value. You can choose a value from the value help or type it in.

    > ### Note:  
    > All rows that appear in a list directly below `RESTRICT` have an `AND` conjunction.
    > 
    > All rows starting their own `RESTRICT` condition have an `OR` conjunction with the other `RESTRICT` rows.

10. Choose the conditions that come with the application in the dropdown list. Next, choose an operator and choose or enter a value.

11. Save your changes.


