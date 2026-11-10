<!-- loioa282b220e1f34661954da0687bc73900 -->

# Configure Provisioning for Applications

Use the *Provisioning* tab to configure group prefixes, activate provisioning types, such as Central Store-Based Provisioning and SAP-Managed Provisioning, and monitor user consolidation for an application.

You can configure the following:


<table>
<tr>
<th valign="top">

Setting

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*Group Prefix* 

</td>
<td valign="top">

Distinguishes groups belonging to a backend system by specific prefix.

The Group Prefix setting under *Application* \> *Provisioning* is primarily intended for customers using the SAP-managed delivery approach, in which SAP automatically preconfigures and maintains the provisioning configuration. As a result, this configuration is not displayed in the UI. However, the setting can also be used by customers following a customer-managed delivery approach.

It allows you to define a group prefix, similar to specifying a value for the `<system>.group.prefix` property on the *Properties* tab of a provisioning system.

</td>
</tr>
<tr>
<td valign="top">

*Provisioning Type* 

</td>
<td valign="top">

Enables the two provisioning types:

-   *Central Store-Based Provisioning*

-   *SAP-Managed Provisioning*




</td>
</tr>
<tr>
<td valign="top">

*User Consolidation* 

</td>
<td valign="top">

Monitors consolidation. Available only after SAP-Managed Provisioning is enabled.

</td>
</tr>
</table>

**Related Information**  


[Enable SAP-Managed Provisioning for Application](enable-sap-managed-provisioning-for-application-0e7063f.md "Enable SAP-managed provisioning for a connected application to support integration scenarios with Joule, SAP Ariba Nexus, and other SAP-managed solutions. If group conflicts exist, resolve them as part of the activation process.")

[Start User Consolidation](start-user-consolidation-d379a30.md "Start user consolidation to create a single profile user in the Identity Directory for each person across SAP applications connected to SAP Cloud Identity Services. User consolidation links application-specific identities that belong to the same person to a single profile user.")

