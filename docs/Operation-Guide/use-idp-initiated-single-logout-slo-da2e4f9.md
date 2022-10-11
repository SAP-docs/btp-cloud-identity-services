<!-- loioda2e4f9866dc45f0b4723ca41f051bea -->

# Use IdP-Initiated Single Logout \(SLO\)

Use this procedure to start the single logout \(SLO\) process at the identity provider.



## Context

Single Logout \(SLO\) enables users to cleanly close all their sessions in a SAML landscape, even across domains. In the identity provider \(IdP\) initiated SLO, the user initiates a logout request at the identity provider.



## Procedure

1.  Direct the user browser to your SLO endpoint.

    Identity Authentication single logout endpoint follows the template `https://<tenant ID>.accounts.ondemand.com/saml2/idp/slo`

2.  Add the Relay State URL parameter.

    Identity Authentication supports only Relay State. Relay State must be a trusted domain and valid URL.




<a name="loioda2e4f9866dc45f0b4723ca41f051bea__result_nnr_xm1_dlb"/>

## Results

After successful logout, the identity provider either redirects the user to the URL provided in the Relay State, or if Relay State isn’t provided, the user is redirected to the profile page.

**Related Information**  


[Configure Trusted Domains](configure-trusted-domains-08fa1fe.md "Service providers that delegate authentication to Identity Authentication can protect their applications when using embedded frames, also called overlays, or when allowing user self-registration.")

