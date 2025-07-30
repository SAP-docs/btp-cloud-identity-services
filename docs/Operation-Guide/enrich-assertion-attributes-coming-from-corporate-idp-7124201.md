<!-- loio7124201682434efb946e1046fde06afe -->

# Enrich Assertion Attributes Coming from Corporate IdP

Tenant administrator can modify the assertion attributes received from the corporate identity provider \(IdP\) before they are sent to the application \(service provider\) that uses the corporate IdP for authentication.



## Context

The attributes received from the corporate IdP by Identity Authentication are modified and thus sent to the application in the assertion.

The attributes are also put in the `id_token` if the application is OpenID connect. For more information, see [Configuring OpenID Connect](configuring-openid-connect-a789c9c.md).

For both the SAML 2.0 and OpenID Connect applications, you can configure attributes with:

-   dynamic values - The assertion attributes can take up to two dynamic values. They are added into the assertions in the following pattern: `<prefix> ${<received_attribute>} <suffix>`. You can also use multivalue attributes.

    > ### Restriction:  
    > The combination of two multivalue attributes is not allowed. The assertion attributes can take two single value attributes or a single value and a multivalue attribute.

-   static values

> ### Restriction:  
> The `sap_licenses` attribute is not supported for the enrich assertion attributes scenario.

You can add up to 30 attributes per corporate IdP.



### Identity Federation

When the application uses corporate IdP for authentication, the assertion attributes enriched in the administration console for SAP Cloud Identity Services are taken into consideration and sent to the application in the modified form, if the *Use Identity Authentication user store* option under *Identity Federation* is disabled.

If *Identity Federation* is configured, use the modified attributes in the *Default Attributes* section for the applications that use the corporate IdP for authentication. For more information, see [Configuring Attributes Based on Flexible Expressions](configuring-attributes-based-on-flexible-expressions-a2f1e46.md).

> ### Note:  
> You can also overwrite the `Subject Name Identifier` via the Enrich Assertion Attributes option. Identity Authentication sends the modified attribute to the application as `name ID` in the SAML 2.0 assertions, and as `subject` in the OpenID Connect tokens.
> 
> The `Subject Name Identifier` must be added in the following pattern:
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
> NameID
> 
> </td>
> <td valign="top">
> 
> `<prefix>${NameID}<suffix>`
> 
> </td>
> </tr>
> </table>

To modify the assertion attributes coming from the corporate IdP, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md).

4.  Under *Trust*, choose the *Enriched Assertion Attributes* list item.

5.  Add the attributes as received from the corporate IdP with the new values to be sent to the application.

6.  Save your configuration.

    If the operation is successful, you receive the message ***Identity provider "<name of identity provider\>" updated***.


