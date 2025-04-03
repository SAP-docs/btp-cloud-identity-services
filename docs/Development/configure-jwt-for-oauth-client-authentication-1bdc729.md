<!-- copy1bdc7291de0e4e529648bfe05856029a -->

# Configure JWT for OAuth Client Authentication

Configure the JSON Web Token \(JWT\) - the issuer and subject of tokens for JWT client authentication in token requests, or the URI for JSON web key retrieval for client authentication.



<a name="copy1bdc7291de0e4e529648bfe05856029a__prereq_lz2_wxt_1tb"/>

## Prerequisites

You have an OpenID Connect application.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](../Operation-Guide/create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Application APIs*, choose *Client Authentication*.

6.  Under *JSON Web Tokens*, configure one of the following options and save your changes:

    -   \(For RFC 7523-based JWT client tokens\) Choose the *Add* button for *Configure Trust by Issuer* and provide the required info in the popup:

        **Configure Trust by Issuer**


        <table>
        <tr>
        <th valign="top">

        Field
        
        </th>
        <th valign="top">

        Notes
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        *Description*
        
        </td>
        <td valign="top">
        
        \(Optional\) - Provide information about the token in the provided field.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Choose *Issuer Configuration* \> *Manual Configuration* radio-button.

        > ### Note:  
        > When you choose *Manual Configuration* radio-button the *Corporate Identity Provider* section is not configurable.


        
        </td>
        <td valign="top">
        
        Under *Manual Configuration* configure:

        1.  *Issuer* \(Required\) - The issuer must be OpenID Connect compliant.
        2.  *JSON Web Key Set URI* \(Required\) - Choose *Check for Metadata* button. If the entered issuer is verified as OpenID Connect compliant, the JSON Web Key Set URI will be retrieved automatically. Otherwise, you need to explicitly specify the *JSON Web Key Set URI* in the field.
        3.  *Refresh Interval* \(Optional\) - Refreshes the URI automatically if it is older than the selected interval. Choose from:
            -   24 hours \(default choice\)

            -   12 hours




        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Choose *Issuer Configuration* \> *Corporate Identity Provider* radio-button.

        > ### Note:  
        > When you choose *Corporate Identity Provider* radio-button, the *Manual Configuration* section is not configurable.


        
        </td>
        <td valign="top">
        
        *Name* - \(Required\) Choose from OpenID Connect compliant corporate identity providers.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *General*
        
        </td>
        <td valign="top">
        
        1.  *Subject* \(Required\) - The sub \(subject\) that is expected in the token.

            > ### Tip:  
            > If you want to use an OAuth 2.0 token from a corporate identity provider as client credentials for an OpenID Connect application in Identity Authentication, and your OAuth client in the corporate identity provider belongs to a pre-configured application, the subject in the token is the Object ID of that pre-configured application.

        2.  *Audience* \(Optional\) - The `audience` claim of the identity provider.
        3.  `API Permission Groups` \(Optional\) - The field is enabled only when the *Provided APIs* option is configured. For more information, see [Provide APIs for Consumption by Other Applications](provide-apis-for-consumption-by-other-applications-9d2fe83.md).


        
        </td>
        </tr>
        </table>
        
    -   \(For OpenID Connect-based JWT client tokens\) Choose the *Add* button for *Configure Trust by URI* and provide the required info in the popup:

        **Configure Trust by URI**


        <table>
        <tr>
        <th valign="top">

        Field
        
        </th>
        <th valign="top">

        Notes
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        *Description*
        
        </td>
        <td valign="top">
        
        \(Optional\) You can provide information about the URI here.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *URI*
        
        </td>
        <td valign="top">
        
        \(Required\) The JSON Web Key Set \(JWKS\) URI of the trusted party.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Refresh Interval*
        
        </td>
        <td valign="top">
        
        \(Optional\) Refreshes the URI automatically if it is older than the selected interval. Choose from:

        -   24 hours \(default choice\)

        -   12 hours



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *API Access*
        
        </td>
        <td valign="top">
        
        > ### Note:  
        > This section is read-only. The predefined choice is OpenID.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *API Permission Groups*
        
        </td>
        <td valign="top">
        
        \(Optional\) `API Permission Groups` field is enabled only when the *Provided APIs* option is configured. For more information, see [Provide APIs for Consumption by Other Applications](provide-apis-for-consumption-by-other-applications-9d2fe83.md).
        
        </td>
        </tr>
        </table>
        


**Related Information**  


[Configure Secrets for API Authentication](configure-secrets-for-api-authentication-9ea13fe.md "This document describes how developers configure secrets with scopes and validity for client authentication.")

[Unlock Client ID](unlock-client-id-e5a6b85.md "Unlock the client ID after five failed logon attempts before the automatic unlock time of 60 minutes has passed.")

[Disable Client ID Locking](disable-client-id-locking-aa38152.md "You can disable the automatic lock of the client ID after five failed logon attempts.")

[Configure Certificates for API Authentication](configure-certificates-for-api-authentication-47e9866.md "This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.")

[JSON Web Token \(JWT\) Profile for OAuth 2.0 Client Authentication and Authorization Grants](https://www.rfc-editor.org/rfc/rfc7523)

[Proof-of-Possession Key Semantics for JSON Web Tokens \(JWTs\)](https://www.rfc-editor.org/rfc/rfc7800.html)

[JSON Web Token Client Authentication](https://openid.net/specs/openid-connect-core-1_0.html#ClientAuthentication)

