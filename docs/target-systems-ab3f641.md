<!-- loioab3f641552464c79b94d10b9205fd721 -->

# Target Systems

A target system is the connector used for writing entities.

Target systems are usually cloud systems, where Identity Provisioning creates or updates the entities read from the source system.

A target system can be connected to a single or multiple source systems. In the case of multiple source systems, we recommend that you run the provisioning jobs **successively** for each system, not simultaneously. This way, you'll avoid incorrect overwriting or merging of entity data, hence failed provisioning jobs.

![](images/IPS_Source_and_Target_Systems_841d159.png)

> ### Restriction:  
> By default, the maximum number of productive target systems you are allowed to add for your tenant is **50**. This restriction is valid for *Customer Managed* systems only.
> 
> If your business requires using more systems, create an incident for component *BC-IAM-IPS* to request them. Describe your scenarios and provide a reason why you need the additional systems.

**Related Information**  


[System Types](system-types-e59ae54.md "Identity Provisioning differentiates systems based on how they are created and what they are used for.")

