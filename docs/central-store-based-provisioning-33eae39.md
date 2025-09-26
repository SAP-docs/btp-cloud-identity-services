<!-- loio33eae39ab1084bd3913df13b1eb43baa -->

# Central Store-Based Provisioning

Central store-based provisioning enables the automatic provisioning of application-specific groups from the Identity Directory to the target systems whenever changes occur. These changes include user assignments or modifications of group attributes.



<a name="loio33eae39ab1084bd3913df13b1eb43baa__section_cqn_xyw_m2c"/>

## Prerequisites

To ensure the groups immediate provisioning to the target systems, the following application configurations are required:

-   An application must be created for the relevant target system under *Applications & Resources* \> *Applications*. See [Create a New Application](Operation-Guide/create-a-new-application-0d4b255.md).

-   The application ID must be set as the value for the `ips.application.id` property in the target system.

    See [List of Properties](list-of-properties-d6f3577.md).

-   The *Central Store-Based Provisioning* option must be enabled under *Applications & Resources* \> *Applications* \> *Provisioning*. See [Enable or Disable Central Store-Based Provisioning](Operation-Guide/enable-or-disable-central-store-based-provisioning-657bbaa.md).




<a name="loio33eae39ab1084bd3913df13b1eb43baa__section_w3k_2zw_m2c"/>

## Context

You can initially create application-specific groups in the Identity Directory by running a provisioning job from a given source system or by using the SAP Cloud Identity Services administration console. For more information, see [Groups](groups-d93be69.md).

When provisioning these groups from the Identity Directory to target systems, groups that do not exist in the target can only be created after they are modified in the source system. New groups in the Identity Directory will not be provisioned unless they have been changed. Additionally, creating and updating application-specific groups through user assignments require that users already exist in the target system. Central store-based provisioning does not create users in the target.

> ### Note:  
> Application-specific groups with supported operations `readOnly`, `userOnlyMembership` and `membership` will not be created even if updates are made to the groups. If you try to provision such groups, you will get an ***Entity Failed*** status. For more information, see [Monitor Central Store Logs](Monitoring-and-Reporting/monitor-central-store-logs-9162898.md).



<a name="loio33eae39ab1084bd3913df13b1eb43baa__section_rvk_3zw_m2c"/>

## Procedure

Here is the necessary configuration to enable central store-based provisioning. The following example uses the Local Identity Directory as the source system and SAP Advanced Financial Closing as the target system.

1.  Sign in to SAP Cloud Identity Services administration console and navigate to *Identity Provisioning*.

2.  Add [Local Identity Directory](local-identity-directory-8c7d05e.md) as a source system.

3.  **Optional**: Configure properties that are relevant for the Local Identity Directory source system, for example `idds.user.filter` and `idds.group.filter`. For more information, see [List of Properties](list-of-properties-d6f3577.md).

4.  **Optional**: Review and adapt the default read transformations as necessary.

5.  Add a target system of your choice, for example *SAP Advanced Financial Closing*.

6.  Select the *Local Identity Directory* as relevant source system.
7.  Set the property `ips.application.id` for the target system. For more information, see [List of Properties](list-of-properties-d6f3577.md).
8.  Start a read job from the *Local Identity Directory* source system.

9.  Navigate to your application in the administration console for SAP Cloud Identity Services under *Applications & Resources* \> *Applications* and enable the *Central Store-Based Provisioning*. For more information, see [Enable or Disable Central Store-Based Provisioning](Operation-Guide/enable-or-disable-central-store-based-provisioning-657bbaa.md).



<a name="loio33eae39ab1084bd3913df13b1eb43baa__section_odz_j1x_m2c"/>

## Result

Once the procedure is executed, any change to an attribute value or a member of an application-specific group in the Local Identity Directory will trigger instant provisioning of the modified entity to the configured target system.

**Related Information**  


[Business-to-Consumer Scenario](business-to-consumer-scenario-fd11ee2.md "The business-to-consumer scenario is related to any actions performed by the consumer, such as registration to applications and consumer retailing. In this scenario, administrators facilitate the consumer processes, but they do not act on the consumer's behalf.")

[Business-to-Business Scenario](business-to-business-scenario-3908c37.md "The business-to-business scenario is related to services for business partners. Unlike the business-to-consumer scenario, consumer self-registration is not allowed, and the administrator of the company is usually the one that triggers the user registration process.")

[Business-to-Employee Scenario](business-to-employee-scenario-3aecb4c.md "The business-to-employee scenario is related to services for employees of an organization. Employees can access various applications with one logon. Furthermore, administrators can upload employees data by using the user import functionality.")

[Centralized Provisioning with Identity Directory](centralized-provisioning-with-identity-directory-9d0235c.md "Identity Directory is the persistency layer of SAP Cloud Identity Services, providing a central place for storing and managing users and groups. You can use it in centralized provisioning scenarios for managing user access to SAP cloud applications from a single, central location.")

[**Blog Post**: Taking Groups to the Next Level with Application-Specific Groups](https://community.sap.com/t5/technology-blogs-by-sap/taking-groups-to-the-next-level-with-application-specific-groups/ba-p/13956003)

