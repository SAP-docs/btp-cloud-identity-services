<!-- loioa2f1e4692e7d4379ab82144ab309e7b3 -->

# Configuring Attributes Based on Flexible Expressions

You can configure attributes based on flexible expressions for the application.



<a name="loioa2f1e4692e7d4379ab82144ab309e7b3__context_qrl_hsh_1fb"/>

## Context

The attributes are sent from Identity Authentication to the application in the assertion. You can set attributes like `location` and `company` with values *Europe* and *Company A* for example, so that the application displays Europe and Company A on its main page.

The attributes are also put in the `id_token` if the application is OpenID connect. For more information, see [OpenID Connect](openid-connect-a789c9c.md).

For both, the SAML 2.0 and OpenID Connect applications, you can configure attributes with dynamic values to be added into the assertions in the following pattern: `<prefix> ${attribute_technical_name>} <suffix>`

> ### Restriction:  
> \(For OpenID Connect applications\) The following claims can't be set via the configuration of attributes with default values: `iss`, `sub`, `zone_uuid`, `exp`, `nbf`, `iat`, `auth_time`, `nonce`, `acr`, `amr`, `cnf`, `azp`, `at_hash`, `c_hash`, `sub_jwk`, and `ias_iss`.

Expand the **Supported Attributes** table below to see the attributes that can take dynamic values:

**Supported Attributes**


<table>
<tr>
<th valign="top">

Attribute Display Name

</th>
<th valign="top">

Attribute Technical Name

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

firstName

</td>
</tr>
<tr>
<td valign="top">

Middle Name

</td>
<td valign="top">

middleName

</td>
</tr>
<tr>
<td valign="top">

Last Name

</td>
<td valign="top">

lastName

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

language

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

User UUID

</td>
<td valign="top">

userUuid

</td>
</tr>
<tr>
<td valign="top">

User Type

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

costCenter

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

personnelNumber

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

companyStreet

</td>
</tr>
<tr>
<td valign="top">

Company Street Address 2

</td>
<td valign="top">

companyStreet2

</td>
</tr>
<tr>
<td valign="top">

Company City

</td>
<td valign="top">

companyCity

</td>
</tr>
<tr>
<td valign="top">

Company ZIP/Postal Code

</td>
<td valign="top">

companyZip

</td>
</tr>
<tr>
<td valign="top">

Company Country

</td>
<td valign="top">

companyCountry

</td>
</tr>
<tr>
<td valign="top">

Company State/Province

</td>
<td valign="top">

companyRegion

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

Job Function

</td>
<td valign="top">

jobFunction

</td>
</tr>
<tr>
<td valign="top">

Groups

</td>
<td valign="top">

companyGroups

> ### Tip:  
> The attributes `companyGroups` and `corporateGroups` support regular expressions, so that they can be filtered.



</td>
</tr>
<tr>
<td valign="top">

Corporate Groups

> ### Note:  
> This attribute is applicable for the corporate user store scenarios and contains the groups the user in the corporate user store is assigned to.



</td>
<td valign="top">

corporateGroups

> ### Tip:  
> The attributes `companyGroups` and `corporateGroups` support regular expressions, so that they can be filtered.



</td>
</tr>
<tr>
<td valign="top">

Contact by Email

</td>
<td valign="top">

contactPreferenceEmail

</td>
</tr>
<tr>
<td valign="top">

Contact by Telephone

</td>
<td valign="top">

contactPreferenceTelephone

</td>
</tr>
<tr>
<td valign="top">

Application Activation Time

</td>
<td valign="top">

activation\_time

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
</table>



### Examples for attributes with dynamic values:

If you set `${uid}` as a value, the response returns the ID of the user to the application:

> ### Example:  
> ```
> 
> SAML 2.0
> 
> <Attribute Name="User ID">
> 	   <AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
>                              xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
>                              xsi:type="xs:string"
>                              >P123456</AttributeValue>
> </Attribute>
> 
> OpenID Connect
> 
>  "User ID": "P123456"
> 
> ```

If you set `${customAttribute1}` as a value, the response returns the first custom attribute of the user to the application, if there is such. If the user does not have a custom attribute, the response contains an empty attribute:

> ### Example:  
> ```
> 
> SAML 2.0
> 
> <Attribute Name="Custom Attribute">
> 	   <AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
>                        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
>                        xsi:type="xs:string"
>                        >{customAttribute1}
> </AttributeValue>
> 
> OpenID Connect
> 
>  "Custom Attribute": "{customAttribute1}"
> 
> 
> ```

If you set `${companyGroups:regex[Admin]}` as a value, the response returns the groups, that contain "Admin" in the name:

> ### Example:  
> ```
> 
> SAML 2.0
> 
> <Attribute Name="Groups">
>        <AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
>                        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
>                        xsi:type="xs:string"
>                        >Admins</AttributeValue>
>        <AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
>                        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
>                        xsi:type="xs:string"
>                        >Administrators</AttributeValue>
> 
> OpenID Connect
> 
>  "Groups": [
>     "Admins"
>     "Administrators",
>  ]
> 
> ```



### Merge User Attributes

For both, the SAML 2.0 and OpenID Connect applications, you can define attributes with the same name, but with different values, or you can define a user attribute and an attribute with default value with the same name. In the response, the attributes are merged into multivalue attributes. Thus, depending on the configuration, several values may appear for a single value attribute.

The order of the attribute's values in the assertion is arbitrary.

For example, you have defined the `mail` user attribute and at the same time the `mail` attribute with default value `example@example.com`.

> ### Example:  
> When the user Dona Moore logs on, the response returns `mail` as a multivalue attribute with the two values.
> 
> ```
> 
> SAML 2.0
> 
>  <Attribute Name="mail">
> 				<AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
>                                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
>                                 xsi:type="xs:string"
>                                 >example@example.com</AttributeValue>
> 				<AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
>                                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
>                                 xsi:type="xs:string"
>                                 >dona.moore@example.com</AttributeValue>
> </Attribute>
> 
> OpenID Connect
> 
>   "mail": [
>     "dona.moore@example.com",
>     "example@example.com"
>   ]
> 
> ```



### Identity Federation

-   *Identity Federation* not configured

    When the application uses corporate IdP for authentication, and the *Use Identity Authentication user store* option under *Identity Federation* is disabled, the attributes configurations with default values in the administration console for SAP Cloud Identity Services are not relevant. For more information about the corporate identity provider scenario, see [Corporate Identity Providers](corporate-identity-providers-19f3eca.md) and [Configure Identity Federation](configure-identity-federation-c029bbb.md).

    The configuration of the attributes with default values for the system applications is disabled.

-   *Identity Federation* configured

    When the application uses a corporate IdP for authentication, and the *Use Identity Authentication user store* under *Identity Federation* option is enabled, the attributes with default values in the administration console for SAP Cloud Identity Services can be configured to reference attributes coming from the assertion of the corporate IdP for the user and merge them with the attributes coming from Identity Authentication, and thus be sent to the application.

    To configure Identity Authentication to reference attributes coming from the assertion of the corporate IdP, you must use the following format for the attribute:

    `<attribute_name> = <prefix> ${corporateIdP.<corporateIdP_attribute_name><:regex[filter]><:function[<method>]>} <suffix>`

    ****


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Required
    
    </th>
    <th valign="top">

    Notes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `attribute_name`
    
    </td>
    <td valign="top">
    
    Yes
    
    </td>
    <td valign="top">
    
    The name of the attribute as defined in the administration console. Free text.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `prefix`
    
    </td>
    <td valign="top">
    
    No
    
    </td>
    <td valign="top">
    
    Free text.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `corporateIdP`
    
    </td>
    <td valign="top">
    
    Yes
    
    </td>
    <td valign="top">
    
    Fixed string, indicating that the value is taken from the assertion coming from the corporate IdP.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `corporateIdP_attribute_name`
    
    </td>
    <td valign="top">
    
    Yes
    
    </td>
    <td valign="top">
    
    The specific attribute from the corporate IdP, whose value is taken.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `:regex[<filter>]`
    
    </td>
    <td valign="top">
    
    No
    
    </td>
    <td valign="top">
    
    Filter the attributes from the corporate IdP.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `:function[<method>]`
    
    </td>
    <td valign="top">
    
    No
    
    </td>
    <td valign="top">
    
    Methods to convert the attributes. Currently the supported methods are:

    -   uppercase - the attribute is converted to uppercase letters.

    -   lowercase - the attribute is converted to lowercase letters.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `suffix`
    
    </td>
    <td valign="top">
    
    No
    
    </td>
    <td valign="top">
    
    Free text.
    
    </td>
    </tr>
    </table>
    
    > ### Example:  
    > For example, you have set up a scenario where Identity Authentication acts as a proxy. The default authenticating identity provider is the corporate IdP, and the *Identity Federation* option is configured for that corporate IdP.
    > 
    > The corporate IdP is configured to send the groups with the `group` user attribute.
    > 
    > You want to send the groups coming from the corporate IdP to the application so you have defined the following attribute in the administration console for SAP Cloud Identity Services:
    > 
    > **Configuration of Attributes with Default Values in Administration Console**
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > Attribute
    > 
    > </th>
    > <th valign="top">
    > 
    > Value
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > groups
    > 
    > </td>
    > <td valign="top">
    > 
    > Group $\{corporateIdP.groups\} Member
    > 
    > </td>
    > </tr>
    > </table>
    > 
    > Dona Moore is assigned to the groups *Management* and *Development* in the corporate IdP. When she logs on to the corporate portal of the company, Identity Authentication sends the `groups` coming from the corporate IdP in the following way:
    > 
    > ```
    >  
    > SAML 2.0
    > 
    > <Attribute Name="groups">
    > 				<AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
    >                                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    >                                 xsi:type="xs:string"
    >                                 >Group Development Member</AttributeValue>
    > 				<AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
    >                                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    >                                 xsi:type="xs:string"
    >                                 >Group Management Member</AttributeValue>
    > </Attribute>
    > 
    > OpenID Connect
    > 
    >   "groups": [
    >     "Group Development Member",
    >     "Group Management Member"
    >   ]
    > 
    > ```

    The example can be expanded with the filtering option.

    > ### Example:  
    > Again, you have a scenario where Identity Authentication is a proxy. The default authenticating identity provider is the corporate IdP, and the *Identity Federation* option is configured for that corporate IdP.
    > 
    > The corporate IdP is configured to send the groups with the `group` user attribute.
    > 
    > You don't want to send all the groups coming from the corporate IdP to the application so you have defined the following attribute in the administration console for SAP Cloud Identity Services:
    > 
    > **Configuration of Attributes with Default Values in Administration Console**
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > Attribute
    > 
    > </th>
    > <th valign="top">
    > 
    > Value
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > groups
    > 
    > </td>
    > <td valign="top">
    > 
    > $\{corporateIdP.groups:regex\[ABC-\]\}
    > 
    > </td>
    > </tr>
    > </table>
    > 
    > Michael Adams is assigned to the groups *ABC-Management*, *Development* , and *ABC-Everyone* in the corporate IdP. When he logs on to the corporate portal of the company, Identity Authentication sends just those `groups` coming from the corporate IdP, that matches *ABC-*, in the following way:
    > 
    > ```
    > 
    > SAML 2.0
    > 
    > </Attribute>
    > 				<Attribute Name="groups"> <AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
    >                                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    >                                 xsi:type="xs:string"
    >                                 >ABC-Everyone</AttributeValue> <AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
    >                                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    >                                 xsi:type="xs:string"
    >                                 >ABC-Management</AttributeValue> </Attribute>
    > 
    > OpenID Connect
    > 
    >   "groups": [
    >     "ABC-Everyone",
    >     "ABC-Management"
    >   ]
    > 
    > ```

    > ### Example:  
    > Another scenario is where Identity Authentication is again a proxy. The default authenticating identity provider is the corporate IdP, and the *Identity Federation* option is configured for that corporate IdP.
    > 
    > The corporate IdP is configured to send the email with the `mail` user attribute. The incoming mail attribute from corporate IdP is in mixed case and it is converted to lower case. For example, Michael Adams' email in the corporate IdP is in mixed case Michael.Adams@example.com, and it is converted into lower case michael.adams@example.com.
    > 
    > **Configuration of Attributes with Default Values in Administration Console**
    > 
    > 
    > <table>
    > <tr>
    > <th valign="top">
    > 
    > Attribute
    > 
    > </th>
    > <th valign="top">
    > 
    > Value
    > 
    > </th>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > mail
    > 
    > </td>
    > <td valign="top">
    > 
    > $\{corporateIdP.mail:function\[lowercase\]\}
    > 
    > </td>
    > </tr>
    > </table>

    > ### Remember:  
    > When Identity Authentication is configured to reference an attribute from the corporate IdP, but this attribute isn't sent in the corporate IdP assertion, the attribute isn't sent to the application either.
    > 
    > If the definition of the attribute includes prefix and/or suffix, only the prefix and/or suffix is sent.
    > 
    > However, if the corporate IdP is not configured to send the `phone` attribute, the response includes only the prefix and suffix, defined in the administration console for SAP Cloud Identity Services:
    > 
    > > ### Example:  
    > > For example, you want to send the `phone` attribute coming from the corporate IdP to the application. You have defined the following attribute in the administration console for SAP Cloud Identity Services:
    > > 
    > > **Configuration of Attributes with Default Values in Administration Console**
    > > 
    > > 
    > > <table>
    > > <tr>
    > > <th valign="top">
    > > 
    > > Attribute
    > > 
    > > </th>
    > > <th valign="top">
    > > 
    > > Value
    > > 
    > > </th>
    > > </tr>
    > > <tr>
    > > <td valign="top">
    > > 
    > > Phone
    > > 
    > > </td>
    > > <td valign="top">
    > > 
    > > \+49 $\{corporateIdP.phone\} Corporate Phone
    > > 
    > > </td>
    > > </tr>
    > > </table>
    > > 
    > > ```
    > > 
    > > SAML 2.0
    > > 
    > > </Attribute> 
    > > 				<Attribute Name="Phone"> <AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
    > >                                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    > >                                 xsi:type="xs:string"
    > >                                 >+49 Corporate Phone</AttributeValue>
    > > </Attribute>
    > > 
    > > OpenID Connect
    > > 
    > > "Phone": "+49 Corporate Phone"
    > > ```




### Send Identity Directory Custom Schema Attributes

You can configure Identity Authentication to send the Identity Directory custom schema attributes as attributes into authentication tokens to applications.

You can define complex custom schema attributes with single-value child attributes.

> ### Example:  
> For example, you have set up a scenario where Identity Authentication acts as a proxy. The default authenticating identity provider is the corporate IdP, and the *Identity Federation* option is configured for that corporate IdP.
> 
> Michael Adams is a user from the corporate identity provider. He is created on the proxy IdP with the custom schema `urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile` with two single-valued attributes, `birthday` and `hobby`, and the complex attribute `name` with its child attribute `firstName`. He logs on to the company's portal with the corporate identity provider.
> 
> The default attributes for the application are configured in the administration console as follows:
> 
> **Configuration of Attributes with Default Values in Administration Console**
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Attribute
> 
> </th>
> <th valign="top">
> 
> Value
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> name
> 
> </td>
> <td valign="top">
> 
> $\{urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile.name.firstName\}
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> hobby
> 
> </td>
> <td valign="top">
> 
> $\{urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile.hobby\}
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> birthday
> 
> </td>
> <td valign="top">
> 
> $\{urn:sap:cloud:scim:schemas:extension:custom:2.0:Profile.birthday\}
> 
> </td>
> </tr>
> </table>
> 
> When Michael logs on the application, the values "Michael", "cycling", and "2000-01-02T0:00:00Z" are added to application token during authentication, and received by the application.
> 
> The attributes are added both to SAML 2.0 and OIDC tokens.



<a name="loioa2f1e4692e7d4379ab82144ab309e7b3__steps_dtr_4xc_fzb"/>

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

    -   *Self-defined Attributes* - self-created applications or automatically created single-tenant applications.
        1.  Choose *Add button to add new attribute for the application* \> *provide the name* \> *Expression* \> *provide the value*.

        2.  Choose *plus button next to an attribute to set multiple values for the attribute* \> *Expression* \> *provide the new value*.



7.  Save your configuration.


