<!-- loio33838e0760f8411daf758a1c11818cc4 -->

# Import or Update Users for a Specific Application

As a tenant administrator, you can import new users or update existing ones for a specific application with a CSV file. You can also send activation emails to the users that have not received activation emails for that application so far.



## Prerequisites

-   You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have uploaded the service provider's metadata or entered the information manually. For more information see, [Configure Trust](configure-trust-f96e4c5.md).

    > ### Note:  
    > You need the metadata to configure the trust between the service provider and Identity Authentication, which is in the role of identity provider.




## Context

By importing new users with a CSV file, you create user profiles without passwords in Identity Authentication. As a result, the users receive emails with instructions how to activate their accounts. After the users set their passwords, they can log on to the application for which they were imported. Based on the user access configuration of the application, the users can log on to other applications connected with the tenant in Identity Authentication.

In addition to the new user import, you can specify existing users in the imported CSV file. You thus define the users to be updated in Identity Authentication.

By specifying existing users in the imported CSV file you can also restrict the access to a specific application via the *Private* options. For more information, see [Configure User Access to the Application](configure-user-access-to-the-application-8b147c4.md).

> ### Note:  
> The user import does not assign any special rights or roles to the created or updated users for the specific application.

The CSV file can contain only columns with no spaces between them, with the following attributes. If you include columns with other attributes, their values in the table are ignored.

> ### Note:  
> If you enter the data in the CSV file as text, you must separate the entries with commas. Beware not to put any spaces before or after the commas. If you enter more than one value in a single entry, separate the values within the entry with commas and enclose the entry in quotation marks.

**CSV Files Attributes**


<table>
<tr>
<th valign="top">

Attributes

</th>
<th valign="top">

Mandatory

</th>
<th valign="top">

Unique

</th>
<th valign="top">

Valid Values

</th>
<th valign="top">

Notes

</th>
</tr>
<tr>
<td valign="top">

`status`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

-   `active`
-   `inactive`



</td>
<td valign="top">

The *status* column defines whether the user is still active in the system and is able to work with any tenant applications. When a user is deleted, it's rendered inactive.

</td>
</tr>
<tr>
<td valign="top">

`loginName`

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

 

</td>
<td valign="top">

Must be a string value of up to 64 characters.

You cannot change the email of an existing user.

</td>
</tr>
<tr>
<td valign="top">

`mail`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

 

</td>
<td valign="top">

> ### Tip:  
> For users without valid email addresses or for testing purposes use the `sap-test.de` domain, for example `<username>@sap-test.de`. Do not use any other existing or non-existing domains.

Must be a string value of up to 64 characters.

Values that are part of the respective exclude list can't be used. For more information, see [Restrict User Attributes Values via Exclude Lists](restrict-user-attributes-values-via-exclude-lists-cb108c2.md).

</td>
</tr>
<tr>
<td valign="top">

`firstName`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

Must be a string value of up to 64 characters.

Values that are part of the respective exclude list can't be used. For more information, see [Restrict User Attributes Values via Exclude Lists](restrict-user-attributes-values-via-exclude-lists-cb108c2.md).

</td>
</tr>
<tr>
<td valign="top">

`lastName`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

Must be a string value of up to 64 characters.

Values that are part of the respective exclude list can't be used. For more information, see [Restrict User Attributes Values via Exclude Lists](restrict-user-attributes-values-via-exclude-lists-cb108c2.md).

</td>
</tr>
<tr>
<td valign="top">

`language`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

Must be a string value specified by a two or four-letter code in one of the following formats: XX. Otherwise, the activation email is in English.

</td>
</tr>
<tr>
<td valign="top">

`validTo`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

Must be a string value in the Zulu format yyyyMMddHHmmss'Z'.

The information in the *validFrom* and *validTo* columns can be processed by the service provider to limit user access. It would affect the authentication of the user, though.

</td>
</tr>
<tr>
<td valign="top">

`validFrom`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

Must be a string value in the Zulu format yyyyMMddHHmmss'Z'.

The information in the *validFrom* and *validTo* columns can be processed by the service provider to limit user access. It would affect the authentication of the user, though.

</td>
</tr>
<tr>
<td valign="top">

`userType`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

-   public

-   employee

-   customer

-   partner

-   external

-   onboardee




</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`urn:ietf:params:scim:schemas:extension:sap:2.0:User:mailVerified`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

-   true
-   false - the default value



</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute1`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute2`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute3`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute4`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`spCustomAttribute5`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`groups`

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

 

</td>
<td valign="top">

The groups in the *groups* column must be existing. You can’t add a user to a user group that is not existing.

</td>
</tr>
</table>



### Examples

> ### Example:  
> A tenant administrator decides to import three new users \(Michael, Julie, Donna\) and to update two others \(John and Denise\) that will use the company's applications. Michael is a member of three groups, namely *Employees*, *Managers*, and *HR*. John and Denise were inactive users that now use tenant's applications. The administrator would also like to update another user \(Richard\) who currently does not work for the company. To do this, the administrator uploads a CSV file with the following information:
> 
> > ### Sample Code:  
> > ```
> > 
> > status,loginName,mail,firstName,lastName,language,validFrom,validTo,spCustomAttribute1,groups
> > active,EID00001,michael.adams@example.com,Michael,Adams,en,20110901120000Z,20150901120000Z,Industry,"Managers, Employees, HR"
> > active,EID00002,julie.armstrong@example.com,Julie,Armstrong,en,20110901120000Z,20150901120000Z,Department,Employees
> > active,EID00003,donna.moore@example.com,Donna,Moore,de,20110901120000Z,20160901120000Z,Shift,HR
> > active,EID00004,john.miller@example.com,John,Miller,en,20110901120000Z,20180901120000Z,Unit,IT
> > active,EID00005,denise.smith@example.com,Denise,Smith,en,20110901120000Z,20140901120000Z,,Administrators
> > inactive,EID00006,richard.wilson@example.com,Richard,Wilson,en,20110901120000Z,20160901120000Z,,All
> > 
> > ```
> 
> The administrator receives the following message: ***3 users will be created. 3 users will be updated because they already exist. Do you want to continue?***
> 
> The users that have not received activation emails will receive such emails, and then can activate their accounts and log on.

> ### Example:  
> A sales company has employed two new people \(Michael Adams and Julie Armstrong\) in the HR department. The tenant administrator has to import these two new employees that will use the company's applications. Michael and Julie are members of the groups **Employees** and **HR**. To do this, the administrator uploads a CSV file with the following information:
> 
> > ### Sample Code:  
> > ```
> > 
> > status,mail,firstName,lastName,groups
> > active,michael.adams@example.com,Michael,Adams,"Employees, HR"
> > active,julie.armstrong@example.com,Julie,Armstrong,"Employees, HR"
> > ```
> 
> Six months later, Julie is promoted as HR Manager, while Michael moves to the Sales department. The tenant administrator has to update the profiles of Michael and Julie to represent the changes. Julie remains in the current groups and has to be included in the **Managers** group. Michael has to be removed from the **HR** group, and to be included in the **Sales** group. To do this, the administrator uploads a CSV file with the following information:
> 
> > ### Sample Code:  
> > ```
> > 
> > status,mail,firstName,lastName,groups
> > active,michael.adams@example.com,Michael,Adams,"Employees, Sales"
> > active,julie.armstrong@example.com,Julie,Armstrong,"Employees, HR, Management"
> > ```
> 
> > ### Remember:  
> > When tenant administrators must update a user via a CSV file, they must include the new information, and repeat the information that remains unchanged.
> > 
> > If you, as a tenant administrator, include only the new information, the information that is not repeated will be deleted.
> > 
> > In this example, the administrator imports Michael with the **Employees** group, and Julie with the **Employees** and **HR** groups in the new table.

To import users for an application into Identity Authentication, and to send activation emails, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *Import Users* tile.

    This operation opens the *Import Users* page.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Under *Upload CSV File*, choose the *Browse...* button and specify the location of the CSV file.

    > ### Note:  
    > Use a file smaller than 100 KB and with an extension `.csv`. If your file is 100 KB or larger, you have to import the user information in iterations with smaller size files.

5.  Choose the *Import* button.

    If the operation is successful, the system displays the message ***Users imported or updated***.

6.  Choose the one of the following options:


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
    
    **Do nothing**
    
    </td>
    <td valign="top">
    
    The users are imported or updated for the selected application, but they will not receive activation emails. The activation emails will be sent when you choose *Send Emails* \> *Send*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Repeat steps 1 to 5**
    
    </td>
    <td valign="top">
    
    The users are imported or updated for the selected application, but they will not receive activation emails. The activation emails will be sent when you choose the *Send* button.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Under *Send Emails* choose the *Send* button
    
    </td>
    <td valign="top">
    
    This will send activation emails to all users that are imported for the selected application, but have not received activation emails so far.

    > ### Note:  
    > The *Send* button is inactive if *Home URL* or SAML 2.0 configuration of the application is missing. You can only import users, but you cannot send activation emails.
    > 
    > You need the *Home URL* configured for the specific application to be able to send the activation emails to the imported new users. For more information, see [Configure an Application's Home URL](configure-an-application-s-home-url-be6d6f2.md).
    > 
    > To access the application, the users have to activate their accounts by following the link they receive in the emails.


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Configure an Application's Home URL](configure-an-application-s-home-url-be6d6f2.md "You can configure the Home URL of an application in the administration console for SAP Cloud Identity Services.")

[Configure User Access to the Application](configure-user-access-to-the-application-8b147c4.md "You can configure public access to the application allowing self-registration, or you can restrict the access to existing users or users registered by an application.")

[List and Edit Groups](list-and-edit-groups-5e8a55c.md "As a tenant administrator, you can list and edit information about the groups in a tenant in the administration console for SAP Cloud Identity Services.")

[Create a Group](create-a-group-b1b638d.md "As a tenant administrator you can create groups in the tenant to organize users based on common characteristics, authorization, or application via the administration console for SAP Cloud Identity Services.")

[Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md "As a tenant administrator, you can edit both your own authorizations and other administrators' authorizations in the administration console for SAP Cloud Identity Services. By editing the administrator authorizations you can also delete an administrator.")

[Export Existing Users of a Tenant of Identity Authentication](export-existing-users-of-a-tenant-of-identity-authentication-40c29d2.md)

