<!-- loiobe600ca4258241789a3ab4adc05e4849 -->

# Regional Availability

Tenants are deployed on the productive domain `accounts.ondemand.com`.



The productive domain represents the productive environment. It can be used by customer and partner accounts only.

The productive domain is available on a country/regional basis, where each country/region represents the locations of data centers.

A customer or partner account is associated with a particular data center and this is independent of your own location. For example, you could be located in North America, but operate your account in Europe. Thus, you use a data center that is situated in Europe.

> ### Note:  
> In cases of significant performance issues or latency, you can request a tenant migration to a new region by reporting an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`.

Country/regions with more than one data centers operate in high availability \(HA\) mode among the respective data centers. Tenants located in these country/regions are distributed among the data centers there.

The country/region, domain, data center, and IP address are listed below:

**Productive Environment**


<table>
<tr>
<th valign="top">

Country/Region

</th>
<th valign="top">

Domain

</th>
<th valign="top">

Data Center

</th>
<th valign="top">

Infrastructure

</th>
<th valign="top">

LB IPs

</th>
<th valign="top">

NAT IPs

</th>
<th valign="top">

First IP - Last IP

</th>
</tr>
<tr>
<td valign="top">

Australia/Japan

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Australia \(Sydney\) / Japan \(Tokyo\)

</td>
<td valign="top">

SAP

</td>
<td valign="top">

`157.133.168.73, 130.214.244.71`

</td>
<td valign="top">

`157.133.168.32/27, 130.214.240.32/27, 157.133.182.32/27, 130.214.244.32/27`

</td>
<td valign="top">

`157.133.168.32-157.133.168.63, 130.214.240.32-130.214.240.63, 157.133.182.32-157.133.182.63, 130.214.244.32-130.214.244.63`

</td>
</tr>
<tr>
<td valign="top">

Brazil

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

AWS

</td>
<td valign="top">

`54.232.33.83, 54.207.203.50, 54.207.116.12`

</td>
<td valign="top">

`18.228.75.28, 18.229.85.43, 54.232.93.209`

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

China

</td>
<td valign="top">

`accounts.sapcloud.cn` 

</td>
<td valign="top">

China

\(Shanghai\)

</td>
<td valign="top">

SAP

</td>
<td valign="top">

`157.133.186.67, 157.133.186.78, 121.91.104.198`

</td>
<td valign="top">

`157.133.186.32/27, 130.214.218.32/27, 121.91.104.32/27,121.91.106.0/28, 121.91.108.0/28`

</td>
<td valign="top">

`157.133.186.32-157.133.186.63, 130.214.218.32-130.214.218.63, 121.91.104.32 -121.91.104.63, 121.91.106.1 - 121.91.106.14, 121.91.108.1 - 121.91.108.14`

</td>
</tr>
<tr>
<td valign="top">

Switzerland

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Switzerland \(Zürich\)

</td>
<td valign="top">

Azure

</td>
<td valign="top">

`20.250.104.188, 20.250.104.193, 20.250.104.202`

</td>
<td valign="top">

`20.250.104.188/32, 20.250.104.193/32, 20.250.104.202/32`

</td>
<td valign="top">

`20.250.104.188-20.250.104.188, 20.250.104.193-20.250.104.193, 20.250.104.202-20.250.104.202`

</td>
</tr>
<tr>
<td valign="top">

Europe

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Germany \(Frankfurt\)

</td>
<td valign="top">

AWS

</td>
<td valign="top">

`3.125.77.225, 3.126.218.72, 3.64.78.167`

</td>
<td valign="top">

\* `52.57.77.94/32, 3.64.73.63/32, 18.192.191.4/32`

</td>
<td valign="top">

`52.57.77.94-52.57.77.94, 3.64.73.63-3.64.73.63, 18.192.191.4-18.192.191.4`

</td>
</tr>
<tr>
<td valign="top">

Europe

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Netherlands \(Amsterdam\) / Germany \(Frankfurt\)

</td>
<td valign="top">

SAP

</td>
<td valign="top">

`155.56.128.137, 157.133.170.72, 130.214.144.214`

</td>
<td valign="top">

`157.133.160.32/27, 130.214.226.32/27, 157.133.170.32/27, 130.214.230.32/27, 130.214.228.32/27`

</td>
<td valign="top">

`157.133.160.32-157.133.160.63, 130.214.226.32-130.214.226.63, 157.133.170.32-157.133.170.63, 130.214.230.32-130.214.230.63, 130.214.228.32-130.214.228.63`

</td>
</tr>
<tr>
<td valign="top">

India

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

India \(Mumbai\)

</td>
<td valign="top">

AWS

</td>
<td valign="top">

`3.109.7.59, 52.66.148.12, 43.205.45.235`

</td>
<td valign="top">

\*`43.205.77.24/32, 13.234.53.169/32, 65.0.145.55/32`

</td>
<td valign="top">

`43.205.77.24-43.205.77.24, 13.234.53.169-13.234.53.169, 65.0.145.55-65.0.145.55`

</td>
</tr>
<tr>
<td valign="top">

Japan

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Japan \(Tokyo\) / Japan \(Osaka\)

</td>
<td valign="top">

SAP

</td>
<td valign="top">

`157.133.182.83, 130.214.246.74`

</td>
<td valign="top">

`157.133.182.32/27, 130.214.244.32/27, 157.133.184.32/27, 130.214.246.32/27`

</td>
<td valign="top">

`157.133.182.32-157.133.182.63, 130.214.244.32-130.214.244.63, 157.133.184.32-157.133.184.63, 130.214.246.32-130.214.246.63`

</td>
</tr>
<tr>
<td valign="top">

North America \(Canada Central\)

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Canada \(Toronto\)

</td>
<td valign="top">

Azure

</td>
<td valign="top">

`20.151.9.145, 20.43.19.31, 52.139.41.10`

</td>
<td valign="top">

\* `20.151.9.145/32, 20.43.19.31/32, 52.139.41.10/32`

</td>
<td valign="top">

`20.151.9.145-20.151.9.145, 20.43.19.31-20.43.19.31, 52.139.41.10-52.139.41.10`

</td>
</tr>
<tr>
<td valign="top">

Saudi Arabia

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Saudi Arabia \(Riyadh, Dammam\)

</td>
<td valign="top">

SAP

</td>
<td valign="top">

`130.214.222.99, 130.214.248.94`

</td>
<td valign="top">

`130.214.222.32/27, 130.214.248.32/27`

</td>
<td valign="top">

`130.214.222.32-130.214.222.63, 130.214.248.32-130.214.248.63`

</td>
</tr>
<tr>
<td valign="top">

Singapore

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Singapore

</td>
<td valign="top">

AWS

</td>
<td valign="top">

`18.138.93.141, 13.251.80.194, 52.221.66.111`

</td>
<td valign="top">

\* `18.138.207.29/32, 54.169.200.14/32, 54.254.117.58/32`

</td>
<td valign="top">

`18.138.207.29-18.138.207.29, 54.169.200.14-54.169.200.14, 54.254.117.58-54.254.117.58`

</td>
</tr>
<tr>
<td valign="top">

South Korea

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Seoul \(South Korea\)

</td>
<td valign="top">

AWS

</td>
<td valign="top">

`3.34.214.12, 52.78.91.176, 15.164.154.86`

</td>
<td valign="top">

\* `13.125.196.137/32, 3.34.68.186/32, 52.79.155.87/32`

</td>
<td valign="top">

`13.125.196.137-13.125.196.137, 3.34.68.186-3.34.68.186, 52.79.155.87-52.79.155.87`

</td>
</tr>
<tr>
<td valign="top">

United Arab Emirates

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

UAE North \(Dubai\)

</td>
<td valign="top">

Azure

</td>
<td valign="top">

`20.196.2.107, 40.123.196.103, 40.123.215.159`

</td>
<td valign="top">

\* `20.196.2.107/32, 40.123.196.103/32, 40.123.215.159/32`

</td>
<td valign="top">

`20.196.2.107-20.196.2.107, 40.123.196.103-40.123.196.103, 40.123.215.159-40.123.215.159`

</td>
</tr>
<tr>
<td valign="top">

US \(North America East\)

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

United States \(Sterling\) / United States \(Colorado\)

</td>
<td valign="top">

SAP

</td>
<td valign="top">

`157.133.166.69, 130.214.207.198`

</td>
<td valign="top">

`157.133.166.32/27, 130.214.234.32/27, 157.133.176.32/27, 130.214.242.32/27`

</td>
<td valign="top">

`157.133.166.32-157.133.166.63, 130.214.234.32-130.214.234.63, 157.133.176.32-157.133.176.63, 130.214.242.32-130.214.242.63```

</td>
</tr>
<tr>
<td valign="top">

US West

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

West US 2

</td>
<td valign="top">

Azure

</td>
<td valign="top">

`52.143.72.52, 40.91.81.47, 52.143.74.249`

</td>
<td valign="top">

\* `20.51.113.99/32, 20.57.161.219/32, 20.57.185.171/32`

</td>
<td valign="top">

`20.51.113.99-20.51.113.99, 20.57.161.219-20.57.161.219, 20.57.185.171-20.57.185.171`

</td>
</tr>
</table>

**Trial Environment**


<table>
<tr>
<th valign="top">

Country/Region

</th>
<th valign="top">

Domain

</th>
<th valign="top">

Data Center

</th>
<th valign="top">

Infrastructure

</th>
<th valign="top">

LB IPs

</th>
<th valign="top">

NAT IPs

</th>
<th valign="top">

First IP - Last IP

</th>
</tr>
<tr>
<td valign="top">

US East

</td>
<td valign="top">

`trial-accounts.ondemand.com` 

</td>
<td valign="top">

East US

</td>
<td valign="top">

Azure

</td>
<td valign="top">

`20.62.179.159, 20.62.181.214, 20.62.180.136`

</td>
<td valign="top">

`20.62.179.159/32, 20.62.181.214/32, 20.62.180.136/32`

</td>
<td valign="top">

`20.62.179.159-20.62.179.159, 20.62.181.214-20.62.181.214, 20.62.180.136-20.62.180.136`

</td>
</tr>
</table>

> ### Restriction:  
> The `accounts.cloud.sap` domain is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

> ### Note:  
> -   LB \(load balancer\) IPs - ingress, for incoming requests
> -   NAT \(network address translation\) IPs - egress, IPs for requests from Identity Authentication app.
> -   \* These IPs are subject to change.

**Related Information**  


[Product Details](product-details-4d404b1.md)

[Tenant Model and Licensing](tenant-model-and-licensing-93160eb.md "This document provides information about the tenant model, tenant licensing, and obtaining a tenant of Identity Authentication.")

[Web-Based Logon Interface](web-based-logon-interface-8e40afc.md "Service providers that delegate authentication to Identity Authentication can use two types of visualization of the web-based user interfaces for the logon pages of their applications.")

[Disaster Recovery/High Availability](disaster-recovery-high-availability-2c1a055.md "Disaster recovery (DR) and high availability (HA) are based on the capabilities of the underlying infrastructure.")

[Browser Support](browser-support-0741076.md "Information on the supported browser version for the administration console, and the end user screens of SAP Cloud Identity Services.")

[Supported Languages](supported-languages-0ea634d.md "Information on the supported languages for the administration console, and the end user screens of Identity Authentication.")

[Accessibility Features in SAP Cloud Identity Services](accessibility-features-in-sap-cloud-identity-services-c7b544b.md "To optimize your experience of SAP Cloud Identity Services, SAP Cloud Identity Services tools provide features and settings that help you use the software efficiently.")

