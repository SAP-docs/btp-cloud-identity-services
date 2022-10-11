<!-- loioe281f207f2c94e19b23ec9c70044e519 -->

# Convert Subject Name Identifier to Uppercase or Lowercase

Tenant administrator can apply function to change the subject name identifier to uppercase or lowercase letters depending on the need of the application.



## Context

The setting is applied in all cases when Identity Authentication issues an assertion or id token - logon in Identity Authentication or delegated authentication to corporate identity provider with or without enabled identity federation.

> ### Note:  
> Conversion for subject name identifier in locale "tr", "az" or "lt" is not supported. If subject name identifier is in "tr", "az" or "lt" locale the conversion may not work properly.



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

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Under the *Trust* tab, choose *Apply Function to Subject Name Identifier*.

5.  Choose one of the options:

    -   None - default configuration
    -   Uppercase - the subject name identifier is converted to uppercase letters.
    -   Lowercase - the subject name identifier is converted to lowercase letters.

6.  Save your configuration.


