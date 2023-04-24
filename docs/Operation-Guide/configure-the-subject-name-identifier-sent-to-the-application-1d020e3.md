<!-- loio1d020e3a3ba34c43a71fde70bfa6419a -->

# Configure the Subject Name Identifier Sent to the Application

The `Subject Name Identifier` is a profile attribute that Identity Authentication sends to the application as `name ID` in the SAML 2.0 assertions, and as `subject` in the OpenID Connect tokens. The application then uses this attribute to identify the user.



## Context

You can choose an attribute from a predefined list for basic configuration, or you can set an attribute with dynamic value for advanced configuration.

For both basic and advanced configuration you can also configure a fallback subject name identifier. The fallback subject name identifier is used only when the regular identifier is not available. If the regular identifier is not available, and you haven't set a fallback attribute, the authentication of the user fails.



### Basic Configuration

The user is identified in one of the following ways:

-   Global User ID
-   User ID
-   E-Mail
-   Display Name
-   Login Name
-   Employee Number.

> ### Note:  
> `Global User ID`, `User ID`, `Login Name` and `E-Mail` can be unique for the tenant. This depends on the tenant configurations.
> 
> The configuration of the `Subject Name Identifier` attribute for the system applications is disabled. The default setting for these applications is `User ID`.

> ### Caution:  
> Identity Authentication does not check the `Employee Number` attribute for uniqueness. Be sure that the users receive unique employee numbers.



### Advanced Configuration

The user is identified by setting an attribute with dynamic value in the following pattern: `<prefix> ${attribute_technical_name} <suffix>`.

Expand the **Supported Attributes** table below to see the technical names of the attributes that can take dynamic values:

**Supported Attributes**


<table>
<tr>
<th valign="top">

Attribute



</th>
<th valign="top">

Attribute Technical Name



</th>
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

Logon Name



</td>
<td valign="top">

loginName



</td>
</tr>
<tr>
<td valign="top">

Display Name



</td>
<td valign="top">

displayName



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

userUuid



</td>
</tr>
<tr>
<td valign="top">

Employee Number



</td>
<td valign="top">

personnelNumber



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 1



</td>
<td valign="top">

customAttribute1



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 2



</td>
<td valign="top">

customAttribute2



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 3



</td>
<td valign="top">

customAttribute3



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 4



</td>
<td valign="top">

customAttribute4



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 5



</td>
<td valign="top">

customAttribute5



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 6



</td>
<td valign="top">

customAttribute6



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 7



</td>
<td valign="top">

customAttribute7



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 8



</td>
<td valign="top">

customAttribute8



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 9



</td>
<td valign="top">

customAttribute9



</td>
</tr>
<tr>
<td valign="top">

Custom Attribute 10



</td>
<td valign="top">

customAttribute10



</td>
</tr>
<tr>
<td valign="top">

SP \(service provider\) user nameID



</td>
<td valign="top">

name\_id



</td>
</tr>
<tr>
<td valign="top">

SP \(service provider\) user Custom Attribute 1



</td>
<td valign="top">

spCustomAttribute1



</td>
</tr>
<tr>
<td valign="top">

SP \(service provider\) user Custom Attribute 2



</td>
<td valign="top">

spCustomAttribute2



</td>
</tr>
<tr>
<td valign="top">

SP \(service provider\) user Custom Attribute 3



</td>
<td valign="top">

spCustomAttribute3



</td>
</tr>
<tr>
<td valign="top">

SP \(service provider\) user Custom Attribute 4



</td>
<td valign="top">

spCustomAttribute4



</td>
</tr>
<tr>
<td valign="top">

SP \(service provider\) user Custom Attribute 5



</td>
<td valign="top">

spCustomAttribute5



</td>
</tr>
<tr>
<td valign="top">

NameID coming from the assertion of the corporate IdP



</td>
<td valign="top">

corporateIdP.NameID



</td>
</tr>
<tr>
<td valign="top">

Attribute coming from the assertion of the corporate IdP



</td>
<td valign="top">

corporateIdP.<corporateIDP attribute\>



</td>
</tr>
</table>

> ### Remember:  
> If the advanced configuration option is used, *Use Identity Authentication user store* must be enabled. When the application uses corporate IdP for authentication, and *Use Identity Authentication user store* is disabled, the `Subject Name Identifier` attribute configurations in the administration console for SAP Cloud Identity Services are not relevant. In such scenarios Identity Authentication sends to the application the `Subject Name Identifier` attribute that comes from the corporate identity provider without changing it. For more information about the corporate identity provider scenario, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md) and [Configure Identity Federation](configure-identity-federation-c029bbb.md).

Optionally, you can configure the default name identifier format of the name ID attribute for SAML 2.0 applications.

> ### Caution:  
> When configuring the `Subject Name Identifier`, take into consideration that some of the attributes can be modified by the users.

To set the `Subject Name Identifier` attribute, proceed as follows:



<a name="loio1d020e3a3ba34c43a71fde70bfa6419a__steps_ksg_x2m_fp"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *Subject Name Identifier*.

6.  Select one of the following:

    -   Basic Configuration:
        -   Select a basic attribute from the drop down: `Global User ID`, `User ID` \(this is the default setting\), `E-Mail`, `Display Name`, `Login Name`, `Employee Number`.

            > ### Note:  
            > If you select *Login Name*, or *Employee Number*, and the selected attribute has no value set for the user, the user is not able to log on the application. The message "**HTTP Status 401 – Unauthorized**" is displayed when the user provides credentials and logs on. In this case, configure also the fallback attribute.

        -   \(optional\) Select a fallback attribute from the drop down: `None` \(this is the default setting\), `Global User ID`, `User ID`, `E-Mail`, `Display Name`, `Login Name`, `Employee Number`.


    > ### Tip:  
    > When Identity Authentication acts as proxy IdP, and the users have no profiles in Identity Authentication, choose the advanced configuration option.

    -   Advanced Configuration:
        -   set an attribute with dynamic value in the following pattern `<prefix> ${attribute_technical_name} <suffix>`. For example: `Phone ${telephone}`

            > ### Note:  
            > If Identity Authentication acts as proxy IdP, and the users have no profiles in Identity Authentication, set an attribute with the following dynamic value: <prefix\> $\{corporateIdP<corporateIDP attribute\>\} <suffix\>

        -   \(optional\) Select a fallback attribute from the drop down: `None` \(this is the default setting\), `Global User ID`, `User ID`, `E-Mail`, `Display Name`, `Login Name`, `Employee Number`.


7.  Save your selection.

    Once the application has been changed, the system displays the message ***Application <name of application\> updated***.


 <a name="task_oyx_34m_x1b"/>

<!-- task\_oyx\_34m\_x1b -->

## \(Optional\) Configure the Default Name ID Format Sent to the Application

The tenant administrator can set a default name ID format via the administration console for SAP Cloud Identity Services.



## Context

The name ID format is used in the `Format` attribute of the `NameID` element that Identity Authentication sends to the application with the SAML assertion. This is the default name ID format. It is used only in case the application or the service provider does not request another name ID format with the SAML authentication request.

 Identity Authentication supports the following name ID formats:


<table>
<tr>
<th valign="top">

Name ID Format



</th>
<th valign="top">

URI



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Unspecified



</td>
<td valign="top">

urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified



</td>
<td valign="top">

Identity Authentication does not use a specific format to express the identity of the user. The application receives the value of the user attribute that is selected as name ID attribute.

By default this is the default Name ID format.



</td>
</tr>
<tr>
<td valign="top">

E-mail address



</td>
<td valign="top">

urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress



</td>
<td valign="top">

The format of the name ID is an e-mail address. You can configure this setting when you have chosen as name ID attribute a user attribute that contains e-mail.

> ### Note:  
> Identity Authentication does not check if the content of the name ID attribute is e-mail address. You can decide which name ID attribute to configure for the application. Make sure that it contains e-mail address in case you want to conform to the SAML2 specification.



</td>
</tr>
</table>

> ### Note:  
> The configuration of the default name ID format for the system applications is disabled. The default setting for these applications is `Unspecified`.

> ### Remember:  
> When the application uses corporate IdP for authentication, and *Use Identity Authentication user store* is disabled, the default name ID attribute configurations in the administration console for SAP Cloud Identity Services are not relevant. In such scenarios Identity Authentication sends to the application name ID format that comes from the SAML assertion sent from the corporate IdP without changing it. For more information about the corporate identity provider scenario, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md) and [Configure Identity Federation](configure-identity-federation-c029bbb.md).

To set the default name ID format, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *Default Name ID Format*.

6.  Select the default name ID format from the following:

    -   Unspecified
    -   E-Mail

7.  Save your selection.

    Once the application has been changed, the system displays the message ***Application <name of application\> updated***.


**Related Information**  


[Troubleshooting for Administrators](troubleshooting-for-administrators-f80beb5.md "This section is intended to help administrators deal with error messages in the administration console for SAP Cloud Identity Services.")

[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

[Configure Trust](configure-trust-f96e4c5.md "This document is intended to help you configure a trusted service provider (SP) or client (relying party) in the administration console for SAP Cloud Identity Services.")

