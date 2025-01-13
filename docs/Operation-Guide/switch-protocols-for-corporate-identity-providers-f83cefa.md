<!-- loiof83cefa782dc4e96bdf9896f44657cb3 -->

# Switch Protocols for Corporate Identity Providers

To take advantage of features of other protocols, switch the protocol of your corporate identity provider, for example from SAML to OpenID Connect \(OIDC\).

SAML isn't obsolete, but the trend is clear that many corporate identity providers are offering more new features with OIDC and not SAML. OIDC also enables you to take advantage of token exchange scenarios to support principal propagation. However, switching from OIDC to SAML is also possible.

To support your move to a new protocol for your corporate identity provider, you can switch all your applications at once or move one application at a time.

<a name="loio8c6d6a2adbef4e148ed38226ca89284c"/>

<!-- loio8c6d6a2adbef4e148ed38226ca89284c -->

## Impact on Applications

While this configuration doesn't necessarily affect your applications directly, what is application-specific are the attribute mappings between the attributes the corporate identity provider sends and the attributes the application needs. The identity provider might send different attribute names with the new protocol or even different values, for example, a different subject.

When identity federation is enabled, these mappings are application-specific in Identity Authentication.

For more information, see [Configure Identity Federation](configure-identity-federation-c029bbb.md).

For each application, check the configurations, such as:

-   Attribute mappings

-   Configuration of SAML 2.0 request to corporate identity providers that includes authentication context and issuer.

-   Identity provider-initiated single sign-on

    OIDC identity providers don’t support such options. Switching to OIDC can break a scenario.

-   You can't configure the signing and encryption methods for JWT tokens in OIDC identity providers.

-   Single logout isn't supported by all OIDC providers.


<a name="loiod3feee7b76a84f7eac58f283a7df6f8a"/>

<!-- loiod3feee7b76a84f7eac58f283a7df6f8a -->

## Switch All Applications at Once

If you're confident that the new integration with the corporate identity provider will work immediately or any issues can be solved in your maintenance window, you can switch to the new corporate identity provider all at once.



<a name="loiod3feee7b76a84f7eac58f283a7df6f8a__prereq_elz_2k5_1yb"/>

## Prerequisites

Plan for some downtime during the switch over.



## Context

-   Advantage: Efficiency. Move many applications to the new protocol at once.

-   Disadvantage: Risk. Unless you've configured a test tenant with your corporate identity provider and your applications, you risk downtime if the applications encounter problems with the new setup.




## Procedure

1.  Go to the *Identity Provider Type* of your identity provider configuration and change the protocol.

    For more information, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md).

2.  Make any protocol-specific configurations.

    See also:

    -   [Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md)

    -   [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md)


3.  Make any application-specific configurations.

    For more information, see [Impact on Applications](switch-protocols-for-corporate-identity-providers-f83cefa.md#loio8c6d6a2adbef4e148ed38226ca89284c).


<a name="loio4163c210c5864c069afd1dfee64bc209"/>

<!-- loio4163c210c5864c069afd1dfee64bc209 -->

## Switch One Application at a Time

If you have many applications, this approach requires more time. However, you can observe any changes in the behavior of your applications and fix them.



## Context

-   Advantage: Lower risk. If you have many applications, the potential for downtime is lower. You only migrate one application at a time.

-   Disadvantage: Time. It takes longer to migrate all applications to the new protocol, because you migrate one application at a time.




## Procedure

1.  Create a new identity provider configuration under the new protocol by copying the configuration of your existing corporate identity provider under the old protocol.

    Use the *Copy Settings from Identity Provider* option.

    For more information, see [Create Corporate IdP in Administration Console](create-corporate-idp-in-administration-console-ae99ba9.md).

2.  Make any protocol-specific configurations.

    See also:

    -   [Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md)

    -   [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md)


3.  In each application configuration, change the identity provider to the new copy under the new protocol.

    For more information, see [Authenticating Identity Provider for an Application](authenticating-identity-provider-for-an-application-b3aae12.md).

4.  Make any application-specific configurations.

    For more information, see [Impact on Applications](switch-protocols-for-corporate-identity-providers-f83cefa.md#loio8c6d6a2adbef4e148ed38226ca89284c).

5.  Check that you've moved all your applications from the old identity provider configuration.

    To see a list of the applications that use your old identity provider configuration, go to the identity provider configuration and choose *Trusting Applications*.

6.  When the list of *Trusting Applications* is empty, delete the old identity provider configuration.

    For more information, see [Delete Corporate Identity Providers](delete-corporate-identity-providers-25a17de.md).


