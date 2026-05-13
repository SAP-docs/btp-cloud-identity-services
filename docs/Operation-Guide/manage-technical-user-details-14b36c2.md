<!-- loio14b36c2c35a74e74b8dd104fdffc78e7 -->

# Manage Technical User Details

As a user with assigned special policy authorizations, you can manage the technical user details and in the administration console for SAP Cloud Identity Services.



## Prerequisites

-   The authorizations based on policies option in the admin console for SAP Cloud Identity Services is enabled. See [Configure Authorizations Based on Policies](configure-authorizations-based-on-policies-08fea39.md).
-   You are assigned with the respective technical user authorizations, depending on the tasks you need to perform. For more information, see [Configure Technical User Authorizations](configure-technical-user-authorizations-885320d.md).
-   There is an existing technical user in the tenant of SAP Cloud Identity Services.



## Context

You can view or edit the technical user details, configure authentication, or delete the technical user.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Choose *Users & Authorizations* \> *Technical User*.

3.  Select the technical user from the list on the left whose details you want to edit.

4.  **Optional:** Under *Details tab* \> *General Information* \> *Edit* \> *choose , change or add new information in the fields* \> *Save*.

5.  **Optional:** Under *Details tab* \> *Client ID*, view and manage the *Client ID* information and status. The *Client ID Lock* option is disabled by default. When enabled, the client ID locks after 5 failed logon attempts using secrets. We recommend you to enable this feature in cases when the client ID secrets are automatically generated.

6.  **Optional:** Under *Details tab* \> *Configure Authentication*, manage the *Certificates* or *Secrets* that are used for authenticating the client and for API authentication.

7.  **Optional:** Under the *Groups tab* \> *Assign* \> *assign a group from the list* \> *Assign*.


**Related Information**  


[Create a Technical User](create-a-technical-user-2c4bcb9.md "As a user with assigned special policy authorizations, you can create a technical user in the administration console for SAP Cloud Identity Services.")

