<!-- loio9ea0024383de4726b6a4aae471eb1039 -->

# Integrating Applications

Enable applications to call each other's APIs, consume reuse services, share authorization context, or hand off authenticated sessions by configuring dependencies in SAP Cloud Identity Services.

SAP Cloud Identity Services supports four types of dependencies. Each type serves a distinct integration scenario as determined by the developer of the application:


<table>
<tr>
<th valign="top">

Dependency Type

</th>
<th valign="top">

Use When

</th>
</tr>
<tr>
<td valign="top">

[Provided APIs](provided-apis-0251c56.md)

</td>
<td valign="top">

One application calls the APIs of another application. The consumer uses technical communication or principal propagation.

</td>
</tr>
<tr>
<td valign="top">

[Configure Service Dependencies](configure-service-dependencies-e6e39c1.md)

</td>
<td valign="top">

An application consumes a reuse service, such as the Destination service or Job Scheduling service, using its own token.

</td>
</tr>
<tr>
<td valign="top">

[Configure Shared Authorization Dependencies](configure-shared-authorization-dependencies-e3efade.md)

</td>
<td valign="top">

A consumer application, such as a portal or shell, needs to know what a user is authorized to do in a provider application without calling that application directly. The provider's authorization groups are projected as claims into the consumer's token.

</td>
</tr>
<tr>
<td valign="top">

[Configure Native-Web Trust Dependencies](configure-native-web-trust-dependencies-d7ab53a.md)

</td>
<td valign="top">

A native or mobile application hands off an authenticated session to a web application without requiring the user to log in again.

</td>
</tr>
</table>

