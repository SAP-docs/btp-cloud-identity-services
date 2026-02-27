<!-- loioc233532da94b43798ac08abc058e849d -->

# Configure Form-Based OAuth Authentication

Configure Identity Provisioning to use form‑based OAuth 2.0 authentication to call SAP Ariba Applications APIs.

In this authentication scenario, the Identity Provisioning Service uses the OAuth 2.0 client credentials flow to obtain an access token from the Identity Authentication Service. The access token is retrieved using a form‑encoded request with a client ID and client secret that are generated for the Administration Console application of SAP Cloud Identity Services. This token is then used to call the next‑generation SCIM API of SAP Ariba Applications.



## Prerequisites

-   SAP Ariba Applications configuration exists in SAP Cloud Identity Services.

-   The required Provided APIs are configured for the SAP Ariba Applications application.

-   A source, target, or proxy system for SAP Ariba Applications is created in Identity Provisioning.




## Application Configuration

To enable token retrieval for the next-generation SCIM API of SAP Ariba Applications, a client ID and client secret must be generated in the Administration Console application under *Trust* \> *Application APIs* \> *Client Authentication*. These credentials are later used in the SAP Ariba Applications provisioning system properties for the technical user \(`User` and `Password`\).

For more information, see [Configure Secrets for API Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/auth-configure-secrets-for-api-authentication?version=Cloud).

Additional configuration in the Administration Console application requires establishing a dependency to the SAP Ariba Applications API. This is maintained under *Trust* \> *Application APIs* \> *Dependencies*, where the dependency name, the application, and the corresponding API are defined.

For more information, see [Integrating Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/integrating-applications?version=Cloud)[Configure Integration Between Applications](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/communicate-between-applications?version=Cloud).

The value provided for the *Dependency Name* is used to identify the API that the consumer application consumes.

> ### Note:  
> The dependency name must match the value of the *<system\_prefix\>*`.api.dependency.name` property in the provisioning system configuration.

For more information, see [List of Properties](../list-of-properties-d6f3577.md).



## Provisioning System Configuration

To configure your SAP Ariba Applications provisioning system, the following properties must be in place:

-   `User` - the Client ID generated in the Administration Console application.

-   `Password` - the Client Secret generated in the Administration Console application.

-   `ariba.applications.api.dependency.name` - the dependency name provided in the Administration Console application.

-   `AuthType` - set to Form

-   `Authentication` - set to BasicAuthentication

-   `OAuth2TokenServiceURL` - the `/oauth2/token` Service URL of Identity Authentication: `https://<Identity Authentication tenant host>/oauth2/token`


**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

[Search and Edit Systems](search-and-edit-systems-68a02be.md "You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.")

[Enable and Disable Systems](enable-and-disable-systems-89da372.md "You can enable and disable source and target systems in Identity Provisioning.")

[Export and Import Systems](export-and-import-systems-1de7de0.md "You can export and import source, target and proxy systems in Identity Provisioning.")

[Delete Systems](delete-systems-3a37213.md "You can delete a source, target, or proxy system from Identity Provisioning.")

[Update Connector Version](update-connector-version-8558733.md "Update a connector version to allow your provisioning system to use a new API.")

[Manage Properties](manage-properties-4e2bc9d.md "You can add, delete and modify properties for a system in Identity Provisioning.")

[Manage Transformations](manage-transformations-2d0fbe5.md "You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.")

[Manage Certificates](manage-certificates-86d06a0.md "Identity Provisioning supports certificate-based authentication for secure communication with the provisioning systems (connectors) provided by the service.")

[Manage Full and Delta Read](manage-full-and-delta-read-b7f817c.md "When you set up your systems and start a scheduled provisioning task, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. However, it may take a long time for every job to be executed.")

[Manage Deleted Entities](manage-deleted-entities-3d6bdf1.md "Manage deletion of entities (users or groups) in the target system after they have been deleted from the source system.")

[Connect to On-Premise Systems](connect-to-on-premise-systems-3f1cac2.md "Set up the connection to on-premise systems when your Identity Provisioning bundle or standalone tenant is running on the infrastructure of SAP Cloud Identity Services.")

[Start and Stop Provisioning Jobs](start-and-stop-provisioning-jobs-531a261.md "You can start and stop a provisioning job from the Identity Provisioning user interface (UI) or from an API client by using the Identity Provisioning tenant admin API.")

[Handle Rate Limits](handle-rate-limits-15f7f23.md "Identity Provisioning APIs implement rate limits to control the number of incoming requests for a given time.")

[Handle Failed Operations](handle-failed-operations-0382a0c.md "In certain cases, you can set a retry for a failed operation due to an occurred exception.")

[Reset Identity Provisioning Settings](reset-identity-provisioning-settings-8c7ba9a.md "Resetting your provisioning settings will delete all provisioning systems configured for your tenant, along with the related job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

