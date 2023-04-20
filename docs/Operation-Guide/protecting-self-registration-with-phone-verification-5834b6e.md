<!-- loio5834b6e2e9224411a5c59e246f7b513e -->

# Protecting Self-Registration with Phone Verification

Tenant administrators can configure applications to require new self-registered users to verify themselves via SMS codes sent to their mobile phones.



## Context

Applications with self-registration process can verify newly created users via a code sent as an SMS to their mobile phones. The applications can therefore protect against users creating numerous dummy accounts.

Newly created users are required to provide their phone numbers during the self-registration process. For more information about how to allow self-registration, see [Configure User Access to the Application](configure-user-access-to-the-application-8b147c4.md).

Existing users are required to provide their phone numbers in the upgrade form.

> ### Remember:  
> Once the phone is verified, the user cannot change it any more on the profile page. This can be done by the administrator via the administration console. For more information, see [List and Edit User Details](list-and-edit-user-details-045cb01.md).

> ### Example:  
> Michael Adams is an administrator at retail company A. He has configured his system in such a way that users can register on their own and then purchase from the company’s site. He allows users to access his *Company A Purchasing* application by self-registration.
> 
> Michael also wants to restrict users to create dummy accounts. To do this, he configures Sinch Service and enables the *Phone Verification via SMS* option in the administration console for SAP Cloud Identity Services.
> 
> Donna Moore is a customer who wants to purchase goods from company A for the first time. When she accesses company A’s application, she is redirected to the company’s logon page. Because she is not registered yet, she has to choose the *Register* button to start the registration process. A registration form then appears, prompting Donna to enter her name, e-mail address, and telephone number, and to accept the organization's terms of use and privacy policy. The telephone number is required when the *Phone Verification via SMS* option is enabled. When she submits the form, she receives an e-mail with instructions on how to activate her registration. Once she has activated her registration, she receives a code via SMS. At the same time she is redirected to a page where she is prompted to verify her phone number by entering the code she received. Once she has verified the phone number, she is able to log on to the retailing application with her user credentials.
> 
> Julie Armstrong is a customer who has an account for company A, but she has never provided her phone number. When she accesses company A's application, she is redirected to the company’s logon page. After she provides her credentials, Julie is required to enter her phone number. She receives a code via SMS, and at the same time is redirected to a page where she is prompted to verify the phone by entering the code she received. Once she has verified the phone number, she is able to log on to the retailing application with her user credentials.

Configuration of phone verification in the administration console for SAP Cloud Identity Services comprises two consecutive steps. As a prerequisite, you must have an account in Sinch Service.

![](images/Image_Map_Phone_Verification_via_SMS_cebb851.png)

