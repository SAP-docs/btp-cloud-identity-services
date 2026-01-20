<!-- loiof19e580088e74aaa96087f1def8972cd -->

# Enrich Token Claims Coming from Corporate IdP

Tenant administrator can modify the token claims received from the corporate identity provider \(IdP\) before they are sent to the application that uses the corporate IdP for authentication.



## Context

The claims are put in the JSON Web Tokens \(JWTs\) for the OpenID Connect application. For more information, see [Configuring OpenID Connect \(OIDC\)](configuring-openid-connect-oidc-a789c9c.md).

For the OpenID Connect applications, you can configure claims with:

-   dynamic values - The claims can take up to two dynamic values. They are added into the tokens in the following pattern: `<prefix> ${<received_attribute>} <suffix>`. You can use also multivalue claims.

    > ### Restriction:  
    > The combination of two multivalue claims is not allowed.

-   static values

You can add up to 30 claims per corporate IdP.



### Identity Federation

If *Use Identity Authentication user store* under *Identity Federation* is disabled, modify the token claims received from the corporate identity provider \(IdP\). The claims enriched in the administration console for SAP Cloud Identity Services are thus taken into consideration and sent to the application in the modified form. The application specific settings, the claims in the *Default Attributes* section, are ignored.

If *Use Identity Authentication user store* under *Identity Federation* is enabled, use the modified claims in the *Default Attributes* section for the applications that use the corporate IdP for authentication. For more information, see [Configuring Attributes Based on Flexible Expressions](configuring-attributes-based-on-flexible-expressions-a2f1e46.md).

> ### Note:  
> You can also overwrite the `Subject Name Identifier` via the Enriched Token Claims option. Identity Authentication sends the modified claim to the application as `subject` in the OpenID Connect tokens.
> 
> The `Subject Name Identifier` must be added in the following pattern:
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Claim
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
> `<prefix> ${<NameID>} <suffix>`
> 
> </td>
> </tr>
> </table>

To modify the claims coming from the corporate IdP, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

4.  Choose the *Enriched Token Claims* list item.

5.  Add the claims as received from the corporate IdP with the new values to be sent to the application.

6.  Save your configuration.

    If the operation is successful, you receive the message ***Identity provider "<name of identity provider\>" updated***.


