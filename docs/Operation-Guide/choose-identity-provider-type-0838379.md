<!-- loio08383795c93d439c91f0bba2318b78e3 -->

# Choose Identity Provider Type

This topic shows you how to choose a type for the corporate identity provider.



## Prerequisites

You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md).

4.  Choose *Identity Provider Type*.

5.  Select the radio button for the type of the identity provider.

    You can choose one of the following options:

    -   SAML 2.0 Compliant

    -   SAP Single Sign-On \(SAML 2.0\)

    -   Microsoft ADFS / Entra ID \(SAML 2.0\)

        > ### Caution:  
        > For this type the digest algorithm of the corporate identity provider must be *SHA-256*. For more information, see 2. Configure Trust on Identity Authentication Side in [Configure Trust with Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md).

    -   OpenID Connect Compliant


6.  Save your selection.

    Once the identity provider has been updated, the system displays the message ***Identity provider <name of identity provider\> updated***.


**Related Information**  


[Corporate Identity Providers](corporate-identity-providers-19f3eca.md "Initially, Identity Authentication is set as the default identity provider for the applications. This section describes the scenarios in which Identity Authentication acts as a proxy to delegate the authentication to a corporate identity provider.")

[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

