<!-- loio789c752d70e64e6c90839284b511e7d7 -->

# Logout URI Rules

Rules for the front and back-channel URIs.



Identity Authentication triggers a logout request to the front or back-channel URI.

The front and back-channel logout URI must be in the following format:

`protocol://domain<:port>/<path><?query parameters>`

For example: `https://example.com:70/logout?abc=123`.

When you construct the front and back-channel URIs have the following in mind:



<a name="loio789c752d70e64e6c90839284b511e7d7__section_wwb_gfp_qnb"/>

## Length

The length is limited to 499 characters.



<a name="loio789c752d70e64e6c90839284b511e7d7__section_xgl_bl3_qnb"/>

## Domains

-   Protocols - Use the HTTPS protocol. The HTTP protocol is only allowed for localhost.

    > ### Example:  
    > https://example.com/logout

-   Localhost - It's allowed in the domain part.

    > ### Example:  
    > http://localhost/logout
    > 
    > https://localhost/logout

-   Wildcard - It's allowed in the domain part. The wildcard support is mainly for multitenant applications.

    > ### Example:  
    > https://\*.example.com/logout
    > 
    > Allow during authorize call to register a URI with parameter `logout_uri`, for example: `https://app1.example.com/logout`.

-   IP Addresses - Usage of IP addresses is not allowed.



## Ports \(optional\)

After the domain part you can put the port numbers. Always use a leading colon \(`:`\).

> ### Example:  
> https://example.com:8080/logout



<a name="loio789c752d70e64e6c90839284b511e7d7__section_elx_zcm_tvb"/>

## Fragments

> ### Restriction:  
> Usage of fragment identifier \(`#`\) is not allowed. For example, you can't use `https://example.com/path#index.html`.

**Related Information**  


[Redirect URIs, Post Logout Redirect URI Rules](redirect-uris-post-logout-redirect-uri-rules-48fdb9a.md "Rules for the redirect URIs or post logout redirect URIs.")

[Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md "Set the token policy for a specific OpenID Connect application. Configure the validity of the refresh token, access and id_token, and the maximum sessions per user.")

[Configure Grant Types](configure-grant-types-c342a7b.md "Configure the allowed grant type for your OpenID Connect application.")

[OpenID Connect Front-Channel Logout 1.0 Specification](https://openid.net/specs/openid-connect-frontchannel-1_0.html)

[OpenID Connect Back-Channel Logout 1.0 Specification](https://openid.net/specs/openid-connect-backchannel-1_0.html#Backchannel)

