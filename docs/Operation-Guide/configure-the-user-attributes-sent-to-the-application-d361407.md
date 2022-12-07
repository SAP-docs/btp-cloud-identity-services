<!-- loiod361407d36c5443298a909acbbd96ec4 -->

# Configure the User Attributes Sent to the Application

After configuring the user attributes to be collected by the registration and upgrade forms, you have to specify how these attributes are sent to the application.



## Context

Identity Authentication defines default names for these assertion attributes, but you can change them in accordance with your requirements.

You configure the attributes by defining which assertion attribute corresponds to the user attribute that you set for the registration and upgrade forms. You can also specify multiple assertion attributes for each user attribute. You perform this mapping to help the application use the same user attribute for different scenarios that require several assertion attributes.

> ### Note:  
> The assertion attribute name must match the name that the application is expecting.

The attributes are also put in the `id_token` if the application is OpenID connect. For more information, see [OpenID Connect](openid-connect-a789c9c.md).

By default, Identity Authentication sets the following assertion attribute names:


<table>
<tr>
<th valign="top">

User Attribute



</th>
<th valign="top">

Assertion Attribute Name



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

E-mail



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
> You can view the configured user language in the administration console for Identity Authentication. For more information, see [Configure the User Attributes Sent to the Application](configure-the-user-attributes-sent-to-the-application-d361407.md).



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

User UUID



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
> Use `Groups` as assertion attribute name for application on the SAP BTP, Cloud Foundry Environment.



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

Contact by E-mail



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
> The application custom attributes are configured by the application \(service provider\). They cannot be defined for the user.
> 
> Custom attributes must not be used to store sensitive personal data.

> ### Note:  
> The **User Attribute** column lists the attributes that can be shown on the registration and upgrade forms. The **Assertion Attribute Name** lists the attributes that are sent in the assertion.
> 
> The configured custom attributes are also put in the `id_token` if the application is OpenID connect. For more information, see [OpenID Connect](openid-connect-a789c9c.md).
> 
> The configured custom attributes can be seen at the user profile page after choosing *View My Data*.
> 
> The configuration of the user attributes for the system applications is disabled. The default settings for these applications are `First Name`, `Company`, `Last Name`, and `E-Mail`.

> ### Remember:  
> When the application uses a corporate IdP for authentication, and *Identity Federation* is disabled, the user attributes configurations in the administration console for Identity Authentication are not relevant. In such scenarios Identity Authentication sends to the application the user attributes that come from the corporate identity provider without changing them. For more information about the corporate identity provider scenario, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md) and [Configure Identity Federation](configure-identity-federation-c029bbb.md).

To configure the assertion attributes, proceed as follows:



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

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *Assertion Attributes*.

6.  Add and modify the names of the assertion attributes that you want to customize.

7.  Save your configuration.

    If the operation is successful, you receive the message ***Assertion attributes updated***.


**Related Information**  


[Configure Registration and Upgrade Forms](configure-registration-and-upgrade-forms-93a9e18.md "In the administration console, you can configure which user attributes Identity Authentication sends to the service provider or client (relying party) to be displayed on application's registration and upgrade forms.")

[Troubleshooting for Administrators](troubleshooting-for-administrators-f80beb5.md "This section is intended to help administrators deal with error messages in the administration console for Identity Authentication.")

[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

[SAML 2.0](saml-2-0-0708833.md "")

