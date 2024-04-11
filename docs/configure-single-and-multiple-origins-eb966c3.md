<!-- loioeb966c3527f54ac8846d8a2dea9f8299 -->

# Configure Single and Multiple Origins

Configure and provision users with single or multiple origins in SAP BTP XS Advanced UAA \(Cloud Foundry\) source system.



<a name="loioeb966c3527f54ac8846d8a2dea9f8299__section_bvw_wlx_wxb"/>

## Overview

An origin tells you which is the identity provider of a user in SAP BTP XS Advanced UAA \(Cloud Foundry\). It is defined in the trust configuration in the SAP BTP cockpit under *Security* \> *Trust Configuration* \> *Origin Key*.

The origin itself is not a concept of Identity Provisioning. The role of the service is to ensure that you can read and provision users with their identity providers. Once you find the identity provider in the Origin Key, you need to set it in the `xsuaa.origin` property. You can configure it in source, target and proxy SAP BTP XS Advanced UAA \(Cloud Foundry\) systems. Both single and multiple values are supported. The value is a string that usually specifies the name of the identity provider or its location.

For example: `xsuaa.origin=`*ldap* and `xsuaa.origin=`*ldap;myaccount-xsuaa.accounts.ondemand.com*, where the ";" \(semicolon\) is the only supported delimiter.



### Provisioning Users with Single Origin

You want to provision a user with a single origin from SAP BTP XS Advanced UAA \(Cloud Foundry\) source system to a given target system.

1.  On the *Properties* tab of the source system, set the `xsuaa.origin.filter.enabled` property to *true*.

    This is a prerequisite for enabling the `xsuaa.origin` property in source systems.

2.  Enter the value for the `xsuaa.origin` property, for example: *idp1*.

    The value of this property acts like a filter as only users with the values specified there are read.

3.  Run a provisioning job.


As a result, one user entry with single origin is read and created in the target system.



### Provisioning Users with Multiple Origins

You want to provision a user with multiple origins from SAP BTP XS Advanced UAA \(Cloud Foundry\) source system to a given target system.

1.  On the *Properties* tab of the source system, set the `xsuaa.origin.filter.enabled` property to *true*.

    This is a prerequisite for enabling the `xsuaa.origin` property in source systems.

2.  Enter multiple values for the `xsuaa.origin` property, for example: *idp1;idp2*.

    The value of this property acts like a filter as only users with the values specified there are read.

3.  Set the `ips.delete.existedbefore.entities` property to *true* on the target system.

    This is needed before you run the provisioning job. It will ensure that previously existed users in the target system will be deleted if they were deleted in the source. For more information, see [Manage Deleted Entities](Operation-Guide/manage-deleted-entities-3d6bdf1.md) 

4.  Run a provisioning job.


As a result, two user entries for one and the same user are read. Only one user is created in the target system, because it does not support the origin concept and recognizes both user entries as one user. The job logs show that two users are read, one is created, and one is updated on the target system. A deletion of one of the origins in the source system would result in the following statistics: one user is read and one user is updated.



### 

> ### Note:  
> Multiple origins are not supported in provisioning scenarios between SAP BTP XS Advanced UAA \(Cloud Foundry\) source system and SAP BTP XS Advanced UAA \(Cloud Foundry\) target system.

