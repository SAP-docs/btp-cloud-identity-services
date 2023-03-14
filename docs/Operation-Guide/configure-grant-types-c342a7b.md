<!-- loioc342a7b6a5d549f28b1c1d61acbe4b72 -->

# Configure Grant Types

Configure the allowed grant type for your OpenID Connect application.



<a name="loioc342a7b6a5d549f28b1c1d61acbe4b72__prereq_grq_3jn_v2b"/>

## Prerequisites

You have an OpenID Connect application in the administration console for SAP Cloud Identity Services. For more information, see [Create OpenID Connect Application](create-openid-connect-application-62fb1c3.md).



## Context

To configure the grant type, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *OpenID Connect Configuration*.

6.  Configure the allowed grant types for the application.


    <table>
    <tr>
    <th valign="top">

    Grant Type


    
    </th>
    <th valign="top">

    Default Behavior


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    **Authorization Code**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Authorization Code / Enforce PKCE \(S256\)**


    
    </td>
    <td valign="top">

    not-selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Password**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **JWT Bearer**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Implicit**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Refresh**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Client Credentials**


    
    </td>
    <td valign="top">

    selected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Token Exchange \(RFC 8693\)**


    
    </td>
    <td valign="top">

    not-selected


    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > Beware that for each flow the respective grant type must be selected.

7.  Save your selection.

    Once the application has been changed, the system displays the message ***Application <name of application\> updated***.


**Related Information**  


[Redirect URIs, Post Logout Redirect URI Rules](redirect-uris-post-logout-redirect-uri-rules-48fdb9a.md "Rules for the redirect URIs or post logout redirect URIs.")

[Front-Channel Logout URI Rules](front-channel-logout-uri-rules-789c752.md "Rules for the front-channel URIs.")

[Token Policy Configuration for Applications](token-policy-configuration-for-applications-c4ba52e.md "Set the token policy for a specific OpenID Connect application. Configure the validity of the refresh token, access and id_token, and the maximum sessions per user.")

