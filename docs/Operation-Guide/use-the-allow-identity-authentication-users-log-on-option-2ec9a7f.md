<!-- loio2ec9a7f7c80a42f1abec683fa94309bd -->

# Use the **Allow Identity Authentication Users Log On** Option

Users can log on with their Identity Authentication credentials, when a corporate identity provider is selected as default.



<a name="loio2ec9a7f7c80a42f1abec683fa94309bd__prereq_ors_br4_1db"/>

## Prerequisites

You have chosen a corporate identity provider as default. For more information, see [Choose a Corporate Identity Provider as Default](choose-a-corporate-identity-provider-as-default-44dd636.md).



<a name="loio2ec9a7f7c80a42f1abec683fa94309bd__context_xnm_tr2_dpb"/>

## Context



<a name="loio2ec9a7f7c80a42f1abec683fa94309bd__steps_yhl_hp4_1db"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

4.  Choose the *Trust* tab.

5.  Under *Conditional Authentication*, select the *Allow users stored in Identity Authentication service to log on* check box.

    > ### Note:  
    > By default this option is disabled.
    > 
    > The check box is visible only if you have chosen a corporate identity provider as default.

6.  Save your selection.

7.  Pass the `idp` parameter with the authentication request to use Identity Authentication tenant for authentication. You have the following two options for the value:


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `idp=<idp_name>`
    
    </td>
    <td valign="top">
    
    You specify the identity provider manually.

    > ### Note:  
    > The `idp_name` must match the name of the identity provider, configured in the *Name* or *URL* field for the issuer under *Tenant Settings*. For more information, see [Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md) or [Tenant OpenID Connect Configurations](tenant-openid-connect-configurations-3d6abcc.md).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `idp=local`
    
    </td>
    <td valign="top">
    
    Use the value `local` to override the conditional authentication configuration and authenticate with Identity Authentication instead.
    
    </td>
    </tr>
    </table>
    
    Depending on the protocol:

    -   for SAML 2.0 - pass the parameter in the body or url.

        > ### Caution:  
        > It depends on the service provider whether the parameter can be passed in `body` or `url`. Identity Authentication doesn't control how the SAML 2.0 request is sent.

    -   for OpenID Connect \(OIDC\) - pass the parameter in the url.


