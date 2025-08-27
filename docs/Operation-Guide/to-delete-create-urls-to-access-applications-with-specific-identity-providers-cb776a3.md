<!-- loiocb776a3c45334ccbbbf91ed56369a5f3 -->

# TO DELETE: Create URLs to Access Applications with Specific Identity Providers

Enhance the user experience by eliminating the need for users to determine which identity provider to use. Users often don’t have the context to choose the correct identity providers.

Sometimes you have multiple identity providers in your landscape, whether they are corporate identity providers or your SAP Cloud Identity Services - Identity Authentication tenant. By providing your users with preconfigured URLs, you can direct them to authenticate with specific identity providers for specific applications.

How you prepare these URLs depends on whether the user starts at the identity provider or at the application. It's further modified by your use case. Some typical use cases are described as follows.



<a name="loiocb776a3c45334ccbbbf91ed56369a5f3__section_vyl_lz2_3gc"/>

## Opting for the Local Identity Provider

You can enable users that are stored in SAP Cloud Identity Services to log on with their Identity Authentication credentials. Thus, the employees log on to the application with their corporate credentials, while the external users, such as clients, partners, or SAP support users are authenticated by the local Identity Authentication tenant. Another example is if you're developing an application and you want to use a test user in the local identity provider instead of creating a test user in the corporate identity provider. The following figure illustrates this architecture.

  
  
**Sign On With the Local Identity Provider and not the Corporate Identity Provider**

![](images/Local_Sign_On_52ae59d.png "Sign On With the Local Identity Provider and not the Corporate Identity
					Provider")

> ### Example:  
> Example link:
> 
> `https://myapplication.cfapps.eu20-001.hana.ondemand.com?idp=https://my_sci_tenant.accounts.ondemand.com`
> 
> Example with local value:
> 
> `https://myapplication.cfapps.eu20-001.hana.ondemand.com?idp=local`
> 
> Example approuter link:
> 
> `https://approuter-myapplication.cfapps.eu20-001.hana.ondemand.com?sap_idp=https://my_sci_tenant.accounts.ondemand.com`



<a name="loiocb776a3c45334ccbbbf91ed56369a5f3__section_yvr_r1f_3gc"/>

## Multiple Corporate Identity Providers

If your application doesn't define rules to determine which identity provider a user authenticates with, SAP Cloud Identity Services offers the choice to your users. To avoid users choosing the wrong identity provider, you can limit their choices. The following figure illustrates this architecture.

  
  
**Help Direct Users to the Correct Identity Provider**

![](images/Multiple_Identity_Providers_2d59bbc.png "Help Direct Users to the Correct Identity Provider")

> ### Example:  
> Example link:
> 
> `https://myapplication.cfapps.eu20-001.hana.ondemand.com?idp=https://corp_idp_2.mydomain.com`
> 
> Example approuter link:
> 
> `https://approuter-myapplication.cfapps.eu20-001.hana.ondemand.com?sap_idp=https://corp_idp_2.mydomain.com`



<a name="loiocb776a3c45334ccbbbf91ed56369a5f3__section_hhy_qcf_3gc"/>

## Deep Hierarchy of Identity Providers

Your landscape has multiple levels of identity providers, perhaps through subsidiaries and conglomerate organizations. You want to direct your users to a specific identity provider, but this identity provider isn't directly known by your SAP Cloud Identity Services tenant. In such cases, provide the chain of identity providers to which the user must be redirected to reach the authenticating identity provider. The following figure illustrates this architecture.

  
  
**Deep Structure of Identity Providers**

![](images/Deep_Structure_of_Identity_Providers_a66a68c.png "Deep Structure of Identity Providers")

> ### Example:  
> Example link:
> 
> `https://myapplication.cfapps.eu20-001.hana.ondemand.com?idp=https://corp_idp_1.mydomain.com,corp_idp_2.mydomain.com`
> 
> Example approuter link:
> 
> `https://approuter-myapplication.cfapps.eu20-001.hana.ondemand.com?sap_idp=https://corp_idp_1.mydomain.com,corp_idp_2.mydomain.com`



<a name="loiocb776a3c45334ccbbbf91ed56369a5f3__section_pjv_qn2_3gc"/>

## Identity-Prover-Initiated Single Sign-On

> ### Restriction:  
> This option is only supported by SAML.

Identity-provider-initiated single sign-on \(IdP-initiated SSO\) is used for central portals in an enterprise from which users access applications. Users log on to the central portal first. You need to identify the identity provider the user must log on with. You also need to identify the service provider that the user is forwarded to after authenticating. The identity provider can be SAP Cloud Identity Services or a corporate identity provider or a hierarchy of corporate identity providers. Another unique aspect of IdP-initiated SSO is that the URL pattern you use is determined by SAP Cloud Identity Services. Otherwise, the URL is defined by the application. The following figure illustrates this architecture.

  
  
**Identity-Provider-Initiated Single Sign-On**

![](images/IdP-Initiated_SSO_7d739e6.png "Identity-Provider-Initiated Single Sign-On")

> ### Example:  
> Example SAML URL:
> 
> `https://my_sci_tenant.accounts.ondemand.com/saml2/idp/sso?sp=https://myapplication.cfapps.eu20-001.hana.ondemand.com&idp=https://corp_idp_1.mydomain.com`

