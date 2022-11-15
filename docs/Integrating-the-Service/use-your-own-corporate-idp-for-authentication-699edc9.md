<!-- loio699edc9a2d2b48a8a242a8bd28e8d1c8 -->

# Use Your Own Corporate IdP for Authentication

This document is intended to help you configure trust with a SAML 2.0 corporate identity provider. In this scenario Identity Authentication acts as a proxy to delegate the authentication to the SAML 2.0 corporate identity provider.



## Context

Identity Authentication can use a SAML 2.0 identity provider as an external authenticating authority. Identity Authentication thus acts as a proxy to delegate authentication to the external corporate identity provider. The requests for authentication sent by a service provider will be forwarded to the corporate identity provider.

As an identity provider proxy, Identity Authentication will act as an SAML 2.0 identity provider to the service provider, and as an SAML 2.0 service provider to the corporate identity provider. Once a user is authenticated at the corporate identity provider, successive authentication requests from service providers, which use the same corporate identity provider will not be forwarded to it as long as the session at Identity Authentication is active. Identity Authentication will issue assertions based on the user data received during the first authentication.

> ### Note:  
> If an application requires force authentication \(ForceAuthn="true"\), users have to authenticate themselves against the corporate identity provider each time they access the application even if single sign-on \(SSO\) is enabled.

To use Identity Authentication as a proxy to delegate authentication to an external corporate identity provider you have to configure trust with that corporate identity provider.

To configure trust with the corporate identity provider, follow the procedures below:

**Related Information**  


[Use Identity Authentication as Authenticating IdP](use-identity-authentication-as-authenticating-idp-2ff9a61.md "In this scenario, to log on to an application, users provide their credentials to Identity Authentication, and Identity Authentication asserts their identity to the application.")

 <a name="task_jlj_2rm_qgb"/>

<!-- task\_jlj\_2rm\_qgb -->

## 1. Configure Trust on the Corporate Identity Provider Side

Set up trust with Identity Authentication as a service provider.



<a name="task_jlj_2rm_qgb__prereq_pyl_55m_qgb"/>

## Prerequisites

You have the SAML 2.0 metadata of Identity Authentication. For more information how to download the metadata, see [Tenant SAML 2.0 Configuration](../Operation-Guide/tenant-saml-2-0-configuration-e81a19b.md).



<a name="task_jlj_2rm_qgb__steps_syl_55m_qgb"/>

## Procedure

1.  Register Identity Authentication as a service provider at the corporate identity provider.

    > ### Remember:  
    > If you want to use IdP-initiated single sign-on \(SSO\) from your corporate identity provider, you have to add the parameter `sp=<sp_name>` to the assertion consumer service \(ACS\) endpoint configured on your corporate identity provider side for Identity Authentication.
    > 
    > > ### Example:  
    > > https://<the current ACS endpoint URL\>?sp=<sp\_name\>\>
    > > 
    > > `sp` is the name of the SAML 2 service provider for which SSO is performed.
    > 
    > To see how to download the SAML 2.0 metadata of Identity Authentication read [Tenant SAML 2.0 Configuration](../Operation-Guide/tenant-saml-2-0-configuration-e81a19b.md).

2.  Download the corporate identity provider SAML 2.0 metadata.

    You need the corporate SAML 2.0 metadata for the setup of the trust on Identity Authentication. Optionally, you can make the configurations manually.


 <a name="task_rkw_frm_qgb"/>

<!-- task\_rkw\_frm\_qgb -->

## 2. Configure Trust on Identity Authentication Side

Set up trust with your corporate identity provider in the administration console for Identity Authentication.



<a name="task_rkw_frm_qgb__prereq_z15_55m_qgb"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).

-   You have registered Identity Authentication as service provider at the corporate identity provider.

-   You have the corporate identity provider SAML 2.0 metadata.




<a name="task_rkw_frm_qgb__steps_cb5_55m_qgb"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure.

    > ### Tip:  
    > If you need to change the protocol, see [Choose Identity Provider Type](../Operation-Guide/choose-identity-provider-type-0838379.md)..

4.  Under *SAML 2.0*, choose *SAML 2.0 Configuration*.

5.  Upload the corporate identity provider metadata XML file or manually enter the communication settings negotiated between Identity Authentication and the identity provider.

    > ### Note:  
    > Use a file with an extension `.xml`.

    When the identity provider metadata is uploaded, the fields are populated automatically with the parsed data from the XML file. The minimum configuration is to complete the *Name* field, add at least one single sign-on endpoint, and provide a signing certificate.

    You can add up to two signing certificates. Both signing certificates are accepted according to the certificate validity.


    <table>
    <tr>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Metadata File


    
    </td>
    <td valign="top">

    The metadata XML file of the identity provider.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Name


    
    </td>
    <td valign="top">

    The entity ID of the identity provider.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Single Sign-On Endpoint URL


    
    </td>
    <td valign="top">

    The URL of the identity provider single sign-on endpoint that receives authentication requests.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Single Logout Endpoint URL


    
    </td>
    <td valign="top">

    The URL of the identity provider's single logout endpoint that receives logout messages.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Binding


    
    </td>
    <td valign="top">

    The SAML-specified HTTP binding used by the identity provider showing how the various SAML protocol messages can be carried over underlying transport protocols.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Signing Certificate


    
    </td>
    <td valign="top">

    A base64-encoded certificate used by the service provider to sign digitally SAML protocol messages sent to Identity Authentication.

    Use the *Add* button to add a second signing certificate.

    > ### Note:  
    > If you have two certificates, you can choose a default one, to mark your primary certificate.


    
    </td>
    </tr>
    </table>
    
6.  Choose the digest algorithm for signing outgoing messages from the dropdown list in the *Algorithm* section. You have the following options:

    -   *SHA-1* 
    -   *SHA-256* - the default option

        > ### Remember:  
        > The algorithm must be *SHA-256* if the Identity provider type is set at *Microsoft ADFS / Azure AD*.


7.  Enable or disable the *Include scoping* attribute to include or exclude the Scoping element in the SAML 2.0 request.

    > ### Remember:  
    > The default setting for the *Include scoping* is enabled. The Scoping element sent in the SAML 2.0 request is 1.
    > 
    > If the identity provider type is set at *Microsoft ADFS / Azure AD* the default setting for the *Include scoping* is disabled and the Scoping element is not sent in the SAML 2.0 request.

8.  Save your selection.

    Once the identity provider has been updated, the system displays the message ***Identity provider <name of identity provider\> updated***.




<a name="task_rkw_frm_qgb__postreq_eb5_55m_qgb"/>

## Next Steps

-   Select the configured identity provider as the authenticating identity provider for the application. For more information, see [Choose Default Identity Provider for an Application](../Operation-Guide/choose-default-identity-provider-for-an-application-e9d8274.md).

-   [\(Optional\) Configure the Name ID Format and AllowCreate Attribute Sent to the SAML 2.0 Corporate IdP](../Operation-Guide/optional-configure-the-name-id-format-and-allowcreate-attribute-sent-to-the-saml-2-0-corp-4fcc090.md) 

 <a name="task_pdb_232_25b"/>

<!-- task\_pdb\_232\_25b -->

## Configure Identity Federation



<a name="task_pdb_232_25b__prereq_tvw_gtk_25b"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).

-   You have configured Identity Authentication to use a corporate identity provider as an external authenticating authority. For more information, see [Configure Trust with SAML 2.0 Corporate Identity Provider](../Operation-Guide/configure-trust-with-saml-2-0-corporate-identity-provider-33832e5.md) or [Configure Identity Federation](../Operation-Guide/configure-identity-federation-c029bbb.md).

-   You have selected the configured identity provider as the authenticating identity provider for your application. For more information, see [Choose Default Identity Provider for an Application](../Operation-Guide/choose-default-identity-provider-for-an-application-e9d8274.md).

-   You have imported the users, authenticated by the corporate identity provider, in Identity Authentication. For more information about how to import users, see [Import or Update Users for a Specific Application](../Operation-Guide/import-or-update-users-for-a-specific-application-33838e0.md).




<a name="task_pdb_232_25b__context_imb_h32_25b"/>

## Context

By default, *Use Identity Authentication user store* is disabled.

In scenarios when the application is using for authentication a corporate identity provider, and the *Use Identity Authentication user store* option is disabled, the user attributes, the name ID attribute, and the default attributes configurations in the administration console for Identity Authentication are not relevant. In such scenarios, Identity Authentication sends to the application the same attributes it has received from the corporate identity provider \(no change in the Subject Name Identifier or its format - Unspecified or E-Mail\). As a consequence, the same format is used not only for the ABAP and SAP Analytics Cloud tenants but also for all other SAP applications connected to the same Identity Authentication tenant, which may lead to contradictions if some applications require a different format.

When *Use Identity Authentication user store* option is enabled, the application checks if the users authenticated by the corporate identity provider exist in the Identity Authentication user store. For users that exist in Identity Authentication, data from Identity Authentication user store is taken and the subject name identifier, assertion and default attributes according to the application configuration are sent. For users with no profile in Identity Authentication, the application receives the nameID attribute from the corporate IdP assertion, and the attributes according to the application configuration.

When *Use Identity Authentication user store* is enabled, it is possible to configure different name ID Formats per application. The values for all necessary formats must be contained in the assertion issued by the corporate identity provider:

-   either as Subject Name Identifier
-   or as a SAML Assertion Attribute.

> ### Example:  
> For example, if the corporate identity provider issues an assertion containing the login name as Subject Name Identifier and an Attribute Statement containing an e-mail address, the SAML assertion XML document would contain:
> 
> > ### Sample Code:  
> > ```
> > 
> > <Subject>
> >   <NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified">P012345</NameID>
> >   ...
> > </Subject>
> > ...
> > <AttributeStatement>
> >   <Attribute Name="mail">
> >     <AttributeValue xsi:type="xs:string">dona.moore@test.com</AttributeValue>
> >   </Attribute>
> >   ...
> > </AttributeStatement>
> > ```

If the ABAP and SAP Analytics Cloud tenants require the e-mail address \(in our example *dona.moore@test.com*\) for logon, but another application requires the login name, this can be achieved with the following configuration in the administration console for Identity Authentication:

****


<table>
<tr>
<th valign="top">

Application



</th>
<th valign="top">

Trust-Related Setting



</th>
<th valign="top">

Value



</th>
</tr>
<tr>
<td valign="top" rowspan="4">

ABAP



</td>
<td valign="top">

`Subject Name Identifier`



</td>
<td valign="top">

Advanced Configuration: `${corporateIdP.mail}`



</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`



</td>
<td valign="top">

***E-Mail***



</td>
</tr>
<tr>
<td valign="top">

`Apply Function to Subject Name Identifier`



</td>
<td valign="top">

***None***



</td>
</tr>
<tr>
<td valign="top">

`Conditional Authentication`



</td>
<td valign="top">

***<your corporate identity provider\>***



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

SAP Analytics Cloud



</td>
<td valign="top">

`Subject Name Identifier`



</td>
<td valign="top">

Advanced Configuration: `${corporateIdP.mail}`



</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`



</td>
<td valign="top">

***E-Mail***



</td>
</tr>
<tr>
<td valign="top">

`Apply Function to Subject Name Identifier`



</td>
<td valign="top">

***None***



</td>
</tr>
<tr>
<td valign="top">

`Conditional Authentication`



</td>
<td valign="top">

***<your corporate identity provider\>***



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Other Application



</td>
<td valign="top">

`Subject Name Identifier`



</td>
<td valign="top">

***Login Name***



</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`



</td>
<td valign="top">

***Unspecified***



</td>
</tr>
<tr>
<td valign="top">

`Apply Function to Subject Name Identifier`



</td>
<td valign="top">

***None***



</td>
</tr>
<tr>
<td valign="top">

`Conditional Authentication`



</td>
<td valign="top">

***<your corporate identity provider\>***



</td>
</tr>
</table>

> ### Note:  
> In this case, the setting Subject Name Identifier = Login Name is relevant only for Identity Authentication administrators, for whom a user record exists in Identity Authentication. These will be logged on to the other application with the login name from their Identity Authentication user record, which must therefore be the same as in their corporate identity provider user record. For all other users, the Subject Name Identifier asserted by the corporate identity provider \(in the example, `P012345`\) will be used for logon to the other application.



<a name="task_pdb_232_25b__steps_enable_idfederation"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure for *Identity Federation*.

    -   If you do not have an identity provider in your list, click the *Add* button to create one, and proceed with the configuration.
    -   If you have an identity provider in your list, choose the one that you want to configure.

4.  Choose *Identity Federation* to configure the options.

5.  Use the slider next to *Use Identity Authentication user store* to enable or disable it.


