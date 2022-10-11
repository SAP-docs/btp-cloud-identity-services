<!-- loio697fd2b4d13f45d5a13e0e6992c28456 -->

# Delete Custom Password Policy

As a tenant administrator, you can delete the custom password policy that you have created in the administration console for Identity Authentication.



## Prerequisites

-   You have created a custom password policy in the administration console for Identity Authentication. For more information, see [Configure Custom Password Policy](configure-custom-password-policy-67bece2.md).

-   The custom password policy should not be set as a password policy for any of the applications in the tenant. For more information about how to set a standard or enterprise policy for an application, see [Set a Password Policy for an Application](set-a-password-policy-for-an-application-04a6e45.md).




## Context

You can only have one custom password policy for your tenant. To change the configuration of the custom password policy, or to create a new one, delete the existing custom policy first.

To delete the custom password policy, proceed as follows:



## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Choose the *Password Policies* tile.

3.  Press the ![](images/DeletePassPolicy_6d0c4a3.png) next to the custom password policy.

    > ### Caution:  
    > You can only delete the password policy if it is not set as a password policy for any applications in the tenant.




## Results

Once the password policy has been deleted, the system displays the message ***Password policy <name of policy\> deleted***.

**Related Information**  


[Set a Password Policy for an Application](set-a-password-policy-for-an-application-04a6e45.md "As a tenant administrator, you can set a password policy that matches your application logon requirements.")

[Configure Custom Password Policy](configure-custom-password-policy-67bece2.md "Tenant administrators can create and configure a custom password policy for scenarios where Identity Authentication is the authenticating authority.")

[Configure Password Exclude List](configure-password-exclude-list-159c09d.md "As a tenant administrator, you can create a password exclude list to restrict their usage.")

