<!-- loio04a1a0b876b54d1b9c6b735f81e24287 -->

# Enforce Nonces for Corporate Identity Providers

Some corporate identity providers require that applications send nonces. If your applications don't comply, enable this feature to ensure that one is sent.



## Context

A nonce is a string associated with a client session and token and is used to mitigate replay attacks. If an application supplies a nonce, Identity Authentication forwards the nonce with requests to the corporate identity provider. By default, if there's no nonce, then Identity Authentication just forwards the request as is. When this feature is enabled and an application doesn't supply a nonce, Identity Authentication generates nonces before forwarding requests to the corporate identity provider.



## Procedure

1.  In the administration console for SAP Cloud Identity Services, navigate to the OpenID Connect configuration of your corporate identity provider.

    For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).

2.  Enable the *Enforce Nonce* check box.

    Use the *Validate* button to confirm that the configuration is still working.

3.  Save your entries.


