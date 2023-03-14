<!-- loioc4ba52e748554863917b046bf1b7b355 -->

# Token Policy Configuration for Applications

Set the token policy for a specific OpenID Connect application. Configure the validity of the refresh token, access and id\_token, and the maximum sessions per user.



## Context



### Token Policy

The following table lists the token policy options for OIDC applications.

**Token Policy Configuration Parameters**


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 *Refresh Token* 



</td>
<td valign="top">

Sets the refresh token lifetime issued by Identity Authentication. The value can range from 1 to 4320 hours, in other words, from 1 hour to 180 days.

The default value is 12 hours.

> ### Note:  
> When using the authorization code flow, if you set the token policy for refresh tokens longer than the session timeout, add the *offline\_access* scope to your authorization code request. Without this scope, the service deletes the refresh token from the database when the resource owner ends the session \(logs out\). Without the refresh token, the OAuth client can't request new tokens anymore.
> 
> For more information, see:
> 
> -   [Configure Session Timeout](configure-session-timeout-5ca23e4.md)
> 
> -   [Using Authorization Code Flow](using-authorization-code-flow-c135fc4.md)



</td>
</tr>
<tr>
<td valign="top">

 *Access / ID Token* 



</td>
<td valign="top">

Sets the access and id\_token lifetime issued by Identity Authentication. The value can range from 1 to 60 minutes.

The default value is 60 minutes.



</td>
</tr>
<tr>
<td valign="top">

 *Max sessions per user* 



</td>
<td valign="top">

Determines the maximum number of tokens that the service issues for the same session in parallel. Imagine you’re logged on to the application through a web interface and a command-line interface in parallel. Then you'd set this parameter to 2. The value can range from 1 to 10.

The default value is 1.



</td>
</tr>
</table>

> ### Remember:  
> The default configurations for the token policy per application are equal to the tenant token policy. If you configure new values for an application, the service ignores the tenant token policy for that application. For more information about the tenant token policy, see [Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md)



### Refresh Token Usage After Renewal

When refresh token flows fail, you can enable the server to accept a refresh token that was already submitted. Normally, a refresh token can only be used once. The configuration aims to solve issues, for example network problems in refresh token calls, and allow an application to retry this call. Define the behavior of clients depending on your scenario and the risk. If you extend the rotation life time, we recommend revoking existing tokens with a separate call.

**Refresh Token Usage After Renewal**


<table>
<tr>
<th valign="top">

Settings



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Off \(Default\)



</td>
<td valign="top">

The new refresh token immediately invalidates the old one.



</td>
</tr>
<tr>
<td valign="top">

Online scenarios



</td>
<td valign="top">

The new refresh token is created and the old one is still active for 5 minutes.



</td>
</tr>
<tr>
<td valign="top">

Mobile scenarios



</td>
<td valign="top">

The new and old refresh token are valid during the configured refresh token life time.



</td>
</tr>
</table>

> ### Note:  
> For online and mobile scenarios, calls to refresh the old refresh token end in the new token. Calls with the new refresh token, invalidates the old refresh token.

To configure the token policy, proceed as follows:



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

6.  Manually configure the token policy for the application.

    Use the slider or provide a number in the input field above the slider.

7.  **Optional:** If needed, use the reset button to set to the default value.

8.  Save your changes.


**Related Information**  


[Redirect URIs, Post Logout Redirect URI Rules](redirect-uris-post-logout-redirect-uri-rules-48fdb9a.md "Rules for the redirect URIs or post logout redirect URIs.")

[Front-Channel Logout URI Rules](front-channel-logout-uri-rules-789c752.md "Rules for the front-channel URIs.")

[Configure Grant Types](configure-grant-types-c342a7b.md "Configure the allowed grant type for your OpenID Connect application.")

[Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md "You as a tenant administrator can view and configure the tenant OpenID Connect configurations.")

