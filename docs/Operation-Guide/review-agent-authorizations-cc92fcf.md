<!-- loiocc92fcf10c04430689f7f90198c6640a -->

# Review Agent Authorizations

After agents are deployed, they arrive in your system with the authorizations the developer created for them. Before you enable access to the agent, review its authorizations and decide whether the agent conforms to your authorization policies.



## Context

> ### Caution:  
> This page is still work in progress. This page contains information about product features that are part of an SAP Early Adopter Care \(EAC\) program. Products or features that are part of an EAC program are not available to users outside of this program.

Each agent arrives in your system with a fixed authorization scope, that is, the APIs it is permitted to call at the agent gateway, and whether the permission for each is read or write. This scope is defined by the agent's developer and is read-only for administrators. You can't modify it in SAP Cloud Identity Services. Your role is to evaluate whether the scope is acceptable before you assign any users to the agent. Even if the scope appears broad, actions are also constrained at runtime by the invoking user's own permissions in the target application. That constraint isn't visible here and should not be relied on as a substitute for a careful scope review.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Users & Authorizations*, choose the *Agents* tile.

    The system displays a list of the agents in the tenant.

3.  Choose an agent from the list on the left to view its details.

4.  Choose the *Authorizations* tab.

5.  Review the authorizations of the agent.

    The *Authorizations* tab shows the agent's scoped access as a list of policies, grouped by target application. Each row names an API by its technical identifier and shows whether the permission is Read or Write. Because the API names are technical identifiers, you may need to look up what each API does before you can evaluate the scope meaningfully. Use the following questions to guide your evaluation.

    **Review Guidance**


    <table>
    <tr>
    <th valign="top">

    Question
    
    </th>
    <th valign="top">

    Guidance
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Does the scope match the agent's purpose?
    
    </td>
    <td valign="top">
    
    An agent designed for read-only reporting should not require write access. A scope broader than the agent's stated function warrants further investigation before you proceed.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Does the scope include write access?
    
    </td>
    <td valign="top">
    
    Write access can create or modify data in the target system. Confirm that these operations are necessary for the agent's function and that the risk is acceptable in your environment.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Do the APIs cover sensitive data or critical processes?
    
    </td>
    <td valign="top">
    
    Even read-only access to APIs that expose personal data, financial records, or privileged configuration may require additional justification before you grant access.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Is the API surface proportionate?
    
    </td>
    <td valign="top">
    
    A scope covering many unrelated APIs may indicate the agent was provisioned with more access than it needs. Apply the principle of least privilege when assessing whether to proceed.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Does the scope cover multiple target systems?
    
    </td>
    <td valign="top">
    
    The authorization list may include entries from more than one target application. Review each application group independently. Write access in one application doesn't justify write access in another.
    
    </td>
    </tr>
    </table>
    



## Next Steps

Use the authorization information to determine which users should have access to this agent. The agent can only call the APIs defined in its authorization scope, and the user's own authorizations in the target application further limit what the agent can do on their behalf. The Agent Gateway also monitors agents and their requests. If the agent's authorization scope is broader than you want to allow in your environment, consider these options:

-   Don't assign any users to the agent. As long as no user is assigned, no one can invoke the agent, regardless of how the landscape is configured. This gives you as the IAM administrator full control.

-   For line-of-business agents, consider reducing the authorizations assigned to the users in the target system. Discuss the situation with the landscape administrator in your organization. The landscape administrator enables the agent for your tenant in SAP for Me. They can determine to which systems the agent has access.

-   For custom agents, discuss the situation with the developer of the agent within your organization. Then assign users to the agent only after reviewing and accepting its authorization scope.


If this agent is invoked by an assistant, repeat this review for the assistant and every other agent in the chain before assigning any users. Access assignments are not inherited across the chain. For more information about how the chain works and how to plan assignments, see [Managing Agents](managing-agents-a51e764.md).

**Related Information**  


[Enable Users to Access Agents](enable-users-to-access-agents-d87d8ad.md "Assign users to agents to grant users the right to invoke them. You can assign individual users or multiple users with user groups.")

[Enable Access to Agents for the SAP Early Adopter Care Program](enable-access-to-agents-for-the-sap-early-adopter-care-program-ae46faa.md "For the SAP Early Adopter Care (EAC) program, the SAP-managed provisioning jobs create application groups for the Joule agents. Assign these groups to users to enable them to use these agents.")

[Identity and Access Management for Joule](../identity-and-access-management-for-joule-050287e.md "Identity and access management architecture required for Joule, including the requirement for a single SAP Cloud Identity Services tenant, SAP-managed provisioning, and global user ID assignment. Understand this foundation before you implement Joule to ensure consistent authentication and authorization across all connected SAP applications.")

[Agents](../agents-12bef24.md "Agent identity represents AI and automation agents in SAP Cloud Identity Services. Agents can authenticate, receive authorization, and be managed like human users while retaining agent-specific capabilities and security controls.")

