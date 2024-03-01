<!-- loioae99ba935c2e4180851a072d1af347fb -->

# Create Corporate IdP in Administration Console

Create a new corporate identity provider \(IdP\) and customize it or copy the configuration from an existing one.



<a name="loioae99ba935c2e4180851a072d1af347fb__prereq_fkh_343_5xb"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).




## Context

When you create a new corporate IdP in the administration console for SAP Cloud Identity Services you can also change the default SAML 2.0 Compliant type choice offered to you to Single Sign-On \(SAML 2.0\), Microsoft ADFS / Entra ID \(SAML 2.0\) or OpenID Connect Compliant types.

You can also copy the settings from an IdP that is already existing in your tenant to the new corporate IdP. For example, you can have separate SAML 2.0 and OpenID Connect IdP trust configurations for one and the same corporate IdP. Thus, you can migrate your applications from one protocol to another by switching application by application to the new trust.

> ### Remember:  
> If you are copying the settings from one type of corporate IdP to another, all settings are copied apart from the ones that are protocol-specific \(SAML 2.0 or OpenID Connect\).
> 
> After copying the setting, configure the trust manually for the newly created IdP, and adjust the key value pairs in the *Enriched Token Claims* section.

To create a new corporate IdP, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Choose the *Create* button on the left-hand panel.

4.  Provide the following information in the dialog box:


    <table>
    <tr>
    <th valign="top">

    Fields
    
    </th>
    <th valign="top">

    Notes
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Display Name*
    
    </td>
    <td valign="top">
    
    Required. The display name of the identity provider.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Identity Provider Type*
    
    </td>
    <td valign="top">
    
    Optional.

    You can choose one of the following options:

    -   SAML 2.0 Compliant

    -   SAP Single Sign-On \(SAML 2.0\)

    -   Microsoft ADFS / Entra ID \(SAML 2.0\)

        > ### Caution:  
        > For this type, the digest algorithm of the corporate identity provider must be *SHA-256*. For more information, see 2. Configure Trust on Identity Authentication Side in [Configure Trust with Corporate Identity Provider](configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md).

    -   OpenID Connect Compliant



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Copy Settings from Identity Provider*
    
    </td>
    <td valign="top">
    
    Optional. You can create a brand new corporate IdP or copy the configurations from an already existing one.

    Possible options:

    -   Don't copy \(default\) - create a corporate IdP and after that configure it.
    -   Choose from a list with all corporate IdPs that are created in the admin console - the new corporate IdP gets all configuration settings apart from the protocol-specific ones \(SAML or OpenID Connect\) of the selected corporate IdP.


    
    </td>
    </tr>
    </table>
    
5.  Save your changes.




<a name="loioae99ba935c2e4180851a072d1af347fb__result_dpz_23k_r2b"/>

## Results

Once the identity provider has been created, the system displays the message ***Identity provider <name of identity provider\> created***.

The newly created identity provider appears on the list on the left. It is selected and you can proceed with its configuration.

