<!-- loio3a217c03afb749c2aae1280d57b58355 -->

# SSH Server \(Beta\)

Follow this procedure to set up an SSH server \(Beta\) as a source system.



<a name="loio3a217c03afb749c2aae1280d57b58355__prereq_nrn_mnf_lbb"/>

## Prerequisites

> ### Restriction:  
> This system is available for bundle tenants running on SAP Cloud Identity infrastructure and standalone tenants running on SAP Cloud Identity infrastructure and SAP BTP, Neo environment. Bundle tenants running on Neo environment can use it only through **SAP Jam Collaboration** and **SAP Identity Access Governance** bundle options.

-   You have credentials for a tenant in SAP Business Technology Platform. For more information, see: [Accounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8ed4a705efa0431b910056c0acdbf377)
-   \(Optional\) You have installed the Cloud Connector in your corporate environment and have done the initial configuration. You need this only when your SSH server resides in a remote system, outside your Neo environment. For more information, see [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

> ### Note:  
> This is a beta feature available on SAP Business Technology Platform. For more information, see: *Enable beta features* in [Change Subaccount Details](https://help.sap.com/docs/btp/sap-business-technology-platform/change-subaccount-details?version=Cloud)



<a name="loio3a217c03afb749c2aae1280d57b58355__context_i2g_rvw_mbb"/>

## Context

**SSH Server** is a system \(connector\) in beta state. It helps you execute bash scripts through SSH connection. The configuration allows you to attach separate scripts per entity lifecycle callback \(such as user create, group create/update, and so on\). This system helps you connect to remote machines via SSH tunnel, with or without use of the Cloud Connector, depending on whether the SSH port is visible or not.

The bash scripts can take as parameters fields that are coming from the entity JSON data. For example: *sudo su - vcap /home/myscript.sh $.userName $.email*



<a name="loio3a217c03afb749c2aae1280d57b58355__steps_c53_3ky_rdb"/>

## Procedure

1.  Access the Identity Provisioning UI.

    -   [Access Identity Provisioning UI of Bundle Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/7ab5884ffbc44461a57622d2f633e57c.html "Access the Identity Provisioning UI when the service is bundled as part of an SAP cloud solution's license.") :arrow_upper_right:
    -   [Access Identity Provisioning UI of Standalone Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/61fd82ed48ab42b2bc74626926c1722c.html "Access the Identity Provisioning user interface as a standalone product.") :arrow_upper_right:

2.  Sign in to the administration console of SAP Cloud Identity Services and navigate to *Identity Provisioning* \> *Source Systems*.

3.  Add *SSH Server \(Beta\)* as a source system. For more information, see [Add New Systems](Operation-Guide/add-new-systems-bd214dc.md).

4.  Choose the *Properties* tab to configure the connection settings for your system.

    > ### Note:  
    > If your tenant is running on SAP BTP, Neo environment, you can create a [connectivity destination](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/72696d6d06c0490394ac3069da600278.html) in your subaccount in the SAP BTP cockpit, and then select it from the *Destination Name* combo box in your Identity Provisioning User Interface.
    > 
    > If one and the same property exists both in the cockpit and in the *Properties* tab, the value set in the *Properties* tab is considered with higher priority.
    > 
    > We recommend that you use the *Properties* tab. Use a connectivity destination only if you need to reuse one and the same configuration for multiple provisioning systems.

    Below are listed all available SSH Server properties. Some of them can be mandatory and others – optional, depending on your scenario.

    **Mandatory Properties**


    <table>
    <tr>
    <th valign="top">

    Property Name
    
    </th>
    <th valign="top">

    Description & Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `ProxyType`
    
    </td>
    <td valign="top">
    
    Possible values:

    -   **Internet** – if the SSH port is visible in your Neo environment
    -   **OnPremise** – if the SSH port is not directly accessible, and you have to use theCloud Connector. You have to configure TCP protocol connection to the SSH host and port \(specify the configuration properties `ssh.host` and `ssh.port`\).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `CloudConnectorLocationId`
    
    </td>
    <td valign="top">
    
    Relevant when the proxy type is *OnPremise*. Use it only if your SAP Business Technology Platform account uses more than one Cloud Connector.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.auth.type`
    
    </td>
    <td valign="top">
    
    Supported SSH authentication types:

    -   **key**
    -   **pwd**
    -   **otp**
    -   **key+otp**
    -   **key+pwd**
    -   **pwd+otp**
    -   **key+pwd+otp**


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.host`
    
    </td>
    <td valign="top">
    

    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.port`
    
    </td>
    <td valign="top">
    
    22
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.username`
    
    </td>
    <td valign="top">
    

    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.password`
    
    </td>
    <td valign="top">
    
    \(Credential\) Taken into account only if the authentication type includes **pwd**. That means any of the following:

    -   `ssh.auth.type` = *pwd*
    -   `ssh.auth.type` = *pwd+otp*
    -   `ssh.auth.type` = *key+pwd*
    -   `ssh.auth.type` = *key+pwd+otp*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.totp.secret.key`
    
    </td>
    <td valign="top">
    
    \(Credential\) Taken into account only if the authentication type includes **otp**. That means any of the following:

    -   `ssh.auth.type` = *otp*
    -   `ssh.auth.type` = *key+otp*
    -   `ssh.auth.type` = *pwd+otp*
    -   `ssh.auth.type` = *key+pwd+otp*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.private.key.type`
    
    </td>
    <td valign="top">
    
    The type of the SSH private key. Possible values:

    -   **ssh-rsa**
    -   **ssh-dsa**

    Default value: *ssh-rsa*

    > ### Note:  
    > If you choose *ssh-rsa*, the key should be in format **PKCS \#8**, non-encrypted.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.private.key`
    
    </td>
    <td valign="top">
    
    \(Credential\) Taken into account only if the authentication type includes **key**. That means any of the following:

    -   `ssh.auth.type` = *key*
    -   `ssh.auth.type` = *key+pwd*
    -   `ssh.auth.type` = *key+otp*
    -   `ssh.auth.type` = *key+pwd+otp*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.read.groups.command`
    
    </td>
    <td valign="top">
    
    Path to the bash command you need to execute to read groups.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `ssh.read.users.command`
    
    </td>
    <td valign="top">
    
    Path to the bash command you need to execute to read users.
    
    </td>
    </tr>
    </table>
    
    To learn what additional properties are relevant to this system, see [List of Properties](list-of-properties-d6f3577.md). You can use the main search, or filter properties by the *Name* or *System Type* columns.

5.  \(Optional\) Configure the transformations.

    Transformations are used to map the user attributes from the data model of the source system to the data model of the target system, and the other way around. The Identity Provisioning offers a default transformation for the *SSH Server \(Beta\)* source system, whose settings are displayed under the *Transformations* tab after saving its initial configuration.

    You can change the default transformation mapping rules to reflect your current setup of entities in your SSH server. For more information, see [Manage Transformations](Operation-Guide/manage-transformations-2d0fbe5.md).

    **Default transformation:**

    > ### Code Syntax:  
    > ```
    > 
    > {
    >     "user": {
    >         "mappings": [
    >             {
    >                 "targetPath": "$",
    >                 "sourcePath": "$"
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem",
    >                 "correlationAttribute": true
    >             },
    >             {
    >                 "sourcePath": "$.userName",
    >                 "optional": true,
    >                 "correlationAttribute": true
    >             }
    >         ]
    >     },
    >     "group": {
    >         "ignore": true,
    >         "mappings": [
    >             {
    >                 "targetPath": "$",
    >                 "sourcePath": "$"
    >             },
    >             {
    >                 "sourcePath": "$.id",
    >                 "targetVariable": "entityIdSourceSystem"
    >             }
    >         ]
    >     }
    > }
    > ```

6.  Now, add a target system to provision users and groups into it. Choose from: [Target Systems](target-systems-ab3f641.md)




<a name="loio3a217c03afb749c2aae1280d57b58355__postreq_vrz_scv_v1b"/>

## Next Steps

-   Before starting a provisioning job, you can first subscribe for e-mail notifications from the source system you use in your scenario. This way, you will be notified by e-mail about eventual failed entities during the jobs. For more information, see [Manage Job Notifications](Monitoring-and-Reporting/manage-job-notifications-d055bc2.md).
-   Start an identity provisioning job. For more information, see [Monitor Provisioning Job Logs](Monitoring-and-Reporting/monitor-provisioning-job-logs-e5b5176.md).

