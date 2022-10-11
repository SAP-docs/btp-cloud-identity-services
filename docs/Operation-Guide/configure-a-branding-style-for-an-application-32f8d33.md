<!-- loio32f8d337f0894d269f5f89956803efac -->

# Configure a Branding Style for an Application

For the configuration of the branding style, you can choose a style for the end-user screens, such as sign in, registration, upgrade. You can also customize the buttons on these screens.



## Context

You can use one of the following styles:

-   *Horizon*:
    -   Standard - This predefined theme is an evolution of the SAP Fiori design system. It uses the the Horizon theme for the end-user screens. To learn more about the theme, see [SAP’s UI Technologies supporting the new Horizon visual theme of SAP Fiori](https://blogs.sap.com/2021/11/17/saps-ui-technologies-supporting-the-new-Horizon-visual-theme-of-SAP-Fiori/).

        You can customize the *Horizon* theme with instructions that appear on the sign in screen. To do this in the administration console:

        1.  Select *Application & Resources* \> *Applications* \> *<your application\>* \> *Branding and Layout* \> *Branding Style* \> *Horizon Theme* \> *Standard* \> *Save*.

        2.  Select *Tenant Texts* \> *\[logon.ui.login.instructions\] Key* \> *<your text\> Value* \> *Save*. For more information about the configuration of the tenant texts, see [Change Tenant Texts Via Administration Console](change-tenant-texts-via-administration-console-c24b1d0.md).

            The *Value* can include text and links.


        > ### Example:  

        ![](images/Horizon_Example_e72add1.png) 

    -   Custom Advanced - You can do advanced customization of the end-user screens, by uploading a CSS file and assign that file to an application. The CSS file overrides the default CSS file of the Horizon theme.

-   *Quartz*
    -   Standard - This predefined theme includes white and brand blue coloring based on SAP Fiori’s color palette.

        > ### Note:  
        > This is the default setting.

        > ### Example:  
        > ![](images/Quartz_Example_5b64afe.png)


    -   Custom Basic

        The custom basic theme allows you to configure a custom branding style for the buttons and information messages. It uses the Quartz theme for all other elements on the screens and error pages. For this configuration, you can customize:

        -   the top and bottom background color of the button
        -   the background color of the information message in the forms
        -   the button's and information message's border line color
        -   and the color of the button's text


    -   Custom Advanced

        You can do advanced customization of the end-user screens, by uploading a CSS file and assign that file to an application. The CSS file overrides the default CSS file for the Quartz theme.



