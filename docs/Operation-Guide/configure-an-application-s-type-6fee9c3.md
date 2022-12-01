<!-- loio6fee9c35a4324c6ca5db2281f867576a -->

# Configure an Application's Type

You can choose and set the *Application Type* in the administration console for Identity Authentication.



## Context

In some cases Identity Authentication can't determine the correct application type because, for example of unknown URL or custom domain. In such cases you can update the application type with one of the following:


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Type



</th>
<th valign="top">

Notes



</th>
</tr>
<tr>
<td valign="top">

SAP Analytics Cloud solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Ariba solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Business ByDesign solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP BTP solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Sales Cloud and SAP Service Cloud solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Concur solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Fieldglass solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Industry Cloud Solution



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

SAP Integrated Business Planning solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Jam solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Marketing Cloud solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Sales Cloud solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP S/4HANA Cloud solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP SuccessFactors solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP Customer Data solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

SAP Central Business Configuration solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Other SAP cloud solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

SAP on-premise solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

Qualtrics solution



</td>
<td valign="top">

`bundled`



</td>
<td valign="top">

SAP managed



</td>
</tr>
<tr>
<td valign="top">

Non-SAP solution



</td>
<td valign="top">

`charged`



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Unkown



</td>
<td valign="top">

`charged`



</td>
<td valign="top">

default value



</td>
</tr>
</table>

> ### Remember:  
> You can't change the application type of the system applications.

To configure the *Application Type*, proceed as follows:



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

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Edit* button on the top-right corner.

5.  Choose the type from the drop-down in the *Application Type* field in the dialog box that appears.

6.  Save your changes.

    Once the application has been updated, the system displays the message ***Application <name of application\> updated***.


**Related Information**  


[Invitation REST API](../Development/invitation-rest-api-e55429f.md "The invitation service allows you to implement a request for user invitations.")

[User Registration](../Development/user-registration-0aa433c.md "The user registration is used for registration of new users or for on-behalf registration of partners.")

