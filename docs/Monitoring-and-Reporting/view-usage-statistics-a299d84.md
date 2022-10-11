<!-- loioa299d84aebe44e61ab93dcde160721d5 -->

# View Usage Statistics

You can view statistical information for a tenant in the administration console for Identity Authentication 



## Context

The *Reporting* view displays a chart of statistical information with the number of the user logon requests. A logon request is a single authentication request managed via Identity Authentication. Identity Authentication counts only one logon request per user per day. Logon requests are independent of the authentication mechanism and user type.

The default statistical information shows the usage of the bundled, charged and system applications for the last six months. You can customize what you see by requesting information about specific applications and modifying the period.

Identity Authentication keeps the usage statistics for three years.

> ### Note:  
> If you need statistics for the period before August 2015, you can report an incident on [SAP Support Portal Home](https://support.sap.com/en/index.html) with a component `BC-IAM-IDS`.



<a name="loioa299d84aebe44e61ab93dcde160721d5__steps_pm2_35m_tt"/>

## Procedure

1.  Access the tenant's administration console for Identity Authentication by using the console's URL.

    > ### Note:  
    > The URL has the following pattern:
    > 
    > `https://<tenant ID>.accounts.ondemand.com/admin`
    > 
    > *Tenant ID* is an automatically generated ID by the system. The first administrator created for the tenant receives an activation e-mail with a URL in it. This URL contains the *tenant ID*. For more information about your tenants, see [Viewing Assigned Tenants and Administrators](../viewing-assigned-tenants-and-administrators-f56e6f2.md).
    > 
    > If you have a configured custom domain, the URL has the following pattern: `<your custom domain>/admin`.

2.  Choose the *Reporting* tile.

3.  Specify the applications that you want to view from the *Logon counters* drop-down.

4.  Modify the statistics period.


