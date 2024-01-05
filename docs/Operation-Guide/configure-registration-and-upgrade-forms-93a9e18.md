<!-- loio93a9e18e1674497ca69aeba76ed46fee -->

# Configure Registration and Upgrade Forms

In the administration console, you can configure which user attributes Identity Authentication sends to the service provider or client \(relying party\) to be displayed on application's registration and upgrade forms.

After the user has filled in the form, the information from these attributes is recorded in the user's profile. This is why these attributes are also called profile attributes and are handled by the profile services.

> ### Note:  
> The user ID attribute cannot be controlled by the user. Because of that it is not included on the registration and upgrade forms, but is available in the user's profile.



## Context

To configure the profile attributes, you need to specify which personal, company, and contact information the application prompts the user to provide when registering or upgrading. The information that the user has to provide depends on the status of the attribute \(required or optional\). You configure which attributes are displayed as required or optional in the administration console for SAP Cloud Identity Services.

The list of the attributes includes:

*PERSONAL INFORMATION*

-   `Salutation`
-   `First Name`
-   `Middle Name`
-   `Last Name`

    > ### Note:  
    > The `Last Name` attribute is always required for user registration or upgrade, so it is not configurable.

-   `Email`

    > ### Remember:  
    > The `Email` attribute is required for user registration or upgrade, and as so not configurable, if marked as required on tenant level. If `Email` is marked as not-required on tenant level, it becomes configurable, and must also be changed here.

-   `Phone`

    > ### Note:  
    > The `Phone` attribute becomes required and not configurable for user registration or upgrade, when *Phone Verification via SMS* is enabled. For more information, see [Configure Registration and Upgrade Forms](configure-registration-and-upgrade-forms-93a9e18.md).
    > 
    > If you disable *Phone Verification via SMS*, the `Phone` attribute remains required for user registration or upgrade. То make it optional, or remove it, follow the procedure in this document.

-   `Street Address`
-   `Street Address 2`
-   `City`
-   `Zip/Postal Code`
-   `Country`

    > ### Note:  
    > The `Country` parameter is required when the `Zip/Postal Code` is filled in by the user in the registration form. For example, this is the situation when both `Zip/Postal Code` and `Country` are optional, and the user fills in the `Zip/Postal Code` field. If the user deletes the information in the `Zip/Postal Code` the `Country` parameter becomes optional.

-   `State/Province`

    > ### Note:  
    > The `State/Province` attribute is configurable only if the `Country` attribute is enabled.


*COMPANY INFORMATION*

-   `Company`
-   `Street Address`
-   `Street Address 2`
-   `City`
-   `ZIP/Postal Code`
-   `Country`

    > ### Note:  
    > The `Country` parameter is required when the `Zip/Postal Code` is filled in by the user in the registration form. For example, this is the situation when both `Zip/Postal Code` and `Country` are optional, and the user fills in the `Zip/Postal Code` field. If the user deletes the information in the `Zip/Postal Code` the `Country` parameter becomes optional.

-   `State/Province`

    > ### Note:  
    > The `State/Province` attribute is configurable only if the `Country` attribute is enabled.

-   `Industry`
-   `Relationship`
-   `Job Function`

*CONTACT PREFERENCES*

-   `By Email`
-   `By Telephone`

> ### Note:  
> The *CONTACT PREFERENCES* attributes define if the self-registration form contains a section *Contact Preferences*. This section asks the user if he or she would like to be contacted by email or phone, or both.
> 
> The presence of this section depends also on the `Country` attribute. The legislation in some countries requires the user to explicitly agree that he or she would like to be contacted by email or phone, or both.
> 
> Based on the specific configuration, the following options are possible:
> 
> -   If one or both *CONTACT PREFERENCES* parameters are enabled, and both `Country` parameters are disabled the *Contact Preferences* section will appear in the registration form.
> -   If one or both `Country` parameters and one or both *CONTACT PREFERENCES* parameters are enabled, the *Contact Preferences* section will appear in the registration form if the user types at least one country which requires the user to explicitly agree that he or she would like to be contacted by email or phone, or both.
> -   If both *CONTACT PREFERENCES* parameters are disabled, the "Contact Preferences" section will not appear in the registration form.
> 
> For the full set of the countries that do not require the user to explicitly agree that he or she would like to be contacted by email or phone copy the respective URL listed below, replace `<tenant ID>` with your *Tenant ID*, and open the edited URL in a Web browser.
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Contact Preference
> 
> </th>
> <th valign="top">
> 
> Countries
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> By Email
> 
> </td>
> <td valign="top">
> 
> **`https://<tenant ID>.accounts.ondemand.com/md/implicitOptInEmailCountryKeys`** 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> By Telephone
> 
> </td>
> <td valign="top">
> 
> **`https://<tenant ID>.accounts.ondemand.com/md/implicitOptInTelefonCountryKeys`** 
> 
> </td>
> </tr>
> </table>

In addition to these profile attributes, the registration and upgrade forms include terms of use and privacy policy documents that are configured separately.

To configure profile attributes, proceed as follows:



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services.

2.  Under *Applications and Resources*, choose the *Applications* tile.

3.  Choose the application that you want to edit.

    > ### Note:  
    > Type the name of the application in the search field to filter the list items, or choose the application from the list on the left.
    > 
    > If you don’t have a created application in your list, you can create one. For more information, see [Create a New Application](create-a-new-application-0d4b255.md).

4.  Choose the *Authentication and Access* tab.

5.  Under *Authentication*, choose *User Attributes for Access*.

6.  Configure which attributes the form displays as required or optional, and save your selection.

    If the operation is successful, you receive the message ***Registration form updated***.

7.  **Optional:** To change the phone country selection, choose *Tenant Settings**Tenant Default Values*, select the desired country from the drop-down and save your changes.

    > ### Note:  
    > The phone country selection appears on the registration and upgrade forms, the verify phone screen, two-factor authentication with SMS screen, and also on the profile page.
    > 
    > The default value is United States.




<a name="loio93a9e18e1674497ca69aeba76ed46fee__postreq_wsz_wsp_zqb"/>

## Next Steps

Configure terms of use and privacy policy documents. For more information, see [Configuring Privacy Policies](configuring-privacy-policies-ed48466.md) and [Configuring Terms of Use](configuring-terms-of-use-61d3a86.md).

**Related Information**  


[Configuring User Attributes from the Identity Directory](configuring-user-attributes-from-the-identity-directory-d361407.md "Specify how the local user attributes, configured to be collected by the registration and upgrade forms, are sent to the application.")

[Configuring Privacy Policies](configuring-privacy-policies-ed48466.md "You can configure a custom privacy policy document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Configuring Terms of Use](configuring-terms-of-use-61d3a86.md "You can configure a custom terms of use document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Troubleshooting for Administrators](troubleshooting-for-administrators-f80beb5.md "This section is intended to help administrators deal with error messages in the administration console for SAP Cloud Identity Services.")

[Create a New Application](create-a-new-application-0d4b255.md "You can create a new application and customize it to comply with your company requirements.")

