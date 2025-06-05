<!-- loioe281f207f2c94e19b23ec9c70044e519 -->

# Convert Subject Name Identifier to Uppercase or Lowercase

Tenant administrator can apply function to change the subject name identifier to uppercase or lowercase letters depending on the need of the application.



## Context

The setting is applied in all cases when Identity Authentication issues an assertion or id token - logon in Identity Authentication or delegated authentication to corporate identity provider with or without enabled identity federation.

> ### Note:  
> Conversion for subject name identifier in locale "tr", "az" or "lt" is not supported. If subject name identifier is in "tr", "az" or "lt" locale the conversion may not work properly.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Under the *Trust* tab, choose *Apply Function to Subject Name Identifier*.

5.  Choose one of the options:

    -   None - default configuration
    -   Uppercase - the subject name identifier is converted to uppercase letters.
    -   Lowercase - the subject name identifier is converted to lowercase letters.

6.  Save your configuration.


