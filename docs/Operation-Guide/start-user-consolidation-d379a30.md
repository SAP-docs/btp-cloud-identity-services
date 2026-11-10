<!-- loiod379a30fa2ec4978a321d868a85cd695 -->

# Start User Consolidation

Start user consolidation to create a single profile user in the Identity Directory for each person across SAP applications connected to SAP Cloud Identity Services. User consolidation links application-specific identities that belong to the same person to a single profile user.



## Prerequisites

-   SAP-managed provisioning is enabled for the application. For more information, see [Enable SAP-Managed Provisioning for Application](enable-sap-managed-provisioning-for-application-0e7063f.md).

-   You have identified the attribute used to match users between the application and the Identity Directory.

-   The application is integrated using the SAP-managed scenario for Joule.




## Context

A **consolidatable user** is an application-specific identity represented in the Identity Directory as a **shadow user** until it is linked to a **profile user** through user consolidation.

SAP-managed provisioning creates a separate shadow user in the Identity Directory for each account in a connected SAP application. As a result, a person with accounts in multiple applications can have multiple shadow users. User consolidation identifies shadow users that belong to the same person and links them to a single profile user, which serves as the central identity and is assigned a global user ID. This enables integration scenarios such as Joule to use the same user record consistently across all connected applications.

To identify matching user records, SAP Cloud Identity Services compares an attribute from the Identity Directory with a corresponding attribute from the application. In this procedure, you define the attributes used for matching.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose the *Applications* tile and select the application.

3.  Select the *Provisioning* tab and choose *Start Consolidation*.

    > ### Note:  
    > *Start Consolidation* is active only when SAP-Managed Provisioning is enabled.

4.  Define the attributes used to match user records between the application and the Identity Directory.

    -   In the *Identity Directory Attribute*, select the attribute that identifies the user in the Identity Directory. Available options are *email* and *username*.
    -   In the *<Application\> Attribute*, select the corresponding application attribute. Depending on the application, this field may be predefined and read-only.

    The selected attributes form the matching key. If a shadow user and a profile user have the same value for the mapped attributes, SAP Cloud Identity Services identifies them as belonging to the same person and links the shadow user to the profile user.

5.  Choose *Start*.

    The following message is displayed: `Consolidation is Running...`. This may take a while.

    The consolidation status changes from `Not Started` to `Running`, and then to `Active` after the provisioning jobs complete successfully.




## Results

During the next provisioning run, Identity Provisioning matches shadow users with existing profile users in the Identity Directory and links them under a single profile user. Users that could not be matched may require manual review.



## Next Steps

Once user consolidation is active, you can view the logs.

1.  On the *Provisioning* tab of the selected application, choose *Go to Log*.

2.  Search and view the list of consolidated users.

3.  Search and view the list of non-consolidated users.


