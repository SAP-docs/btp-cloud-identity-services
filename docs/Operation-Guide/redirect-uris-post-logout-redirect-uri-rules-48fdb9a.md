<!-- loio48fdb9ab1a094859ac79c9b25e0ab58b -->

# Redirect URIs, Post Logout Redirect URI Rules

Rules for the redirect URIs or post logout redirect URIs.



The redirect URI defines the redirection URIs to which the response can be sent. The post logout redirect URI defines the redirection URIs where the user can be forwarded after logout.

The redirect URI or post logout redirect URI must be in the following format:

`protocol://domain<:port>/<path>`

For example: `https://example.com:70/path`.

> ### Note:  
> The URL parameters are not taken into consideration during runtime.

When you construct the redirect URIs or post logout redirect URIs have the following in mind:



<a name="loio48fdb9ab1a094859ac79c9b25e0ab58b__section_wwb_gfp_qnb"/>

## Length

The length is limited to 499 characters.



<a name="loio48fdb9ab1a094859ac79c9b25e0ab58b__section_pm2_3xh_qnb"/>

## Domains

Top level domains are allowed. The domain part can't end with a hyphen "-".

-   Protocols - Use the HTTPS protocol. The HTTP protocol is only allowed for localhost.

    > ### Example:  
    > https://example.com
    > 
    > https://10.11.12.13

-   Localhost is allowed in the domain part.

    > ### Example:  
    > http://localhost
    > 
    > https://localhost
    > 
    > http://127.0.0.1
    > 
    > https://127.0.0.1

-   Non-ascii characters are not allowed in the domain part.
-   Custom schemas are supported, except `ftp`, `sftp`, `tftp`, `file`, `telnet` and `http`.

    Custom schemas must have at least 2 characters. The following are allowed: lower case characters, numbers, and the special characters "`.`", "`-`", and "`+`" .

    > ### Example:  
    > custom-schema://example




<a name="loio48fdb9ab1a094859ac79c9b25e0ab58b__section_xgl_bl3_qnb"/>

## Wildcards

-   You can use asterisk \(`*`\) in the beginning, only for the first subdomain.

    > ### Example:  
    > https://\*.test.example.com

-   You can use asterisk \(\*\) as first subdomain for localhost addresses. No other subdomains allowed.

    > ### Example:  
    > http://\*.localhost
    > 
    > https://\*.localhost

-   You can use asterisk \(`*`\) in between the domain part, but there must be at least 3 subdomains left after the asterisk.

    > ### Example:  
    > https://app.\*.test.example.com

-   You can use asterisk \(`*`\) at the end of the path, or between paths.

    > ### Example:  
    > https://example.com/path/\*
    > 
    > https://example.com/path/\*/path2

-   You can use double wildcard, two asterisks \(`**`\), at the end of a path.

    > ### Example:  
    > https://example.com/\*\*
    > 
    > http://localhost/path/\*/path2/\*\*




## Ports \(optional\)

After the domain you can put port number. Always use a leading colon \(`:`\).

> ### Example:  
> https://example.com:8080

**Related Information**  


[Front-Channel Logout URI Rules](front-channel-logout-uri-rules-789c752.md "Rules for the front-channel URIs.")

[Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md "Set the token policy for a specific OpenID Connect application. Configure the validity of the refresh token, access and id_token, and the maximum sessions per user.")

