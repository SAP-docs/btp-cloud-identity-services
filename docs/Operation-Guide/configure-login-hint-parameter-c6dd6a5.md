<!-- loioc6dd6a5f141f4df0ae93b98904014e17 -->

# Configure Login Hint Parameter

Tenant administrator can configure the login hint parameter via the administration console for SAP Cloud Identity Services.



## Context

The configuration of the login hint parameter affects the following scenarios:

-   Identity Authentication acting as proxy to delegate authentication to an external corporate identity provider \(IdP\). The user is authenticated via that corporate identity provider.
-   Identity Authentication acting as a conditional proxy where an external corporate identity provider is configured to be used as an authenticating IdP under certain conditions.

The login hint parameter helps the user when he or she is known to the service provider \(SP\) or relying party. Thus it prevents the user from re-typing the user identifier on the logon. If the corporate IdP supports the login hint parameter, then it requests only the user credentials.

If the corporate IdP does not support the login hint parameter, it requires both the user identifier and password. You can configure the login hint parameter for corporate IdP via the administration console for SAP Cloud Identity Services.

There are two aspects in the configuration of the login hint parameter: the value of the parameter, and how it is sent to the corporate IdP. The *How it is sent to the corporate IdP* configuration is only relevant for SAML 2.0 corporate identity ptoviders and depends on the *Value* configuration:

**Configuration Options**


<table>
<tr>
<th valign="top">

Value



</th>
<th valign="top">

How it is sent to the corporate IdP



</th>
<th valign="top">

Additional Info



</th>
</tr>
<tr>
<td valign="top">

User Input



</td>
<td valign="top">

-   Login Hint URL parameter - the login hint is sent in the URL as `login_hint parameter`
-   Authentication Request - the login hint is sent in the SAML 2.0 authentication request as <`Subject`\> attribute \(for SAML 2.0 only\)



</td>
<td valign="top">

As `login_hint` will be sent the user identifier provided at the conditional authentication sign in screen of Identity Authentication.



</td>
</tr>
<tr>
<td valign="top">

None



</td>
<td valign="top">

no login hint parameter is sent



</td>
<td valign="top">

The user will need to provide user identifier and password at the corporate identity provider sign in screen.



</td>
</tr>
<tr>
<td valign="top">

User Attributes

-   Login Name
-   E-Mail



</td>
<td valign="top">

-   Login Hint URL parameter - the login hint is sent in the URL as `login_hint parameter`
-   Authentication Request - the login hint is sent in the SAML 2.0 authentication request as <`Subject`\> attribute \(for SAML 2.0 only\)



</td>
<td valign="top">

As `login_hint` will be sent one of the following:

-   Login Name
-   E-Mail

.



</td>
</tr>
</table>

> ### Note:  
> The *User Input* is the default value option.
> 
> The *User Attributes* option is valid only for users that exist in the Identity Authentication local user store. If the user is missing the specified attribute in the configuration, then login hint parameter will not be sent to the corporate IdP.
> 
> If the user does not exist in Identity Authentication local user store, then the User Input will be sent as login hint to the corporate IdP.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](choose-identity-provider-type-0838379.md)..

4.  Set a value for the login hint parameter:

    -   User Input
    -   None
    -   User Attribute \(local users only\)

5.  \(For SAML 2.0 providers only\) Set how the login hint parameter should be sent to the corporate IdP:

    -   *Login Hint URL parameter* -
    -   *Authentication Request*

    > ### Remember:  
    > The options are valid only if *User Input* or *User Attribute \(local users only\)* values are set.

6.  Save your configuration.


