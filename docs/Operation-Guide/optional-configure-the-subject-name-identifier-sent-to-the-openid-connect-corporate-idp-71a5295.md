<!-- loio71a529531dd444bf941c127dde28c626 -->

# \(Optional\) Configure the Subject Name Identifier Sent to the OpenID Connect Corporate IdP

Define the claim which is used as subject name identifier.



<a name="loio71a529531dd444bf941c127dde28c626__prereq_rdz_3dj_zsb"/>

## Prerequisites

You have enabled the *Use Identity Authentication user store* option. For more information, see [Configure Identity Federation](configure-identity-federation-c029bbb.md).



## Context

In this scenario, the tenant administrator can define the claim from the token of the corporate identity provider which Identity Authentication should use as subject name identifier. The Subject Name Identifier configuration defines with which value the identity provider user will be searched in the Identity Authentication user store. The attribute used for the user search is `E-Mail`.

To define the claim which is used as subject name identifier, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

4.  Under *Trust*, choose *Subject Name Identifier*.

5.  Select the Subject Name Identifier from the following:

    -   *None* - Subject claim \(`sub`\) is used as subject name identifier. Corporate IdP decides which attribute to use.
    -   *E-Mail* - E-Mail claim \(`email`\) is used as subject name identifier.

6.  Save your selection.

    Once the identity provider has been updated, the system displays the message ***Identity provider <name of identity provider\> updated***.


**Related Information**  


[Configure Trust with SAML 2.0 Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md "This document is intended to help you configure trust with a SAML 2.0 corporate identity provider. In this scenario Identity Authentication acts as a proxy to delegate the authentication to the SAML 2.0 corporate identity provider.")

[Choose Identity Provider Type](choose-identity-provider-type-0838379.md "This topic shows you how to choose a type for the corporate identity provider.")

