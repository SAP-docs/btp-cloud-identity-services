<!-- loio5e98ecf5d0ae4a41b69d93bc4c27c976 -->

# Add Logon Overlays in Customer Applications

This document describes how service providers that delegate authentication to Identity Authentication can use embedded frames, also called overlays, for the logon pages of their applications.



<a name="loio5e98ecf5d0ae4a41b69d93bc4c27c976__prereq_ol4_hjt_hsb"/>

## Prerequisites

You have added the domains of the applications for which you want to use overlays as trusted in the administration console for SAP Cloud Identity Services. For more information, see [Configure Trusted Domains](../Operation-Guide/configure-trusted-domains-08fa1fe.md).



## Context

The use of overlays maintains the application context, by keeping the application page as dimmed background, to provide for minimum disturbance to the workflow. By default, after a successful logon via an overlay page, the application's parent page reloads. For more information how to configure that option, see [Enable or Disable Reload Parent Page Option](../Operation-Guide/enable-or-disable-reload-parent-page-option-0c0e9d2.md).

> ### Note:  
> When the application uses overlay for the logon page, but the client's browser doesn’t accept third party cookies, the logon page opens in fullscreen.
> 
> To open the logon page of the application in an overlay instead of in fullscreen when the browser is set not to accept third-party cookies, the user has to add an exception for the domain of this application. The users can consult the documentations of the different browsers for more information about how to enable third-party cookies for specific Web sites and domains.

To add a logon overlay into your application proceed as follows:



<a name="loio5e98ecf5d0ae4a41b69d93bc4c27c976__steps_fzg_2cg_5r"/>

## Procedure

1.  Include the following libraries to the landing page of your application:

    -   *jQuery*

        If you have already included *jQuery* you don’t need to do it again.

        You can download the *jQuery* from a Content Delivery Network \(CDN\), or you can use the following pattern:

        > ### Sample Code:  
        > ```
        > <script src="https://<tenant ID>.accounts.ondemand.com/ui/resources/javascripts/jquery.min.js"></script>
        > ```

    -   SAP\_IDS.js

        Use the following pattern:

        > ### Sample Code:  
        > ```
        > <script src="https://<tenant ID>.accounts.ondemand.com/ui/resources/javascripts/SAP_IDS.js"></script>
        > ```


    > ### Caution:  
    > Make sure that the reference to the javascript file is pointing to the same Identity Authentication tenant that is used for authentication of this application. Have this in mind when you migrate your applications from quality to productive environment, if different Identity Authentication tenants are used.

2.  Add a logon link.

    > ### Note:  
    > The logon link must be an HTML anchor with the following attributes:


    <table>
    <tr>
    <th valign="top">

    Attribute
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    rel
    
    </td>
    <td valign="top">
    
    IDS\_login
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    href
    
    </td>
    <td valign="top">
    
    -   points to an actual resource in your application that generates SAML 2.0 authentication request to Identity Authentication
    -   the name of the resource isn’t important


    
    </td>
    </tr>
    </table>
    
    > ### Sample Code:  
    > ```
    > <a href="/login.jspa" rel="IDS_Login">Log in</a>
    > ```




<a name="loio5e98ecf5d0ae4a41b69d93bc4c27c976__result_w32_3xc_g1b"/>

## Results

When the user chooses the logon link, the following happens:

-   If the user isn’t logged on, the log on overlay is displayed.
-   If the user is logged on to an application with the same Identity Authentication tenant, in other words he or she has an active application session, the user is automatically logged on to the second application.

> ### Caution:  
> The logon link should be visible only if the user doesn’t have an active application session.
> 
> If you still want to show the logon link when the user has an active application session, you must change the logic for the logonon link for this case. The logon link should not contain `rel="IDS_Login"` in this case. For example, the logic could be that, when the user chooses the logon link, he or she is directly redirected to the protected resource.



## Next Steps

Protect applications against clickjacking when using overlays. For more information, see [Configure Clickjacking Protection](configure-clickjacking-protection-af3712b.md).

<a name="concept_zws_kch_5r"/>

<!-- concept\_zws\_kch\_5r -->

## Further Options



## Locale

If the locale is known, this can be communicated to Identity Authentication by adding a locale parameter to *SAP\_IDS.js*.

> ### Sample Code:  
> ```
> <script src="https://<tenant ID>.accounts.ondemand.com/ui/resources/javascripts/SAP_IDS.js?locale=en_GB"></script>
> ```

> ### Note:  
> The locale parameter follows the Java specifications for a locale and must be of the format `ll_CC` where:
> 
> -   `ll` is the language two letter code in small letters
> 
> -   `CC` is the country \(region\) two letter code in capital letters



<a name="concept_zws_kch_5r__section_n2q_cns_frb"/>

## Token URL Separator

If your application is using overlays, you can configure the delimiter used in the token URL sent for the different application processes, such as forgot password, for example.

You can choose from:

-   `;` - parameter, the default configuration
-   `#` - fragment
-   `?/&` - query string parameter

**Procedure**

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.
3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](../Operation-Guide/create-a-new-application-0d4b255.md).

4.  Choose the *Branding and Layout* tab.
5.  Under *Email Configurations*, choose the *Token Url Separator* list item.
6.  Choose a deliminator from the list:
    -   `;` - parameter, the default configuration
    -   `#` - fragment
    -   `?/&` - query string parameter

7.  Save your selection.

