<!-- loio9942ede4fae84934a8eb184a0015c305 -->

# Corporate User Store \(Cloud Foundry Environment\)

Configure corporate user store for applications in the Cloud Foundry environment to allow users to authenticate with their corporate credentials, without the need to use another set of credentials for their cloud access.

> ### Note:  
> The content in this section is only relevant for SAP BTP, Cloud Foundry environment.



## Overview

Identity Authentication can connect with the following corporate user stores:

-   Microsoft Active Directory

This scenario works with the connectivity proxy component \(logically part of the Connectivity service\). For more information about the connectivity proxy, see [How the Connectivity Proxy Works](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/14ad61db386949d8abaf45c641aa7dc9.html)

The connection between SAP BTP and the corporate user store is carried out with a Cloud Connector.

![](images/Cloud_Connector_CF_70e45ef.png)



## Authentication Flow

The *Corporate User Store* option is configured properly. A user tries to access a trusted application for the first time with the on-premise credentials, *Login Name* and *Password* entered correctly. This user is authenticated successfully against the corporate user store. With this initial successful authentication of the user, a partial user record is created in the user store for Identity Authentication. It is created with user details taken from the corporate user store. The cloud user store doesn’t copy the user's credentials. For more details about what data is copied from the corporate user store, see [User Records](corporate-user-store-neo-environment-461d71c.md#loio2243cbca63e5480fb4a6e2bba8049678). With subsequent logins, the user is always authenticated against the corporate user store, and the user record is updated.

For the first logon with on-premise credentials, the user enters his or her *Login Name* and a *Password*. For subsequent logins the user can use either his or her *Login Name*, *E-Mail*, or *User ID*, and the *Password*.

> ### Remember:  
> If the user has enabled the *Remember me* option, the following limitations are observed:
> 
> -   when a user is authenticating with remember me cookie, his or her user record in Identity Authentication is not updated.
> -   if the user changes his or her password in the corporate network, the remember me cookie is not invalidated.
> 
> For more information, see [Use the Remember Me Option](../User-Guide/use-the-remember-me-option-bc7c6c6.md).

> ### Note:  
> The user in the corporate user store must have the `mail` attribute.
> 
> The tenant administrator needs to monitor and prevent the coexistence of a cloud and on-premise user with one and the same e-mail address. The tenant administrator has to instruct the users to logon for the first time with their *Login Name*, not with the *E-Mail*.

If a user with a user record in the cloud user store is deleted in the corporate user store, the user can’t authenticate using Identity Authentication. The user record for this user remains in the cloud user store, and the tenant administrator can delete it via the administration console for SAP Cloud Identity Services. For more information, see [Delete Users](delete-users-bbfaf5f.md).

For all users from the corporate user store, a second factor for authentication can be enabled for some applications, or cloud user groups can be assigned. For more details, see [Configure Risk-Based Authentication for an Application](configure-risk-based-authentication-for-an-application-bc52fbf.md#loiobc52fbf3d59447bbb6aa22f80d8b6056) and [Assign Groups to a User](assign-groups-to-a-user-bfdeb9c.md).



## Control Access to Applications and Resources

In the scope of the *Corporate User Store* scenario, you can manage access to applications and their resources based on the groups available in the corporate user store.

The corporate user groups are sent to an application in the SAML 2.0 assertion. `corporate_groups` is the attribute that contains the groups that the user in the corporate user store is assigned to. For more details about how the groups are sent to the application in the SAML 2.0 assertion, see [Configure the User Attributes Sent to the Application](configure-the-user-attributes-sent-to-the-application-d361407.md).

> ### Note:  
> If your application is deployed on the SAP BTP, the corporate user store groups, relevant for the application, and contained in the `corporate_groups` attribute in the SAML 2.0 assertion, can be mapped to assertion-based groups created in SAP BTP cockpit. For more information, see [Map Role Collections to User Attributes](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/b3fbb1a9232d4cf99967a0b29dd85d4c.html).

You can also restrict access to applications based on membership in a corporate user group by setting different rules via risk-based authentication. For more information, see [Configure Risk-Based Authentication for an Application](configure-risk-based-authentication-for-an-application-bc52fbf.md#loiobc52fbf3d59447bbb6aa22f80d8b6056).

 <a name="loio500ac5e7d6574fdb8177ff4b637f1da2"/>

<!-- loio500ac5e7d6574fdb8177ff4b637f1da2 -->

## User Records

When a user has been successfully authenticated for the first time with the credentials from the corporate user store, a record for that user is created in Identity Authentication. That user record is created with details from the corporate user store. In this record, the user is created with a *User Type* `employee`. This *User Type* cannot be changed.

For more information about the attributes taken from the Active Directory and their mapping to the user store of Identity Authentication, see **Configure SAP BTP When Connecting to an LDAP User Store** in [Configure SAP BTP](corporate-user-store-cloud-foundry-environment-9942ede.md#loiodd8240d6a4f54e938ec867c21a4e9222).

**Related Information**  


[Security Information](../Security/security-information-6e88d82.md "This document is an overview of security-relevant information that applies to Identity Authentication, and contains recommendations about how administrators should secure it.")

 <a name="loio141af10d3c204f399b388898b4ef81af"/>

<!-- loio141af10d3c204f399b388898b4ef81af -->

## Configure Connection to a Corporate User Store

To configure connection to a corporate user store, you have to make the following configurations in SAP BTP and in Identity Authentication.

For more details about how to configure these systems, see:

-   [Configure SAP BTP](corporate-user-store-cloud-foundry-environment-9942ede.md#loiodd8240d6a4f54e938ec867c21a4e9222)
-   [Configure Identity Authentication](corporate-user-store-cloud-foundry-environment-9942ede.md#loiode5cff7e1ec14bd08d01e429390fe193)

 <a name="loiodd8240d6a4f54e938ec867c21a4e9222"/>

<!-- loiodd8240d6a4f54e938ec867c21a4e9222 -->

## Configure SAP BTP



## Context

The configuration of SAP BTP depends on the type of the user store. You have the option to connect to a Microsoft Active Directory user store.

**Data Center Mapping**


<table>
<tr>
<th valign="top">

Identity Authentication Data Center



</th>
<th valign="top">

Cloud Foundry Data Center



</th>
</tr>
<tr>
<td valign="top">

eu-nl/eu-de - Rot/Amsterdam



</td>
<td valign="top">

cf-eu10



</td>
</tr>
<tr>
<td valign="top">

ap-cn - Shanghai



</td>
<td valign="top">

cf-ap11 - Singapore



</td>
</tr>
<tr>
<td valign="top">

na-us - Sterling/Toronto



</td>
<td valign="top">

cf-us10 - US East \(VA\)



</td>
</tr>
<tr>
<td valign="top">

ap-jp - Tokyo/Osaka



</td>
<td valign="top">

cf-jp10 - Japan \(Tokyo\)



</td>
</tr>
<tr>
<td valign="top">

ap-au Sydney/Tokyo



</td>
<td valign="top">

cf-ap10 - Australia \(Sydney\)



</td>
</tr>
<tr>
<td valign="top">

la-br - São Paulo



</td>
<td valign="top">

cf-br10 - Brazil \(São Paulo\)



</td>
</tr>
<tr>
<td valign="top">

aws-ap-se-1 Singapore



</td>
<td valign="top">

cf-ap11 - Singapore



</td>
</tr>
<tr>
<td valign="top">

azr-us-we / US West



</td>
<td valign="top">

cf-us20 - US West \(WA\)



</td>
</tr>
<tr>
<td valign="top">

azr-na-ca / Toronto



</td>
<td valign="top">

cf-ca10 - Canada \(Montreal\)



</td>
</tr>
<tr>
<td valign="top">

aws-fr - Frankfurt



</td>
<td valign="top">

cf-eu10 - Europe \(Frankfurt\)



</td>
</tr>
<tr>
<td valign="top">

aws/ap-northeast-2 / Seoul



</td>
<td valign="top">

cf-ap12 - South Korea \(Seoul\)



</td>
</tr>
<tr>
<td valign="top">

ap-sa / Riyadh



</td>
<td valign="top">

cf-eu10 - Europe \(Frankfurt\)



</td>
</tr>
<tr>
<td valign="top">

ap-ae / Dubai



</td>
<td valign="top">

cf-eu10 - Europe \(Frankfurt\)



</td>
</tr>
</table>

 <a name="task_hlb_hrr_gv"/>

<!-- task\_hlb\_hrr\_gv -->

### Configure SAP BTP When Connecting to a Microsoft Active Directory User Store



<a name="task_hlb_hrr_gv__steps_lsv_gsr_gv"/>

## Procedure

1.  Log on to SAP BTP cockpit with the cockpit administrator role. For more information, see [Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8d6e3a0fa4ab43e4a421d3ed08128afa).

2.  In the SAP BTP cockpit, choose in the navigation area *Services* \> *Instances and Subscriptions*.

3.  Choose *Create* and select the following info from the dropdowns:

    -   *Service* - ***Cloud Identity Services***
    -   *Plan* - ***Connectivity***

        > ### Note:  
        > If the *Connectivity* plan is not available check the entitlements configurations of your subaccount. For more information, see [Managing Entitlements and Quotas Using the Cockpit](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/c8248745dde24afb91479361de336111.html).


    The Cloud Identity Services appears under the *Subscriptions* tab.

4.  Install an Cloud Connector in your corporate network.

    For more information, see [Installation](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/57ae3d62f63440f7952e57bfcef948d3.html).

5.  Connect the Cloud Connector between your corporate user store and SAP BTP account.

    -   If you haven't used your Cloud Connector before, see [Initial Configuration](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/db9170a7d97610148537d5a84bf79ba2.html).

    -   If you have used your Cloud Connector before, you can start the configuration from [Set up Connection Parameters and HTTPS proxy](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/db9170a7d97610148537d5a84bf79ba2.html#loiodb9170a7d97610148537d5a84bf79ba2__configure_proxy).


6.  Connect SAP BTP with your corporate user store.

    > ### Note:  
    > You have to specify the SAP BTP settings. For more information, see [Configure the On-Premise User Store](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/933034aeb00d489eaf21d50bbb12fed5.html), without the *Prerequisites* section.
    > 
    > The *User Name* field must be in the ***<service\_user\_name\>@<domain\>*** format.
    > 
    > For the *User Path* and *Group Path* fields, specify the Microsoft Active Directory tree that contains the users and groups, respectively. For example, if the tree has the following structure:
    > 
    > ![](images/LDAP_Tree_ca9584b.png)
    > 
    > The user and group paths should appear as in the table below:
    > 
    > 
    > <table>
    > <tr>
    > <td valign="top">
    > 
    > User Path
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > ou=People,dc=example,dc=com
    > 
    > 
    > 
    > </td>
    > </tr>
    > <tr>
    > <td valign="top">
    > 
    > Group Path
    > 
    > 
    > 
    > </td>
    > <td valign="top">
    > 
    > ou=People,dc=example,dc=com
    > 
    > 
    > 
    > </td>
    > </tr>
    > </table>

7.  Include additional attributes.

    > ### Note:  
    > You can add the `employeeNumber`, `division`, `department`, and `organization` attributes that are defined in the SCIM Enterprise User Schema Extension.
    > 
    >  Cloud Connector uses the SCIM protocol to transfer the data, so the Active Directory attributes are mapped first to the SCIM attributes. When the data is provisioned, the SCIM attributes are mapped to the user store attributes of Identity Authentication.

    1.  In your system go to `/sapcc-<version>/config_master/com.sap.core.connectivity.protocol.scim/`

    2.  On that level, create a new *idstorage.cfg* file based on the *idstorage\_extended\_schema.cfg* file which is given as an example in the folder.

    3.  Edit the newly created file. For more details, see the information below:

        To add new user attributes you have to edit the whole file.

        > ### Caution:  
        > This file overwrites the configurations you made in [Configure the User Store](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/933034aeb00d489eaf21d50bbb12fed5.html) Be careful not to change the user attributes taken from Microsoft Active Directory.

        In this section, provide the same information as when you specified the SAP BTP settings in the previous step.

        ```
        
         {
         "LDAPServers": [
            {
              "Host": "<The host name of the LDAP server to be contacted>",
        	  "Port": "<The port where the LDAP service is running. If omitted then the default LDAP port will be used - 389 for plain connections and 636 for SSL connections>"
            }
         ],
        
         "UserPath": "<LDAP subtree containing the users. Example "DC=users,DC=organisation,DC=location">",
         "GroupPath": "<LDAP subtree containing the groups. Example "DC=groups,DC=organisation,DC=location">",
        
         "ServiceUser": {
            "Name": "<The name of the user that will be used to establish communication with the LDAP. In case of Active Directory the user name should contains Domain suffix, e.g. "john@ACME.COM">",
            "Password": "<Password of this user>"
         },
        ```

        If you want to use SSL, we recommend that you configure this section.

        ```
        
         "UseSSL": "<Possible values are "true" or "false". If true then the communication to LDAP will go over SSL>",
         "IdentityKeystorePath": "<File system path to the client identity keystore - must be set if the used LDAP server requires client certificate authentication>",
         "IdentityKeystorePassword": "<The password of the client identity keystore>",
         "TrustKeystorePath": "<File system path to the trusted CAs keystore - must be set if UseSSL is true>",
         "TrustKeystorePassword": "<The password of the trusted CAs keystore>",
        
         "IsActiveDirectory": "<Possible values are "true" (default value if missing) or "false". "true" indicates that the LDAP server is Active Directory>",
         "ExcludeUsersAttribute": {
            "AttributeName": "<Name of user attribute that will be used to exclude some users from the result depending on their type. Attribute is treated as bitwise. Such attribute for Active Directory is "UserAccountControl">",
            "AttributeMask": "<Bitwise mask represented as decimal value. In case any of the high bits of this mask match with the corresponding bit of the value of the above attribute, the user will be excluded from the result. Example mask for Active Directory is "67121154" - it is the sum of the following flags ACCOUNTDISABLE(2), WORKSTATION_TRUST_ACCOUNT(4096), SERVER_TRUST_ACCOUNT(8192) and PARTIAL_SECRETS_ACCOUNT(67108864)>"
         },
        ```

        In this section add the additional attributes `employeeNumber`, `division`, `department`, and `organization`, defined in the SCIM Enterprise User Schema Extension.

        ```
        
         {
          "SingularAttributes": [
              {
                  "SCIMAttribute": "userName",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "sAMAccountname"
                         }
                      }
                  ]
               },
                  "SCIMAttribute": "name",
                  "mappings": [
                      {
                         "SCIMSubAttribute": "givenName",
                         "LDAPAttribute": {
                             "name": "givenName"
                         }
                      },
                      {
                         "SCIMSubAttribute": "familyName",
                         "LDAPAttribute": {
                             "name": "sn"
                         }
                      },
                      {
                         "SCIMSubAttribute": "honorificPrefix",
                         "LDAPAttribute": {
                             "name": "personalTitle"
                         }
                      }
                  ]
               },
               {
                  "SCIMAttribute": "displayName",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "displayName"
                         }
                      }
                  ]
               },
               {
                  "SCIMAttribute": "locale",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "locale"
                         }
                      }
                  ]
               },
               {
                  "SCIMAttribute": "timeZone",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "timezone"
                         }
                      }
                  ]
               },
               {
                  "SCIMAttribute": "employeeNumber",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "<LDAP property containing the employee number"
                         }
                      }
                  ]
               },
               {
                  "SCIMAttribute": "division",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "<LDAP property containing the division>"
                         }
                      }
                  ]
               },
               {
                  "SCIMAttribute": "department",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "<LDAP property containing the department>"
                         }
                      }
                  ]
               },
               {
                  "SCIMAttribute": "organization",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "company"
                         }
                      }
                  ]
               },
        	  {
                  "SCIMAttribute": "costCenter",
                  "mappings": [
                      {
                         "LDAPAttribute": {
                             "name": "<LDAP property containing the cost center>"
                         }
                      }
                  ]
               }
          ],
          "MultiValuedAttributes": [
              {
                 "SCIMAttribute": "emails",
                 "values": [
                     {
                        "primary": "true",
                        "mappings": [
                            {
                                "SCIMSubAttribute": "value",
                                "LDAPAttribute": {
                                    "name": "mail"
                                }
                            }
                        ]
                     }
                 ]
              },
              {
                 "SCIMAttribute": "phoneNumbers",
                 "values": [
                     {
                         "type": "work",
                         "primary": "true",
                         "mappings": [
                             {
                                 "SCIMSubAttribute": "value",
                                 "LDAPAttribute": {
                                     "name": "telephoneNumber"
                                 }
                             }
                         ]
                     },
                     {
                         "type": "fax",
                         "mappings": [
                             {
                                 "SCIMSubAttribute": "value",
                                 "LDAPAttribute": {
                                     "name": "facsimileTelephoneNumber"
                                 }
                             }
                         ]
                     },
                     {
                         "type": "cell",
                         "mappings": [
                             {
                                 "SCIMSubAttribute": "value",
                                 "LDAPAttribute": {
                                     "name": "mobile"
                                 }
                             }
                         ]
                     }
                 ]
              },
              {
                 "SCIMAttribute": "addresses",
                 "values": [
                     {
                         "primary": "true",
                         "mappings": [
                             {
                                 "SCIMSubAttribute": "streetAddress",
                                 "LDAPAttribute": {
                                     "name": "streetAddress"
                                 }
                             },
                             {
                                 "SCIMSubAttribute": "locality",
                                 "LDAPAttribute": {
                                     "name": "l"
                                 }
                             },
                             {
                                 "SCIMSubAttribute": "region",
                                 "LDAPAttribute": {
                                     "name": "st"
                                 }
                             },
                             {
                                 "SCIMSubAttribute": "postalCode",
                                 "LDAPAttribute": {
                                     "name": "postalCode"
                                 }
                             },
                             {
                                 "SCIMSubAttribute": "country",
                                 "LDAPAttribute": {
                                     "name": "co"
                                 }
                             }
                         ]
                     }
                 ]
              }
          ]
          }
        
        ```

    4.  Save your changes.

    5.  Restart Cloud Connector to apply the new attributes mapping, which comes from *idstorage.cfg*


    This file overwrites the configurations you made in [Configuring the User Store](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/933034aeb00d489eaf21d50bbb12fed5.html).




## Next Steps

The following table shows the default mapping between the Active Directory user attributes and the SCIM attributes. It also shows the existing mapping between the SCIM attributes and the attributes in the user store of Identity Authentication.

**Detailed Attribute Mapping Between Active Directory and SCIM, and between SCIM and the User Store of Identity Authentication**


<table>
<tr>
<th valign="top">

Microsoft Active Directory Attributes



</th>
<th valign="top">

SCIM Attributes



</th>
<th valign="top">

 Identity Authentication User Store Attribute



</th>
</tr>
<tr>
<td valign="top">

sAMAccountname



</td>
<td valign="top">

userName



</td>
<td valign="top">

loginName



</td>
</tr>
<tr>
<td valign="top">

givenName



</td>
<td valign="top">

givenName



</td>
<td valign="top">

firstName



</td>
</tr>
<tr>
<td valign="top">

sn



</td>
<td valign="top">

familyName



</td>
<td valign="top">

lastName



</td>
</tr>
<tr>
<td valign="top">

personalTitle



</td>
<td valign="top">

honorificPrefix



</td>
<td valign="top">

title



</td>
</tr>
<tr>
<td valign="top">

displayName



</td>
<td valign="top">

displayName



</td>
<td valign="top">

displayName



</td>
</tr>
<tr>
<td valign="top">

locale



</td>
<td valign="top">

locale



</td>
<td valign="top">

language



</td>
</tr>
<tr>
<td valign="top">

timezone



</td>
<td valign="top">

timeZone



</td>
<td valign="top">

timeZone



</td>
</tr>
<tr>
<td valign="top">

employeeNumber



</td>
<td valign="top">

employeeNumber



</td>
<td valign="top">

personnelNumber



</td>
</tr>
<tr>
<td valign="top">

division



</td>
<td valign="top">

division



</td>
<td valign="top">

division



</td>
</tr>
<tr>
<td valign="top">

department



</td>
<td valign="top">

department



</td>
<td valign="top">

department



</td>
</tr>
<tr>
<td valign="top">

costCenter



</td>
<td valign="top">

costCenter



</td>
<td valign="top">

costCenter



</td>
</tr>
<tr>
<td valign="top">

company



</td>
<td valign="top">

organization



</td>
<td valign="top">

company



</td>
</tr>
<tr>
<td valign="top">

mail



</td>
<td valign="top">

emails.value



</td>
<td valign="top">

mail



</td>
</tr>
<tr>
<td valign="top">

telephoneNumber



</td>
<td valign="top">

phoneNumbers\[work\].value



</td>
<td valign="top">

telephone



</td>
</tr>
<tr>
<td valign="top">

facsimileTelephoneNumber



</td>
<td valign="top">

phoneNumbers\[fax\].value



</td>
<td valign="top">

fax



</td>
</tr>
<tr>
<td valign="top">

mobile



</td>
<td valign="top">

phoneNumbers\[cell\].value



</td>
<td valign="top">

mobile



</td>
</tr>
<tr>
<td valign="top">

streetAddress



</td>
<td valign="top">

addresses. streetAddress



</td>
<td valign="top">

street



</td>
</tr>
<tr>
<td valign="top">

l



</td>
<td valign="top">

Addresses.locality



</td>
<td valign="top">

city



</td>
</tr>
<tr>
<td valign="top">

st



</td>
<td valign="top">

Addresses.region



</td>
<td valign="top">

state



</td>
</tr>
<tr>
<td valign="top">

postalCode



</td>
<td valign="top">

Addresses. postalCode



</td>
<td valign="top">

zip



</td>
</tr>
<tr>
<td valign="top">

co



</td>
<td valign="top">

Addresses.country



</td>
<td valign="top">

country



</td>
</tr>
</table>

> ### Note:  
> The attributes `employeeNumber`, `division`, `department`, `costCenter` in the *Microsoft Active Directory Attributes* column are given as examples. They can differ according to the specific LDAP properties containing these attributes.
> 
> If the attribute `language` or `country` comes from the corporate user store in:
> 
> -   small letters, then the respective keys in the master data service must be updated to small letters to be sent in this way to the service provider.
> 
> -   capital letters, then the respective keys in the master data service must be updated to capital letters to be sent in this way to the service provider. By default, `language` and `country` are in capital letters in the master date service.
> 
> 
> For more information how to update the master data service, see [Change Master Data Texts REST API](../Development/change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c).

[Configure Identity Authentication](corporate-user-store-neo-environment-461d71c.md#loio2c3ede1d7c454b8a8f820248ee3b705c)

 <a name="loiode5cff7e1ec14bd08d01e429390fe193"/>

<!-- loiode5cff7e1ec14bd08d01e429390fe193 -->

## Configure Identity Authentication



<a name="loiode5cff7e1ec14bd08d01e429390fe193__context_w4m_f5f_hnb"/>

## Context



<a name="loiode5cff7e1ec14bd08d01e429390fe193__steps_ibc_d4t_hs"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Identity Providers*, choose the *Source Systems* tile.

3.  Press the *Create* button on the left-hand panel to add a new source system to the list.

4.  Make the corresponding entries in the configuration for the target system you want to add:

    -   *Source System*


        <table>
        <tr>
        <th valign="top">

        Configuration


        
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

        \(optional\) The name of the configuration.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Type*


        
        </td>
        <td valign="top">

        Select the *Microsoft Active Directory* type.


        
        </td>
        </tr>
        </table>
        

    -   *Configuration*


        <table>
        <tr>
        <th valign="top">

        Configurations


        
        </th>
        <th valign="top">

        Description


        
        </th>
        </tr>
        <tr>
        <td valign="top">

        *Environment*


        
        </td>
        <td valign="top">

        Cloud Foundry


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *System ID*


        
        </td>
        <td valign="top">

        This is the name of the system. Provide a name of your choice as *System ID*.


        
        </td>
        </tr>
        <tr>
        <td valign="top">

        *Subaccount domains*


        
        </td>
        <td valign="top">

        Select your SAP BTP subaccount's domain from the drop-down.


        
        </td>
        </tr>
        </table>
        

5.  Save your configuration.

    If the operation is successful, you receive the message ***Source system <System ID name\> created***.




## Results

When the configuration is complete, the user can log in to the application with the on-premise credentials. The first logon requires *Login Name* and password. After successful authentication, a new user record is created in Identity Authentication with type `employee`.

