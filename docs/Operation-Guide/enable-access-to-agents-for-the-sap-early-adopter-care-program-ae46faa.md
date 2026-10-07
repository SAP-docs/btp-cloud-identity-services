<!-- loioae46faaaeb6b46579fc035f42d892bd8 -->

# Enable Access to Agents for the SAP Early Adopter Care Program

For the SAP Early Adopter Care \(EAC\) program, the SAP-managed provisioning jobs create application groups for the Joule agents. Assign these groups to users to enable them to use these agents.



## Prerequisites

> ### Caution:  
> This page is still a work in progress. This page contains information about product features that are part of an SAP Early Adopter Care \(EAC\) program. Products or features that are part of an EAC program aren't available to users outside of this program.

Before you begin, ensure the following are in place:

-   SAP-managed provisioning jobs have completed successfully and agent authorization groups are available in SAP Cloud Identity Services.

    See also [Set Up Identity and Access Management](https://help.sap.com/docs/cloud-identity-services/setup-identity-and-access-management/setup-identity-and-access-management).

-   The users you want to assign already exist in SAP Cloud Identity Services.
-   You are assigned an administrator role with the *Manage Users* or *Manage Groups* authorizations in the SAP Cloud Identity Services administration console.



## Context

After SAP-managed provisioning jobs create authorization groups for Joule agents in SAP Cloud Identity Services, you must assign users to these groups to grant them access to specific agents. This task is part of Stage 2 deployment, where users with real identities in SAP Cloud Identity Services can be authorized to use agents alongside the conversational Joule assistant.

Each agent has its own authorization group. Users must be members of an agent's group to see and interact with that agent. Without group membership, users can still access conversational Joule functions but can't use agents.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Groups* tile.

3.  Choose a group from the list on the left.

    Agent authorization groups are created by SAP-managed provisioning jobs. You can sort the list by group type to find the correct authorization group.

4.  Choose *\+ Add*.

5.  Add users to the group.

6.  Save your changes.




## Results

Users assigned to the agent authorization group can now access and interact with the agent. The changes take effect immediately. Users may need to refresh their browser session to see newly available agents.



## Next Steps

If users can't access the agent after being assigned to its authorization group:

-   Verify that the user has a real identity in SAP Cloud Identity Services with a global user ID assigned.
-   Confirm that the user has logged in at least once to the connected line-of-business application using SAP Cloud Identity Services as the identity provider.
-   Ask the user to sign out and sign back in to refresh their session.

**Related Information**  


[Review Agent Authorizations](review-agent-authorizations-cc92fcf.md "After agents are deployed, they arrive in your system with the authorizations the developer created for them. Before you enable access to the agent, review its authorizations and decide whether the agent conforms to your authorization policies.")

[Enable Users to Access Agents](enable-users-to-access-agents-d87d8ad.md "Assign users to agents to grant users the right to invoke them. You can assign individual users or multiple users with user groups.")

[Enable Users to Access Agents](enable-users-to-access-agents-d87d8ad.md "Assign users to agents to grant users the right to invoke them. You can assign individual users or multiple users with user groups.")

[Identity and Access Management for Joule](../identity-and-access-management-for-joule-050287e.md "Identity and access management architecture required for Joule, including the requirement for a single SAP Cloud Identity Services tenant, SAP-managed provisioning, and global user ID assignment. Understand this foundation before you implement Joule to ensure consistent authentication and authorization across all connected SAP applications.")

