<!-- loioe920324b086e4ee2b34e80936b1df6e9 -->

# Add a New Phone Verification Rule

You can add rules to skip phone verification for user types.



## Context

Each rule contains the following information:

-   **Action**

    You can choose the *Skip* action. Users of the selected user type in the rule will not be prompted to verify their phones when the *Phone Verification Via SMS* option is enabled.

-   *User Type*

    Specify the type, which the user must have.




## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the list item of the application that you want to edit.

    > ### Note:  
    > If you do not have a created application in your list, you can create one. For more details, see Related Information.

    > ### Caution:  
    > The list also includes the `Administration Console` application. If you enable risk-based authentication for that application, make sure that you, as a tenant administrator, meet the authentication rules and the default authentication rule. Otherwise when you log out of the administration console you will not be able to log in it again if you don't meet the rules.
    > 
    > If `Administration Console` is not in the list of the applications you may request it. To do this, you need to report an incident with a subject on [SAP Support Portal Home](https://support.sap.com/en/index.html) under the component `BC-IAM-IDS`.

4.  Choose the *Branding and Layout* tab.

5.  Under *Application Forms Customization*, choose *Phone Verification Via SMS*.

6.  Choose *Add Rule*.

7.  Fill in the fields on the *New Verification Rule* window.

8.  Confirm your changes.

9.  Choose *Save*.

    If the operation is successful, the system displays the message ***Verification rules updated***.


**Related Information**  


[Add a New Phone Verification Rule](add-a-new-phone-verification-rule-e920324.md "You can add rules to skip phone verification for user types.")

[Protecting Self-Registration with Phone Verification](protecting-self-registration-with-phone-verification-5834b6e.md "Tenant administrators can configure applications to require new self-registered users to verify themselves via SMS codes sent to their mobile phones.")

