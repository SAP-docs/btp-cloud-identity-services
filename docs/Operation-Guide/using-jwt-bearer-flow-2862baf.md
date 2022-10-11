<!-- loio2862baff60f944878f73897d3aabcc14 -->

# Using JWT Bearer Flow

To authenticate using the JWT Bearer flow, follow the procedures below. Tasks 1 and 2 are configurations on Identity Authentication side. Task 3 is a configuration, done on the client \(relying party\) side.

The JWT Bearer flow is used for token exchanges from a server application, where the server already has a token. For example:

-   To switch for a public client with restricted audience to a confidential client with full audience list
-   To authenticate with a token coming from a different identity provider \(IdP\) to an Identity Authentication token

> ### Remember:  
> If the `id_token` is issued by another OpenID Connect provider, like Azure for example, you must configure that provider as a corporate identity provider in the administration console of Identity Authentication. For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).

