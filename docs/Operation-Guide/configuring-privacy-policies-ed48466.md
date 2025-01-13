<!-- loioed48466d770f4519aa23bba754851fbd -->

# Configuring Privacy Policies

You can configure a custom privacy policy document by creating a new document, adding and editing its language versions, and defining the document for an application.

Every time you want to update the privacy policy document you add a new language versions for the document.

Each privacy policy document can have one draft and one active version. You can view all language version in the administration console. Optionally you can edit the draft version of a document before making it an active version.

Once a privacy policy document is created it can't be renamed.

For each language version, you have to upload a text file. You can define a privacy policy document in the following languages:

Arabic, Azerbaijani, Bulgarian, Catalan, Chinese \(PRC\), Chinese \(Taiwan\), Croatian, Czech, Danish, Dutch, English \(United Kingdom\), English \(United States\), Estonian, Finnish, French \(Standard\), French \(Canada\), German \(Standard\), Greek, Hebrew, Hungarian, Italian, Japanese, Korean, Latvian, Malay, Norwegian, Polish, Portuguese \(Portugal\), Romanian, Russian, Serbian, Slovak, Slovenian, Spanish \(Spain\), Spanish \(Mexico\), Swedish, Thai, Turkish, Ukrainian, Vietnamese, Welsh.

The language is defined in the following order of importance:

-   By the `locale` parameter in the URL used for accessing the application.

    > ### Note:  
    > If the SP is configured to support a specific language, only this language is used by the application.

-   By the language of the application's browser.

    > ### Note:  
    > The application takes the browser language only if the SP's language is not selected, and the `locale` parameter isn’t set in the URL. The default browser setting is *English*.


> ### Note:  
> If there is only one language for the document, it is recommended to be *English \(United States\)*.
> 
> If the languages are more than one, one of them must be *English \(United States\)*.

To configure privacy policy in the administration console, do the following:

**Related Information**  


[Configuring Applications](configuring-applications-61ad3b0.md "This section describes how you can configure the user authentication, access to an application, and use a branding style in accordance with your company requirements. It also explains the trust configuration between Identity Authentication and a service provider or client (relying party).")

[Configuring Tenant Settings](configuring-tenant-settings-d4d6fdc.md "Initially, the tenants are configured to use default settings. This section describes how you as a tenant administrator can make custom tenant configurations.")

[Configuring Password Policies](configuring-password-policies-12b3395.md "Passwords for the authentication of users are subject to certain rules. These rules are defined in the password policy. Identity Authentication provides you with two predefined password policies, in addition to which you can create and configure up to three custom password policies.")

[Configuring Authorization Policies](configuring-authorization-policies-982ac5f.md "Authorization management enables SAP Cloud Identity Services administrators to use authorization policies, customize them, and assign them to users.")

[Configuring Terms of Use](configuring-terms-of-use-61d3a86.md "You can configure a custom terms of use document by creating a new document, adding and editing its language versions, and defining the document for an application.")

[Configuring Email Templates](configuring-email-templates-b2afbcd.md "Tenant administrators can use the default or a custom email template set for the application processes.")

[Managing Administrators](managing-administrators-786eea2.md "This section describes how, as a tenant administrator, you can list all administrators in the administration console for SAP Cloud Identity Services, add new administrators, and edit the administrator authorizations. You can also remove administrators.")

[Managing Users](managing-users-228428f.md "Tenant administrators can manage user accounts via the administration console for SAP Cloud Identity Services, and via APIs.")

[Managing Groups](managing-groups-ddd067c.md "Tenant administrators can create groups, and assign and unassign these groups to users via the administration console for SAP Cloud Identity Services.")

[Configuring Provisioning Systems](configuring-provisioning-systems-f149f76.md "Configure provisioning systems for synchronizing users and groups between business applications.")

[Configuring Real-Time Provisioning](configuring-real-time-provisioning-617dd4b.md "As a tenant administrator, you can configure real-time provisioning to immediately provision entities from source to target systems.")

[Configuring Social Identity Providers](configuring-social-identity-providers-17d400d.md "By configuring a social provider, users can log on to applications with their social media credentials by linking their accounts in Identity Authentication to the social media account.")

[Integrating with Existing Customer Landscape](integrating-with-existing-customer-landscape-cf29ea1.md "Identity Authentication can be integrated with already existing customer landscape and supports different types of delegated authentication.")

[Configuring External Authentication Providers](configuring-external-authentication-providers-4f02f94.md "Configure authentication providers in the administration console for SAP Cloud Identity Services to manage users from external providers.")

[Configuring OpenID Connect](configuring-openid-connect-a789c9c.md "You can use Identity Authentication for authentication in OpenID Connect protected applications.")

