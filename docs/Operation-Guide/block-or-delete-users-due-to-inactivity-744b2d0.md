<!-- loio744b2d0b557041dab64f8fe824304a68 -->

# Block or Delete Users Due to Inactivity

Tenant administrator can configure specific user types to be blocked and deleted, or only blocked, or only deleted after a certain period of inactivity.



<a name="loio744b2d0b557041dab64f8fe824304a68__context_aqn_1kl_q4b"/>

## Context

The users for which blocking can be enabled are of the type:

-   *Public*
-   *Customers*
-   *Partners*
-   *Employees*

You can enable the chosen user type or types to be only blocked, or only deleted, or both blocked and deleted after a certain period of inactivity. The period spans from 14 up to 2000 days.

To enable blocking and or deletion, you must choose at least one user type and set at least one period.

After a user has exceeded the set period of inactivity, they will be blocked and their status will be updated on the next sign-in attempt.

You can also configure when the deletion script starts.

> ### Note:  
> If you configure both *Block after* and *Delete after* periods, the *Delete after* period must be longer than the *Block after* period.



<a name="loio744b2d0b557041dab64f8fe824304a68__steps_xph_x4w_q4b"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page, you can view the administrative and license relevant information of the tenant.

3.  Choose the *Blocking and Deletion* list item.

4.  Choose *Edit*.

5.  Select a user type.

6.  Enable the options under *Inactivity Periods*. By default the options are disabled. At least one of the status fields *Block after* or *Delete after* must be enabled.


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Blocking status**
    
    </td>
    <td valign="top">
    
    When enabled, configure the *Block after* period. The *Block after* period can be between 14 and 2000 days.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Deletion status**
    
    </td>
    <td valign="top">
    
    When enabled, configure the *Delete after* period. The *Delete after* period can be between 14 and 2000 days.

    > ### Remember:  
    > If you configure both *Block after* and *Delete after* periods, the *Delete after* period must be longer than the *Block after* period.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Deletion script start date**
    
    </td>
    <td valign="top">
    
    This status is optional and it appears only after the *Deletion status* is enabled. Configure the date after which the deletion script starts. The automatic configuration is based on the current date plus the days specified in the *Delete after* period. The deletion process starts from the chosen date and is runs nightly at 04:00 UTC.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Creation grace period status**
    
    </td>
    <td valign="top">
    
    This status is optional and it can be configured only after the *Deletion status* is enabled. When enabled, configure when users who have been created but never logged in will be deleted. The grace period can be between 2 and 30 days.

    > ### Remember:  
    > If the status is disabled, users that are created before the start of the deletion script, but have never logged in, they will be deleted even if the period of their inactivity is less than the delete after period that is configured in the administration console.


    
    </td>
    </tr>
    </table>
    
7.  Save your changes.




<a name="loio744b2d0b557041dab64f8fe824304a68__postreq_pxc_s12_r4b"/>

## Next Steps

To unblock users, follow the procedure in [Unblock a User](unblock-a-user-d50eec9.md)

