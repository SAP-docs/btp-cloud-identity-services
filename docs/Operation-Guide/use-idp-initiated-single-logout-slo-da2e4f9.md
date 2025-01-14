<!-- loioda2e4f9866dc45f0b4723ca41f051bea -->

# Use IdP-Initiated Single Logout \(SLO\)

Use this procedure to start the single logout \(SLO\) process at Identity Authentication as an identity provider.



## Context

Single Logout \(SLO\) enables users to cleanly close all their sessions in an SSO landscape, even across domains. In this identity provider \(IdP\) initiated SLO scenario, the user initiates a logout request at Identity Authentication being an identity provider.

SLO can also be initiated at the corporate identity provider \(IdP\). Identity Authentication accepts SLO requests from corporate identity providers via both SAML and OpenID Connect.



## Procedure

1.  Direct the user browser to your SLO endpoint.

    Identity Authentication single logout endpoint follows the template `https://<tenant ID>.accounts.ondemand.com/saml2/idp/slo` or `https://<tenant ID>.accounts.cloud.sap/saml2/idp/slo`

2.  **Optional:** Add the `RelayState` parameter to provide a relative URL to which the identity provider redirects after the SLO process is complete.

    > ### Remember:  
    > The `RelayState` must be a trusted domain and valid URL. For example, `https://myapplication.ondemand.com/saml2/idp/slo?RelayState=https://example.com`




<a name="loioda2e4f9866dc45f0b4723ca41f051bea__result_nnr_xm1_dlb"/>

## Results

After successful logout, the identity provider either redirects the user to the URL provided in the RelayState, or if RelayState isn’t provided, the user is redirected to the profile page.

**Related Information**  


[Configure Trusted Domains](configure-trusted-domains-08fa1fe.md "Service providers that delegate authentication to Identity Authentication can protect their applications when using embedded frames, also called overlays, or when allowing user self-registration.")

