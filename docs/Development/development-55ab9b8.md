<!-- loio55ab9b85dcf445b3b538ef8b77544f45 -->

# Development

The developer guide is aimed mainly at organization developers who can implement configurations in addition to the ones in the administration console of Identity Authentication.Developers can use REST API services to configure various authentication and registration mechanisms for their applications. The applications that administrators configure use different application services for all user-related processes.



## Application Services

The application services are used by the cloud services and cloud applications to interact with Identity Authentication with regard to user records in the tenant.

The following APIs are offered to cloud applications:

-   An API to register users

    For more information, see [User Registration](user-registration-0aa433c.md)

-   An API to invite users

    For more information, see [Invitation REST API](invitation-rest-api-e55429f.md)

-   Identity Authentication implementation of the System for Cross-domain Identity Management \(SCIM\) REST API protocol.

    For more information, see [SCIM REST API \(Deprecated\)](scim-rest-api-deprecated-2f21568.md).

-   An API to change the predefined texts and messages for end-user screens available per tenant in the Identity Authentication.

    For more information, see [Change Tenant Texts REST API](change-tenant-texts-rest-api-66ad80a.md#loio66ad80a6bbaf4fc3911232f7cc9a7de6).

-   An API to change the predefined master data texts.

    For more information, see [Change Master Data Texts REST API](change-master-data-texts-rest-api-b10fc6a.md#loiob10fc6a9a37c488a82ce7489b1fab64c).


**Related Information**  


[Error and Success Codes](error-and-success-codes-7f87a75.md "This section is to help developers with solutions to the REST API response codes.")

[Configure Certificates for API Authentication](../Operation-Guide/configure-certificates-for-api-authentication-c408083.md "This document describes how developers configure the certificates used for authentication when the API methods and OpenID Connect scenarios of Identity Authentication are used.")

