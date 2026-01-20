<!-- loio69d8cad2a03643b4a73f5931cf150252 -->

# Edit Applications

After creating the application, you can change its display name, home URL, type and parent application.



<a name="loio69d8cad2a03643b4a73f5931cf150252__prereq_ijb_kgc_btb"/>

## Prerequisites

You are assigned the *Manage Applications* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).



## Context

The *Display Name* is required. You can't leave that field empty.

The *Home URL* field is optional. Users are redirected to the *Home URL* after activating their accounts, when they are created via a CSV file import or the user registration service of Identity Authentication. Initially, the *Home URL* for an application isn’t configured in the administration console for SAP Cloud Identity Services. Once the *Home URL* has been set, you can change it.

> ### Recommendation:  
> From a usability perspective we recommend you to use URL of a protected page.

> ### Remember:  
> *Home URL* is necessary when you import new users in Identity Authentication. Identity Authentication needs to send activation emails to the new users and the home URL has to be mentioned in the emails. To access the application, the users have to activate their accounts. For more information see [Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md).

The *Application Type* is optional. You can update the *Application Type* with one of the following:


<table>
<tr>
<th valign="top">

Name Type

</th>
<th valign="top">

Application Type

</th>
</tr>
<tr>
<td valign="top">

SAP Analytics Cloud solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Ariba solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Business ByDesign solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP BTP solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Central Business Configuration solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Concur solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Customer Data solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Data Custodian solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Datasphere solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Emarsys Customer Engagement solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Fieldglass solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Enable Now solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Industry Cloud Solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Integrated Business Planning solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Jam solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Marketing Cloud solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Sales Cloud solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Signavio solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP SuccessFactors solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP S/4HANA Cloud solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

Other SAP cloud solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP on-premise solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

Qualtrics solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP LeanIX solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

SAP Business Data Cloud solution

</td>
<td valign="top">

`bundled`

</td>
</tr>
<tr>
<td valign="top">

Non-SAP solution

</td>
<td valign="top">

`charged`

</td>
</tr>
<tr>
<td valign="top">

Unknown

</td>
<td valign="top">

`charged`

</td>
</tr>
</table>

> ### Remember:  
> You can't change the application type of the system applications.
> 
> Bundled SAP S/4 HANA Cloud and SAP Integrated Business Planning solutions are managed and configured by SAP and can't be deleted. Part of their SAML 2.0 configurations are read-only. Be careful when you make configuration changes.

The *Parent Application* field is optional.

Changing child application's configuration doesn't affect the configuration of the parent.

Applications that have a parent application configured can't be selected as parent application.

An application that is chosen as a parent application to another can't have a parent application assigned for it.

> ### Remember:  
> An application that is chosen as a parent application to another cannot be deleted.

To edit the application configurations, proceed as follows:



<a name="loio69d8cad2a03643b4a73f5931cf150252__steps_qqh_hfk_q4"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Filter the list items in the search field by typing the name, display name, application ID, organization ID, or client ID, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Edit* button on the top right corner.

5.  Edit the fields:


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
    
    *Display Name*
    
    </td>
    <td valign="top">
    
    Required
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Home URL*
    
    </td>
    <td valign="top">
    
    Optional
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Type*
    
    </td>
    <td valign="top">
    
    Optional

    > ### Caution:  
    > If the type of the application is not the correct one, the system may change it automatically without a warning.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Parent Application*
    
    </td>
    <td valign="top">
    
    Optional.

    Existing applications that have a parent application assigned to them will inherit only the configurations that have not been changed, including the configurations that are made at the creation of the application. The configurations that are changed, and the configurations made at the creation of the application are not inherited. See the list below for the configurations made at the creation of the application:

    -   Protocol
    -   Subject Name Identifier

        > ### Note:  
        > When a subscribed application becomes a child application, the configuration of the `Subject Name Identifier` of that child application can be different from the parent application or from the application it is subscribed to. You can make the configuration of the `Subject Name Identifier` the same as the parent application by choosing the *Inherit from Parent* button on the top right-hand corner of the screen. You can also make the configuration of the `Subject Name Identifier` the same as the application it is subscribed to by choosing the *Reset* button on the top right-hand corner of the screen. Depending on your configuration, either the *Inherit from Parent* or the *Reset* button is active, or both buttons are active.

    -   Default Name ID Format
    -   Attributes

        > ### Note:  
        > Attributes from different sources are inherited separately. For more information about the different user attribute sources, see [User Attributes](user-attributes-ed2797d.md).

    -   Dependencies
    -   Risk-Based Authentication
    -   Conditional Authentication
    -   Email Verification
    -   Password Policy
    -   Terms Of Use
    -   Privacy Policy
    -   User Application Access
    -   User Attributes for Access
    -   Token Url Separator
    -   Reload Parent Page

    > ### Tip:  
    > A child application can override all the configurations inherited from the parent application. If you change a configuration in the child that is inherited from the parent, and after that you decide to return to the inherited one, go to the respective configuration and choose the *Inherit from Parent* button on the top right-hand corner of the screen.

    > ### Caution:  
    > If you change a configuration in the child that is inherited from the parent, also change the name of the child, so that it differs from the name of the parent. Saving the configuration without changing the child application's name may result in failing authentication requests.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Organization ID*
    
    </td>
    <td valign="top">
    
    > ### Remember:  
    > The field is visible to users assigned to application authorization policies, or with Manage Applications role. For more information about the application authorization policies, see [Configure Application Authorizations](configure-application-authorizations-01cff18.md).

    This field allows you to group the applications under a specific organization and on the basis of the *Organization ID* to restrict the access to these applications.

    By default all applications are in the `global` *Organization ID*. Enter a new name to change the value of *Organization ID*.

    > ### Note:  
    > Applications created either as subscriptions within or with the Identity service of an SAP BTP subaccount receive the *Organization ID* of the application that represents the trust configuration of that subaccount.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Protocol Type*
    
    </td>
    <td valign="top">
    
    Choose from:

    -   SAML 2.0 \(default selection\)
    -   OpenID Connect

    > ### Note:  
    > There are applications that show the ***SAML 2.0 & OpenID Connect*** protocol type. You can't create such applications.

    > ### Remember:  
    > If you change the parent application, the child application will inherit the protocol from the new parent. To change the protocol, first finish the editing and then repeat the procedure again, this time changing the protocol.


    
    </td>
    </tr>
    </table>
    
6.  Save your changes.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


