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

You can also configure when the deletion script starts.

> ### Note:  
> If you configure both *Block after* and *Delete after* periods, the *Delete after* period must be longer than the *Block after* period.



<a name="loio744b2d0b557041dab64f8fe824304a68__steps_xph_x4w_q4b"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Tenant Settings* tile.

    At the top of the page you can view the administrative and license relevant information of the tenant.

3.  Choose the *Blocking and Deletion* list item.

4.  Choose a user type and enable it.

5.  Configure at least one of the periods: *Delete after* or *Block after*.

    > ### Remember:  
    > If you configure both *Block after* and *Delete after* periods, the *Delete after* period must longer than the *Block after* period.

6.  Configure the date after which the deletion script starts.

    The automatic configuration is based on the current date plus the days specified in the *Delete after* period. The deletion process starts from the chosen date and is executed nightly at 04:00 UTC.

7.  Save your changes.




<a name="loio744b2d0b557041dab64f8fe824304a68__postreq_pxc_s12_r4b"/>

## Next Steps

To unblock users, follow the procedure in [Unblock a User](unblock-a-user-d50eec9.md)

