<!-- loiod361407d36c5443298a909acbbd96ec4 -->

# Configuring User Attributes from the Identity Directory

Specify how the local user attributes, configured to be collected by the registration and upgrade forms, are sent to the application.



## Context

Identity Authentication defines default names for the user attributes, but you can change them in accordance with your requirements.

You configure the attributes by defining which user attribute corresponds to the user attribute that you set for the registration and upgrade forms. You can also specify multiple user attributes for each user attribute. You perform this mapping to help the application use the same user attribute for different scenarios that require several user attributes.

> ### Note:  
> The user attribute name must match the name that the application is expecting.

The attributes are also put in the `id_token` if the application is OpenID connect. For more information, see [Configuring OpenID Connect](configuring-openid-connect-a789c9c.md).

By default, Identity Authentication sets only the following user attribute names which are added at the creation of the application:


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

First Name

</td>
<td valign="top">

first\_name

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

Language

</td>
<td valign="top">

locale

> ### Note:  
> `locale` takes as value the language of the user.
> 
> You can view the configured user language in the administration console for SAP Cloud Identity Services. For more information, see [Configuring User Attributes from the Identity Directory](configuring-user-attributes-from-the-identity-directory-d361407.md).



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

Global User ID

</td>
<td valign="top">

user\_uuid

</td>
</tr>
</table>

> ### Note:  
> The **Value** column lists the attributes that can be shown on the registration and upgrade forms. The **Name** lists the attributes that are sent in the assertion.

Identity Authentication supports also the following user attributes:

-   `Application Activation Time`
-   `Application Custom Attribute 1`
-   `Application Custom Attribute 2`
-   `Application Custom Attribute 3`
-   `Application Custom Attribute 4`
-   `Application Custom Attribute 5`

    > ### Note:  
    > The application custom attributes are configured by the application \(service provider\). They can't be defined for the user.
    > 
    > Custom attributes must not be used to store sensitive personal data.

-   `City`
-   `Company`
-   `Company City`
-   `Company Country/Region`
-   `Company State/Province`
-   `Company Street Address`
-   `Company Street Address 2`
-   `Company ZIP/Postal Code`
-   `Contact by Email`
-   `Contact by Telephone`
-   `Corporate Groups`

    > ### Note:  
    > This attribute is applicable for the corporate user store scenarios and contains the groups the user in the corporate user store is assigned to.

-   `Cost Center`
-   `Country/Region`
-   `Department`
-   `Display Name`
-   `Email Verified`
-   `Employee Number`
-   `All Groups`

    > ### Note:  
    > > ### Note:  
    > > Lists all the groups that a user is a member of.
    > > 
    > > Use `Groups` as user attribute name for application on the SAP BTP, Cloud Foundry Environment.

-   `Application Groups`

    > ### Note:  
    > > ### Note:  
    > > Lists only the application-specific groups to which the user is assigned to.

-   `Company Industry`
-   `Job Function`
-   `Login Name`
-   `Middle Name`
-   `Company Relationship`
-   `State/Province`
-   `Street Address`
-   `Street Address 2`
-   `Telephone Number`
-   `Salutation`
-   `User ID`
-   `ZIP/Postal Code`.

> ### Tip:  

> ### Remember:  
> The application custom attributes are configured by the application \(service provider\). They can't be defined for the user.
> 
> Custom attributes must not be used to store sensitive personal data.

> ### Note:  
> The **Value** column lists the attributes that can be shown on the registration and upgrade forms. The **Name** lists the attributes that are sent in the assertion.
> 
> The configured custom attributes are also put in the `id_token` if the application is OpenID connect. For more information, see [Configuring OpenID Connect](configuring-openid-connect-a789c9c.md).

> ### Remember:  
> When the application uses a corporate IdP for authentication, and *Identity Federation* is disabled, the user attributes configurations in the administration console for SAP Cloud Identity Services aren't relevant. In such scenarios Identity Authentication sends to the application the user attributes that come from the corporate identity provider without changing them. For more information about the corporate identity provider scenario, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md) and [Configure Identity Federation](configure-identity-federation-c029bbb.md).



<a name="loiod361407d36c5443298a909acbbd96ec4__steps_nls_rnc_fzb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
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

