<!-- loio4c39dd09859843d991118ff7a494c115 -->

# Internal Policies

Developers can create authorization policies for internal purposes. The policies aren't deployed and don't appear in the administration console.

You can use internal authorization policies and map them to a technical client, for example for app-to-app communication. In this case, the policies are set at runtime and are passed to the decision engine in the client libraries. For more information, see [SAP Cloud Identity Services Developer Guide](https://sap.github.io/cloud-identity-developer-guide/).

You can create internal policies by using the keyword `INTERNAL`.

**Effect of Using the INTERNAL Keyword**


<table>
<tr>
<th valign="top">

Element

</th>
<th valign="top">

Description

</th>
<th valign="top">

Effect

</th>
</tr>
<tr>
<td valign="top">

Base policy

</td>
<td valign="top">

A `USE` of such a policy isn't allowed.

</td>
<td valign="top">

Compile error

</td>
</tr>
<tr>
<td valign="top">

Tenant-specific policy

</td>
<td valign="top">

Annotation isn't allowed at tenant level.

</td>
<td valign="top">

Compile error

</td>
</tr>
</table>

In a downstream tool like Authorization Management, an `INTERNAL` element doesn't show in the user interface. This prevents reuse \(not allowed as described above\) and policy assignment.

You can't combine an `INTERNAL POLICY` with `DEFAULT`. It should be explicitly set with the DCL runtime client API. You can also mark it with `INTERNAL`.

