<!-- loioed2797dcac0643bebc89821faaa97487 -->

# User Attributes

Tenant administrator has an overview of all the attributes provided to the application, regardless of the source of the values, and can provide the attributes needed by the application, specifying the attribute names expected by the application.



<a name="loioed2797dcac0643bebc89821faaa97487__context_ucy_ytc_fzb"/>

## Context

> ### Restriction:  
> The attributes configurations in the administration console for SAP Cloud Identity Services are relevant only when the application uses for authentication Identity Authentication, or when it uses a corporate identity provider \(IdP\), and the *Identity Federation* option is enabled.
> 
> When the application uses a corporate IdP for authentication, and *Identity Federation* is disabled, Identity Authentication sends to the application the attributes that come from the corporate identity provider without changing them, and if configured, some of the same values with additional attribute names, namely configured on the trust to the corporate IdP, enriched assertion attributes or enriched token claims.

> ### Tip:  
> For OpenID Connect, the supported scopes are `email`, `profile`, `openid`, and `groups`. The usage of these claims ensure uniqueness, especially in proxy mode, they are recommended over the configuration of attributes in the administration console for SAP Cloud Identity Services.

The application can get different values for a certain attribute name. The following options for sources are possible:

-   *Identity Directory* - The local user attribute. You choose the value from a drop-down. See [Configuring User Attributes from the Identity Directory](configuring-user-attributes-from-the-identity-directory-d361407.md).
-   *Corporate IdP* - The user attribute provided by the corporate IdP. You just enter the attribute name provided by the corporate IdP. See [Configuring User Attributes from a Corporate Identity Provider](configuring-user-attributes-from-a-corporate-identity-provider-621017f.md).
-   *Expression* - A static or dynamic value. It can be a user attribute coming from *Identity Directory* or *Corporate Identity Provider*, or even a combination of all sources. See [Configuring Attributes Based on Flexible Expressions](configuring-attributes-based-on-flexible-expressions-a2f1e46.md).

> ### Tip:  
> The *Identity Directory* source maps to the *Assertion Attributes* term used before in this documentation.
> 
> Depending on the scenario, the *Corporate Identity Provider* and *Expression* map to the *Default Attributes* term used before in this documentation.

> ### Note:  
> You can specify multiple user attribute values for each user attribute. Up to 300 attribute values are allowed for self-created customer applications and automatically created single-tenant applications, and up to 50 attribute values for automatically created single-tenant applications.
> 
> -   for OpenID Connect - the attributes are included in the token as string if there is one value, and array if multiple.
> 
> -   for SAML 2.0 - the attributes are included in the assertion as one attribute statement with multiple values in it.



### Self-Defined Attributes

If you have self-created applications or automatically created single-tenant applications in your SAP Cloud Identity Services tenant, you configure the attribute mappings under the *Self-Defined Attributes* section in the administration console. You must know the attributes that the application support, and configure the mappings accordingly.



### Application Attributes

If you have subscribed multi-tenant applications in your SAP Cloud Identity Services tenant, the attributes supported by these applications are predefined and listed under the *Primary Attribute* section, with default mappings for source *Identity Directory*. You can see which attributes are supported, and add or remove mappings for the other sources - *Corporate Identity Provider* and *Expression*.

> ### Tip:  
> For some subscribed applications, you might need to add custom attribute mappings \(under the *Self-Defined Attributes* section\). For example, an SAP BTP application connects to another application using a destination that is customer-managed. As *User ID* for principal propagation, the customer decides to use an attribute that is not in the list of predefined application attributes. So, this customer need to add the attribute configured in the destination as a self-defined attribute in the application in the SAP Cloud Identity Services tenant.

