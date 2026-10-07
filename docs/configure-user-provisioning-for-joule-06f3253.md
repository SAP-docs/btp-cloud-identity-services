<!-- loio06f32538db5f4c6ba2e7175262b7065c -->

# Configure User Provisioning for Joule

Use SAP Cloud Identity Services to establish a centralized user identity across SAP applications for Joule integration scenarios.



## Overview

Joule is an AI solution embedded into the flow of work across SAP and non-SAP systems. It requires a consistent user identity across connected SAP applications to correctly associate requests from different applications with the same user. To support this, users, application groups, roles, and their assignments must be synchronized and stored centrally in the Identity Directory of SAP Cloud Identity Services.

To establish the centralized user identity, you must configure two-way provisioning between the Identity Directory and each SAP application that participates in Joule scenarios. Each system must be configured with the required connectivity and authentication settings.

The setup for each SAP solution integrated with Joule follows a three-step phase.

1.  Provisioning from the SAP application to the Identity Directory

    The SAP solution is configured as the source system and the *Local Identity Directory*, which represents the Identity Directory, as the target system. Users, application groups, roles, and their assignments are replicated to the Identity Directory. During this process, users who are members of replicated groups and do not already have a Global User ID are assigned one. The Global User ID is used by Joule to correlate user identities across different SAP applications.

2.  Storing users and groups in the Identity Directory

    After provisioning, users are stored centrally in the Identity Directory. During this step, you verify that users have been correctly stored and resolve any conflicts in the groups they are members of. Resolving group conflicts ensures that users are correctly associated with their application groups before their updated identities are provisioned back to the connected SAP applications.

3.  Provisioning from the Identity Directory to the SAP application

    The Local Identity Directory is configured as the source system and the same SAP application as the target system. The assigned Global User IDs are provisioned back to the SAP application, updating the corresponding local users. This ensures that users are consistently identified across all connected applications.


> ### Note:  
> During user replication, only a minimal user representation is provisioned to and from the Identity Directory, indicating the source application from which the user originates. The primary purpose of this replication is to provide users with a consistent identity across connected SAP applications by assigning a Global User ID.



## Phase 1: Provision Users and Groups from the SAP Application to the Identity Directory

**Prerequisite**:

The administrator user has the *Manage Identity Provisioning* role assigned. For more information, see [Add Administrators](Operation-Guide/add-administrators-bbbdbdd.md#loiobbbdbdd3899942ce874f3aae9ba9e21d).

In this phase, each SAP application acts as the source system, and the Local Identity Directory acts as the target. Users and groups are replicated to the Identity Directory, and a Global User ID is assigned to each user.

1.  Sign in to the SAP Cloud Identity Services administration console and navigate to Identity Provisioning.

    For more information, see [Access Admin Console](access-admin-console-2609e81.md).

2.  Select *Source Systems*, choose *Add*, and configure the SAP application as a source system.

    For more information, see [Source Systems](source-systems-58033be.md).

3.  Configure the required connectivity and authentication properties.

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

4.  Select *Target Systems*, choose *Add*, and configure the *Local Identity Directory* as a target system.

    For more information, see [Local Identity Directory](local-identity-directory-59557ae.md).

5.  Run the provisioning job from the source system.

    For more information, see [Start and Stop Provisioning Jobs](Operation-Guide/start-and-stop-provisioning-jobs-531a261.md).




## Phase 2: Store Users and Groups in the Identity Directory

After the provisioning job in Phase 1 completes, verify that users are stored in the Identity Directory and resolve any group conflicts.

1.  Navigate to *Users & Authorizations* \> *User Management* and verify that users from the SAP application are stored in the Identity Directory.

2.  Navigate to *Applications & Resources* and select the application.

3.  On the *Provisioning* tab, verify that the *SAP-Managed Provisioning* option is enabled.

    > ### Note:  
    > If the *SAP-Managed Provisioning* option is disabled, this indicates unresolved group conflicts. A wizard will display the application-specific groups in the Identity Directory and their corresponding groups in the business application.

4.  Map the matching groups.


> ### Note:  
> Group conflicts must be resolved before updated user identities can be provisioned back to the connected SAP applications in Phase 3.



## Phase 3: Provision Updated Identities from the Identity Directory to the SAP Application

1.  Navigate to *Identity Provisioning*.

2.  Select *Source Systems*, choose *Add*, and configure the *Local Identity Directory* as a source system.

    For more information, see [Local Identity Directory](local-identity-directory-8c7d05e.md).

3.  Select *Target Systems*, choose *Add*, and configure the SAP application as a target system.

4.  Configure the required connectivity and authentication properties.

    For more information, see [List of Properties](list-of-properties-d6f3577.md).

5.  Run the provisioning job from the source system.

    For more information, see [Start and Stop Provisioning Jobs](Operation-Guide/start-and-stop-provisioning-jobs-531a261.md).

6.  Monitor provisioning jobs and verify that they complete successfully. If you encounter issues, warnings, or other unexpected results, contact your administrator.

    For more information, see [Manage Provisioning Job Logs](Monitoring-and-Reporting/manage-provisioning-job-logs-041b5ff.md).




## Results

The SAP application is integrated with the Identity Directory through two-way identity provisioning. The following is now in place:

-   Users and groups from the connected SAP application are stored centrally in the Identity Directory.

-   Users have a consistent identity across connected SAP applications through the Global User ID, enabling Joule to correctly correlate user requests across applications.


