<!-- loio01171f7799bb46c089c40a0b2b5896fb -->

# Disable ID Token Hints for Corporate Identity Providers

Corporate identity providers sometimes have trouble when the ID token is included as a URL parameter in logout requests. Use this option to disable the inclusion of the ID token.



## Context

Identity Authentication includes the ID token in the `id_token_hint` URL parameter. This parameter can help the corporate identity provider identify the applications relevant to this call. For example, the user triggered a logout and the identity provider needs to identify all the applications related to the session. Including the ID token can exceed the length of URL that the corporate identity provider can consume. Your best option is then to disable the `id_token_hint`.



## Procedure

1.  In the administration console for SAP Cloud Identity Services, navigate to the OpenID Connect configuration of your corporate identity provider.

    For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).

2.  Enable the *Disable Logout ID Token Hint* check box.

3.  Save your entries.


