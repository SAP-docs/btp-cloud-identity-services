<!-- loio108607a9d90b4712a1acb6e179ffeddf -->

# Social Authentication



<a name="loio108607a9d90b4712a1acb6e179ffeddf__context_gnk_rrg_vgb"/>

## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) region.

<a name="xxx"/>

<!-- xxx -->

## Log on with a Social Provider Account

You can log on to applications that use Identity Authentication via your accounts in Twitter, Facebook, LinkedIn, or Google.



## Prerequisites

The applications must be configured to allow logon via social networks.



## Context

Using the social network authentication, you link your Identity Authentication account with your social network account or accounts. After the initial setup, when you link the accounts, you can log on to the applications with your social network credentials.

Identity Authentication has access to the following data from the social providers:


<table>
<tr>
<th valign="top">

Social Identity Provider

</th>
<th valign="top">

Data Used by Identity Authentication 

</th>
</tr>
<tr>
<td valign="top">

Apple

</td>
<td valign="top">

ID of your user - used to link your Apple account with your Identity Authentication account

</td>
</tr>
<tr>
<td valign="top">

Facebook

</td>
<td valign="top">

-   ID of your user - used to link your Facebook account with your Identity Authentication account

-   your display name - used to prefill the registration form in case of non-existing user




</td>
</tr>
<tr>
<td valign="top">

Google

</td>
<td valign="top">

-   ID of your user - used to link your Google account with your Identity Authentication account

-   your display name, first name, and last name - used to prefill the registration form in case of non-existing user




</td>
</tr>
<tr>
<td valign="top">

LinkedIn

</td>
<td valign="top">

-   ID of your user - used to link your LinkedIn account with your Identity Authentication account

-   your first name and last name - used to prefill the registration form in case of non-existing user




</td>
</tr>
<tr>
<td valign="top">

Twitter

</td>
<td valign="top">

-   ID of your user - used to link your Twitter account with your Identity Authentication account

-   your display name - used to prefill the registration form in case of non-existing user

-   your logon name




</td>
</tr>
</table>

This data is used for the initial linking of your Identity Authentication account with the social network account. Later, if you update the personal information in your social account, the updated information will not be copied by Identity Authentication.

To link your Identity Authentication account with a social network account, proceed as follows:



<a name="xxx__steps_xwd_m2g_pt"/>

## Procedure

1.  Access the application's logon page.

2.  Choose the icon of the social network provider you want to log on with.

    > ### Note:  
    > Which social networks are displayed on the page depends on the application.

3.  Sign in to your social network account.

4.  Choose one of the following options:

    -   Link your Identity Authentication account with your social network account.
    -   Create a new Identity Authentication account that will be linked with your social network account.

        > ### Note:  
        > This option appears only for applications that allow user registration.





## Results

Once you allow Identity Authentication to link your account with the social providers' accounts, you can log on to the applications via the social providers.

<a name="yyy"/>

<!-- yyy -->

## Unlink a Social Provider Account

You can unlink your social provider account via the profile page.



## Context

To remove your social network logon information from your Identity Authentication account, proceed as follows:



<a name="yyy__steps_social_auth"/>

## Procedure

1.  Access the profile page.

    > ### Note:  
    > If you don't know the URL of your profile page, contact your system administrator.

2.  Press *Edit* under *Social Sign-On*.

3.  Press *Unlink* to remove your social network logon information from your account.

    If the operation is successful, the system displays the message *Profile updated* .


