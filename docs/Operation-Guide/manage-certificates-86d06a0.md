<!-- loio86d06a0fadec41f0a53dd74b2e77fa96 -->

# Manage Certificates

Identity Provisioning supports certificate-based authentication for secure communication with the provisioning systems \(connectors\) provided by the service.



<a name="loio86d06a0fadec41f0a53dd74b2e77fa96__context_zhc_lzx_xrb"/>

## Context

Certificates can be used in outbound and inbound connections to Identity Provisioning.

In **outbound connections**, Identity Provisioning acts as an SSL client. The service generates an X.509 client certificate for mutual Transport Layer Security \(mTLS\) authentication against a given provisioning system acting as a server. The Identity Provisioning client certificate must be uploaded to the given provisioning system for configuring the certificate-based authentication there. For example, in SAP BTP ABAP Environment, the Identity Provisioning certificate must be uploaded to the communication user used in the communication arrangement.

> ### Note:  
> Outbound certificates generated by Identity Provisioning can also be used for OAuth authentication with provisioning systems. In OAuth certificate authentication, Identity Provisioning acts as a client application that sends requests to the URL of the access token provider service \(the authorization server\). The server issues access tokens following a successful authentication with certificate \(instead of using client ID and client secret\).
> 
> Currently, OAuth certificate authentication is supported for SAP Business Network and Procurement Data Warehouse.

In **inbound connections**, Identity Provisioning acts as a server whereas the given provisioning system acts as a client and must present a client certificate for establishing the communication to the service. Customers of bundle and standalone tenants running on SAP BTP, Neo environment import client certificates in the Identity Provisioning admin console. Customers of bundle and standalone tenants running on SAP Cloud Identity infrastructure upload the client certificates in the Identity Authentication admin console on the technical user of type *System*.

Inbound certificates are supported for source and proxy systems in the following scenarios: configuring proxy systems and real-time provisioning.

> ### Note:  
> Client certificate authentication is not supported for systems where the *ProxyType* and *ldap.proxyType* properties, required for the HTTP and LDAP connection respectively, are set to `OnPremise`.

> ### Note:  
> If you are using Identity Provisioning proxy and real-time provisioning scenarios, ensure that you trust the new root CA: DigiCert Global Root G2 as the old one DigiCert Global Root CA will be deprecated. For more information, see [Root Certificate Replacement](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Platform%20Domains&locale=en-US&version=Cloud).

**Related Information**  


[Add New Systems](add-new-systems-bd214dc.md "You can add source, target, and proxy systems for your provisioning scenarios.")

[Search and Edit Systems](search-and-edit-systems-68a02be.md "You can search and edit source, target, and proxy systems in the Identity Provisioning user interface.")

[Enable and Disable Systems](enable-and-disable-systems-89da372.md "You can enable and disable source and target systems in Identity Provisioning.")

[Export and Import Systems](export-and-import-systems-1de7de0.md "You can export and import source, target and proxy systems in Identity Provisioning.")

[Delete Systems](delete-systems-3a37213.md "You can delete a source, target, or proxy system from Identity Provisioning.")

[Update Connector Version](update-connector-version-8558733.md "Update a connector version to allow your provisioning system to use a new API.")

[Manage Properties](manage-properties-4e2bc9d.md "You can add, delete and modify properties for a system in Identity Provisioning.")

[Manage Transformations](manage-transformations-2d0fbe5.md "You can manage transformations with graphical and JSON text editor. Regardless of which one you choose, the following initial steps are the same.")

[Manage Full and Delta Read](manage-full-and-delta-read-b7f817c.md "When you set up your systems and start a scheduled provisioning task, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. However, it may take a long time for every job to be executed.")

[Manage Deleted Entities](manage-deleted-entities-3d6bdf1.md "Manage deletion of entities (users or groups) in the target system after they have been deleted from the source system.")

[Connect to On-Premise Systems](connect-to-on-premise-systems-3f1cac2.md "Set up the connection to on-premise systems when your Identity Provisioning bundle or standalone tenant is running on the infrastructure of SAP Cloud Identity Services.")

[Start and Stop Provisioning Jobs](start-and-stop-provisioning-jobs-531a261.md "You can start and stop a provisioning job from the Identity Provisioning user interface (UI) or from an API client by using the Identity Provisioning tenant admin API.")

[Handle Rate Limits](handle-rate-limits-15f7f23.md "Identity Provisioning APIs implement rate limits to control the number of incoming requests for a given time.")

[Handle Failed Operations](handle-failed-operations-0382a0c.md "In certain cases, you can set a retry for a failed operation due to an occurred exception.")

[Reset Identity Provisioning Settings](reset-identity-provisioning-settings-8c7ba9a.md "Resetting your provisioning settings will delete all provisioning systems configured for your tenant, along with the related job execution logs.")

[Reset Identity Provisioning System](reset-identity-provisioning-system-0bc1e53.md "Resetting an Identity Provisioning system (source or target) deletes all Identity Provisioning operational data.")

[Generate and Manage Certificates for Outbound Connection](generate-and-manage-certificates-for-outbound-connection-76867db.md "Identity Provisioning handles the following tasks related to X.509 client certificates for outbound connection: generating, automatic regenerating, activating, deactivating, downloading and deleting.")

[Manage Certificates for Inbound Connection](manage-certificates-for-inbound-connection-952e7c7.md "Identity Provisioning handles the following tasks related to X.509 client certificates for inbound connection: importing and deleting.")

