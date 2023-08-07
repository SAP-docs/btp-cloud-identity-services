<!-- loio621017f2623c4ac59923e4ef531304d2 -->

# Configure Default Attributes for Subscribed Applications

Tenant administrator can configure default attributes in subscribed applications.



<a name="loio621017f2623c4ac59923e4ef531304d2__prereq_vmn_lx2_sxb"/>

## Prerequisites

You have a subscription to a multitenant application.



<a name="loio621017f2623c4ac59923e4ef531304d2__context_fq2_hyk_sxb"/>

## Context

You can configure the value of existing application-defined default attributes, like email, first name, last name, for example to values coming from the corporate identity provider \(IdP\), and add new attributes.​



<a name="loio621017f2623c4ac59923e4ef531304d2__steps_p4r_1tk_sxb"/>

## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application created from the multitenant application that you want to edit.

4.  Choose the *Trust* tab.

5.  Under *SINGLE SIGN-ON*, choose *Default Attributes*.

    Under *Application Attributes* you can see the attributes defined by the multitenant application.

6.  **Optional:** Under *Application Attributes*, set the new value for the attribute defined by the multitenant application.

    > ### Note:  
    > Press the button that appears next to the changed value to evert it to its default value defined in the multitenant application.

7.  **Optional:** Under *Custom Attributes*, add attributes with default values for the application created from the multitenant application.

8.  Save your configuration.

    If the operation is successful, you receive the message ***Default attributes updated***.


**Related Information**  


[Developing Multitenant Applications in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/developing-multitenant-applications-in-cloud-foundry-environment)

[Configure the Default Attributes Sent to the Application](configure-the-default-attributes-sent-to-the-application-a2f1e46.md "In addition to the user attributes, you can also configure attributes with default values for the application.")

