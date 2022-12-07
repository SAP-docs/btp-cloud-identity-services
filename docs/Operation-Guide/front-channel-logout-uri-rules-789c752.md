<!-- loio789c752d70e64e6c90839284b511e7d7 -->

# Front-Channel Logout URI Rules

Rules for the front-channel URIs.



The front-channel URI specifies where the browser of the OpenID Connect application ends up after logout is triggered. The service ensures that all other sessions of the user are ended as well, including any SAML sessions or sessions with corporate identity providers.

The front-channel logout URI must be in the following format:

`protocol://domain<:port>/<path><?query parameters>`

For example: `https://example.com:70/logout?abc=123`.

When you construct the front-channel URIs have the following in mind:



<a name="loio789c752d70e64e6c90839284b511e7d7__section_wwb_gfp_qnb"/>

## Length

The length is limited to 499 characters.



<a name="loio789c752d70e64e6c90839284b511e7d7__section_xgl_bl3_qnb"/>

## Domains

-   Protocols - Use the HTTPS protocol. The HTTP protocol is only allowed for localhost.

    > ### Example:  
    > https://example.com
    > 
    > http://localhost

-   Localhost - It's allowed in the domain part.

    > ### Example:  
    > http://localhost
    > 
    > https://localhost

-   Wildcards - Only absolute URIs are allowed.
-   IP Addresses - Usage of IP addresses is not allowed.



## Ports \(optional\)

After the domain you can put port number. Always use a leading colon \(`:`\).

> ### Example:  
> https://example.com:8080/logout?abc=123



<a name="loio789c752d70e64e6c90839284b511e7d7__section_elx_zcm_tvb"/>

## Fragments

> ### Restriction:  
> Fragments are not allowed. For example, if you use `https://example.com/path#index.html`, the `#index.html` is not allowed in that case.

**Related Information**  


[Redirect URIs, Post Logout Redirect URI Rules](redirect-uris-post-logout-redirect-uri-rules-48fdb9a.md "Rules for the redirect URIs or post logout redirect URIs.")

[Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md "Set the token policy for a specific OpenID Connect application. Configure the validity of the refresh token, access and id_token, and the maximum sessions per user.")

[OpenID Connect Front-Channel Logout 1.0](https://openid.net/specs/openid-connect-frontchannel-1_0.html)

