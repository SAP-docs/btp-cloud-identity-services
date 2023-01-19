<!-- loio334964514e8b48cb88c8ed07f5ee6a14 -->

# Configure Identity Provisioning Target Systems for Real-Time User Provisioning

You can configure Identity Provisioning target systems for real-time user provisioning via the administration console for SAP Cloud Identity Services.



## Context

In this scenario you configure Identity Provisioning as a target system in Identity Authentication, and Identity Authentication as a source system in Identity Provisioning. As a result Identity Authentication provisions users to Identity Provisioning, which in its turn provisions these users to the targets systems, configured for Identity Authentication.

> ### Note:  
> The user update to Identity Provisioning won't be triggered when the operation on the user \(create,update, delete\) is initiated by Identity Provisioning.

![](images/Configure_Identity_Provisioning_Target_System_d2dddcf.png)

The configuration of the OAuth authentication scenario is done in the SAP BTP cockpit, the user interface of the Identity Provisioning service, and the administration console for SAP Cloud Identity Services. To create OAuth Client credentials, and add a source and target system in Identity Provisioning, and configure Identity Authentication, choose your scenario, and follow the steps described in [Real-Time Provisioning: Identity Authentication](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/70afd909734842b08ff8f1be5b01bc2a.html).

> ### Note:  
> For the OAuth authentication scenario, you should skip the procedure below, done in the administration console for SAP Cloud Identity Services, if you have completed all steps \(procedure I, II, III\) described in [Real-Time Provisioning: Identity Authentication](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/70afd909734842b08ff8f1be5b01bc2a.html).

**Prerequisites**

-   You are assigned the *Manage Users* role. For more information about how to assign administrator roles, see [Edit Administrator Authorizations](edit-administrator-authorizations-86ee374.md).

-   You have added a source system in the Identity Provisioning UI of type *Identity Authentication*. For more information, see [Identity Authentication](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/e4e25f1fae094c2a89ad62159e1cd230.html) .
-   \(OAuth authentication scenario\) You have made the required configurations in the SAP BTP cockpit, and in the Identity Provisioning UI.



<a name="loio334964514e8b48cb88c8ed07f5ee6a14__steps_esh_zdb_vhb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Real-Time Provisioning* tile.

    This operation opens a list of the target systems.

3.  Press the *\+Add* button on the left-hand panel to add a new target system to the list.

4.  Make the corresponding entries in the *Target Configurations* and *Authentication Configurations* fields for the target system you want to add.

    All fields are obligatory.


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

    *Display Name* 


    
    </td>
    <td valign="top">

    Put a name for the target system you are creating.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Type*


    
    </td>
    <td valign="top">

    Choose *Identity Provisioning* from the dropdown.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Version*


    
    </td>
    <td valign="top">

    -   Version 1 - real-time provisioning works when the Identity Authentication source system uses the Identity Authentication SCIM API \(in short, SCIM API version 1\). This means, you need to set the `ias.api.version` property to 1, and use transformations which are relevant to SCIM API version 1.

    -   Version 2 - real-time provisioning works when the Identity Authentication source system uses the Identity Directory SCIM API \(in short, SCIM API version 2\). This means, you need to set the `ias.api.version` property to 2, and use transformations which are relevant to SCIM API version 2.

    For more information, see [Source Systems - Identity Authentication](https://help.sap.com/docs/IDENTITY_PROVISIONING/f48e822d6d484fa5ade7dda78b64d9f5/e4e25f1fae094c2a89ad62159e1cd230.html).


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *SCIM URL*


    
    </td>
    <td valign="top">

    The *SCIM URL* should be in the following pattern: `https://ipsproxy<provider_subaccount>-<consumer_subaccount>.<sap_cp_domain>/ipsproxy/api/v1/systems/<Identity_Authentication_source_system_id>/entities/user`

    For example: `https://ipsproxyxyz123az-abcd456qw.hana.ondemand.com/ipsproxy/api/v1/systems/12ab12345-1234-a1b2-12ab-12a34bcde678d/entities/user`

    > ### Tip:  
    > -   You can copy the basic part of the URL from the cockpit. Under your subaccount, go to *Applications* \> *Subscriptions* \> *Subscribed Java Applications* \> *ipsproxy*. The *Application URL* is the basic part of the URL.
    > 
    > -   The `source_system_id` is a randomly generated string of numbers and letters. You can see this ID at the end of the URL, when the respective source system is chosen in Identity Provisioning.


    
    </td>
    </tr>
    </table>
    
5.  Select the *Authentication Mechanism* and fill in the respective fields.

    -   For *OAuth*

        ****


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

        *OAuth URL*


        
        </td>
        <td valign="top">

        In the Cockpit, choose the *Security* \> *OAuth* section, and go to the *Branding* tab. Copy the *Token Endpoint* link and paste it in the *OAuth URL* field in the administration console for SAP Cloud Identity Services.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Client ID*


        
        </td>
        <td valign="top">

        Use the *ID* of your registered OAuth client.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Client Secret*


        
        </td>
        <td valign="top">

        Use the *Secret* of your registered OAuth client.


        
        </td>
        </tr>
        </table>
        
    -   For *Basic* - add *Username* and *Password*. The credentials are the same as the credentials specified in the creation of an source system in the Identity Provisioning tenant. For more information, see [Identity Authentication](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/e4e25f1fae094c2a89ad62159e1cd230.html).
    -   For *Certificate* - Add a Common Name \(CN\) and password to generate the X.509 certificate. The maximum length of the CN is 64 characters. Once the certificate is generated it is saved as a .crt file. The common name \(CN\) in the generated certificate is in the format <common name\> \(<admin user ID\>\), where common name is the CN provided by the administrator, and admin user ID is the administrator's user id.

        Identity Authentication supports SAP Passport CA as trusted certificate authority \(CA\).


    > ### Note:  

6.  Save your changes.

    If the operation is successful, the system displays the message `System <name of system> configuration updated.`

7.  Choose *Test Connection* before executing the provisioning.

    If the setup is correct, the following message is displayed: *"Connection to the selected target system was established successfully."*

8.  Choose *Provision*.




<a name="loio334964514e8b48cb88c8ed07f5ee6a14__postreq_nq5_pwf_rpb"/>

## Next Steps

Now go to your system, the one for which you have created a target connector in the Identity Provisioning administration console, and check if the new users have been provisioned there.

> ### Remember:  
> Once the initial operation is successfully executed, every next newly created or updated user will be provisioned immediately and automatically.

**Related Information**  


[Configure SAP Jam Target Systems for Real-Time Provisioning](configure-sap-jam-target-systems-for-real-time-provisioning-a923427.md "Tenant administrators can configure SAP Jam target systems for real-time provisioning via the administration console for SAP Cloud Identity Services.")

[Provision Users to Target Systems](provision-users-to-target-systems-af6f78b.md "Tenant administrators can provision users of Identity Authentication to SAP Jam and Identity Provisioning target systems target system.")

[Delete Target System](delete-target-system-6372e9a.md "As a tenant administrator, you can delete one or more target systems in a tenant of Identity Authentication.")

