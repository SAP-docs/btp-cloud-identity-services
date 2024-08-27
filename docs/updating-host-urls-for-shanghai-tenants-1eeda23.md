<!-- loio1eeda236f67f482bbb561f1b17532792 -->

# Updating Host URLs for Shanghai Tenants

If your Identity Authentication tenant host is in the Asia-Pacific region, precisely Shanghai \(China\), you must update it to the new host: `accounts.sapcloud.cn`.



<a name="loio1eeda236f67f482bbb561f1b17532792__context_psf_kqv_3nb"/>

## Context

The former domain on which you've accessed your Shanghai \(China\) tenants is: `accounts.ondemand.com`. This domain will soon stop working, thus we recommend that you start using the new one. Effective September 2020, tenants from Shanghai \(China\) should be accessed via the following domain: `accounts.sapcloud.cn`.

> ### Note:  
> The other productive domains, available on a country/regional basis, are working as usual.

The migration procedure for Identity Authentication tenants affects the following scenarios:

-   SAML 2.0 Application Configuration
-   OpenID Connect Application Configuration
-   Real-Time User Provisioning
-   Delegated Authentication
-   API Usage
-   IdP-Initated SSO

For more information about the migration procedure for SAP Cloud Identity Services - Identity Provisioning, see [Updating Host URLs for Shanghai Tenants](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/80563ee65d96451db3c063a083b199e6.html).

<a name="task_j5h_15t_3nb"/>

<!-- task\_j5h\_15t\_3nb -->

## SAML 2.0 Application Configuration



<a name="task_j5h_15t_3nb__context_bdy_34g_snb"/>

## Context

When you set the trust between Identity Authentication, acting as identity provider \(IdP\), and the service provider, make sure that you use the Identity Authentication metadata downloaded via the new host `https://<tenant Id>.accounts.sapcloud.cn/admin`.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services via the new URL `https://<tenant Id>.accounts.sapcloud.cn/admin`.

2.  Access *Applications and Resources* \> *Tenant Settings* \> *SAML 2.0 Configuration*.

3.  Download the new SAML metadata of Identity Authentication.

    > ### Note:  
    > If you do not have access to the trust configuration on the application side report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`.

4.  Configure the new metadata of the Identity Provider \(IdP\) on the application \(service provider\) side. See [Tenant SAML 2.0 Configurations](Operation-Guide/tenant-saml-2-0-configurations-e81a19b.md).

    If you have set trusts with more than one service provider, configure the metadata in every service provider. For more information about how to configure the metadata, see the documentation of the respective service providers.


<a name="task_xny_kvt_3nb"/>

<!-- task\_xny\_kvt\_3nb -->

## OpenID Connect Application Configuration



<a name="task_xny_kvt_3nb__context_z5k_dzg_snb"/>

## Context

If your application an OpenID Connect one, update the configurations in the administration console for SAP Cloud Identity Services to match the new host.



<a name="task_xny_kvt_3nb__steps_izw_mvt_3nb"/>

## Procedure

1.  In the administration console for SAP Cloud Identity Services, access *Applications and Resources* \> *Tenant Settings* \> *OpenID Connect Configuration*.

2.  Update the name of the identity provider to match the new host name \(https:// <tenant ID\>.accounts.sapcloud.cn\).

3.  Update the endpoints on the relying party \(RP\) side to match the new host.


<a name="task_ang_1zt_3nb"/>

<!-- task\_ang\_1zt\_3nb -->

## Real Time User Provisioning



<a name="task_ang_1zt_3nb__context_yfd_vhh_snb"/>

## Context

When you want to perform real-time provisioning through the administration console for SAP Cloud Identity Services, make sure you use the correct domain when you construct your OAuth URL and SCIM URL.



<a name="task_ang_1zt_3nb__steps_hkf_phv_3nb"/>

## Procedure

1.  Access theIdentity Authentication tenant via the new domain `<tenant Id>.accounts.sapcloud.cn`.

2.  In the administration console, access *User Provisioning*.

3.  Update the *host* part in the *SCIM URL* and *OAuth URL* of the Identity Provisioning target system with the new domain `dispatcher.cn1.platform.sapcloud.cn`. See [Real-Time Provisioning: Identity Authentication](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/70afd909734842b08ff8f1be5b01bc2a.html)

    SCIM URL Pattern: `https://ipsproxy<provider_account>-<consumer_subaccount>.<host>/ipsproxy/api/v1/systems/<Identity_Authentication_ID>/entities/user`

    OAuth URL Pattern: `https://oauthasservices-<consumer_subaccount>.<host>/oauth2/api/v1/token`


<a name="task_gml_yhv_3nb"/>

<!-- task\_gml\_yhv\_3nb -->

## Delegated Authentication



<a name="task_gml_yhv_3nb__context_k5q_s3h_snb"/>

## Context

In this scenario Identity Authentication acts as a proxy to the corporate identity provider.

When you set the trust between Identity Authentication, acting as a proxy\), and the corporate IdP, make sure that you use the Identity Authentication metadata downloaded via the new host `https://<tenant Id>.accounts.sapcloud.cn/admin`.

For more information about the scenario, [Corporate Identity Providers](Operation-Guide/corporate-identity-providers-19f3eca.md).



## Procedure

1.  Access theIdentity Authentication tenant via the new domain `<tenant Id>.accounts.sapcloud.cn/admin`.

2.  In the administration console, access *Applications and Resources* \> *Tenant Settings* \> *SAML 2.0 Configuration*.

3.  Download the new SAML metadata of the identity provider \(IdP\).

    > ### Note:  
    > If you don’t have access to the trust configuration on the application side report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`.

4.  Update the trust configuration on the corporate identity provider side.


<a name="task_b1d_llv_3nb"/>

<!-- task\_b1d\_llv\_3nb -->

## API Usage



<a name="task_b1d_llv_3nb__steps_dn4_wlv_3nb"/>

## Procedure

Use the new domain in the URLs. See [API Documentation](Development/api-documentation-cce8d64.md).

URL: https://<tenant ID\>.accounts.sapcloud.cn/<...\>

<a name="task_t4d_d4v_3nb"/>

<!-- task\_t4d\_d4v\_3nb -->

## Identity Authentication IdP-Initated SSO



<a name="task_t4d_d4v_3nb__steps_tcg_t4v_3nb"/>

## Procedure

Inform the end users about the new IdP-initiated links, updated with the new domain.

