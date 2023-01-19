<!-- loio749284f4498649ba8e8bcc3e8342b9dd -->

# Configure Identity Federation



<a name="loio749284f4498649ba8e8bcc3e8342b9dd__prereq_tvw_gtk_25b"/>

## Prerequisites

-   You are assigned the *Manage Corporate Identity Providers* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](../Operation-Guide/edit-administrator-authorizations-86ee374.md).

-   You have configured Identity Authentication to use the OpenID Connect corporate identity provider as an external authenticating authority. For more information, see [Configure Trust with OpenID Connect Corporate Identity Provider](../Operation-Guide/configure-trust-with-openid-connect-corporate-identity-provider-8ff83a1.md).

-   You have selected the configured identity provider as the authenticating identity provider for your application. For more information, see [Choose Default Identity Provider for an Application](../Operation-Guide/choose-default-identity-provider-for-an-application-e9d8274.md).

-   You have imported the users, authenticated by the corporate identity provider, in Identity Authentication. For more information about how to import users, see [Import or Update Users for a Specific Application](../Operation-Guide/import-or-update-users-for-a-specific-application-33838e0.md).




<a name="loio749284f4498649ba8e8bcc3e8342b9dd__context_imb_h32_25b"/>

## Context

By default, *Use Identity Authentication user store* is disabled.

In scenarios when the application is using for authentication a corporate identity provider, and the *Use Identity Authentication user store* option is disabled, the user attributes, the name ID attribute, and the default attributes configurations in the administration console for SAP Cloud Identity Services are not relevant. In such scenarios, Identity Authentication sends to the application the same attributes it has received from the corporate identity provider \(no change in the Subject Name Identifier or its format - Unspecified or E-Mail\). As a consequence, the same format is used not only for the ABAP and SAP Analytics Cloud tenants but also for all other SAP applications connected to the same Identity Authentication tenant, which may lead to contradictions if some applications require a different format.

When *Use Identity Authentication user store* option is enabled, the application checks if the users authenticated by the corporate identity provider exist in the Identity Authentication user store. For users that exist in Identity Authentication, data from Identity Authentication user store is taken and the subject name identifier, assertion and default attributes according to the application configuration are sent. For users with no profile in Identity Authentication, the application receives the nameID attribute from the corporate IdP assertion, and the attributes according to the application configuration.

When *Use Identity Authentication user store* is enabled, it is possible to configure different name ID Formats per application. The values for all necessary formats must be contained in the assertion issued by the corporate identity provider:

-   as Subject Name Identifier in the SAML 2.0 assertion
-   or as a SAML Assertion Attribute.
-   or as a claim in an OpenID Connect token

> ### Example:  
> SAML 2.0 Scenario
> 
> If the corporate identity provider issues an assertion containing the login name as Subject Name Identifier and an Attribute Statement containing an e-mail address, the SAML assertion XML document would contain:
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
> 
> > ### Note:  
> > In this case, the setting Subject Name Identifier = Login Name is relevant only for Identity Authentication administrators, for whom a user record exists in Identity Authentication. These will be logged on to the other application with the login name from their Identity Authentication user record, which must therefore be the same as in their corporate identity provider user record. For all other users, the Subject Name Identifier asserted by the corporate identity provider \(in the example, `P012345`\) will be used for logon to the other application.

> ### Example:  
> OpenID Connect Scenario
> 
> If the corporate identity provider issues an OpenID Connect token containing the login name as Subject Name Identifier and the email address as an Assertion Attribute. The JSON web token would contain claims like:
> 
> > ### Sample Code:  
> > ```
> > {"sub": "P012345",
> >  "mail": "dona.moore@test.com",
> >  ...}
> > ```

If the ABAP and SAP Analytics Cloud tenants require the e-mail address \(in our example *dona.moore@test.com*\) for logon, but another application requires the login name, this can be achieved with the following configuration in the administration console for SAP Cloud Identity Services:

**SAML 2.0 Scenario**


<table>
<tr>
<th valign="top">

Application



</th>
<th valign="top">

Trust-Related Setting



</th>
<th valign="top">

Value \(SAML 2.0 Scenario\)



</th>
<th valign="top">

Value \(OpenID Connect Scenario\)



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
<td valign="top">

Advanced Configuration: `${corporateIdP.mail}`



</td>
</tr>
<tr>
<td valign="top">

`Default Name ID Format`



</td>
<td valign="top">

***Unspecified***



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
<td valign="top">

***<your corporate identity provider\>***



</td>
</tr>
</table>



<a name="loio749284f4498649ba8e8bcc3e8342b9dd__steps_enable_idfederation"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Corporate Identity Providers* tile.

3.  Select the corporate identity provider that you want to configure for *Identity Federation*.

    -   If you do not have an identity provider in your list, click the *Add* button to create one, and proceed with the configuration.
    -   If you have an identity provider in your list, choose the one that you want to configure.

4.  Choose *Identity Federation* to configure the options.

5.  Use the slider next to *Use Identity Authentication user store* to enable or disable it.


