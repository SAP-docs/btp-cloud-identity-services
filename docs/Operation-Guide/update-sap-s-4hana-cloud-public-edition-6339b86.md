<!-- loio6339b86f23b54f48a02ab269b12733c8 -->

# Update SAP S/4HANA Cloud Public Edition

Update the SAP S/4HANA Cloud Public Edition connector to a new version.

The SAP S/4HANA Cloud Public Edition connector supports two versions, corresponding to the APIs used for integration with Identity Provisioning:

-   **Version 1**: Uses the SOAP-based API provided through the communication scenario SAP\_COM\_0193.

-   **Version 3**: Uses the SCIM-based API provided through the communication scenario SAP\_COM\_0465.


Updating the connector to version 3 depends on your provisioning flow, specifically whether the SAP S/4HANA Cloud Public Edition system is configured as a source or a target system in that flow.



<a name="loio6339b86f23b54f48a02ab269b12733c8__section_m55_12n_dhc"/>

## Update Source System

> ### Note:  
> If you have only an SAP S/4HANA Cloud Public Edition source system, or if it is connected in a flow with a target system such as Identity Authentication version 2 or Local Identity Directory, always start the update from the source system.

Proceed as follows:

1.  Open your SAP S/4HANA Cloud Public Edition source system and verify that it is configured for version 1. The system is on version 1 if the `ibp.api.version` property is either not set or set to `1`.

2.  Select the *Properties* tab and set the following:

    -   *s4hana.cloud.api.version*=`3`

    -   *ips.application.id*=*<The ID of the application that is created under Applications & Resources for the corresponding SAP S/4HANA Cloud Public Edition provisioning system\>*.


3.  Select the *Transformations* tab and replace the read transformation with the default transformation provided for version 3. Use the Identity Provisioning connector documentation as a source of information for the transformation you need.

4.  [Reset the source system](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/reset-identity-provisioning-system?locale=en-US&state=DRAFT&version=Dev). This is necessary because it is assumed that you have already run provisioning jobs to the target systems.

    The reset will clear the operational data. After the reset, running subsequent provisioning jobs will update the existing users and groups instead of creating new ones.

5.  Open the target system that is connected to your source system \(Identity Authentication version 2 or Local Identity Directory\). Select the *Transformations* tab and add the mapping for `externalName` if it is missing:

    ```
    {
       "condition":"$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId'] EMPTY false",
       "sourcePath":"$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']",
       "optional":true,
       "targetPath":"$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']"
    }
    ```

6.  Open the source system and run a provisioning job.

7.  Open the target system, select the *Properties* tab and add the properties for handling conflict resolution for the respective target system and the property for deleting entities.

    -   *ias.group.unique.attribute*=`['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type'],['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName'],['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']`

    -   *idds.group.unique.attribute*=`['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type'],['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName'],['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['applicationId']`

    -   *ips.delete.existedbefore.entities*=`true`

        When you reset a source system, this property must be configured in every connected target system. This ensures that if you later delete entities in the source system, those entities are recognized as previously existing in the target system and are deleted there as well.



**Result**: Following a successful run, it is expected that business roles are provisioned as groups of type `Authorization` for the respective application in SAP Cloud Identity Services, as well as new user groups are successfully created as groups of type `User Group`.



<a name="loio6339b86f23b54f48a02ab269b12733c8__section_yfc_pvt_dhc"/>

## Update Target System

You have an SAP S/4HANA Cloud Public Edition version 1 target system, that is connected with source systems such as Identity Authentication version 2 or Local Identity Directory.

Proceed as follows:

1.  Open your source system, respectively Identity Authentication version 2 or Local Identity Directory and ensure that it has the following mapping for `externalName` attribute.

    ```
    {
       "sourcePath":"$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']",
       "targetPath":"$['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['externalName']",
       "optional":true
    }
    
    ```

    > ### Note:  
    > Groups in Identity Authentication version 2 or Local Identity Directory source systems must have the `externalName` attribute to be provisioned successfully to an SAP S/4HANA Cloud Public Edition version 2 target system.

2.  Open the SAP S/4HANA Cloud Public Edition version 1 target system and set the following on the *Properties* tab:

    -   *s4hana.cloud.api.version*=`3`

    -   *s4hana.cloud.group.unique.attribute*=`externalId,['urn:ietf:params:scim:schemas:extension:sap:2.0:Group']['type']`

    -   *ips.application.id*=*<The ID of the application that is created under Applications & Resources for the corresponding SAP S/4HANA Cloud Public Edition provisioning system\>*

    -   *ips.delete.existedbefore.entities*=`true`

        When you reset the target system \(in step 4\), this property will ensure that if you later delete entities in the source system, those entities are recognized as previously existing in the target system and are deleted there as well.

    -   Remove unnecessary properties that are valid for SAP S/4HANA Cloud Public Edition version 1.


3.  Select the *Transformations* tab and replace the write transformation with the default transformation provided for version 3. Use the Identity Provisioning connector documentation as a source of information for the transformation you need.

4.  [Reset the target system](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/reset-identity-provisioning-system?locale=en-US&state=DRAFT&version=Dev). This is necessary because it is assumed that you have already run provisioning jobs to the target systems.

    The reset will clear the operational data. After the reset, running subsequent provisioning jobs will update the existing users and groups instead of creating new ones.

5.  Open the source system and run a provisioning job.




<a name="loio6339b86f23b54f48a02ab269b12733c8__section_xb5_cwm_2hc"/>

## Update Proxy System

Proceed as follows:

1.  Open your SAP S/4HANA Cloud Public Edition proxy system and verify that it is configured for version 1.

    The system is on version 1 if the `s4hana.cloud.api.version` property is either not set or set to `1`.

2.  Select the *Properties* tab and set the following:

    -   *s4hana.cloud.api.version*=`3`

    -   Remove unnecessary properties that are valid for SAP S/4HANA Cloud Public Edition version 1.


3.  Select the *Transformations* tab and replace the proxy read and proxy write transformations with the default transformations provided for version 3. Use the Identity Provisioning connector documentation as a source of information for the transformation you need.


