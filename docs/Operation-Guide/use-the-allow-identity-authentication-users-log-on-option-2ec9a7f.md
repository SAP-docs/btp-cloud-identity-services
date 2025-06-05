<!-- loio2ec9a7f7c80a42f1abec683fa94309bd -->

# Use the **Allow Identity Authentication Users Log On** Option

Users can log on with their Identity Authentication credentials, when a corporate identity provider is selected as default \(for SAML 2.0 applications\).



<a name="loio2ec9a7f7c80a42f1abec683fa94309bd__prereq_ors_br4_1db"/>

## Prerequisites

You have chosen a corporate identity provider as default. For more information, see [Choose a Corporate Identity Provider as Default](choose-a-corporate-identity-provider-as-default-44dd636.md).



<a name="loio2ec9a7f7c80a42f1abec683fa94309bd__context_xnm_tr2_dpb"/>

## Context

> ### Note:  
> The **Allow Identity Authentication Users Log On** option is supported for SAML 2.0 applications only.



<a name="loio2ec9a7f7c80a42f1abec683fa94309bd__steps_yhl_hp4_1db"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Trust* tab.

5.  Under *Conditional Authentication*, select the *Allow users stored in Identity Authentication service to log on* check box.

    > ### Note:  
    > By default this option is disabled.
    > 
    > The check box is visible only if you have chosen a corporate identity provider as default.

6.  Save your selection.

7.  Pass the parameter `idp=<idp_name>` with the SAML 2.0 authentication request in the body or url to use this Identity Authentication tenant for authentication.

    > ### Caution:  
    > It depends on service provider whether the parameter can be passed in body or URL. Identity Authentication doesn't control how the SAML 2.0 request is sent.

    > ### Note:  
    > The `idp_name` must match the name of the identity provider, configured in the *Name* field under *Tenant Settings*. For more information, see [Tenant SAML 2.0 Configurations](tenant-saml-2-0-configurations-e81a19b.md).


