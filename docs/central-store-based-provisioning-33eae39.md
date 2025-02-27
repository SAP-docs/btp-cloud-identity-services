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

The application-specific groups can be created initially in the Identity Directory by running a provisioning job from a specified source system or by using the SAP Cloud Identity Services administration console. For more information, see [Groups](groups-d93be69.md). When provisioning application-specific groups from the Identity Directory to the target systems, groups that do not exist in the target can be created only after they are modified in the source system. New groups in the Identity Directory will not be provisioned unless they are changed.

> ### Note:  
> Application-specific groups with supported operations `readOnly`, `userOnlyMembership` and `membership` will not be created even if updates are made to the groups. If you try to provision such groups, you will get an ***Entity Failed*** status. For more information, see [Monitor Central Store Logs](Monitoring-and-Reporting/monitor-central-store-logs-9162898.md).



<a name="loio33eae39ab1084bd3913df13b1eb43baa__section_rvk_3zw_m2c"/>

## Procedure

Here is the necessary configuration to enable central store-based provisioning. The following example uses the Local Identity Directory as the source system and SAP Advanced Financial Closing as the target system.

1.  Sign in to SAP Cloud Identity Services administration console and navigate to *Identity Provisioning*.

2.  Add [Local Identity Directory](local-identity-directory-59557ae.md) as a source system.

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

