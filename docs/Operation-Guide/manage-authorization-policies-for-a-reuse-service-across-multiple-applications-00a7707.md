<!-- loio00a77072c10c454dbd222f33e800607e -->

# Manage Authorization Policies for a Reuse Service Across Multiple Applications

The authorization data for a reuse service is shared among multiple business applications in the same tenant, ensuring consistent authorization policies across different applications for users logged on to these applications.



## Context

A reuse service is consumed by multiple business applications, for example application 1 and application 2. The authorization data is not separated among the applications, though. The applications, which are in the same SAP Cloud Identity Services tenant, share the authorization policies and assignments of the reuse service. Thus you make sure that the authorization policies of the reuse service are consistent across different applications.

When an administrator assigns a user to an authorization policy of the reuse service, the reuse grants this permission regardless of the authorization context of the business application. That means, if the user logs on to application 1 or application 2, the permissions for the reuse service are the same, meaning the authorization policies of the reuse service.

The same is reflected on the administration side. Users assigned to authorization policies of the reuse service can always consume the same content. It doesn't matter whether they have logged on to application 1 or application 2.

If you assign the authorization policies of the reuse service to users of application 1 or 2, you enable these users to access the reuse service. They can simply log on to application 1 or 2 and immediately use the reuse service.

To assign authorization policies of the reuse service to users, take the following steps.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications & Resources*, choose the *Applications* tile.

3.  Choose the application that supports authorization management and authorization policies for the reuse service.

4.  Choose the *Authorization Policies* tab. You see the list of the authorization policies of your application. Next to the table title, there's a dropdown list where you can select the reuse service. Currently, it displays the name you your application.

5.  Open the drowdown list.

6.  Select the reuse service. The table displays the list of the policies that belong to the reuse service.

    > ### Note:  
    > If your application doesn't have policies, the administration console displays the policies of the reuse service.

7.  Choose an authorization policy you want to assign. The *Assignments* pane opens.

8.  Choose *Add*.

9.  Select the users that you want to add to the authorization policy and choose *Add*.

    You have added the selected users to an authorization policy. These users are now authorized to access and use the reuse service with the rules and restrictions defined in the authorization policy.


