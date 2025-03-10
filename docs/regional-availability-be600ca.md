<!-- loiobe600ca4258241789a3ab4adc05e4849 -->

# Regional Availability

Tenants are deployed on the productive domains `accounts.ondemand.com` and `accounts.cloud.sap`.



The productive domain is available on a country/regional basis, where each country/region represents the locations of data centers. The productive domain represents the productive environment. It can be used by customer and partner accounts only.

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

Australia

</td>
<td valign="top">

`accounts.ondemand.com`

`accounts.cloud.sap`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

SAP / Azure

</td>
<td valign="top">

`157.133.168.73, 4.200.99.225`

</td>
<td valign="top">

`157.133.168.32/27, 130.214.240.32/27, 13.70.93.153/32`

</td>
<td valign="top">

`157.133.168.32-157.133.168.63, 130.214.240.32-130.214.240.63, 13.70.93.153-13.70.93.153`

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

`54.232.33.83, 54.207.203.50, 54.207.116.12, 52.67.178.118, 54.207.2.140, 54.94.82.121`

</td>
<td valign="top">

`18.228.21.223/32, 54.94.238.246/32, 54.94.95.71/32, 18.231.202.16/32, 18.230.68.1/32, 54.232.108.119/32`

</td>
<td valign="top">

`18.228.21.223-18.228.21.223, 54.94.238.246-54.94.238.246, 54.94.95.71-54.94.95.71, 18.231.202.16, 18.230.68.1-18.230.68.1, 54.232.108.119-54.232.108.119`

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

`121.91.104.198, 121.91.104.204`

</td>
<td valign="top">

`121.91.104.32/27, 121.91.106.0/28, 121.91.108.0/28`

</td>
<td valign="top">

`121.91.104.32 -121.91.104.63, 121.91.106.0-121.91.106.15, 121.91.108.0-121.91.108.15`

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

`3.125.77.225, 3.126.218.72, 3.64.78.167, 3.78.87.109, 18.192.230.105, 3.126.8.63`

</td>
<td valign="top">

`35.159.253.27/32, 18.192.171.14/32, 63.176.37.171/32, 3.65.162.41/32, 18.193.241.90/32, 18.199.198.32/32`

</td>
<td valign="top">

`35.159.253.27-35.159.253.27, 18.192.171.14-18.192.171.14, 63.176.37.171-63.176.37.171, 3.65.162.41-3.65.162.41, 18.193.241.90-18.193.241.90, 18.199.198.32-18.199.198.32`

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

`3.109.7.59, 52.66.148.12, 43.205.45.235, 3.6.178.171, 43.205.3.38, 3.6.141.120`

</td>
<td valign="top">

`3.108.210.169/32, 13.127.105.96/32, 13.232.175.70/32, 3.7.5.154/32, 43.205.169.10/32, 65.2.62.24/32`

</td>
<td valign="top">

`3.108.210.169-3.108.210.169, 13.127.105.96-13.127.105.96, 13.232.175.70- 13.232.175.70, 3.7.5.154-3.7.5.154, 43.205.169.10-43.205.169.10, 65.2.62.24-65.2.62.24`

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

`4.206.67.217/32, 4.205.230.84/32`

</td>
<td valign="top">

`4.206.67.217-4.206.67.217, 4.205.230.84-4.205.230.84`

</td>
</tr>
<tr>
<td valign="top">

Saudi Arabia

</td>
<td valign="top">

`sa2.accounts.ondemand.com` 

</td>
<td valign="top">

Dammam, Saudi Arabia, Middle East

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

`34.166.65.197, 34.166.56.10`

</td>
<td valign="top">

`34.166.19.58/32, 34.166.58.219/32, 34.166.53.185/32, 34.166.10.70/32`

</td>
<td valign="top">

`34.166.19.58-34.166.19.58, 34.166.58.219-34.166.58.219, 34.166.53.185-34.166.53.185, 34.166.10.70-34.166.10.70`

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

`18.138.93.141, 13.251.80.194, 52.221.66.111, 13.215.237.53, 13.251.19.109, 3.0.227.4`

</td>
<td valign="top">

`54.254.59.23/32, 52.76.191.74/32, 47.129.67.102/32, 18.140.41.153/32, 47.129.16.236/32, 13.213.203.26/32`

</td>
<td valign="top">

`54.254.59.23-54.254.59.23, 52.76.191.74-52.76.191.74, 47.129.67.102-47.129.67.102, 18.140.41.153-18.140.41.153, 47.129.16.236-47.129.16.236, 13.213.203.26-13.213.203.26`

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

`3.34.214.12, 52.78.91.176, 15.164.154.86, 3.35.109.127, 3.37.25.236, 15.164.195.144`

</td>
<td valign="top">

`3.39.112.56/32, 54.180.170.146/32, 3.38.127.188/32, 43.202.135.25/32, 3.36.27.20/32, 52.79.160.50/32`

</td>
<td valign="top">

`3.39.112.56-3.39.112.56, 54.180.170.146-54.180.170.146, 3.38.127.188-3.38.127.188, 43.202.135.25-43.202.135.25, 3.36.27.20-3.36.27.20, 52.79.160.50-52.79.160.50`

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

`20.250.104.188, 20.250.104.193`

</td>
<td valign="top">

`172.161.63.46/32, 172.161.59.62/32`

</td>
<td valign="top">

`172.161.63.46-172.161.63.46,`

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

SAP

</td>
<td valign="top">

`130.214.250.103, 130.214.250.118`

</td>
<td valign="top">

`130.214.80.0/26, 130.214.250.32/27`

</td>
<td valign="top">

`130.214.80.0-130.214.80.63, 130.214.250.32-130.214.250.63`

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

`52.143.72.52, 40.91.81.47`

</td>
<td valign="top">

`4.246.74.117/32, 13.66.186.117/32`

</td>
<td valign="top">

`4.246.74.117-4.246.74.117, 13.66.186.117-13.66.186.117/32`

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

`172.171.209.145/32, 172.190.167.36/32`

</td>
<td valign="top">

172.171.209.145-172.171.209.145, 172.190.167.36-172.190.167.36

</td>
</tr>
</table>

> ### Restriction:  
> The `accounts.cloud.sap` domain is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

> ### Note:  
> -   LB \(load balancer\) IPs - ingress, for incoming requests
> -   NAT \(network address translation\) IPs - egress, IPs for requests from Identity Authentication app.

**Related Information**  


[Product Details](product-details-4d404b1.md)

[Disaster Recovery/High Availability](disaster-recovery-high-availability-2c1a055.md "Disaster recovery (DR) and high availability (HA) are based on the capabilities of the underlying infrastructure.")

[Web-Based Logon Interface](web-based-logon-interface-8e40afc.md "Service providers that delegate authentication to Identity Authentication can use two types of visualization of the web-based user interfaces for the logon pages of their applications.")

[Browser Support](browser-support-0741076.md "Information on the supported browser version for the administration console, and the end user screens of SAP Cloud Identity Services.")

[Supported Languages](supported-languages-0ea634d.md "Information on the supported languages for the administration console, and the end user screens of Identity Authentication.")

[Accessibility Features in SAP Cloud Identity Services](accessibility-features-in-sap-cloud-identity-services-c7b544b.md "To optimize your experience of SAP Cloud Identity Services, SAP Cloud Identity Services tools provide features and settings that help you use the software efficiently.")

