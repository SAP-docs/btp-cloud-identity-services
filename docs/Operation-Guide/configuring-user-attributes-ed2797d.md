<!-- loioed2797dcac0643bebc89821faaa97487 -->

# Configuring User Attributes

Tenant administrator can specify how, after configuring the user attributes that are collected by the registration and upgrade forms, these attributes are sent to the application. They can also configure attributes with default values for the application, including the values of attributes defined by the multitenant application.



<a name="loioed2797dcac0643bebc89821faaa97487__context_ucy_ytc_fzb"/>

## Context

**Attributes**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Source

</th>
<th valign="top">

Value

</th>
<th valign="top">

More Information

</th>
</tr>
<tr>
<td valign="top" rowspan="3">

The names of the user attributes that are sent in the assertion/added in the token.

</td>
<td valign="top">

*Identity Directory* - specify how the user attributes, configured to be collected by the registration and upgrade forms attributes, are sent to the application.

</td>
<td valign="top">

The attribute display name. Choose a value from the drop-down.

> ### Note:  
> The drop-down lists the attributes that can be shown on the registration and upgrade forms.



</td>
<td valign="top">

[User Attributes Sent to the Application](user-attributes-sent-to-the-application-d361407.md)

</td>
</tr>
<tr>
<td valign="top">

*Corporate Identity Provider* - configure Identity Authentication to reference attributes coming from the assertion of the corporate identity provider.

</td>
<td valign="top">

The specific attribute from the corporate IdP, whose value is taken.

add and modify the names of the attributes that you want to customize

</td>
<td valign="top">

[Attributes with Default Values](attributes-with-default-values-a2f1e46.md)

</td>
</tr>
<tr>
<td valign="top">

*Expression* - configure attributes with dynamic values to be added into the assertions.

</td>
<td valign="top">

The static or dynamic value of the attribute.

Configure attributes with dynamic values to be added into the assertions in the following pattern: `<prefix> ${attribute_technical_name>} <suffix>`

> ### Note:  
> Always use the *Attribute Technical Name* to configure attributes with dynamic values.



</td>
<td valign="top">

[Attributes with Default Values](attributes-with-default-values-a2f1e46.md)

</td>
</tr>
</table>

Based on the type of your application, choose one of the following:

-   Choose the Configure Self-Defined Attributes section for applications that are not subscribed, and for subscribed applications for which the provider application has not defined an attribute yet.

-   Choose the Configure Application Attributes section for applications that are subscribed, and the provider application has already defined an attribute.


For more information, see [Application Types](../application-types-8f61880.md).

<a name="task_sm3_xcc_fzb"/>

<!-- task\_sm3\_xcc\_fzb -->

## Configure Self-Defined Attributes



<a name="task_sm3_xcc_fzb__steps_nls_rnc_fzb"/>

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

6.  Under the *Self-defined Attributes* section, choose *Expand All* to view all the information about the user attributes.

7.  Choose the *Add* button:

    -   Choose *Identity Directory* source to add and modify the names of the attributes that you want to customize.
    -   Choose *Corporate Identity Provider* or *Expression* to add the default attributes with their values to be sent to the application.
    -   Choose the plus button next to the attribute to set the new value for the attribute.

8.  Save your configuration.


<a name="task_ezf_5cc_fzb"/>

<!-- task\_ezf\_5cc\_fzb -->

## Configure Application Attributes \(for Subscribed Applications\)



<a name="task_ezf_5cc_fzb__context_fbq_dcd_fzb"/>

## Context

You can configure the value of existing application-defined attributes, like email, first name, last name, for example to values coming from the corporate identity provider \(IdP\), and add new attributes.



<a name="task_ezf_5cc_fzb__steps_dtr_4xc_fzb"/>

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

6.  Under the *Application Attributes* section:

    1.  Choose *Expand All* to view all the information about the user attributes that are inherited.

    2.  Choose the plus button next to the attribute to set the new value for the attribute defined by the multitenant application.


7.  Under the *Self-defined Attributes* section:

    1.  Choose *Expand All* to view all the information about the user attributes.

    2.  Choose the *Add* button to add attributes with default values for the application created from the multitenant application.


    -   Choose *Identity Directory* source to add and modify the names of the attributes that you want to customize.
    -   Choose *Corporate Identity Provider* or *Expression* to add the default attributes with their values to be sent to the application.
    -   Choose the plus button next to the attribute to set the new value for the attribute.

8.  Save your configuration.


