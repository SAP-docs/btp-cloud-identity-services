<!-- loio5ccec0b19422406fac24b9323294b980 -->

# Erasure

When handling personal data, consider the legislation in the different countries where your organization operates. After the data has passed the end of purpose, regulations may require you to delete the data. However, additional regulations may require you to keep the data longer. During this period, you must block access to the data by unauthorized persons until the end of the retention period, when the data is finally deleted.

Only the service provider is aware of the retention policies of the user, and thus whether a user record has to be blocked first, and deleted at a certain time in the future, or whether a user record can be deleted immediately.

The end user who wants to cancel his or her registration from the service should start the process via the service provider, not via Identity Authentication. Identity Authentication keeps user information for every service provider. Each service provider deletes its specific data stored about the user in Identity Authentication via an API call. If the user has accounts in more than one service provider, his or her whole user profile in Identity Authentication is deleted when the information for the last service provider is deleted. For more information, see [SP User Deletion](../Development/sp-user-deletion-dba2028.md).

Apart from deleting, users can be blocked. When users are blocked, they exist in Identity Authentication, but cannot be authenticated when they try to log on. For more information, see [SP User Deactivation](../Development/sp-user-deactivation-de64bd8.md).

Tenant administrators can delete and block users via the administration console for Identity Authentication. For more information, see [Delete Users](../Operation-Guide/delete-users-bbfaf5f.md) and [Deactivate Users](../Operation-Guide/deactivate-users-99cf468.md).

Tenant administrators can also configure blocking and deletion for specific user types and after certain period of time, For more information, see [Block or Delete Users Due to Inactivity](../Operation-Guide/block-or-delete-users-due-to-inactivity-744b2d0.md).

