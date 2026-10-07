<!-- loiod87d8adf5da5457490214c1f5bd83e1b -->

# Enable Users to Access Agents

Assign users to agents to grant users the right to invoke them. You can assign individual users or multiple users with user groups.



## Prerequisites

> ### Caution:  
> This page is still work in progress. This page contains information about product features that are part of an SAP Early Adopter Care \(EAC\) program. Products or features that are part of an EAC program are not available to users outside of this program.
> 
> See also [Enable Access to Agents for the SAP Early Adopter Care Program](enable-access-to-agents-for-the-sap-early-adopter-care-program-ae46faa.md).

Before you begin, ensure the following are in place:

-   The agent is deployed and registered in SAP Cloud Identity Services. Agents appear automatically in the *Users & Authorizations* area after deployment. You can't register them manually.

-   The users or user groups you want to assign already exist in SAP Cloud Identity Services. You can't create users or user groups from within this procedure.

    For more information, see [Managing Users](managing-users-228428f.md) or [Managing Groups](managing-groups-ddd067c.md).

-   You're assigned an administrator role with the *Manage Users* or *Manage Groups* authorizations in the SAP Cloud Identity Services administration console.

    For more information, see [Add Administrators](add-administrators-bbbdbdd.md#loiobbbdbdd3899942ce874f3aae9ba9e21d).




## Context

This task configures the first of three authorization layers that govern agent access: whether a user can invoke the agent. The agent gateway enforces this check on each incoming request before the agent runs. For an overview of all three layers and how they interact, see [Managing Agents](managing-agents-a51e764.md).

Assigning a user or user group to an agent does not expand that user's permissions in the connected back-end systems. After invocation, the agent acts strictly within the bounds of the invoking user's authorizations. A user can't use an agent to perform an action that their authorizations wouldn't otherwise allow.

Access assignments are not inherited. If an assistant invokes one or more agents, assigning a user to the assistant does not automatically grant them access to those agents. You must assign the user to the assistant and to each agent it invokes separately. If any assignment is missing, the user receives an authorization error when the assistant attempts to call the agent.

You can assign access to individual users or to user groups. Assigning user groups is the recommended approach for most scenarios. Group-based access remains consistent as your user base changes: adding or removing a user from the user group automatically updates their agent access without any change to the agent's configuration. Assign access to individual users only when access is specific to one person and isn't expected to extend to others.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Agents* tile.

3.  Choose an agent from the list on the left.

    The system displays a list of the agents in the tenant.

4.  Choose the *Access* tab.

5.  Choose the *Users* or *Groups* tab and then choose *Manage Access*.

6.  Add users or user groups to the agent. You have the following options:

    -   Select users or groups from the list.
    -   Search for users or groups.
        -   *Starts With*: \(default\) Returns only entities that start with the entered value.

        -   *Contains*: Returns all entities that contain the entered value. This option may take longer to process.


7.  Choose *Review Changes*.

8.  Save your changes.




## Results

The selected users and members of the selected user groups can now invoke the agent. The change takes effect the next time the user gets a token.



## Granting a Team Access to a Joule Assistant and Its Agents

Donna Moore's organization has deployed a Joule assistant for financial analysts in SAP S/4HANA. The assistant invokes two agents: a report generation agent and a data retrieval agent. She wants to grant the entire finance team access to all three.

Before she starts, she confirms that a user group for the finance team already exists in SAP Cloud Identity Services. For example, `Joule_Finance_Analysts`. If the user group doesn't yet exist, she creates it first.

Because access is not inherited, Donna must perform this procedure once for each entity: the assistant and each of its agents. She performs the following steps three times, selecting a different entity each time.

To assign the user group to the agent:

1.  In the administration console, Donna goes to *Users & Authorizations* and chooses the *Agents* tile.

2.  She selects the financial reporting agent from the list.

3.  She chooses the *Access* tab, then the *Groups* tab, and then chooses *Manage Access*.

4.  She searches for `Joule_Finance_Analysts`, selects it, chooses *Review Changes*, and then saves.


After Donna completes all three assignments, members of `Joule_Finance_Analysts` can invoke the assistant and the agents it calls. If Donna assigns the group to the assistant but omits one of the agents, users will receive an authorization error when the assistant attempts to call that agent.

When a new analyst joins the team, Donna adds them to the user group `Joule_Finance_Analysts` in SAP Cloud Identity Services. Donna doesn't need to modify the access configuration of the assistant or either agent. When an analyst transfers to another department, removing them from the group revokes their access to all three entities at once.

Each analyst can use the assistant and agents only to perform actions that their own SAP S/4HANA authorizations permit. Assigning the group doesn't grant any additional permissions in the back-end system.

**Related Information**  


[Review Agent Authorizations](review-agent-authorizations-cc92fcf.md "After agents are deployed, they arrive in your system with the authorizations the developer created for them. Before you enable access to the agent, review its authorizations and decide whether the agent conforms to your authorization policies.")

[Enable Access to Agents for the SAP Early Adopter Care Program](enable-access-to-agents-for-the-sap-early-adopter-care-program-ae46faa.md "For the SAP Early Adopter Care (EAC) program, the SAP-managed provisioning jobs create application groups for the Joule agents. Assign these groups to users to enable them to use these agents.")

[Identity and Access Management for Joule](../identity-and-access-management-for-joule-050287e.md "Identity and access management architecture required for Joule, including the requirement for a single SAP Cloud Identity Services tenant, SAP-managed provisioning, and global user ID assignment. Understand this foundation before you implement Joule to ensure consistent authentication and authorization across all connected SAP applications.")

[Agents](../agents-12bef24.md "Agent identity represents AI and automation agents in SAP Cloud Identity Services. Agents can authenticate, receive authorization, and be managed like human users while retaining agent-specific capabilities and security controls.")

