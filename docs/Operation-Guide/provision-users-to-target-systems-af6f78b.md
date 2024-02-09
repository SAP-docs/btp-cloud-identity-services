<!-- loioaf6f78bd75f044d0afbbfb45ec8beb3e -->

# Provision Users to Target Systems

Tenant administrators can provision users of Identity Authentication to SAP Jamand Identity Provisioning target systems target system.



## Prerequisites

-   You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have configured a target system in the administration console for SAP Cloud Identity Services. For more details about how to configure target systems, see [Configure SAP Jam Target Systems for Real-Time Provisioning](configure-sap-jam-target-systems-for-real-time-provisioning-a923427.md)or [Configure Identity Provisioning Target Systems for Real-Time User Provisioning](configure-identity-provisioning-target-systems-for-real-time-user-provisioning-3349645.md).


> ### Note:  
> Currently, Identity Provisioning supports real-time provisioning to instances of:
> 
> -   SAP Jam
> 
>     > ### Remember:  
>     > Use the Identity Authentication real-time provisioning feature for provisioning of up to 500 users. If you want to provision more than 500 user, use Identity Provisioning. For more information, see [SAP Cloud Identity Services - Identity Provisioning](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/2d2685d469a54a56b886105a06ccdae6.html)
> 
> -   SAP Cloud Identity Services - Identity Provisioning



## Context

Identity Authentication supports the following scenarios for real-time provisioning to target systems:

-   *Provision all users to selected target systems* - In this scenario, all users in the user store of Identity Authentication are provisioned to a specific target system. The tenant administrator chooses the target system that all users will be provisioned to.

-   *Provision selected users to all target systems* - In this scenario, the tenant administrator provisions particular users to all target systems that are configured. The administrator chooses which users to provision.

-   *Provision users from corporate user store* - In this scenario, the users who are stored in a corporate user store are provisioned during authentication.

-   *Provision users at user creation and update* - In this scenario, all newly created or updated the users are automatically provisioned to all target systems.


> ### Remember:  
> The users that are in the user store of Identity Authentication are provisioned to the SAP Jam target system with a certain set of attributes. The table below shows the attributes taken from Identity Authentication and their mapping to the SAP Jam target system.
> 
> **Attribute Mapping Between Identity Authentication and SAP Jam**
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Identity Authentication Attribute
> 
> </th>
> <th valign="top">
> 
> SAP Jam Attribute
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> **Core Schema**
> 
> </td>
> <td valign="top">
> 
>  
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> firstName
> 
> </td>
> <td valign="top">
> 
> name.givenName
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> lastName
> 
> </td>
> <td valign="top">
> 
> name.familyName
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> uid
> 
> </td>
> <td valign="top">
> 
> userName
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> title
> 
> </td>
> <td valign="top">
> 
> jobFunction
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> userType
> 
> </td>
> <td valign="top">
> 
> type
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> mail
> 
> </td>
> <td valign="top">
> 
> emails.value
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> status
> 
> </td>
> <td valign="top">
> 
> active
> 
> > ### Note:  
> > `active` is *true* only when `status` in Identity Authentication is equal to `active`. In the other case `active` is false.
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> telephone
> 
> </td>
> <td valign="top">
> 
> phoneNumbers\[work\].value
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> street
> 
> </td>
> <td valign="top">
> 
> addresses\[home\].streetAddress
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> city
> 
> </td>
> <td valign="top">
> 
> addresses\[home\].locality
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> zip
> 
> </td>
> <td valign="top">
> 
> addresses\[home\].postalCode
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> country
> 
> </td>
> <td valign="top">
> 
> addresses\[home\].country
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> companyStreet
> 
> </td>
> <td valign="top">
> 
> addresses\[work\].streetAddress
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> companyCity
> 
> </td>
> <td valign="top">
> 
> addresses\[work\].locality
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> companyZip
> 
> </td>
> <td valign="top">
> 
> addresses\[work\].postalCode
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> companyCountry
> 
> </td>
> <td valign="top">
> 
> addresses\[work\].country
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> locale
> 
> </td>
> <td valign="top">
> 
> locale
> 
> > ### Note:  
> > The locale must be of the format ll\_CC where:
> > 
> > -   `ll` is the language two letter code in small letters
> > 
> > -   `CC` is the country \(region\) two letter code in capital letters
> 
> > ### Caution:  
> > Do not send `locale` if `language` or `country` user attribute is missing.
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> **Enterprise User Schema Extension** 
> 
> </td>
> <td valign="top">
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> employeeNumber
> 
> </td>
> <td valign="top">
> 
> personnelNumber
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> costCenter
> 
> </td>
> <td valign="top">
> 
> costCenter
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> organization
> 
> </td>
> <td valign="top">
> 
> company
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> division
> 
> </td>
> <td valign="top">
> 
> division
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> department
> 
> </td>
> <td valign="top">
> 
> department
> 
> </td>
> </tr>
> </table>

> ### Note:  
> If Identity Authentication is used as proxy to delegate the authentication to a corporate identity provider, the users that are authenticated by the corporate identity provider will not be provisioned during authentication.
> 
> When you delete a user, he or she is automatically deprovisioned from the configured target systems.

To provision users, choose one of the options below and follow the corresponding procedure.

**Related Information**  


[Configure SAP Jam Target Systems for Real-Time Provisioning](configure-sap-jam-target-systems-for-real-time-provisioning-a923427.md "Tenant administrators can configure SAP Jam target systems for real-time provisioning via the administration console for SAP Cloud Identity Services.")

[Configure Identity Provisioning Target Systems for Real-Time User Provisioning](configure-identity-provisioning-target-systems-for-real-time-user-provisioning-3349645.md "You can configure Identity Provisioning target systems for real-time user provisioning via the administration console for SAP Cloud Identity Services.")

[Delete Target System](delete-target-system-6372e9a.md "As a tenant administrator, you can delete one or more target systems in a tenant of Identity Authentication.")

<a name="task_avw_k4r_cv"/>

<!-- task\_avw\_k4r\_cv -->

## Provision All Users to a Selected Target System



## Context

The tenant administrator can select the target systems that all users will be provisioned to.



<a name="task_avw_k4r_cv__steps_iv4_5bs_cv"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Real-Time Provisioning* tile.

    This operation opens a list of the target systems.

3.  Choose the list item of the target system that you want to provision the users to.

    > ### Note:  
    > If you do not have a configured target system in your list, you can add one. For more details, see [Configure SAP Jam Target Systems for Real-Time Provisioning](configure-sap-jam-target-systems-for-real-time-provisioning-a923427.md).

4.  Press *Provision*.

    If the operation is successful, the system displays the message ***<number of users\> provisioned***.


<a name="task_ejf_l4r_cv"/>

<!-- task\_ejf\_l4r\_cv -->

## Provision Selected Users to All Target Systems



## Context

The tenant administrator can choose which of the users to be provisioned to the configured target systems.



<a name="task_ejf_l4r_cv__steps_ndz_n4r_cv"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose the *User Management* tile.

    The system displays the first 20 users in the tenant sorted by their user ID number.

3.  **Optional:** You can choose one of the following:

    **Search Options**


    <table>
    <tr>
    <td valign="top">
    
    **List All Users**

    Press *More*
    
    </td>
    <td valign="top">
    
    This will expand the list by 20 users.

    > ### Note:  
    > This option is available only if the users in the tenant are more than 20.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Unfiltered Search**

    -   \(default mode\) Type your search criteria string in the search field and press the *Enter* key

    -   \(when in *Filtered Search* mode\) Press *Hide Filters*, type your search criteria string in the search field, and press the *Enter* key



    
    </td>
    <td valign="top">
    
    Once the search is completed, the system will list the users whose *User ID*, *Global User ID*, *SCIM ID*, *Email*, or *Login Name* match your search criteria string. In this case the system doesn’t include the *First Name* and *Last Name* fields in the search.

    If you aren’t satisfied with the search result, edit your search criteria and repeat the step again.

    > ### Note:  
    > The search is case insensitive. The system searches for entries that begin with the typed string.
    > 
    > If you place asterisk \(\*\) in the beginning or in the middle of your search string the system will treat it as a regular character and will include it in the search. For example, if you type ***\*on*** in the *search* field, the system will look for users whose first three letters in any of the three fields are ***\*on***. If you type ***on*** or ***on\**** in the search field, the system will look for users whose first two letters in any of the three fields are ***on***.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Filtered Search**

    Press *Show Filters*, type your search criteria strings in at least one of the search fields, and press the *Enter* key
    
    </td>
    <td valign="top">
    
    The system checks the search fields simultaneously. Once the search is completed, it will list the users that match the search criteria from all the fields.

    > ### Note:  
    > The search is case insensitive. The system searches for entries that begin with the typed string.
    > 
    > If you place asterisk \(\*\) in the beginning or in the middle of your search string the system will treat it as a regular character and will include it in the search. For example, if you type ***\*on*** in the *First Name* field, the system will look for users whose first three letters of the first name are ***\*on***. If you type ***on*** or ***on\**** in the *First Name* field, the system will look for users whose first two letters of the first name are ***on***.


    
    </td>
    </tr>
    </table>
    
4.  Select the checkbox next to the user or users that you want to provision.

5.  Press *Provision Users*.

6.  Confirm the operation.

    If the operation is successful, the system displays the message ***<number of users\> provisioned***.


<a name="concept_iyh_s4y_cv"/>

<!-- concept\_iyh\_s4y\_cv -->

## Provision Users from Corporate User Store

> ### Note:  
> The content in this section is only relevant for SAP BTP, Neo environment.

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.

A user is automatically provisioned after he or she has been authenticated.

For more information about how to configure Identity Authentication to use a corporate user store in addition to its own user store, see [Configure Connection to a Corporate User Store](corporate-user-store-neo-environment-461d71c.md#loioe5e9662146f948b49c11d01284231d75).

<a name="concept_hch_gyr_cv"/>

<!-- concept\_hch\_gyr\_cv -->

## Provision Users at User Create and User Update

All newly created and updated users are automatically provisioned to the target systems configured in the administration console for SAP Cloud Identity Services. The users that use the self-registration service will be automatically provisioned to the target systems too.

For more information about user creation or user update, see **Related Information**

**Related Information**  


[Create a New User](create-a-new-user-348deef.md "As a tenant administrator, you can create a new user in the administration console for SAP Cloud Identity Services.")

[Add Administrators](add-administrators-bbbdbdd.md#loiobbbdbdd3899942ce874f3aae9ba9e21d "As a tenant administrator, you can add new administrators in the administration console for SAP Cloud Identity Services.")

[Import or Update Users for a Specific Application](import-or-update-users-for-a-specific-application-33838e0.md "As a tenant administrator, you can import new users or update existing ones for a specific application with a CSV file. You can also send activation emails to the users that have not received activation emails for that application so far.")

[Create User Resource \(Deprecated\)](../Development/create-user-resource-deprecated-cea8778.md "The create user resource method of the Identity Authentication implementation of the SCIM REST API protocol provides information on the creation of a user.")

[Update User Resource \(Deprecated\)](../Development/update-user-resource-deprecated-9e36479.md "The update user method of the implementation of the SCIM REST API protocol provides information on the update of a known user. The method does not create a new user.")

[Scenarios](../scenarios-fb9898d.md "Identity Authentication supports scenarios for consumers (business-to-consumer scenarios), for partners (business-to-business scenarios), and for employees (business-to-employee scenarios).")

