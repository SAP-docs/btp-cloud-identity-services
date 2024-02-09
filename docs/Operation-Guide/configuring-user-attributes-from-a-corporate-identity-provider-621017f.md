<!-- loio621017f2623c4ac59923e4ef531304d2 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configuring User Attributes from a Corporate Identity Provider

You can configure the value of existing application-defined attributes, like email, first name, last name, for example to values coming from the corporate identity provider \(IdP\), and add new attributes.



<a name="loio621017f2623c4ac59923e4ef531304d2__context_fq2_hyk_sxb"/>

## Context

Configure the user attributes as they come from the corporate identity provider \(IdP\).



<a name="loio621017f2623c4ac59923e4ef531304d2__steps_dtr_4xc_fzb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *Attributes*.

6.  Depending on the type of your application go to:

    -   *Application Attributes* - for subscribed multitenant applications.

        1.  Choose the plus button next to an attribute to set multiple values for the attribute.
        2.  Choose *Corporate Identity Provider* source.
        3.  Provide the new value.

        > ### Tip:  
        > You can enable or disable the attribute mappings inherited from the subscribed multitenant applications:
        > 
        > -   To disable the attribute mappings, choose the <span class="SAP-icons"></span> disable button on the right of the inherited attribute.
        > 
        > -   To enable the attribute, choose :heavy_check_mark: button on the right of the inherited attribute.

    -   *Self-defined Attributes* - for self-created applications or automatically created single-tenant applications.
        1.  Choose *Add button to add new attribute for the application* \> *provide the name* \> *Corporate Identity Provider* \> *provide the value*.

        2.  Choose *plus button next to an attribute to set multiple values for the attribute* \> *Corporate Identity Provider* \> *provide the new value* \> **.


7.  Save your configuration.


