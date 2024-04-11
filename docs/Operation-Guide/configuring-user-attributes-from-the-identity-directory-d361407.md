<!-- loiod361407d36c5443298a909acbbd96ec4 -->

# Configuring User Attributes from the Identity Directory

Specify how the local user attributes, configured to be collected by the registration and upgrade forms, are sent to the application.



## Context

Identity Authentication defines default names for the user attributes, but you can change them in accordance with your requirements.

You configure the attributes by defining which user attribute corresponds to the user attribute that you set for the registration and upgrade forms. You can also specify multiple user attributes for each user attribute. You perform this mapping to help the application use the same user attribute for different scenarios that require several user attributes.

> ### Note:  
> The user attribute name must match the name that the application is expecting.

The attributes are also put in the `id_token` if the application is OpenID connect. For more information, see [Configuring OpenID Connect](configuring-openid-connect-a789c9c.md).

By default, Identity Authentication sets the following user attribute names:


<table>
<tr>
<th valign="top">

User Attribute

</th>
<th valign="top">

User Attribute Name

</th>
</tr>
<tr>
<td valign="top">

Salutation

</td>
<td valign="top">

title

</td>
</tr>
<tr>
<td valign="top">

First Name

</td>
<td valign="top">

first\_name

</td>
</tr>
<tr>
<td valign="top">

Middle Name

</td>
<td valign="top">

middle\_name

</td>
</tr>
<tr>
<td valign="top">

Last Name

</td>
<td valign="top">

last\_name

</td>
</tr>
<tr>
<td valign="top">

Email

</td>
<td valign="top">

mail

</td>
</tr>
<tr>
<td valign="top">

Telephone Number

</td>
<td valign="top">

telephone

</td>
</tr>
<tr>
<td valign="top">

Language

</td>
<td valign="top">

locale/language

> ### Note:  
> `locale` is added at the creation of the application. It takes as value the language of the user.
> 
> You can view the configured user language in the administration console for SAP Cloud Identity Services. For more information, see [Configuring User Attributes from the Identity Directory](configuring-user-attributes-from-the-identity-directory-d361407.md).



</td>
</tr>
<tr>
<td valign="top">

Login Name

</td>
<td valign="top">

login\_name

</td>
</tr>
<tr>
<td valign="top">

Display Name

</td>
<td valign="top">

display\_name

</td>
</tr>
<tr>
<td valign="top">

User ID

</td>
<td valign="top">

uid

</td>
</tr>
<tr>
<td valign="top">

Global User ID

</td>
<td valign="top">

user\_uuid

</td>
</tr>
<tr>
<td valign="top">

User Type

> ### Note:  
> For example, consumer, partner, or employee.



</td>
<td valign="top">

type

</td>
</tr>
<tr>
<td valign="top">

Street Address

</td>
<td valign="top">

street

</td>
</tr>
<tr>
<td valign="top">

Street Address 2

</td>
<td valign="top">

street2

</td>
</tr>
<tr>
<td valign="top">

City

</td>
<td valign="top">

city

</td>
</tr>
<tr>
<td valign="top">

ZIP/Postal Code

</td>
<td valign="top">

zip

</td>
</tr>
<tr>
<td valign="top">

Country

</td>
<td valign="top">

country

</td>
</tr>
<tr>
<td valign="top">

State/Province

</td>
<td valign="top">

state

</td>
</tr>
<tr>
<td valign="top">

Cost Center

</td>
<td valign="top">

cost\_center

</td>
</tr>
<tr>
<td valign="top">

Department

</td>
<td valign="top">

department

</td>
</tr>
<tr>
<td valign="top">

Division

</td>
<td valign="top">

division

</td>
</tr>
<tr>
<td valign="top">

Employee Number

</td>
<td valign="top">

employee\_number

</td>
</tr>
<tr>
<td valign="top">

Company

</td>
<td valign="top">

company

</td>
</tr>
<tr>
<td valign="top">

Company Street Address

</td>
<td valign="top">

company\_street

</td>
</tr>
<tr>
<td valign="top">

Company Street Address 2

</td>
<td valign="top">

company\_street\_2

</td>
</tr>
<tr>
<td valign="top">

Company City

</td>
<td valign="top">

company\_city

</td>
</tr>
<tr>
<td valign="top">

Company ZIP/Postal Code

</td>
<td valign="top">

company\_zip

</td>
</tr>
<tr>
<td valign="top">

Company Country

</td>
<td valign="top">

company\_country

</td>
</tr>
<tr>
<td valign="top">

Company State/Province

</td>
<td valign="top">

company\_region

</td>
</tr>
<tr>
<td valign="top">

Company Industry

</td>
<td valign="top">

industry

</td>
</tr>
<tr>
<td valign="top">

Company Relationship

</td>
<td valign="top">

relationship

</td>
</tr>
<tr>
<td valign="top">

Job Function

</td>
<td valign="top">

job\_function

</td>
</tr>
<tr>
<td valign="top">

Groups

</td>
<td valign="top">

groups

> ### Note:  
> Use `Groups` as user attribute name for application on the SAP BTP, Cloud Foundry Environment.



</td>
</tr>
<tr>
<td valign="top">

Corporate Groups

> ### Note:  
> This attribute is applicable for the corporate user store scenarios and contains the groups the user in the corporate user store is assigned to.



</td>
<td valign="top">

corporate\_groups

</td>
</tr>
<tr>
<td valign="top">

Contact by Email

</td>
<td valign="top">

contact\_preference\_mail

</td>
</tr>
<tr>
<td valign="top">

Contact by Telephone

</td>
<td valign="top">

contact\_preference\_telephone

</td>
</tr>
<tr>
<td valign="top">

Application Custom Attribute 1

</td>
<td valign="top">

app\_custom\_attribute\_1

</td>
</tr>
<tr>
<td valign="top">

Application Custom Attribute 2

</td>
<td valign="top">

app\_custom\_attribute\_2

</td>
</tr>
<tr>
<td valign="top">

Application Custom Attribute 3

</td>
<td valign="top">

app\_custom\_attribute\_3

</td>
</tr>
<tr>
<td valign="top">

Application Custom Attribute 4

</td>
<td valign="top">

app\_custom\_attribute\_4

</td>
</tr>
<tr>
<td valign="top">

Application Custom Attribute 5

</td>
<td valign="top">

app\_custom\_attribute\_5

</td>
</tr>
</table>

> ### Remember:  
> The application custom attributes are configured by the application \(service provider\). They can't be defined for the user.
> 
> Custom attributes must not be used to store sensitive personal data.

> ### Note:  
> The **Value** column lists the attributes that can be shown on the registration and upgrade forms. The **Name** lists the attributes that are sent in the assertion.
> 
> The configured custom attributes are also put in the `id_token` if the application is OpenID connect. For more information, see [Configuring OpenID Connect](configuring-openid-connect-a789c9c.md).
> 
> The configured custom attributes can be seen at the user profile page after choosing *View My Data*.
> 
> The configuration of the user attributes for the system applications is disabled. The default values for these applications are `First Name`, `Company`, `Last Name`, and `Email`.

> ### Remember:  
> When the application uses a corporate IdP for authentication, and *Identity Federation* is disabled, the user attributes configurations in the administration console for SAP Cloud Identity Services aren't relevant. In such scenarios Identity Authentication sends to the application the user attributes that come from the corporate identity provider without changing them. For more information about the corporate identity provider scenario, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md) and [Configure Identity Federation](configure-identity-federation-c029bbb.md).



<a name="loiod361407d36c5443298a909acbbd96ec4__steps_nls_rnc_fzb"/>

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

7.  **Optional:** Choose the *Add* button:

    1.  Provide a name for the attribute.

    2.  Choose *Identity Directory* source.

    3.  Choose a value from the drop-down list.


8.  **Optional:** Choose the plus button next to the attribute to set a new value for the attribute.

9.  Save your configuration.


**Related Information**  


[Configure Registration and Upgrade Forms](configure-registration-and-upgrade-forms-93a9e18.md "In the administration console, you can configure which user attributes Identity Authentication sends to the service provider or client (relying party) to be displayed on application's registration and upgrade forms.")

[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

