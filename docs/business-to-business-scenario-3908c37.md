<!-- loio3908c37546cf4e3982145c4181df88be -->

# Business-to-Business Scenario

The business-to-business scenario is related to services for business partners. Unlike the business-to-consumer scenario, consumer self-registration is not allowed, and the administrator of the company is usually the one that triggers the user registration process.

The administrator invites partners or registers them on their behalf.

This scenario includes the following features:

-   Authentication with user name and password
-   A secure SSO to cloud applications
-   Social sign-on to cloud applications

    > ### Note:  
    > The content in this section is not relevant for China \(Shanghai\) region.

-   Invitation of partners by administrators
-   On-behalf registration of partners by administrators
-   Branding elements on all the forms for logon, password update, and account activation
-   Customized privacy policy and terms of use documents
-   Partner security policy
-   User import and export

> ### Example:  
> Donna Moore is a tenant administrator at company A. This company is a goods and services retailer. She would like to invite five transportation companies to join her organization in helping the distribution of goods and services to distant locations. The distributors will purchase from the *Company A Distribution* application. For this purpose, Donna registers these distributors on their behalf, logs on to the administration console for SAP Cloud Identity Services, navigates to *Applications* \> *Company A Distribution* page, and chooses *Authentication and Access* \> *User Application Access*. She selects the *Private* radio button in order to restrict access to just these users. The partners then activate their registration via the on-behalf registration email and can log on to the *Company A Distribution* application.
> 
> ![](images/Business-to-Business_Scenario_05f5abe.png)
> 
> 1.  Invites or registers partner.
> 2.  Activates account.
> 3.  Provides credentials.
> 4.  Delegates authentication.
> 5.  Confirms authentication.

**Related Information**  


[Business-to-Consumer Scenario](business-to-consumer-scenario-fd11ee2.md "The business-to-consumer scenario is related to any actions performed by the consumer, such as registration to applications and consumer retailing. In this scenario, administrators facilitate the consumer processes, but they do not act on the consumer's behalf.")

[Business-to-Employee Scenario](business-to-employee-scenario-3aecb4c.md "The business-to-employee scenario is related to services for employees of an organization. Employees can access various applications with one logon. Furthermore, administrators can upload employees data by using the user import functionality.")

[Centralized Provisioning with Identity Directory](centralized-provisioning-with-identity-directory-9d0235c.md "Identity Directory is the persistency layer of SAP Cloud Identity Services, providing a central place for storing and managing users and groups. You can use it in centralized provisioning scenarios for managing user access to SAP cloud applications from a single, central location.")

[Central Store-Based Provisioning](central-store-based-provisioning-33eae39.md "Central store-based provisioning enables the automatic provisioning of application-specific groups from the Identity Directory to the target systems whenever changes occur. These changes include user assignments or modifications of group attributes.")

[Administration](Operation-Guide/administration-6a8e67c.md "The SAP Cloud Identity Services administration and configuration tasks are intended for administrators. They include configuring tenant settings, applications, authorization policies and provisioning, as well as managing users and groups, to ensure proper operations.")

[Development](Development/development-55ab9b8.md "The developer guide is aimed mainly at organization developers who can implement configurations in addition to the ones in the administration console of Identity Authentication.")

[Configure User Access to the Application](Operation-Guide/configure-user-access-to-the-application-8b147c4.md "You can configure public access to the application allowing self-registration, or you can restrict the access to existing users or users registered by an application.")

